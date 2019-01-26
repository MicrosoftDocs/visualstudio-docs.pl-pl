---
title: MODULE_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 32b0e89a69bc39e43d4ff4fbc4e8f4d5816565ad
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54975390"
---
# <a name="moduleflags"></a>MODULE_FLAGS
Używane do opisywania modułu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
typedef DWORD MODULE_FLAGS;  
```  
  
```csharp  
public enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 MODULE_FLAG_NONE  
 Określa nie modułu.  
  
 MODULE_FLAG_SYSTEM  
 Określa moduł systemu.  
  
 MODULE_FLAG_SYMBOLS  
 Określa moduł symboli.  
  
 MODULE_FLAG_64BIT  
 Określa moduł 64-bitowych.  
  
 MODULE_FLAG_OPTIMIZED  
 Określa, że moduł został zoptymalizowany. Ten stan jest odzwierciedlana w **modułów** okna.  
  
 MODULE_FLAG_UNOPTIMIZED  
 Określa, że moduł nie został zoptymalizowany. Ten stan jest odzwierciedlana w **modułów** okna. Jest to domyślny stan.  
  
## <a name="remarks"></a>Uwagi  
 Używany do `m_dwModuleFlags` członkiem [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) struktury.  
  
 Te flagi mogą być łączone przy użyciu bitowego operatora `OR`.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)