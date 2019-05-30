---
title: IDebugBreakpointUnboundEvent2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointUnboundEvent2
helpviewer_keywords:
- IDebugBreakpointUnboundEvent2
ms.assetid: 6b1e1863-0c64-4d85-8ab9-aface522fdea
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94adbbefc6307d18906c3c88de3c8a68e74d04a3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351285"
---
# <a name="idebugbreakpointunboundevent2"></a>IDebugBreakpointUnboundEvent2
Ten interfejs informuje Menedżer debugowania sesji (SDM), czy powiązany punkt przerwania został niezwiązanej z załadowanych programu.

## <a name="syntax"></a>Składnia

```
IDebugBreakpointUnboundEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs jako część jego obsługę punktów przerwania. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu (SDM używa [QueryInterface](/cpp/atl/queryinterface) dostęp do `IDebugEvent2` interfejsu).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 DE tworzy i wysyła tego obiektu zdarzenia, gdy powiązany punkt przerwania został niepowiązanej. Zdarzenia są wysyłane przy użyciu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkcji wywołania zwrotnego dostarczonych przez model SDM, gdy jest on dołączony do debugowanego programu.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugBreakpointUnboundEvent2`.

|Metoda|Opis|
|------------|-----------------|
|[GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)|Pobiera punkt przerwania, które stały się niepowiązanych.|
|[GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)|Pobiera powodów, dla którego punkt przerwania został niepowiązanej.|

## <a name="remarks"></a>Uwagi
 Gdy zwalnia aparat debugowania, biblioteki DLL lub klasy, wszystkie punkty przerwania, które były powiązane z kodu w module musi być niezwiązanej z debugowanego programu. `IDebugBreakpointUnboundEvent2` Jest wysyłana dla każdego niepowiązanych punktu przerwania.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)