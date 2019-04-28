---
title: Obliczanie wyrażenia w trybie przerwania | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a31bc56673ec9e82206a8829aaf89328eb9198d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925684"
---
# <a name="expression-evaluation-in-break-mode"></a>Obliczanie wyrażenia w trybie przerwania
W poniższej sekcji opisano proces, który występuje, gdy debuger jest w trybie przerwania, a także musi przeprowadzić obliczenia wyrażenia.

## <a name="expression-evaluation-process"></a>Proces oceny wyrażenia
 Poniżej przedstawiono podstawowe etapy obliczenia wyrażenia:

1. Menedżer debugowania sesji (SDM) wywołuje [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) uzyskać interfejs wyrażenia kontekstu [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).

2. Następnie wywołuje SDM [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) ciąg, który ma być analizowany.

3. Jeśli ParseText nie zwraca S_OK, zwracany jest przyczyną tego błędu.

     — w przeciwnym-

     Jeśli ParseText zwróci S_OK, SDM następnie wywołać albo [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) można pobrać jako końcowa wartość wyrażenia przeanalizowany.

    - Korzystając z `IDebugExpression2::EvaluateSync`, interfejs wywołania zwrotnego danego komunikuje się ciągły proces oceny. Końcowa wartość jest zwracana w [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfejsu.

    - Korzystając z `IDebugExpression2::EvaluateAsync`, interfejs wywołania zwrotnego danego komunikuje się ciągły proces oceny. Po zakończeniu oceny EvaluateAsync wysyła [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) interfejs za pomocą wywołania zwrotnego. Z tym interfejsem zdarzeń końcowa wartość wyniki z [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).

## <a name="see-also"></a>Zobacz także
- [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)