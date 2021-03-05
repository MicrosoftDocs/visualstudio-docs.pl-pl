---
description: Zwraca powód, dla którego nie powiązano punkt przerwania.
title: BP_UNBOUND_REASON | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_UNBOUND_REASON
helpviewer_keywords:
- BP_UNBOUND_REASON enumeration
ms.assetid: 939b6f9c-113b-471d-9f30-b03871af6285
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 857f07e70809200567b6c2f79c5a22aff78b4af8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162553"
---
# <a name="bp_unbound_reason"></a>BP_UNBOUND_REASON
Zwraca powód, dla którego nie powiązano punkt przerwania.

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
Przyczyna jest nieznana.

`BPUR_CODE_UNLOADED`\
Kod, który zawiera punkt przerwania został zwolniony.

`BPUR_BREAKPOINT_REBIND`\
Punkt przerwania został Przewiązany do innej lokalizacji. Może to nastąpić po przejściu operacji Edytuj i Kontynuuj, gdy punkt przerwania jest przenoszony lub gdy punkt przerwania jest powiązany z plikiem o ścieżce, która nie jest już prawidłowa.

`BPUR_ BREAKPOINT_ERROR`\
Punkt przerwania jest określany jako błąd, po którym jest powiązany. Dzieje się tak w przypadku zarządzanych punktów przerwania, których warunki nie są już prawidłowe.

## <a name="remarks"></a>Uwagi
Zwrócone przez metodę [getpowód](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md) .

## <a name="requirements"></a>Wymagania
Nagłówek: Msdbg. h

Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Wyliczenia](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)
