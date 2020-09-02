---
title: MODULE_FLAGS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ae51d604f455b12fd6933a54954b75a97aea4eb7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547471"
---
# <a name="module_flags"></a>MODULE_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Używane do opisywania modułu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 Określa Brak modułu.  
  
 MODULE_FLAG_SYSTEM  
 Określa moduł systemowy.  
  
 MODULE_FLAG_SYMBOLS  
 Określa moduł symboli.  
  
 MODULE_FLAG_64BIT  
 Określa moduł 64-bitowy.  
  
 MODULE_FLAG_OPTIMIZED  
 Określa, że moduł został zoptymalizowany. Ten stan jest widoczny w oknie **moduły** .  
  
 MODULE_FLAG_UNOPTIMIZED  
 Określa, że moduł nie został zoptymalizowany. Ten stan jest widoczny w oknie **moduły** . Jest to stan domyślny.  
  
## <a name="remarks"></a>Uwagi  
 Używane dla `m_dwModuleFlags` elementu członkowskiego struktury [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) .  
  
 Flagi te mogą być połączone z bitową `OR` .  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
