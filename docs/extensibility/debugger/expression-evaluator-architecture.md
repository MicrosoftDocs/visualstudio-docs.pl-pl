---
title: Architektura ewaluatora wyrażeń | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aac782c653f230d5598a49d43eb70f548de6dc41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738697"
---
# <a name="expression-evaluator-architecture"></a>Architektura ewaluatora wyrażeń
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [oceniający wyrażenia CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład oceniającego zarządzane wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Integracja zastrzeżonego języka z pakietem debugowania programu Visual Studio oznacza, że należy skonfigurować interfejsy wymaganego oceniającego wyrażenie (EE) i wywołać wspólny dostawca symboli wykonywania języka (SP) i interfejsy spinacza. SP i spinacza obiektów, wraz z bieżącego adresu wykonywania, są kontekst, w którym wyrażenia są oceniane. Informacje, które te interfejsy produkują i zużywają reprezentuje kluczowe pojęcia w architekturze EE.

## <a name="overview"></a>Omówienie

### <a name="parse-the-expression"></a>Analizuj wyrażenie
 Podczas debugowania programu wyrażenia są oceniane z wielu powodów, ale zawsze, gdy program debugowany został zatrzymany w punkcie przerwania (punkt przerwania umieszczony przez użytkownika lub jeden spowodowany przez wyjątek). Jest w tym momencie, gdy visual studio uzyskuje ramki stosu, reprezentowane przez interfejs [IDebugStackFrame2,](../../extensibility/debugger/reference/idebugstackframe2.md) z aparatu debugowania (DE). Visual Studio następnie wywołuje [GetExpressionContext,](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) aby uzyskać [interfejs IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md) Ten interfejs reprezentuje kontekst, w którym wyrażenia mogą być oceniane; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) jest punktem wejścia do procesu oceny. Do tego momentu wszystkie interfejsy są implementowane przez DE.

 Po `IDebugExpressionContext2::ParseText` wywołaniu DE wystąpienia EE skojarzone z językiem pliku źródłowego, w którym wystąpił punkt przerwania (DE również wystąpienia SH w tym momencie). EE jest reprezentowany przez interfejs [IDebugExpressionEvaluator.](../../extensibility/debugger/reference/idebugexpressionevaluator.md) De następnie wywołuje [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) przekonwertować wyrażenie (w formie tekstowej) do wyrażenia analizowane, gotowe do oceny. To wyrażenie analizowane jest reprezentowane przez interfejs [IDebugParsedExpression.](../../extensibility/debugger/reference/idebugparsedexpression.md) Wyrażenie jest zazwyczaj analizowane i nie jest oceniane w tym momencie.

 DE tworzy obiekt, który implementuje interfejs [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) `IDebugParsedExpression` `IDebugExpression2` umieszcza obiekt w `IDebugExpression2` obiekcie i zwraca obiekt z `IDebugExpressionContext2::ParseText`.

### <a name="evaluate-the-expression"></a>Oceń wyrażenie
 Visual Studio wywołuje [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) do oceny analizowane wyrażenie. Obie te metody [wywołać EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (`IDebugExpression2::EvaluateSync` `IDebugExpression2::EvaluateAsync` wywołuje metodę natychmiast, podczas gdy wywołuje metodę za pośrednictwem wątku w tle) do oceny analizowane wyrażenie i zwraca interfejs [IDebugProperty2,](../../extensibility/debugger/reference/idebugproperty2.md) który reprezentuje wartość i typ wyrażenia analizowane. `IDebugParsedExpression::EvaluateSync`używa podanego modułu SH, adresu i spinacza do konwersji analizowanego `IDebugProperty2` wyrażenia na rzeczywistą wartość, reprezentowaną przez interfejs.

### <a name="for-example"></a>Na przykład:
 Po trafieniu punktu przerwania w uruchomionym programie użytkownik zdecyduje się wyświetlić zmienną w oknie dialogowym **QuickWatch.** To okno dialogowe zawiera nazwę zmiennej, jej wartość i jej typ. Użytkownik zazwyczaj można zmienić wartość.

 Po wyświetleniu okna dialogowego **QuickWatch** nazwa badanej zmiennej jest wysyłana jako tekst do [programu ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Zwraca obiekt [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) reprezentujący wyrażenie analizowane, w tym przypadku zmienną. [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) jest następnie wywoływana do tworzenia obiektu, `IDebugProperty2` który reprezentuje zmienną wartość i typ, a także jego nazwę. Jest to informacja, która jest wyświetlana.

 Jeśli użytkownik zmieni wartość zmiennej, [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) jest wywoływana z nową wartością, która zmienia wartość zmiennej w pamięci, dzięki czemu będzie używana, gdy program wznowi uruchamianie.

 Zobacz [Wyświetlanie lokalnych,](../../extensibility/debugger/displaying-locals.md) aby uzyskać więcej informacji na temat tego procesu wyświetlania wartości zmiennych. Zobacz [Zmienianie wartości lokalnego, aby](../../extensibility/debugger/changing-the-value-of-a-local.md) uzyskać więcej informacji na temat zmiany wartości zmiennej.

## <a name="in-this-section"></a>W tej sekcji
 [Kontekst oceny](../../extensibility/debugger/evaluation-context.md) Zawiera argumenty, które są przekazywane, gdy DE wywołuje EE.

 [Interfejsy oceniającego kluczowe wyrażenia](../../extensibility/debugger/key-expression-evaluator-interfaces.md) Opisuje kluczowe interfejsy potrzebne podczas pisania EE, wraz z kontekstu oceny.

## <a name="see-also"></a>Zobacz też
- [Pisanie ewaluatora wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Wyświetlanie lokalnych](../../extensibility/debugger/displaying-locals.md)
- [Zmiana wartości lokalnego](../../extensibility/debugger/changing-the-value-of-a-local.md)
