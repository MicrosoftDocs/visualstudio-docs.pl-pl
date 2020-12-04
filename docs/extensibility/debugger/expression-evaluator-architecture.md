---
title: Architektura ewaluatora wyrażeń | Microsoft Docs
description: Dowiedz się więcej o integrowaniu języka własnościowego z pakietem debugowania programu Visual Studio, w tym ewaluatora wyrażeń i dostawcami symboli/interfejsów spinacza.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 216bf2f19d528084685a2361a158e105e2284010
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560164"
---
# <a name="expression-evaluator-architecture"></a>Architektura ewaluatora wyrażeń
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz testerzy [wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzana próbnik wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Integrowanie języka własnościowego z pakietem debugowania programu Visual Studio oznacza, że musisz skonfigurować wymagane interfejsy ewaluatora wyrażeń (EE) i wywoływać interfejsy dostawcy symboli czasu uruchomieniowego (SP) i programu bindery typowego języka. Obiekty SP i Binder, wraz z bieżącym adresem wykonywania, to kontekst, w którym są oceniane wyrażenia. Informacje, które te interfejsy produkują i zużywają, przedstawiają kluczowe koncepcje dotyczące architektury EE.

## <a name="overview"></a>Omówienie

### <a name="parse-the-expression"></a>Analizowanie wyrażenia
 Podczas debugowania programu wyrażenia są oceniane z kilku powodów, ale zawsze, gdy debugowany program został zatrzymany w punkcie przerwania (punkt przerwania umieszczony przez użytkownika lub jeden z nich spowodowany przez wyjątek). Obecnie jest to możliwe, gdy program Visual Studio uzyska ramkę stosu, jak to zostało reprezentowane przez interfejs [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , z aparatu debugowania. Program Visual Studio następnie wywołuje [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) , aby uzyskać Interfejs [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) . Ten interfejs reprezentuje kontekst, w którym można ocenić wyrażenia; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) jest punktem wejścia do procesu oceny. Do tego momentu wszystkie interfejsy są implementowane przez DE.

 Gdy `IDebugExpressionContext2::ParseText` jest wywoływana, powoduje de tworzy wystąpienie programu EE skojarzone z językiem pliku źródłowego, w którym wystąpiło punkt przerwania (a także tworzy wystąpienie SH na tym etapie). Program EE jest reprezentowany przez interfejs [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) . A następnie wywołuje metodę [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) , aby przekonwertować wyrażenie (w formie tekstowej) na wyrażenie przeanalizowane, gotowe do oceny. To wyrażenie analizowane jest reprezentowane przez interfejs [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) . Wyrażenie jest zwykle analizowane i nie jest oceniane w tym momencie.

 Element DE tworzy obiekt, który implementuje interfejs [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , umieszcza `IDebugParsedExpression` obiekt w `IDebugExpression2` obiekcie i zwraca `IDebugExpression2` obiekt z `IDebugExpressionContext2::ParseText` .

### <a name="evaluate-the-expression"></a>Oceń wyrażenie
 Program Visual Studio wywołuje [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) , aby oszacować przeanalizowane wyrażenie. Obie metody wywołują [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) ( `IDebugExpression2::EvaluateSync` wywołuje metodę natychmiast, jednocześnie `IDebugExpression2::EvaluateAsync` wywołuje metodę przez wątek w tle), aby oszacować przeanalizowane wyrażenie i zwrócić Interfejs [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , który reprezentuje wartość i typ wyanalizowanego wyrażenia. `IDebugParsedExpression::EvaluateSync` używa dostarczonych wartości SH, Address i Binder, aby przekonwertować przeanalizowane wyrażenie na wartość rzeczywistą reprezentowane przez `IDebugProperty2` interfejs.

### <a name="for-example"></a>Na przykład
 Po trafieniu punktu przerwania w uruchomionym programie użytkownik wybiera zmienną w oknie dialogowym **QuickWatch** . To okno dialogowe zawiera nazwę zmiennej, jej wartość i typ. Użytkownik może zazwyczaj zmienić wartość.

 Gdy zostanie wyświetlone okno dialogowe **QuickWatch** , nazwa analizowanej zmiennej jest wysyłana jako tekst do [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Zwraca obiekt [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) reprezentujący wyrażenie przeanalizowane, w tym przypadku zmienną. [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) jest następnie wywoływana w celu utworzenia `IDebugProperty2` obiektu, który reprezentuje wartość zmiennej i typ, a także jego nazwę. Są to informacje, które są wyświetlane.

 Jeśli użytkownik zmieni wartość zmiennej, [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) jest wywoływana z nową wartością, która zmienia wartość zmiennej w pamięci, dzięki czemu zostanie użyta, gdy program wznawia działanie.

 Aby uzyskać szczegółowe informacje na temat tego procesu wyświetlania wartości zmiennych, zobacz temat [Wyświetlanie ustawień lokalnych](../../extensibility/debugger/displaying-locals.md) . Aby uzyskać szczegółowe informacje na temat zmiany wartości zmiennej, zobacz [zmiana wartości elementu lokalnego](../../extensibility/debugger/changing-the-value-of-a-local.md) .

## <a name="in-this-section"></a>W tej sekcji
 [Kontekst oceny](../../extensibility/debugger/evaluation-context.md) Dostarcza argumenty, które są przekazane, gdy wywołanie EE zostanie zakończone.

 [Interfejsy ewaluatora wyrażeń klucza](../../extensibility/debugger/key-expression-evaluator-interfaces.md) Opisuje kluczowe interfejsy, które są niezbędne podczas pisania EE, wraz z kontekstem oceny.

## <a name="see-also"></a>Zobacz także
- [Pisanie ewaluatora wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Wyświetlanie ustawień lokalnych](../../extensibility/debugger/displaying-locals.md)
- [Zmiana wartości elementu lokalnego](../../extensibility/debugger/changing-the-value-of-a-local.md)
