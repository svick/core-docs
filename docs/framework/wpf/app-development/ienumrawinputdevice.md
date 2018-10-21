---
title: "IEnumRAWINPUTDEVICE"
ms.date: "03/30/2017"
helpviewer_keywords: 
  - "IEnumRAWINPUTDEVICE interface [WPF]"
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
---
# IEnumRAWINPUTDEVICE
This interface enumerates the raw input devices, and is only used by PresentationHost.exe.  
  
> [!NOTE]
>  This API is only intended and supported for use on the local client machine  
  
## Members  
  
|Member|Description|  
|------------|-----------------|  
|[IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md)|Enumerates the next `celt` elements (that is, RAWINPUTDEVICE structures) in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.|  
|[IEnumRAWINPUTDEVIC:Skip](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-skip.md)|Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) will not return those elements.|  
|[IEnumRAWINPUTDEVIC:Reset](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-reset.md)|Resets the enumeration sequence to the beginning.|  
|[IEnumRAWINPUTDEVIC:Clone](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-clone.md)|Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.|  
  
## See Also  
 [About Raw Input](https://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/aboutrawinput.asp)
