---
title: BP_PASSCOUNT_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4ea44ef70ba086a58454891987711ce7cca643e8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353052"
---
# <a name="bppasscountstyle"></a>BP_PASSCOUNT_STYLE
Określa warunek skojarzony z liczbą — dostęp próbny punkt przerwania, który powoduje, że punkt przerwania uruchomić.

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
Określa styl liczba — dostęp próbny nie w punkt przerwania.

`BP_PASSCOUNT_EQUAL`\
Ustawia styl punkt przerwania — dostęp próbny liczba wartość. Punkt przerwania jest uruchamiana, gdy liczba przypadków, gdy zostanie osiągnięty punkt przerwania jest równa Liczba — dostęp próbny.

`BP_PASSCOUNT_EQUAL_OR_GREATER`\
Ustawia styl liczba — dostęp próbny punktu przerwania równym lub większym. Punkt przerwania jest uruchamiana, gdy liczba przypadków, gdy zostanie osiągnięty punkt przerwania jest równa lub większa niż liczba — dostęp próbny.

`BP_PASSCOUNT_MOD`\
Określa modulo Liczba przebiegów. Na przykład, jeśli liczba — dostęp próbny jest typu `BP_PASSCOUNT_MOD` i przekaż wartość licznika jest 4, uruchamiany punkt przerwania, za każdym razem, gdy liczba trafień jest wielokrotnością liczby 4.

## <a name="remarks"></a>Uwagi
Używany do `stylePassCount` członkiem [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) strukturę, która z kolei jest elementem członkowskim [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) i [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struktury.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
