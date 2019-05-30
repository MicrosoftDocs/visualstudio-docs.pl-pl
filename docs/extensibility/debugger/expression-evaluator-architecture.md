---
title: Architektura ewaluatora wyrażeń | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42c52e3d6b71b58668a05434e9ca8f65eb3e7832
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353762"
---
# <a name="expression-evaluator-architecture"></a>Architektura ewaluatora wyrażeń
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Uzyskać informacji o implementowaniu ewaluatory wyrażeń CLR, zobacz [ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykładowe ewaluatora wyrażeń zarządzane](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Integrowanie własności języka programu Visual Studio, debugowanie pakietu oznacza, że możesz musisz skonfigurować wymagane wyrażenie interfejsy ewaluatora (EE) i wywoływania dostawcy symbol środowiska wykonawczego języka wspólnego (SP) i interfejsów integratorów modeli. SP i integratorów modeli obiektów, wraz z bieżącego adresu wykonywania są kontekst, w którym określeń są oceniane. Informacje te interfejsy, tworzenia i wykorzystywania reprezentuje podstawowe pojęcia dotyczące architektury EE.

## <a name="overview"></a>Omówienie

### <a name="parse-the-expression"></a>Przeanalizować wyrażenia
 Podczas debugowania programu wyrażenia są obliczane przez liczbę powodów, ale zawsze gdy program poddawany został zatrzymany w punkcie przerwania (punkt przerwania umieszczone przez użytkownika lub jedną spowodowane przez wyjątek). Jest w tej chwili, gdy program Visual Studio uzyskuje ramkę stosu, reprezentowane przez [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interfejsu z aparatu debugowania (DE). Program Visual Studio następnie wywołuje [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) można pobrać [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfejsu. Ten interfejs reprezentuje kontekst, w którym mogą być obliczane wyrażenia; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) jest punktem wejścia do procesu oceny. Do tej pory wszystkie interfejsy są implementowane przez DE.

 Gdy `IDebugExpressionContext2::ParseText` jest wywoływana, DE tworzy EE skojarzone z językiem pliku źródłowego, gdzie wystąpił punkt przerwania (DE również tworzy SH w tym momencie). EE jest reprezentowany przez [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) interfejsu. Następnie wywołuje DE [przeanalizować](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) można przekonwertować wyrażenia (w postaci tekstu) do przeanalizowanej wyrażenia, gotowe do oceny. To wyrażenie przeanalizowany jest reprezentowany przez [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) interfejsu. Wyrażenie jest zazwyczaj przeanalizować i nie są sprawdzane w tym momencie.

 DE tworzy obiekt, który implementuje [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfejsu umieszcza `IDebugParsedExpression` do obiektu `IDebugExpression2` obiektu i zwraca `IDebugExpression2` obiektu z `IDebugExpressionContext2::ParseText`.

### <a name="evaluate-the-expression"></a>Obliczenia wyrażenia
 Wywołuje program Visual Studio, albo [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) można obliczyć wartości wyrażenia przeanalizowany. Obie te metody wywołania [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (`IDebugExpression2::EvaluateSync` wywołuje metodę natychmiast, podczas gdy `IDebugExpression2::EvaluateAsync` wywołuje metodę za pomocą wątku w tle) wyrażenie przeanalizowany oceniana i zwracana [ IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interfejs, który reprezentuje wartość i typ wyrażenia przeanalizowany. `IDebugParsedExpression::EvaluateSync` używa podanej SH, adres i obiekt wiążący Aby przekonwertować wyrażenia przeanalizowana wartość rzeczywistą, reprezentowane przez `IDebugProperty2` interfejsu.

### <a name="for-example"></a>Na przykład
 Po osiągnięciu punktu przerwania w uruchomiony program użytkownik wybierze opcję wyświetlania zmiennej w **QuickWatch** okno dialogowe. To okno dialogowe zawiera nazwę zmiennej, jego wartość i jego typu. Użytkownik może zmienić zazwyczaj wartość.

 Gdy **QuickWatch** okno dialogowe jest wyświetlana, nazwa zmiennej, sprawdzane są wysyłane jako tekst w celu [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Spowoduje to zwrócenie [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) obiekt reprezentujący wyrażenie przeanalizowany, w tym przypadku, zmienna. [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) jest następnie wywoływana w celu wygenerowania `IDebugProperty2` obiekt, który reprezentuje wartość zmiennej i typ, a także jego nazwę. Jest to wyświetlane informacje.

 Jeśli użytkownik zmieni wartość zmiennej [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) jest wywoływana z nową wartością, która zmienia wartość zmiennej w pamięci, dzięki czemu będzie on używany, gdy program wznawia uruchomiona.

 Zobacz [wyświetlanie zmiennych lokalnych](../../extensibility/debugger/displaying-locals.md) Aby uzyskać więcej informacji na temat tego procesu wyświetlania wartości zmiennych. Zobacz [zmiana wartości zmiennej lokalnej](../../extensibility/debugger/changing-the-value-of-a-local.md) więcej informacji na temat sposobu zmiennej wartość zostanie zmieniona.

## <a name="in-this-section"></a>W tej sekcji
 [Kontekst oceny](../../extensibility/debugger/evaluation-context.md) zawiera argumenty, które są przekazywane, gdy DE wywołuje EE.

 [Interfejsy ewaluatora wyrażeń klucza](../../extensibility/debugger/key-expression-evaluator-interfaces.md) Opisuje kluczowe interfejsy, podczas zapisywania EE wraz z kontekstu oceny.

## <a name="see-also"></a>Zobacz także
- [Pisanie ewaluatora wyrażeń środowiska CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Wyświetlanie zmiennych lokalnych](../../extensibility/debugger/displaying-locals.md)
- [Zmienianie wartości zmiennej lokalnej](../../extensibility/debugger/changing-the-value-of-a-local.md)