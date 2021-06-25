---
title: Ocena wyrażeń (Visual Studio SDK debugowania) | Microsoft Docs
description: W trybie przerwania ide ocenia wyrażenia obejmujące zmienne programu. Dowiedz się, jak aparat debugowania analizuje i ocenia wyrażenie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cf213c30ef26490b44579d83c68b2640360584a7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904516"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Ocena wyrażeń (Visual Studio SDK debugowania)
W trybie przerwania ide musi oceniać proste wyrażenia obejmujące kilka zmiennych programu. Aby można było dokonać oceny, aparat debugowania (DE) musi analizuje i oceniać wyrażenie wprowadzone w jednym z okien środowiska IDE.

 Wyrażenia są tworzone przy użyciu metody [IDebugExpressionContext2::P arseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) i reprezentowane przez wynikowy interfejs [IDebugExpression2.](../../extensibility/debugger/reference/idebugexpression2.md)

 **Interfejs IDebugExpression2** jest implementowany przez de i wywołuje jego metodę **EvalAsync** w celu zwrócenia [interfejsu IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) do środowiska IDE w celu wyświetlenia wyników oceny wyrażenia w ide. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) zwraca strukturę, która jest używana do umieszczania wartości wyrażenia w oknie wyrażenie czujki lub w **oknie Wartości** lokalne. 

 Pakiet debugowania lub menedżer debugowania sesji (SDM) wywołuje interfejs [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) lub [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) w celu uzyskania interfejsu [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) reprezentującego wynik oceny. `IDebugProperty2` Metoda ma metody, które zwracają nazwę, typ i wartość wyrażenia. Te informacje są wyświetlane w różnych oknach debugera.

## <a name="using-expression-evaluation"></a>Korzystanie z oceny wyrażeń
 Aby użyć oceny wyrażeń, należy zaimplementować metodę [IDebugExpressionContext2::P arseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) i wszystkie metody interfejsu [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) jak pokazano w poniższej tabeli.

|Metoda|Opis|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Oblicza wyrażenie asynchronicznie.|
|[Przerwać](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Kończy ocenę wyrażeń asynchronicznych.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Ocenia wyrażenie synchronicznie.|

 Ocena synchroniczna i asynchroniczna wymaga implementacji metody [IDebugProperty2::GetPropertyInfo.](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) Asynchroniczna ocena wyrażeń wymaga [implementacji interfejsu IDebugExpressionEvaluationCompleteEvent2.](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)

## <a name="see-also"></a>Zobacz też
- [Kontrola wykonywania i ocena stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
