---
title: "WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) Method"
ms.date: "03/30/2017"
ms.technology: dotnet-standard
dev_langs: 
  - "csharp"
  - "vb"
api_name: 
  - "System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream"
api_location: 
  - "System.Runtime.WindowsRuntime.dll"
ms.assetid: dcc72283-caed-49ee-b45d-ccaf94e97129
author: "mairaw"
ms.author: "mairaw"
---
# WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) Method

[Supported in the .NET Framework 4.5.1 and later versions]

Converts the specified stream to a random access stream.

**Namespace:** <xref:System.IO?displayProperty=nameWithType>
**Assembly:** System.Runtime.WindowsRuntime (in System.Runtime.WindowsRuntime.dll)

## Syntax

```csharp
[CLSCompliantAttribute(false)]
public static IRandomAccessStream AsRandomAccessStream(Stream stream)
```

```vb
'Declaration
<ExtensionAttribute> _
<CLSCompliantAttribute(False)> _
Public Shared Function AsRandomAccessStream ( _
        stream As Stream) As IRandomAccessStream
```

## Parameters

`stream`

Type: <xref:System.IO.Stream?displayProperty=nameWithType>  
The stream to convert.

## Return Value

Type: <xref:Windows.Storage.Streams.RandomAccessStream>  
A [!INCLUDE[wrt](../../../includes/wrt-md.md)] random access stream, which represents the converted stream.

## Exceptions

|Exception|Condition|
|---------------|---------------|
|<xref:System.NotSupportedException>|The stream to convert does not support seeking.|

## Remarks

This extension method is available only when you develop Windows Store apps. This method provides a convenient way of working with streams in Windows Store apps. The .NET Framework stream you want to convert must support seeking. For more information, see the <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> method.

> [!IMPORTANT]
> This API is supported in the .NET Framework 4.5.1 and later versions, but not in version 4.5.

## Version Information

**.NET for Windows Store apps**

Supported in: Windows 8.1

## See also

-[System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions(v=vs.110).aspx)
-[How to: Convert Between .NET Framework Streams and Windows Runtime Streams](../io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)
