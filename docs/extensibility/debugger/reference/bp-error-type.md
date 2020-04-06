---
title: BP_ERROR_TYPE | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e777e1f8cb67187a81f8f3bb4f79299939bfa31c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738078"
---
# <a name="bp_error_type"></a>BP_ERROR_TYPE
Określa typ błędu punktu przerwania.

## <a name="syntax"></a>Składnia

```cpp
enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
typedef DWORD BP_ERROR_TYPE;
```

```csharp
public enum enum_BP_ERROR_TYPE {
    BPET_NONE            = 0x00000000,
    BPET_TYPE_WARNING    = 0x00000001,
    BPET_TYPE_ERROR      = 0x00000002,
    BPET_SEV_HIGH        = 0x0F000000,
    BPET_SEV_GENERAL     = 0x07000000,
    BPET_SEV_LOW         = 0x01000000,
    BPET_TYPE_MASK       = 0x0000ffff,
    BPET_SEV_MASK        = 0xffff0000,
    BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,
    BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,
    BPET_ALL             = 0xffffffff
};
```

## <a name="fields"></a>Pola
`BPET_NONE`\
Określa brak błędu punktu przerwania.

`BPET_TYPE_WARNING`\
Określa błąd punktu przerwania w stylu ostrzeżenia.

`BPET_TYPE_ERROR`\
Określa błąd punktu przerwania w stylu błędu.

`BPET_SEV_HIGH`\
Określa błąd punktu przerwania o wysokiej ważności.

`BPET_SEV_GENERAL`\
Określa błąd punktu przerwania o średniej ważności.

`BPET_SEV_LOW`\
Określa błąd punktu przerwania o niskiej ważności.

`BPET_TYPE_MASK`\
Określa błąd punktu przerwania w stylu maski.

`BPET_SEV_MASK`\
Określa błąd punktu przerwania w stylu ważności maski.

`BPET_GENERAL_WARNING`\
Określa błąd punktu przerwania w stylu ostrzeżenia ogólnego.

`BPET_GENERAL_ERROR`\
Określa błąd punktu przerwania w stylu błędu ogólnego.

`BPET_ALL`\
Określa wszystkie typy błędów punktu przerwania.

## <a name="remarks"></a>Uwagi
Wartości te mogą być łączone z bitowym `OR` i używane dla `dwType` elementu członkowskiego [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) struktury. Przekazany jako parametr do [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) metody.

Typ błędu punktu przerwania składa się z typu i ważności. Oznacza to, że typ błędu punktu przerwania nigdy `BPET_TYPE_ERROR`nie jest tylko typem `BPET_SEV_GENERAL`(na przykład ,) lub ważnością (na przykład) sam. `BPET_GENERAL_WARNING`i `BPET_GENERAL_ERROR` podaj wstępnie zdefiniowane wartości dla ogólnych punktów przerwania ostrzeżeń i błędów.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
