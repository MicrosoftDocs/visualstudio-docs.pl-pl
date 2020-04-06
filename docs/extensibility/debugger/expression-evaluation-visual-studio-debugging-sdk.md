---
title: Ocena wyrażenia (zestaw SDK debugowania programu Visual Studio) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e41179fd530818f5ac59aa54420ede1b4eafa1ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738712"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Ocena wyrażenia (zestaw SDK debugowania programu Visual Studio)
W trybie przerwania IDE musi oceniać proste wyrażenia obejmujące kilka zmiennych programu. Aby wykonać jego oceny, aparat debugowania (DE) musi analizować i oceniać wyrażenie, które jest wprowadzone w jednym z okien IDE.

 Wyrażenia są tworzone za pomocą [metody IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) i są reprezentowane przez wynikowy interfejs [IDebugExpression2.](../../extensibility/debugger/reference/idebugexpression2.md)

 Interfejs **IDebugExpression2** jest implementowany przez DE i wywołuje jego **EvalAsync** metody zwracania interfejsu [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) do IDE, w celu wyświetlenia wyników oceny wyrażenia w IDE. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) zwraca strukturę, która jest używana do umieszczenia wartości wyrażenia w oknie **Czujka** lub w oknie **Locals.**

 Pakiet debugowania lub menedżer debugowania sesji (SDM) wywołuje [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) lub [EvaluateSync,](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) aby uzyskać interfejs [IDebugProperty2,](../../extensibility/debugger/reference/idebugproperty2.md) który reprezentuje wynik oceny. `IDebugProperty2`ma metody, które zwracają nazwę, typ i wartość wyrażenia. Te informacje są wyświetlane w różnych oknach debugera.

## <a name="using-expression-evaluation"></a>Korzystanie z oceny wyrażenia
 Aby użyć oceny wyrażenia, należy zaimplementować [metodę IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) i wszystkie metody interfejsu [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) jak pokazano w poniższej tabeli.

|Metoda|Opis|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Ocenia wyrażenie asynchronicznie.|
|[Przerwanie](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Kończy ocenę wyrażenia asynchronicznej.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Oblicza wyrażenie synchronicznie.|

 Synchronicznej i asynchronicznej oceny wymagają zaimplementowania [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metody. Ocena wyrażenia asynchronicznej wymaga implementacji [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).

## <a name="see-also"></a>Zobacz też
- [Kontrola wykonania i ocena stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
