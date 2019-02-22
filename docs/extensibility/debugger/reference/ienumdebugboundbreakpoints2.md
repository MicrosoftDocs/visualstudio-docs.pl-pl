---
title: IEnumDebugBoundBreakpoints2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40097fab8a45a08ce11c9f58fa22f4464174ef32
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56680207"
---
# <a name="ienumdebugboundbreakpoints2"></a>IEnumDebugBoundBreakpoints2
Ten interfejs wylicza powiązane punkty przerwania, skojarzone z Oczekujący punkt przerwania lub punkt przerwania powiązane zdarzenia.

## <a name="syntax"></a>Składnia

```
IEnumDebugBoundBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs jako część jego obsługę punktów przerwania. Należy można zaimplementować ten interfejs, jeśli punkty przerwania są obsługiwane.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Visual Studio calls:

-   [EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) uzyskać ten interfejs reprezentujący listę wszystkich punktów przerwania, które zostały wyzwolone.

-   [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) uzyskać ten interfejs reprezentujący listę wszystkich punktów przerwania, które były powiązane.

-   [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) uzyskać ten interfejs reprezentujący listę wszystkich punktów przerwania, powiązany z tym oczekujący punkt przerwania.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IEnumDebugBoundBreakpoints2`.

|Metoda|Opis|
|------------|-----------------|
|[Next](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|Pobiera określoną liczbę powiązanych punktów przerwania w kolejności wyliczenia.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|Pomija określoną liczbę powiązanych punktów przerwania w kolejności wyliczenia.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|Resetuje sekwencji wyliczenia na początku.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżącego modułu wyliczającego.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|Pobiera liczbę powiązanych punktów przerwania w moduł wyliczający.|

## <a name="remarks"></a>Uwagi
 Aby zaktualizować wyświetlane punkty przerwania w środowisku IDE programu Visual Studio korzysta z powiązane punkty przerwania reprezentowany przez ten interfejs.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)