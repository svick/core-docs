---
title: .NET Core additional tools
description: An overview of the additional tools that support and extend .NET Core functionality.
author: mlacouture
ms.author: johalex
ms.date: 01/19/2018
ms.custom: mvc
---
# .NET Core additional tools

This section compiles a list of tools that support and extend the .NET Core functionality, in addition to the [.NET Core command-line interface (CLI)](../tools/index.md) tools.

## [WCF Web Service Reference tool](wcf-web-service-reference-guide.md)

The WCF (Windows Communication Foundation) Web Service Reference is a Visual Studio connected service provider that made its debut in [Visual Studio 2017 version 15.5](https://visualstudio.microsoft.com/news/releasenotes/vs2017-relnotes#WCFTools). This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file, and generates a source file compatible with .NET Core, defining a WCF proxy class with methods that you can use to access the web service operations.

## [WCF dotnet-svcutil tool](dotnet-svcutil-guide.md)

The WCF (Windows Communication Foundation) dotnet-svcutil tool is a .NET Core CLI tool that retrieves metadata from a web service on a network location or from a WSDL file, and generates a source file compatible with .NET Core, defining a WCF proxy class with methods that you can use to access the web service operations. 
The **dotnet-svcutil** tool is an alternative option to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider which first shipped with Visual Studio 2017 v15.5. The **dotnet-svcutil** tool as a .NET Core CLI tool, is available cross-platform on Linux, macOS, and Windows.

## [XML Serializer Generator](xml-serializer-generator.md)

Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the solution for .NET Core and .NET Standard libraries. It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.