---
title: IDebugBoundBreakpoint2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4d22b10085baefeb3a0286c1b4edcb5876c0dac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735422"
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
Ten interfejs reprezentuje punkt przerwania, który jest powiązany z lokalizacją kodu.

## <a name="syntax"></a>Składnia

```
IDebugBoundBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs jako część jego obsługi punktów przerwania.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) tworzy ten interfejs. Wywołania [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) i [Next](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) można również uzyskać ten interfejs.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugBoundBreakpoint2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Pobiera oczekujących punktu przerwania, z którego utworzono określony powiązany punkt przerwania.|
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Pobiera stan tego powiązanego punktu przerwania.|
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Pobiera bieżącą liczbę trafień dla tego powiązanego punktu przerwania.|
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Pobiera rozdzielczość punktu przerwania, który opisuje ten punkt przerwania.|
|[Włącz](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Włącza lub wyłącza punkt przerwania.|
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Ustawia liczbę trafień dla tego powiązanego punktu przerwania.|
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Ustawia lub zmienia warunek skojarzony z tym powiązanym punktem przerwania.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Ustawia lub zmienia liczbę przebiegów skojarzonych z tym powiązanym punktem przerwania.|
|[Usuwanie](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Usuwa punkt przerwania.|

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)
- [Dalej](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)
- [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
