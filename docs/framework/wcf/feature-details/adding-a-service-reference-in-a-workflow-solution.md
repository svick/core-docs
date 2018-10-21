---
title: "Adding a Service Reference in a Workflow Solution"
ms.date: "03/30/2017"
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
---
# Adding a Service Reference in a Workflow Solution

Adding a service reference in a workflow application works a little differently than a regular WCF application. When you select **Add > Service Reference** and specify the URL to the service, the metadata is downloaded and custom activities are generated that allow you to call the WCF service or WCF workflow service you added a reference to. After adding a service reference, rebuild the solution so the generated activities are built. They will then appear in the workflow designer toolbox. Note however, that this will only work if you are adding a service reference within a workflow solution. The following web cast shows how to add a service reference in other types of projects: [Calling a WCF Service from a Workflow in a Web Project](https://go.microsoft.com/fwlink/?LinkId=207725).

Adding two or more service references to services that contain the same operation name will cause a problem. The generated activities will call only the first service operation. To work around this issue rename the service operations so they are different or change the endpoint configuration name within each generated activity.

## See Also

- [Workflow Services](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Calling a WCF Service from a Workflow in a Web Project](https://go.microsoft.com/fwlink/?LinkId=207725)
