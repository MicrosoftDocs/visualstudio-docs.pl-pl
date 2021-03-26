---
description: Określa informacje, które mają zostać pobrane o pomyślnym rozpoznaniu punktu przerwania.
title: BPRESI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 652d1423b95f923a8413bdec6fbbed528e9f624a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096697"
---
# <a name="bpresi_fields"></a>BPRESI_FIELDS
Określa informacje, które mają zostać pobrane o pomyślnym rozpoznaniu punktu przerwania.

## <a name="syntax"></a>Składnia

```cpp
enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
typedef DWORD BPRESI_FIELDS;
```

```csharp
public enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
```

## <a name="fields"></a>Pola
`BPRESI_BPRESLOCATION`\
Zainicjuj/Użyj `bpResLocation` pola (lokalizacja rozpoznawania punktów przerwania) struktury [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) .

`BPRESI_PROGRAM`\
Zainicjuj/Użyj `pProgram` pola `BP_RESOLUTION_INFO` struktury.

`BPRESI_THREAD`\
Zainicjuj/Użyj `pThread` pola `BP_RESOLUTION_INFO` struktury.

`BPRESI_ALLFIELDS`\
Określa wszystkie pola.

## <a name="remarks"></a>Uwagi
Przeszedł do metody [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) , aby wskazać, które pola struktury [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) mają być inicjowane.

Te flagi są również używane do wskazywania, które pola `BP_RESOLUTION_INFO` struktury są używane i są prawidłowe podczas zwracania tej struktury.

Te wartości mogą być połączone z bitową `OR` .

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
