---
title: BP_UNBOUND_REASON | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b0ee695e1108bf9f1c6069084a0826ee23bf37d4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737773"
---
# <a name="bp_unbound_reason"></a>BP_UNBOUND_REASON
Podaje powód, dla którego punkt przerwania był niezwiązany.

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

## <a name="fields"></a>Pola
`BPUR_UNKNOWN`\
Przyczyna nie jest znana.

`BPUR_CODE_UNLOADED`\
Kod, który zawiera punkt przerwania został zwolniony.

`BPUR_BREAKPOINT_REBIND`\
Punkt przerwania został odbicia do innej lokalizacji. Może się to zdarzyć po operacji Edycji i Kontynuuj, gdy punkt przerwania zostanie przeniesiony lub gdy punkt przerwania jest powiązany z plikiem ze ścieżką, która nie jest już prawidłowa.

`BPUR_ BREAKPOINT_ERROR`\
Punkt przerwania jest określany jako błąd po jego powiązaniu. Dzieje się tak w przypadku zarządzanych punktów przerwania, których warunki nie są już prawidłowe.

## <a name="remarks"></a>Uwagi
Zwrócony przez [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) metody.

## <a name="requirements"></a>Wymagania
Nagłówek: msdbg.h

Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
