---
title: Obliczanie wyrażenia w trybie przerwania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 362e50e20519c358564d13ba169f706fe384ca5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152761"
---
# <a name="expression-evaluation-in-break-mode"></a>Ocena wyrażeń w trybie przerwania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Poniżej opisano proces, który występuje, gdy debuger jest w trybie przerwania i musi prowadzić obliczenia wyrażenia.  
  
## <a name="expression-evaluation-process"></a>Proces oceny wyrażeń  
 Oto podstawowe kroki związane z obliczaniem wyrażenia:  
  
1. Menedżer debugowania sesji (SDM) wywołuje [IDebugStackFrame2:: GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) w celu uzyskania interfejsu kontekstu wyrażenia, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2. Model SDM następnie wywołuje [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) z ciągiem, który ma zostać przeanalizowany.  
  
3. Jeśli ParseText nie zwraca S_OK, zwracany jest powód błędu.  
  
     przypadku  
  
     Jeśli ParseText zwraca S_OK, model SDM może następnie wywołać [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) , aby uzyskać ostateczną wartość z przeanalizowanego wyrażenia.  
  
    - W przypadku użycia `IDebugExpression2::EvaluateSync` dany interfejs wywołania zwrotnego jest używany do przekazywania trwającego procesu oceny. Końcowa wartość jest zwracana w interfejsie [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) .  
  
    - W przypadku użycia `IDebugExpression2::EvaluateAsync` dany interfejs wywołania zwrotnego jest używany do przekazywania trwającego procesu oceny. Po zakończeniu oceny EvaluateAsync wysyła Interfejs [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) za pomocą wywołania zwrotnego. Za pomocą tego interfejsu zdarzenia końcowa wartość może zostać uzyskana za pomocą [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wywoływanie zdarzeń debugera](../../extensibility/debugger/calling-debugger-events.md)
