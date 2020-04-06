---
title: BP_PASSCOUNT_STYLE | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1633c5e9aa6ff251fedce83a0243664cd9e0e0a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737916"
---
# <a name="bp_passcount_style"></a>BP_PASSCOUNT_STYLE
Określa warunek skojarzony z liczbą przebiegów punktu przerwania, która powoduje, że punkt przerwania jest uruchamiany.

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
Określa styl liczby przebiegów punktu przerwania.

`BP_PASSCOUNT_EQUAL`\
Ustawia styl liczby przebiegów punktu przerwania na równy. Punkt przerwania jest uruchamiany, gdy liczba trafień punktu przerwania jest równa liczbie przebiegów.

`BP_PASSCOUNT_EQUAL_OR_GREATER`\
Ustawia styl liczby przebiegów punktu przerwania na równy lub większy. Punkt przerwania jest uruchamiany, gdy liczba trafień punktu przerwania jest równa lub większa niż liczba przebiegów.

`BP_PASSCOUNT_MOD`\
Określa liczbę przebiegów modulo. Na przykład jeśli liczba przebiegów `BP_PASSCOUNT_MOD` jest typu i liczba przebiegów wartość wynosi 4, punkt przerwania uruchamia za każdym razem, gdy liczba trafień jest wielokrotnością 4.

## <a name="remarks"></a>Uwagi
Używany dla `stylePassCount` członka [struktury BP_PASSCOUNT,](../../../extensibility/debugger/reference/bp-passcount.md) który z kolei jest członkiem [struktur BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) i [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
