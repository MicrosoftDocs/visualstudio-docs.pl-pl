---
title: MODULE_FLAGS | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 78c7f24d64ffca667706c3b2fcebeffad16a9d85
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714257"
---
# <a name="module_flags"></a>MODULE_FLAGS
Służy do opisywania modułu.

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

## <a name="fields"></a>Pola
 `MODULE_FLAG_NONE`\
 Określa brak modułu.

 `MODULE_FLAG_SYSTEM`\
 Określa moduł systemowy.

 `MODULE_FLAG_SYMBOLS`\
 Określa moduł symbolu.

 `MODULE_FLAG_64BIT`\
 Określa moduł 64-bitowy.

 `MODULE_FLAG_OPTIMIZED`\
 Określa, że moduł został zoptymalizowany. Ten stan jest odzwierciedlony w oknie **Moduły.**

 `MODULE_FLAG_UNOPTIMIZED`\
 Określa, że moduł nie został zoptymalizowany. Ten stan jest odzwierciedlony w oknie **Moduły.** Jest to stan domyślny.

## <a name="remarks"></a>Uwagi
 Używany dla `m_dwModuleFlags` członka struktury [MODULE_INFO.](../../../extensibility/debugger/reference/module-info.md)

 Flagi te mogą być łączone z bitowym `OR`.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
