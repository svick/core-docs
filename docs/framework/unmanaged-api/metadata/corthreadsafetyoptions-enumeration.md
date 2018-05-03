---
title: "CorThreadSafetyOptions Enumeration"
ms.date: "03/30/2017"
api_name: 
  - "CorThreadSafetyOptions"
api_location: 
  - "mscoree.dll"
api_type: 
  - "COM"
f1_keywords: 
  - "CorThreadSafetyOptions"
helpviewer_keywords: 
  - "CorThreadSafetyOptions enumeration [.NET Framework metadata]"
ms.assetid: dae07d9b-df51-488c-b17e-52d6e48217bd
topic_type: 
  - "apiref"
author: "mairaw"
ms.author: "mairaw"
---
# CorThreadSafetyOptions Enumeration
Specifies flags to select options for thread safety.  
  
## Syntax  
  
```  
typedef enum CorThreadSafetyOptions {  
    MDThreadSafetyDefault       = 0x00000000,  
    MDThreadSafetyOff           = 0x00000000,  
    MDThreadSafetyOn            = 0x00000001,  
} CorThreadSafetyOptions;  
```  
  
## Members  
  
|Member|Description|  
|------------|-----------------|  
|`MDThreadSatetyDefault`|Default value. Same as `MDThreadSatetyOff`.|  
|`MDThreadSatetyOff`|Indicates that a reader/writer lock cannot be set.|  
|`MDThreadSatetyOn`|Indicates that a reader/writer lock can be set.|  
  
## Requirements  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorHdr.h  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## See Also  
 [Metadata Enumerations](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
