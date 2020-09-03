---
title: IDebugPendingBreakpoint2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e6f2c1df37e953a5d8c66bad9d0a3574a463fad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725649"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
Ten interfejs reprezentuje punkt przerwania, który jest gotowy do powiązania z lokalizacją w kodzie.

## <a name="syntax"></a>Składnia

```
IDebugPendingBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs w ramach obsługi punktów przerwania.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) tworzy oczekujący punkt przerwania z interfejsu [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) . Wywołanie [powiązania](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) tworzy `IDebugBreakpoint2` interfejs, który reprezentuje powiązany punkt przerwania w programie.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugPendingBreakpoint2` .

|Metoda|Opis|
|------------|-----------------|
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Określa, czy ten oczekujący punkt przerwania można powiązać z lokalizacją w kodzie.|
|[Węglowodor](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Wiąże ten oczekujący punkt przerwania z co najmniej jedną lokalizacją kodu.|
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Pobiera stan tego oczekującego punktu przerwania.|
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Pobiera żądanie punktu przerwania, które zostało użyte do utworzenia tego oczekującego punktu przerwania.|
|[Virtualize](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Przełącza zwirtualizowany stan tego oczekującego punktu przerwania.|
|[Włączenie](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Przełącza włączony stan tego oczekującego punktu przerwania.|
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Ustawia lub zmienia warunek skojarzony z tym oczekującym punktem przerwania.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Ustawia lub zmienia liczbę przebiegów skojarzoną z tym oczekującym punktem przerwania.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Wylicza wszystkie punkty przerwania powiązane z tym oczekującym punktem przerwania.|
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Wylicza wszystkie punkty przerwania błędów, które spowodowały ten oczekujący punkt przerwania.|
|[Usuń](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Usuwa ten oczekujący punkt przerwania i wszystkie punkty przerwania powiązane z nim.|

## <a name="remarks"></a>Uwagi
 `IDebugPendingBreakpoint2` może być uważany za dostawcę wszystkich niezbędnych informacji potrzebnych do powiązania punktu przerwania z kodem, który można zastosować do jednego lub wielu programów.

 Oczekujący punkt przerwania może potencjalnie utworzyć więcej niż jeden związany punkt przerwania. Na przykład punkt przerwania w szablonie w stylu C++ może generować związany punkt przerwania dla każdego unikatowego wystąpienia tego szablonu.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)
