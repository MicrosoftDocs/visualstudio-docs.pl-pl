---
title: Zdarzenia kontrolne | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc2c3ad9c9b63923bdf2f107e7bc582f3c76cd62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739089"
---
# <a name="control-events"></a>Sterowanie zdarzeniami
Zdarzenia należy wysyłać podczas kontrolowanego wykonywania programu. Wszystkie zdarzenia są wysyłane przy użyciu interfejsu [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) i mają atrybuty, które wymagają zaimplementowania [metody IDebugEvent2::GetAttributes.](../../extensibility/debugger/reference/idebugevent2-getattributes.md)

## <a name="additional-methods"></a>Dodatkowe metody
 Niektóre zdarzenia wymagają wdrożenia dodatkowych metod, w następujący sposób:

- Wysyłanie interfejsu [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) po zainicjowaniu aparatu debugowania (DE) wymaga zaimplementowania metody [IDebugEngineCreateEvent2::GetEngine.](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)

- Kontrola wykonania wymaga implementacji takich zdarzeń kontroli, jak [interfejsy IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) i[IDebugStepCompleteEvent2.](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) **IDebugBreakEvent2** jest wymagane tylko dla przerw asynchronicznych.

- Przechodzenie do funkcji wymaga implementacji interfejsu [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) i jego metod.

  Zdarzenia pochodzące z punktów przerwania wymagają implementacji interfejsów [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)i [IDebugBreakpointBoundEvent2,](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) a także metod [IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) i [EnumBoundBreakpoints.](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)

  Ocena wyrażenia asynchronicznej wymaga zaimplementowania interfejsu [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) i jego [IDebugExpressionEvaluationCompleteEvent2::GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[i GetResult.](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)

  Zdarzenia synchroniczne wymagają implementacji [metody IDebugEngine2::ContinueFromSynchronousEvent.](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)

  Aby aparat do zapisu danych wyjściowych w stylu ciągu, należy zaimplementować [IDebugOutputStringEvent2::GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) metody.

## <a name="see-also"></a>Zobacz też
- [Kontrola wykonania i ocena stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
