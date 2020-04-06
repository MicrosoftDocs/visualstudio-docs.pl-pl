---
title: IDebugEvent2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6341f8003b962a7f45420b076b23623ebdaf861
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729910"
---
# <a name="idebugevent2"></a>IDebugEvent2
Ten interfejs jest używany do przekazywania zarówno krytycznych informacji debugowania, takich jak zatrzymanie w punkcie przerwania, jak i informacji niekrytycznych, takich jak komunikat debugowania.

## <a name="syntax"></a>Składnia

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) i dostawca portu niestandardowego implementują ten interfejs na tym samym obiekcie, co wszystkie inne interfejsy zdarzeń.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Za pomocą argumentu identyfikator interfejsu (IID) podane [do zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) lub [zdarzenia](../../../extensibility/debugger/reference/idebugportevents2-event.md), menedżer debugowania sesji (SDM) wywołuje [QueryInterface](/cpp/atl/queryinterface) w interfejsie, `IDebugEvent2` aby uzyskać odpowiedni interfejs zdarzeń.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugEvent2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Pobiera atrybuty dla tego zdarzenia debugowania.|

## <a name="remarks"></a>Uwagi
 Bardziej szczegółowe interfejsy zdarzeń, takie jak [IDebugBreakpointEvent2,](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)nie pochodzą z interfejsu IDebugEvent2, ale są implementowane `IDebugEvent2`jako oddzielny interfejs na tym samym obiekcie co .

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [Wydarzenie](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Wydarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
