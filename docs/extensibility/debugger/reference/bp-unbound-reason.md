---
title: BP_UNBOUND_REASON | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65393f6e162cb15ded7a0e598e360c7ce90bb3cd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62881788"
---
# <a name="bpunboundreason"></a>BP_UNBOUND_REASON
Zapewnia powodów, dla którego punkt przerwania został niepowiązanej.

## <a name="syntax"></a>Składnia

```cpp
enum enum_BP_UNBOUND_REASON {
    BPUR_UNKNOWN           = 0x0000,
    BPUR_CODE_UNLOADED     = 0x0002,
    BPUR_BREAKPOINT_REBIND = 0x0003,
    BPUR_BREAKPOINT_ERROR  = 0x0004
};
typedef DWORD BP_UNBOUND_REASON;
```

```csharp
public enum enum_BP_UNBOUND_REASON {
    BPUR_UNKNOWN           = 0x0000,
    BPUR_CODE_UNLOADED     = 0x0002,
    BPUR_BREAKPOINT_REBIND = 0x0003,
    BPUR_BREAKPOINT_ERROR  = 0x0004
};
```

## <a name="members"></a>Elementy członkowskie
BPUR_UNKNOWN przyczyną jest nieznany.

BPUR_CODE_UNLOADED kodu, który zawiera punkt przerwania został zwolniony.

BPUR_BREAKPOINT_REBIND punkt przerwania ma zostało odbitych do innej lokalizacji. To jest wykonywane podczas edycji i kontynuowania działania w przypadku, gdy punkt przerwania lub gdy punkt przerwania jest powiązana z pliku ze ścieżką, która nie jest już prawidłowy.

BREAKPOINT_ERROR BPUR_ punkt przerwania jest określana jest błędny po jest powiązany. Dzieje się to do zarządzanego punktów przerwania, którego warunki nie są już prawidłowe.

## <a name="remarks"></a>Uwagi
Zwrócone przez [getreason —](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) metody.

## <a name="requirements"></a>Wymagania
Header: msdbg.h

Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
