---
title: Obliczanie wyrażeń (zestaw SDK debugowania Visual Studio) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738712"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Obliczanie wyrażeń (zestaw SDK debugowania programu Visual Studio)
W trybie przerwania IDE musi oszacować proste wyrażenia obejmujące kilka zmiennych programu. Aby wykonać swoją ocenę, aparat debugowania (DE) musi analizować i oceniać wyrażenie, które jest wprowadzane do jednego z okien IDE.

 Wyrażenia są tworzone przy użyciu metody [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) i reprezentowanej przez otrzymany Interfejs [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) .

 Interfejs **IDebugExpression2** jest implementowany przez de i wywołuje metodę **EvalAsync** w celu ZWRÓCENIA interfejsu [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) do IDE w celu wyświetlenia wyników oceny wyrażenia w IDE. [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) zwraca strukturę, która jest używana do umieszczania wartości wyrażenia w oknie **czujki** lub w oknie **zmiennych lokalnych** .

 Pakiet Debug lub Menedżer debugowania sesji (SDM) wywołuje [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) lub [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) , aby uzyskać Interfejs [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , który reprezentuje wynik oceny. `IDebugProperty2` ma metody, które zwracają nazwę, typ i wartość wyrażenia. Te informacje są wyświetlane w różnych oknach debugera.

## <a name="using-expression-evaluation"></a>Używanie oceny wyrażeń
 Aby użyć oceny wyrażeń, należy zaimplementować metodę [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) i wszystkie metody interfejsu [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , jak pokazano w poniższej tabeli.

|Metoda|Opis|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Zwraca wartość wyrażenia asynchronicznie.|
|[Anuluj](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Zakończenie obliczania wyrażeń asynchronicznych.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Oblicza wyrażenie synchronicznie.|

 Obliczanie synchroniczne i asynchroniczne wymagają wykonania metody [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) . Obliczanie wyrażeń asynchronicznych wymaga implementacji elementu [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).

## <a name="see-also"></a>Zobacz też
- [Kontrola wykonywania i Ocena stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
