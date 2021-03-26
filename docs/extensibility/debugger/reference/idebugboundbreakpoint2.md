---
description: Ten interfejs reprezentuje punkt przerwania, który jest powiązany z lokalizacją w kodzie.
title: IDebugBoundBreakpoint2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b8a48ffcb3c0409839ec9323679e396a7e23b8f3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088825"
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
Ten interfejs reprezentuje punkt przerwania, który jest powiązany z lokalizacją w kodzie.

## <a name="syntax"></a>Składnia

```
IDebugBoundBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs w ramach obsługi punktów przerwania.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [powiązania](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) tworzy ten interfejs. Wywołania metody [Getpunkt przerwania](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) i [Next](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) mogą również uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugBoundBreakpoint2` .

|Metoda|Opis|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Pobiera oczekujący punkt przerwania, z którego został utworzony określony powiązany punkt przerwania.|
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Pobiera stan tego powiązanego punktu przerwania.|
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Pobiera bieżącą liczbę trafień dla tego powiązanego punktu przerwania.|
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Pobiera rozdzielczość punktu przerwania opisującą ten punkt przerwania.|
|[Włączenie](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Włącza lub wyłącza punkt przerwania.|
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Ustawia liczbę trafień dla tego powiązanego punktu przerwania.|
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Ustawia lub zmienia warunek skojarzony z tym związanym punktem przerwania.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Ustawia lub zmienia liczbę przebiegów skojarzoną z tym związanym punktem przerwania.|
|[Usuwanie](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Usuwa punkt przerwania.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)
- [Dalej](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)
- [Węglowodor](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
