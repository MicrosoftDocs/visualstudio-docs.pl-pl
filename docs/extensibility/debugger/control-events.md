---
title: Kontrolowanie zdarzeń | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c79abb6ca0912ba0a8872d87c830ba455836595
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312440"
---
# <a name="control-events"></a>Zdarzenia obiektu Controls
Konieczne jest wysłanie zdarzenia podczas kontrolowanego wykonywania programu. Wszystkie zdarzenia są wysyłane przy użyciu [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) interfejs i mieć atrybuty, które wymagają wykonania [IDebugEvent2::GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) metody.

## <a name="additional-methods"></a>Dodatkowe metody
 Niektóre zdarzenia wymagają wykonania dodatkowych metod, w następujący sposób:

- Wysyłanie [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) interfejsu po zainicjowaniu aparat debugowania (DE), musisz zaimplementować [IDebugEngineCreateEvent2::GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) metody.

- Kontrola wykonywania wymaga implementacji takich zdarzeń formantu jako [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) i[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) interfejsów. **IDebugBreakEvent2** jest wymagany tylko w przypadku podziału asynchronicznego.

- Przechodzenie krok po kroku do funkcji wymaga wykonania [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) interfejsu i jej metody.

  Zdarzenia wynikające z punktów przerwania wymagają wykonania [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), i [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) interfejsy, jak również [IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) i [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) metody.

  Obliczanie wyrażenia asynchroniczne, musisz zaimplementować [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) interfejsu i jego [IDebugExpressionEvaluationCompleteEvent2::GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md) [i GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) metody.

  Zdarzenia synchroniczne wymagać zaimplementowania [IDebugEngine2::ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) metody.

  Aparat do zapisywania danych wyjściowych styl ciągu, musisz zaimplementować [IDebugOutputStringEvent2::GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) metody.

## <a name="see-also"></a>Zobacz także
- [Wykonanie kontroli i stan oceny](../../extensibility/debugger/execution-control-and-state-evaluation.md)