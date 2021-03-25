---
description: Ten interfejs informuje Menedżera debugowania sesji (SDM) o tym, że nie można powiązać oczekującego punktu przerwania z załadowanego programu z powodu ostrzeżenia lub błędu.
title: IDebugBreakpointErrorEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointErrorEvent2
helpviewer_keywords:
- IDebugBreakpointErrorEvent2
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a7ebfa6b5d1cc2a0fe1a03c9e70952c5cec1a74e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054533"
---
# <a name="idebugbreakpointerrorevent2"></a>IDebugBreakpointErrorEvent2
Ten interfejs informuje Menedżera debugowania sesji (SDM) o tym, że nie można powiązać oczekującego punktu przerwania z załadowanego programu z powodu ostrzeżenia lub błędu.

## <a name="syntax"></a>Składnia

```
IDebugBreakpointErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE implementuje ten interfejs w ramach obsługi punktów przerwania. Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany w tym samym obiekcie co ten interfejs (model SDM używa [metody QueryInterface](/cpp/atl/queryinterface) do uzyskiwania dostępu do `IDebugEvent2` interfejsu).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Element DE tworzy i wysyła ten obiekt Event, gdy oczekujący punkt przerwania nie może zostać powiązany z debugowanym programem. Zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) dostarczonej przez model SDM, gdy jest on dołączony do debugowanego programu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugBreakpointErrorEvent2` .

|Metoda|Opis|
|------------|-----------------|
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|Pobiera Interfejs [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) , który opisuje ostrzeżenie lub błąd.|

## <a name="remarks"></a>Uwagi
 Za każdym razem, gdy punkt przerwania jest powiązany, do modelu SDM jest wysyłane zdarzenie. Jeśli punkt przerwania nie może być powiązany, `IDebugBreakpointErrorEvent2` jest wysyłany; w przeciwnym razie jest wysyłany [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) .

 Na przykład gdy warunek skojarzony z oczekującym punktem przerwania nie zostanie przeanalizowany lub oceniony, zostanie wysłane ostrzeżenie, że w tym momencie nie można powiązać oczekującego punktu przerwania. Taka sytuacja może wystąpić, jeśli kod punktu przerwania nie został jeszcze załadowany.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
