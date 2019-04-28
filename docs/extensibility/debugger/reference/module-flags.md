---
title: MODULE_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: c3ec96c5ba806e6eff735edc8093868b19ebaf5b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62913838"
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
 MODULE_FLAG_NONE określa nie modułu.

 MODULE_FLAG_SYSTEM Określa moduł systemu.

 MODULE_FLAG_SYMBOLS Określa moduł symboli.

 MODULE_FLAG_64BIT Określa moduł 64-bitowych.

 MODULE_FLAG_OPTIMIZED Określa, który został zoptymalizowany moduł. Ten stan jest odzwierciedlana w **modułów** okna.

 MODULE_FLAG_UNOPTIMIZED Określa, który nie został zoptymalizowany moduł. Ten stan jest odzwierciedlana w **modułów** okna. Jest to domyślny stan.

## <a name="remarks"></a>Uwagi
 Używany do `m_dwModuleFlags` członkiem [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) struktury.

 Te flagi mogą być łączone przy użyciu bitowego operatora `OR`.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)