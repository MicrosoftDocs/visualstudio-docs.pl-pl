---
title: Obliczanie wyrażenia w trybie przerwania | Microsoft Docs
description: Dowiedz się więcej o procesie, który występuje, gdy debuger jest w trybie przerwania i musi przeanalizować wyrażenie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e73d98e9fff713258f4797577fd8402932fe266
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2020
ms.locfileid: "96559639"
---
# <a name="expression-evaluation-in-break-mode"></a>Obliczanie wyrażeń w trybie przerwania
W poniższej sekcji opisano proces, który występuje, gdy debuger jest w trybie przerwania i musi prowadzić obliczenia wyrażenia.

## <a name="expression-evaluation-process"></a>Proces oceny wyrażeń
 Poniżej przedstawiono podstawowe kroki związane z obliczaniem wyrażenia:

1. Menedżer debugowania sesji (SDM) wywołuje [IDebugStackFrame2:: GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) , aby uzyskać interfejs kontekstu wyrażenia, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).

2. Model SDM następnie wywołuje [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) z ciągiem, który ma zostać przeanalizowany.

3. Jeśli ParseText nie zwróci S_OK, zwracany jest powód błędu.

     przypadku

     Jeśli ParseText zwraca S_OK, model SDM może następnie wywołać [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) , aby uzyskać ostateczną wartość z przeanalizowanego wyrażenia.

    - W przypadku korzystania `IDebugExpression2::EvaluateSync` z programu dany interfejs wywołania zwrotnego komunikuje trwający proces oceny. Końcowa wartość jest zwracana w interfejsie [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) .

    - W przypadku korzystania `IDebugExpression2::EvaluateAsync` z programu dany interfejs wywołania zwrotnego komunikuje trwający proces oceny. Po zakończeniu oceny EvaluateAsync wysyła Interfejs [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) za pomocą wywołania zwrotnego. Za pomocą tego interfejsu zdarzenia końcowa wartość jest wynikiem [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).

## <a name="see-also"></a>Zobacz także
- [Zdarzenia debugera wywołań](../../extensibility/debugger/calling-debugger-events.md)
