---
title: Ocena wyrażenia okna zegarka | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9cef2f27eec095ee7b136153ecb764feba9effbb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738840"
---
# <a name="evaluate-a-watch-window-expression"></a>Ocena wyrażenia okna zegarka
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [oceniający wyrażenia CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład oceniającego zarządzane wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Po wstrzymaniu wykonywania visual studio wywołuje aparat debugowania (DE), aby określić bieżącą wartość każdego wyrażenia na liście obserwowanych. DE ocenia każde wyrażenie przy użyciu ewaluatora wyrażenia (EE), a visual studio wyświetla jego wartość w **watch** okna.

 Poniżej przedstawiono omówienie sposobu oceny wyrażenia listy obserwowanych:

1. Visual Studio wywołuje [DE GetExpressionContext,](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) aby uzyskać kontekst wyrażenia, które mogą służyć do oceny wyrażeń.

2. Dla każdego wyrażenia na liście obserwowanych program Visual Studio wywołuje [ParseText,](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) aby przekonwertować tekst wyrażenia na wyrażenie analizowane.

3. `IDebugExpressionContext2::ParseText`wywołuje [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) do wykonywania rzeczywistej pracy analizowania tekstu i produkcji [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) obiektu.

4. `IDebugExpressionContext2::ParseText`tworzy obiekt [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) i `IDebugParsedExpression` umieszcza w nim obiekt. Ten`DebugExpression2` obiekt I jest następnie zwracany do programu Visual Studio.

5. Visual Studio wywołuje [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) do oceny wyrażenia analizowane.

6. `IDebugExpression2::EvaluateSync`przekazuje wywołanie [evaluatesync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) do rzeczywistej oceny i produkcji [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) obiektu, który jest zwracany do programu Visual Studio.

7. Visual Studio wywołuje [GetPropertyInfo,](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) aby uzyskać wartość wyrażenia, które jest następnie wyświetlane na liście obserwowanych.

## <a name="parse-then-evaluate"></a>Analizuj, a następnie oceń
 Ponieważ analizowanie wyrażenia złożonego może trwać znacznie dłużej niż jego ocena, proces oceny wyrażenia jest podzielony na dwa kroki: 1) przeanalizowanie wyrażenia i 2) oceny wyrażenia analizowanego. W ten sposób ocena może wystąpić wiele razy, ale wyrażenie musi być analizowane tylko raz. Pośrednie analizowane wyrażenie jest zwracany z EE w [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) obiektu, który jest z kolei hermetyzowany i zwracany z DE jako [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) obiektu. Obiekt `IDebugExpression` odpiera wszystkie `IDebugParsedExpression` oceny do obiektu.

> [!NOTE]
> Nie jest konieczne, aby EE stosować się do tego dwuetapowego procesu, mimo że visual studio zakłada, że to; EE może analizować i oceniać w tym samym kroku, gdy [evaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) jest wywoływana (jest to, jak działa przykład MyCEE, na przykład). Jeśli język może tworzyć złożone wyrażenia, można oddzielić krok analizy od kroku oceny. Może to zwiększyć wydajność w debugerze programu Visual Studio, gdy wiele wyrażeń zegarka są wyświetlane.

## <a name="in-this-section"></a>W tej sekcji
 [Przykładowa implementacja oceny wyrażenia](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md) Używa przykładu MyCEE, aby przejść przez proces oceny wyrażenia.

 [Ocena wyrażenia zegarka](../../extensibility/debugger/evaluating-a-watch-expression.md) Wyjaśnia, co się dzieje po pomyślnej analizy wyrażenia.

## <a name="related-sections"></a>Powiązane sekcje
 [Kontekst oceny](../../extensibility/debugger/evaluation-context.md) Zawiera argumenty, które są przekazywane, gdy aparat debugowania (DE) wywołuje oceniającego wyrażenie (EE).

## <a name="see-also"></a>Zobacz też
 [Pisanie ewaluatora wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
