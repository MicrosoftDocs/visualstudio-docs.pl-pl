---
title: Ocena wyrażenia w trybie przerwania | Dokumenty firmy Microsoft
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
ms.openlocfilehash: bc09fc43bd9f0edea4f6dc32e5f37c387c045796
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738725"
---
# <a name="expression-evaluation-in-break-mode"></a>Ocena wyrażenia w trybie przerwania
W poniższej sekcji opisano proces, który występuje, gdy debuger jest w trybie przerwania i musi przeprowadzić ocenę wyrażenia.

## <a name="expression-evaluation-process"></a>Proces oceny wyrażenia
 Poniżej przedstawiono podstawowe kroki związane z oceną wyrażenia:

1. Menedżer debugowania sesji (SDM) wywołuje [IDebugStackFrame2::GetExpressionContext,](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) aby uzyskać interfejs kontekstu wyrażenia [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).

2. SDM następnie wywołuje [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) z ciągiem do przeanalizowania.

3. Jeśli ParseText nie zwraca S_OK, powodem błędu jest zwracany.

     -w przeciwnym razie-

     Jeśli ParseText zwraca S_OK, SDM można następnie wywołać [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub [IDebugExpression2::EvaluateAsync,](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) aby uzyskać wartość końcową z analizowanego wyrażenia.

    - Podczas `IDebugExpression2::EvaluateSync`korzystania, dany interfejs wywołania zwrotnego komunikuje trwający proces oceny. Wartość końcowa jest zwracana w interfejsie [IDebugProperty2.](../../extensibility/debugger/reference/idebugproperty2.md)

    - Podczas `IDebugExpression2::EvaluateAsync`korzystania, dany interfejs wywołania zwrotnego komunikuje trwający proces oceny. Po zakończeniu oceny EvaluateAsync wysyła interfejs [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) za pośrednictwem wywołania zwrotnego. Za pomocą tego interfejsu zdarzenia [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)ostateczna wartość jest owak.

## <a name="see-also"></a>Zobacz też
- [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)
