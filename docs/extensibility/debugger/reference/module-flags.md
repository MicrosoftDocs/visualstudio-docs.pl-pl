---
description: Używane do opisywania modułu.
title: MODULE_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b78e0ec9f720307a60485283b98939dee954ff29
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079790"
---
# <a name="module_flags"></a>MODULE_FLAGS
Używane do opisywania modułu.

## <a name="syntax"></a>Składnia

```cpp
enum enum_MODULE_FLAGS { 
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
public enum enum_MODULE_FLAGS { 
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
 Określa Brak modułu.

 `MODULE_FLAG_SYSTEM`\
 Określa moduł systemowy.

 `MODULE_FLAG_SYMBOLS`\
 Określa moduł symboli.

 `MODULE_FLAG_64BIT`\
 Określa moduł 64-bitowy.

 `MODULE_FLAG_OPTIMIZED`\
 Określa, że moduł został zoptymalizowany. Ten stan jest widoczny w oknie **moduły** .

 `MODULE_FLAG_UNOPTIMIZED`\
 Określa, że moduł nie został zoptymalizowany. Ten stan jest widoczny w oknie **moduły** . Jest to stan domyślny.

## <a name="remarks"></a>Uwagi
 Używane dla `m_dwModuleFlags` elementu członkowskiego struktury [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) .

 Flagi te mogą być połączone z bitową `OR` .

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
