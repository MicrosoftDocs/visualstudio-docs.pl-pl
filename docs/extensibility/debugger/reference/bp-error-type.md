---
title: BP_ERROR_TYPE | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_TYPE
helpviewer_keywords:
- BP_ERROR_TYPE enumeration
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2964c833abfa25b57678680f8b821f992cb31de8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689190"
---
# <a name="bperrortype"></a>BP_ERROR_TYPE
Określa typ błąd punktu przerwania.

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

## <a name="members"></a>Elementy członkowskie
BPET_NONE określa nie błąd punktu przerwania.

BPET_TYPE_WARNING określa błąd stylu ostrzeżenie punktu przerwania.

BPET_TYPE_ERROR określa błąd punktu przerwania stylu błędu.

BPET_SEV_HIGH określa błąd punktu przerwania o wysokiej ważności.

BPET_SEV_GENERAL określa o średniej ważności, punkt przerwania.

BPET_SEV_LOW określa o niskiej ważności, punkt przerwania.

BPET_TYPE_MASK określa błąd punktu przerwania stylu maski.

BPET_SEV_MASK określa błąd punktu przerwania ważność maska stylu.

BPET_GENERAL_WARNING określa błąd punktu przerwania ogólne ostrzeżenie stylu.

BPET_GENERAL_ERROR określa błąd punktu przerwania stylu w przypadku błędu ogólnego.

BPET_ALL Określa typy błąd punktu przerwania.

## <a name="remarks"></a>Uwagi
Te wartości mogą być łączone przy użyciu bitowego operatora `OR` i jest używana do `dwType` członkiem [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) struktury. Przekazany jako parametr do [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) metody.

Typ błędu punktu przerwania składa się z typu i ważności. Oznacza, że typ błąd punktu przerwania nigdy nie tylko typem (na przykład `BPET_TYPE_ERROR`,) lub ważność (na przykład `BPET_SEV_GENERAL`) przez siebie. `BPET_GENERAL_WARNING` i `BPET_GENERAL_ERROR` zapewnia wstępnie zdefiniowane wartości dla punktów przerwania ogólne, ostrzeżeń i błędów.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
