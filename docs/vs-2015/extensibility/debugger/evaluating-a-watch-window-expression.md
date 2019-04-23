---
title: Ocenianie wyrażenia okna wyrażeń kontrolnych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6b5ea8cbdfa9644e103f32d49ea0964bbb90bad8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60075860"
---
# <a name="evaluating-a-watch-window-expression"></a>Ocenianie wyrażenia okna wyrażeń kontrolnych
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacji dotyczących implementowania ewaluatory wyrażeń CLR, zobacz [Ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykładowe ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Podczas wykonywania jest wstrzymana, Visual Studio wywołuje aparat debugowania (DE), aby określić bieżącą wartość każde wyrażenie w swojej listy obserwowanych. DE ocenia każdy wyrażenia przy użyciu ewaluatora wyrażeń (EE) i Visual Studio wyświetla jego wartości w **Obejrzyj** okna.  
  
 Poniżej przedstawiono omówienie sposobu szacowania wyrażenia kontrolnego listy:  
  
1. Program Visual Studio wywołuje DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) pobrać kontekstu wyrażenia, który może służyć do oceny wyrażenia.  
  
2. Dla każdego wyrażenia na liście wywołań programu Visual Studio [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) do konwertowania tekstu wyrażenia do przeanalizowanej wyrażenia.  
  
3. `IDebugExpressionContext2::ParseText` wywołania [przeanalizować](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) do wykonują rzeczywistą pracę analizy tekstu i wygenerować [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) obiektu.  
  
4. `IDebugExpressionContext2::ParseText` Tworzy [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) obiektu i umieszcza `IDebugParsedExpression` obiektu do niego. Mam`DebugExpression2` obiekt jest następnie zwracany do programu Visual Studio.  
  
5. Visual Studio wywołania [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) można obliczyć wartości wyrażenia przeanalizowany.  
  
6. `IDebugExpression2::EvaluateSync` przekazuje wywołanie [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) oceny rzeczywiste i wygenerować [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) obiekt, który jest zwracany do programu Visual Studio.  
  
7. Visual Studio wywołania [getpropertyinfo —](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) do uzyskania wartości wyrażenia, które są następnie wyświetlane na liście obserwowanych.  
  
## <a name="parse-then-evaluate"></a>Analizowanie, a następnie oceny  
 Ponieważ analizowania złożone wyrażenie może trwać znacznie dłużej niż jej oceny, procesu oceny wyrażenia został podzielony na dwie czynności: ((1) analizowania wyrażenia i 2) obliczenia wyrażenia przeanalizowany. W ten sposób oceny można przeprowadzić na wiele razy, ale wyrażenie musi być analizowana tylko raz. Pośredni przeanalizowany wyrażenie jest zwracana z EE w [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) obiekt, który z kolei jest hermetyzowany i zwrócony z DE jako [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) obiektu. `IDebugExpression` Obiekt różni się wszystkie oceny `IDebugParsedExpression` obiektu.  
  
> [!NOTE]
>  Nie jest konieczne EE stosować się do ten dwuetapowy proces, mimo że program Visual Studio zakłada EE można przeanalizować i oceny w tym samym kroku podczas [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) nosi nazwę (jest to przykład MyCEE działania, na przykład). Język może tworzyć złożone wyrażenia, można oddzielić kroku analizy od kroku oceny. Może to zwiększyć wydajność w debugerze programu Visual Studio, gdy wiele Obejrzyj wyrażenia są pokazywane.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przykład implementacji oceny wyrażenia](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 Używa przykładowych MyCEE, aby przejść przez proces oceny wyrażenia.  
  
 [Ocenianie wyrażenia kontrolnego](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 W tym artykule wyjaśniono, co się stanie po przeanalizowaniu pomyślne wyrażenia.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Kontekst oceny](../../extensibility/debugger/evaluation-context.md)  
 Zawiera argumenty, które są przekazywane, gdy aparat debugowania (DE) wywołuje Ewaluator wyrażeń (EE).  
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie ewaluatora wyrażeń środowiska CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
