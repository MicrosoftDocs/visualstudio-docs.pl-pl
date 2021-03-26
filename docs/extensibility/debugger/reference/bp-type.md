---
description: Określa, czy punkt przerwania znajduje się w lokalizacji kodu, jest lokalizacją danych lub jest innym typem punktu przerwania.
title: BP_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_TYPE
helpviewer_keywords:
- BP_TYPE enumeration
ms.assetid: ef07191e-7966-43ab-96fb-1a0b1db3115d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 23f7b6c42b1c4736ba0eb76a451bb91e74ca5ff5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089098"
---
# <a name="bp_type"></a>BP_TYPE
Określa, czy punkt przerwania znajduje się w lokalizacji kodu, jest lokalizacją danych lub jest innym typem punktu przerwania.

## <a name="syntax"></a>Składnia

```cpp
enum enum_BP_TYPE {
    BPT_NONE    = 0x0000,
    BPT_CODE    = 0x0001,
    BPT_DATA    = 0x0002,
    BPT_SPECIAL = 0x0003
};
typedef DWORD BP_TYPE;
```

```csharp
public enum enum_BP_TYPE {
    BPT_NONE    = 0x0000,
    BPT_CODE    = 0x0001,
    BPT_DATA    = 0x0002,
    BPT_SPECIAL = 0x0003
};
```

## <a name="fields"></a>Pola
`BPT_NONE`\
Określa typ punktu przerwania.

`BPT_CODE`\
Określa punkt przerwania kodu.

`BPT_DATA`\
Określa punkt przerwania danych.

`BPT_SPECIAL`\
Określa punkt przerwania, który nie jest kodem ani typem danych. Ten typ jest przestarzały i nie powinien być używany.

## <a name="remarks"></a>Uwagi
Przekazanie jako parametr do metod getpunkion [](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md) [i](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) getpunks.

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)
- [GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)
