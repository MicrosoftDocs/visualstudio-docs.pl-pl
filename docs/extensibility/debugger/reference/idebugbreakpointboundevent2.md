---
title: IDebugBreakpointBoundEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointBoundEvent2
helpviewer_keywords:
- IDebugBreakpointBoundEvent2
ms.assetid: 24ba362e-5be1-481a-b071-e1ebd3cae6e8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 149b3f4d474c0304fab26f9ff3f772440ae761ca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948338"
---
# <a name="idebugbreakpointboundevent2"></a>IDebugBreakpointBoundEvent2
Ten interfejs nakazuje menedżerowi debugowania sesji (SDM), że oczekujący punkt przerwania został pomyślnie powiązany z załadowanym programem.

## <a name="syntax"></a>Składnia

```
IDebugBreakpointBoundEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE implementuje ten interfejs w ramach obsługi punktów przerwania. Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany w tym samym obiekcie co ten interfejs (model SDM używa [metody QueryInterface](/cpp/atl/queryinterface) do uzyskiwania dostępu do `IDebugEvent2` interfejsu).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Element DE tworzy i wysyła ten obiekt Event, gdy oczekujący punkt przerwania został pomyślnie powiązany z debugowanym programem. Zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) dostarczonej przez model SDM, gdy jest on dołączony do debugowanego programu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugBreakpointBoundEvent2` .

|Metoda|Opis|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)|Pobiera oczekujący punkt przerwania.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)|Tworzy moduł wyliczający punktów przerwania, które zostały powiązane z tym zdarzeniem.|

## <a name="remarks"></a>Uwagi
 Za każdym razem, gdy punkt przerwania jest powiązany, do modelu SDM jest wysyłane zdarzenie. Jeśli punkt przerwania nie może być powiązany, wysyłany jest [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) . w przeciwnym razie `IDebugBreakpointBoundEvent2` jest wysyłane.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
