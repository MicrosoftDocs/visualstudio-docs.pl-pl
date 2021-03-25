---
description: Określa warunek skojarzony z licznikiem przebiegu punktu przerwania, który powoduje, że punkt przerwania jest wyzwalany.
title: BP_PASSCOUNT_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 39a0dba08aa74386c442a7732b6522d8ee27652c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094474"
---
# <a name="bp_passcount_style"></a>BP_PASSCOUNT_STYLE
Określa warunek skojarzony z licznikiem przebiegu punktu przerwania, który powoduje, że punkt przerwania jest wyzwalany.

## <a name="syntax"></a>Składnia

```cpp
enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
typedef DWORD BP_PASSCOUNT_STYLE;
```

```csharp
public enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
```

## <a name="fields"></a>Pola
`BP_PASSCOUNT_NONE`\
Określa styl liczby przebiegów przerwań.

`BP_PASSCOUNT_EQUAL`\
Ustawia styl liczby przebiegów punktu przerwania na równy. Punkt przerwania jest uruchamiany, gdy liczba trafień punktu przerwania jest większa niż liczba przebiegów.

`BP_PASSCOUNT_EQUAL_OR_GREATER`\
Ustawia styl liczby przebiegów punktu przerwania na równy lub większy. Punkt przerwania jest uruchamiany, gdy liczba trafień punktu przerwania jest równa lub większa niż liczba przebiegów.

`BP_PASSCOUNT_MOD`\
Określa liczbę przebiegów modulo. Na przykład, jeśli liczba przebiegów jest typu `BP_PASSCOUNT_MOD` i wartość liczby przeskoków wynosi 4, punkt przerwania jest uruchamiany za każdym razem, gdy liczba trafień jest wielokrotnością 4.

## <a name="remarks"></a>Uwagi
Używane dla `stylePassCount` składowej struktury [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) , która jest w przekształcaniu składowej struktur [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) i [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
