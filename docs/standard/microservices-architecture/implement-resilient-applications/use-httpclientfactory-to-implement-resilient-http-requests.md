---
title: Use HttpClientFactory to implement resilient HTTP requests
description: HttpClientFactory is an opinionated factory, available since .NET Core 2.1, for creating `HttpClient` instances to be used in your applications. 
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 07/03/2018
---
# Use HttpClientFactory to implement resilient HTTP requests

`HttpClientFactory` is an opinionated factory, available since .NET Core 2.1, for creating `HttpClient` instances to be used in your applications. 

## Issues with the original HttpClient class available in .NET Core

The original and well-known [HttpClient](https://docs.microsoft.com/dotnet/api/system.net.http.httpclient?view=netstandard-2.0) class can be easily used, but in some cases, it is not being properly used by many developers. 

As a first issue, while this class is disposable, using it with the `using` statement is not the best choice because even when you dispose `HttpClient` object, the underlying socket is not immediately released and can cause a serious issue named ‘sockets exhaustion’. For more information about this issue, see [You're using HttpClient wrong and it is destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/) blog post.

Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application. Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads. That issue will result in `SocketException` errors. Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](https://docs.microsoft.com/dotnet/csharp/tutorials/console-webapiclient). 

But there’s a second issue with `HttpClient` that you can have when you use it as singleton or static object. In this case, a singleton or static `HttpClient` doesn't respect DNS changes, as explained in this [issue at the .NET Core GitHub repo](https://github.com/dotnet/corefx/issues/11224). 

To address those mentioned issues and make the management of `HttpClient` instances easier, .NET Core 2.1 offers a new `HttpClientFactory` that can also be used to implement resilient HTTP calls by integrating Polly with it.   

## What is HttpClientFactory

`HttpClientFactory` is designed to:

- Provide a central location for naming and configuring logical HttpClients. For example, you may configure a client (Service Agent) that is pre-configured to access a specific microservice.
- Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly’s policies for resiliency.
- `HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests. You register http clients into the factory plus you can use a Polly handler that allows Polly policies to be used for Retry, CircuitBreakers, etc.
- Manage the lifetime of HttpClientMessageHandlers to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself. 

## Multiple ways to use HttpClientFactory

There are several ways that you can use `HttpClientFactory` in your application:

- Use `HttpClientFactory` Directly
- Use Named Clients
- Use Typed Clients
- Use Generated Clients

For the sake of brevity, this guidance shows the most structured way to use `HttpClientFactory` that is to use Typed Clients (Service Agent pattern), but all options are documented and are currently listed in this [article covering HttpClientFactory usage](https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?#consumption-patterns).  

## How to use Typed Clients with HttpClientFactory

The following diagram shows how Typed Clients are used with HttpClientFactory.

![Diagram with an MVC controller using an injected ClientService, which internally is using a configured HttpClient by HttpClientFactory and Polly's policies](./media/image3.5.png)

**Figure 10-4**. Using `HttpClientFactory`with Typed Client classes.

First, setup `HttpClientFactory` in your application. Add a reference to the `Microsoft.Extensions.Http` package which includes the `AddHttpClient()` extension method for `IServiceCollection`. This extension method registers the `DefaultHttpClientFactory` to be used as a singleton for the interface `IHttpClientFactory`. It defines a transient configuration for the `HttpMessageHandlerBuilder`. This message handler (`HttpMessageHandler` object), taken from a pool, is used by the `HttpClient` returned from the factory.

In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services) 
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

Just by adding your typed client classes with AddHttpClient(), whenever you use the `HttpClient` object that will be injected to your class through its constructor, that `HttpClient` object will be using all the configuration and policies provided. In the next sections, you will see those policies like Polly’s retries or circuit-breakers.

### HttpClient lifetimes

Each time you get an `HttpClient` object from IHttpClientFactory, a new instance of an `HttpClient` is returned. There will be an HttpMessageHandler** per named of typed client. `IHttpClientFactory` will pool the HttpMessageHandler instances created by the factory to reduce resource consumption. An HttpMessageHandler instance may be reused from the pool when creating a new `HttpClient` instance if its lifetime hasn't expired.

Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays. Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.

The HttpMessageHandler objects in the pool have a lifetime that is the length of time that an HttpMessageHandler instance in the pool can be reused. The default value is two minutes, but it can be overridden per named or typed client basis. To override it, call SetHandlerLifetime() on the IHttpClientBuilder that is returned when creating the client, as shown in the following code.

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client 
services.AddHttpClient<ICatalogService, CatalogService>()
                 .SetHandlerLifetime(TimeSpan.FromMinutes(5));  
```

Each typed client or named client can have its own configured handler lifetime value. Set the lifetime to InfiniteTimeSpan to disable handler expiry.

### Implement your Typed Client classes that use the injected and configured HttpClient

As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like ‘BasketService’, ‘CatalogService’, ‘OrderingService’, etc. – A typed client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service. For example:

```csharp
public class CatalogService : ICatalogService
{
    private readonly HttpClient _httpClient;
    private readonly string _remoteServiceBaseUrl;

    public CatalogService(HttpClient httpClient)
    {
        _httpClient = httpClient;
    }

    public async Task<Catalog> GetCatalogItems(int page, int take, 
                                               int? brand, int? type)
    {
        var uri = API.Catalog.GetAllCatalogItems(_remoteServiceBaseUrl, 
                                                 page, take, brand, type);

        var responseString = await _httpClient.GetStringAsync(uri);

        var catalog = JsonConvert.DeserializeObject<Catalog>(responseString);
        return catalog;
    }
}
```

The typed client (CatalogService in the example) is activated by DI (Dependency Injection), meaning that it can accept any registered service in its constructor, in addition to HttpClient.

A typed client is, effectively, a transient object, meaning that a new instance is created each time one is needed and it will receive a new `HttpClient` instance each time it is constructed. However, the HttpMessageHandler objects in the pool are the objects that are reused by multiple Http requests.

### Use your Typed Client classes

Finally, once you have your type classes implemented and have them registered with AddHttpClient(), you can use it anywhere you can have services injected by DI, for example in any Razor page code or any controller of an MVC web app, like in the following code from eShopOnContainers.

```csharp
namespace Microsoft.eShopOnContainers.WebMVC.Controllers
{
    public class CatalogController : Controller
    {
        private ICatalogService _catalogSvc;

        public CatalogController(ICatalogService catalogSvc) => 
                                                           _catalogSvc = catalogSvc;

        public async Task<IActionResult> Index(int? BrandFilterApplied, 
                                               int? TypesFilterApplied, 
                                               int? page, 
                                               [FromQuery]string errorMsg)
        {
            var itemsPage = 10;
            var catalog = await _catalogSvc.GetCatalogItems(page ?? 0, 
                                                            itemsPage, 
                                                            BrandFilterApplied, 
                                                            TypesFilterApplied);
            //… Additional code
        }

        }
}
```

Until this point, the code shown is just performing regular Http requests, but the ‘magic’ comes in the following sections where, just by adding policies and delegating handlers to your registered typed clients, all the Http requests to be done by `HttpClient` will behave taking into account resilient policies such as retries with exponential backoff, circuit breakers, or any other custom delegating handler to implement additional security features, like using auth tokens, or any other custom feature. 


## Additional resources

-   **Using HttpClientFactory in .NET Core 2.1**
    [*https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1*](https://docs.microsoft.com/aspnet/core/fundamentals/http-requests?view=aspnetcore-2.1)


-   **HttpClientFactory GitHub repo**

    [*https://github.com/aspnet/HttpClientFactory*](https://github.com/aspnet/HttpClientFactory)



>[!div class="step-by-step"]
[Previous] (explore-custom-http-call-retries-exponential-backoff.md)
[Next] (implement-http-call-retries-exponential-backoff-polly.md)
