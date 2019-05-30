---
title: IDebugBreakpointErrorEvent2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointErrorEvent2
helpviewer_keywords:
- IDebugBreakpointErrorEvent2
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bae4a63ef03ca3b8d3fa642f7333ff2357084b47
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352935"
---
# <a name="idebugbreakpointerrorevent2"></a>IDebugBreakpointErrorEvent2
Ten interfejs informuje Menedżer debugowania sesji (SDM), czy oczekujący punkt przerwania nie można powiązać załadować program, z powodu ostrzeżenia lub błędu.

## <a name="syntax"></a>Składnia

```
IDebugBreakpointErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE implementuje ten interfejs jako część jego obsługę punktów przerwania. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu (SDM używa [QueryInterface](/cpp/atl/queryinterface) dostęp do `IDebugEvent2` interfejsu).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 DE tworzy i wysyła tego obiektu zdarzenia, jeśli oczekujący punkt przerwania nie można powiązać z debugowanego programu. Zdarzenia są wysyłane przy użyciu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkcji wywołania zwrotnego dostarczonych przez model SDM, gdy jest on dołączony do debugowanego programu.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugBreakpointErrorEvent2`.

|Metoda|Opis|
|------------|-----------------|
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|Pobiera [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interfejsu, który opisuje ostrzeżenia lub błędu.|

## <a name="remarks"></a>Uwagi
 Zawsze, gdy punkt przerwania jest związany, zdarzenia są wysyłane do SDM. Jeśli nie można powiązać punkt przerwania, `IDebugBreakpointErrorEvent2` jest wysyłany; w przeciwnym razie [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) są wysyłane.

 Na przykład gdy warunek skojarzony z Oczekujący punkt przerwania nie można przeanalizować lub oceń, wysyłane jest ostrzeżenie, że w tej chwili nie można powiązać oczekujący punkt przerwania. Może to nastąpić, jeśli kod dla punktu przerwania nie został jeszcze załadowany.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)