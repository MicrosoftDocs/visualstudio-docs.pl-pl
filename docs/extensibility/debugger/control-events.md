---
title: Zdarzenia kontroli | Microsoft Docs
description: Dowiedz się więcej o wysyłaniu zdarzeń podczas kontrolowanego wykonywania programu przy użyciu interfejsu IDebugEvent2.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: aeee5ed91eca7666d08dfd08ec02b850a7739db9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085536"
---
# <a name="control-events"></a>Zdarzenia kontroli
Podczas kontrolowanego wykonywania programu należy wysyłać zdarzenia. Wszystkie zdarzenia są wysyłane przy użyciu interfejsu [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) i mają atrybuty, które wymagają implementacji metody [IDebugEvent2:: GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) .

## <a name="additional-methods"></a>Dodatkowe metody
 Niektóre zdarzenia wymagają implementacji dodatkowych metod w następujący sposób:

- Wysyłanie interfejsu [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) po zainicjowaniu aparatu debugowania (de) wymaga zaimplementowania metody [IDebugEngineCreateEvent2:: GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) .

- Kontrola wykonywania wymaga implementacji takich zdarzeń kontroli jak interfejsy [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) i[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) . **IDebugBreakEvent2** jest wymagany tylko w przypadku przerw asynchronicznych.

- Przechodzenie do funkcji wymaga implementacji interfejsu [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) i jego metod.

  Zdarzenia pochodzące z punktów przerwania wymagają implementacji interfejsów [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)i [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) , a także metod [IDebugBreakpointBoundEvent2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) i [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) .

  Obliczanie wyrażeń asynchronicznych wymaga zaimplementowania interfejsu [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) oraz jego metod [IDebugExpressionEvaluationCompleteEvent2:: GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[i GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) .

  Zdarzenia synchroniczne wymagają implementacji metody [IDebugEngine2:: ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) .

  Aby aparat pisał dane wyjściowe w stylu ciągu, należy zaimplementować metodę [IDebugOutputStringEvent2:: GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) .

## <a name="see-also"></a>Zobacz też
- [Kontrola wykonywania i Ocena stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
