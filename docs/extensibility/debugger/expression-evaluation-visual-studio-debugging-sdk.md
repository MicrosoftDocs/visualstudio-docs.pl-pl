---
title: Szacowanie wyrażeń (zestaw SDK debugowania programu Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b100ccac042aeed3ed8211c56fc1129311d850b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889856"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Obliczanie wyrażenia (Visual Studio debugowanie zestawu SDK)
W trybie break IDE musi zwrócić proste wyrażenia wielu zmiennych program. Aby wykonać ocenę, aparat debugowania (DE) należy przeanalizować i ocenić wyrażenie, które jest wprowadzany do jednego z okien środowiska IDE.

 Wyrażenia są tworzone za pomocą [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metody i reprezentowany przez wartość wynikowa [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfejsu.

 **IDebugExpression2** interfejs jest implementowany przez DE i wywołuje jego **EvalAsync** metodę, aby zwrócić [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfejsu środowiska IDE, aby wyświetlić wyniki oceny wyrażenia w środowisku IDE. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) zwraca strukturę, która jest używana do umieszczenia wartości wyrażenia w **Obejrzyj** okna lub **lokalne** okna.

 Debugowanie pakietu lub sesja debugowania manager (SDM) wywołuje [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) lub [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) można pobrać [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfejs, który reprezentuje wynik oceny. `IDebugProperty2` zawiera metody, które zwracają nazwa, typ i wartość wyrażenia. Te informacje są wyświetlane w różnych oknach debugera.

## <a name="using-expression-evaluation"></a>Za pomocą oceny wyrażenia
 Aby użyć obliczenia wyrażenia, należy zaimplementować [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metody i wszystkie metody [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfejsu, jak pokazano w poniższej tabeli.

|Metoda|Opis|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Oblicza wyrażenie asynchronicznie.|
|[Abort](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Kończy się obliczenia wyrażenia asynchroniczne.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Oblicza wyrażenie synchronicznie.|

 Ocena synchroniczne i asynchroniczne wymagać zaimplementowania [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) metody. Obliczanie wyrażenia asynchroniczne wymaga implementacji [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).

## <a name="see-also"></a>Zobacz także
- [Wykonanie kontroli i stan oceny](../../extensibility/debugger/execution-control-and-state-evaluation.md)