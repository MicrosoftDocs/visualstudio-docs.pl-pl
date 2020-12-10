---
title: Pisanie ewaluatora wyrażeń środowiska uruchomieniowego języka wspólnego | Microsoft Docs
description: Dowiedz się więcej na temat pisania ewaluatora wyrażeń dla środowiska uruchomieniowego języka wspólnego, które oblicza wyrażenia w debugowanym języku kodu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1674ae8345873ede5d1b4afb04774d6ed0469b4c
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996321"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Pisanie ewaluatora wyrażeń środowiska uruchomieniowego języka wspólnego
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz testerzy [wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzana próbnik wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Ewaluatora wyrażeń (EE) jest częścią aparatu debugowania (DE), która obsługuje składnię i semantykę języka programowania, który wygenerował kod debugowany. Wyrażenia muszą być oceniane w kontekście języka programowania. Na przykład w niektórych językach wyrażenie "A + B" oznacza "sumę a i B". W innych językach to samo wyrażenie może oznaczać "A lub B". W tym celu należy napisać osobne wersje EE dla każdego języka programowania, który generuje kod obiektu do debugowania w środowisku IDE programu Visual Studio.

 Niektóre aspekty pakietu debugowania programu Visual Studio muszą interpretować kod w kontekście języka programowania. Na przykład po zatrzymaniu wykonywania w punkcie przerwania, wszystkie wyrażenia, które użytkownik wpisze do okna **czujki** , muszą być oceniane i wyświetlane. Użytkownik może zmienić wartość zmiennej lokalnej, wpisując wyrażenie w oknie **czujki** lub w oknie **bezpośrednim** .

## <a name="in-this-section"></a>W tej sekcji
 [Środowisko uruchomieniowe języka wspólnego i Ocena wyrażeń](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md) Wyjaśniono, że podczas integrowania własnościowego języka programowania z programem Visual Studio IDE, pisanie EE może oceniać wyrażenia w kontekście języka własnościowego, dzięki czemu można kompilować do języka pośredniego firmy Microsoft (MSIL) bez konieczności pisania aparatu debugowania.

 [Architektura ewaluatora wyrażeń](../../extensibility/debugger/expression-evaluator-architecture.md) W tym artykule omówiono sposób implementacji wymaganych interfejsów EE i wywoływania dostawcy symboli środowiska uruchomieniowego języka wspólnego (SP) i interfejsów spinacza.

 [Rejestrowanie ewaluatora wyrażeń](../../extensibility/debugger/registering-an-expression-evaluator.md) Uwagi, że EE muszą zarejestrować się jako fabrykę klasy zarówno w środowisku uruchomieniowym języka wspólnego, jak i w środowiskach środowiska uruchomieniowego programu Visual Studio.

 [Implementowanie ewaluatora wyrażeń](../../extensibility/debugger/implementing-an-expression-evaluator.md) Opisuje, jak proces oceny wyrażenia obejmuje aparat debugowania (DE), dostawcę symboli (SP), obiekt spinacza oraz ewaluatora wyrażeń (EE).

 [Wyświetl elementy lokalne](../../extensibility/debugger/displaying-locals.md) Opisuje, jak w przypadku wstrzymania wykonywania pakiet debugowania wywołuje polecenie Cofnij, aby uzyskać listę zmiennych lokalnych i argumentów.

 [Oceń wyrażenie okna czujki](../../extensibility/debugger/evaluating-a-watch-window-expression.md) Dokumenty, w jaki sposób pakiet debugowania programu Visual Studio wywołuje metodę DE, aby określić bieżącą wartość każdego wyrażenia na liście obserwowanych elementów.

 [Zmień wartość lokalnego](../../extensibility/debugger/changing-the-value-of-a-local.md) Wyjaśniono, że w przypadku zmiany wartości lokalnej każdy wiersz okna zmiennych lokalnych ma skojarzony obiekt, który zawiera nazwę, typ i bieżącą wartość lokalnego.

 [Implementowanie wizualizatorów typów i podglądów niestandardowych](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md) Wyjaśnia, który interfejs musi być zaimplementowany przez składnik do obsługi wizualizatorów typów i niestandardowych osób przeglądających.

## <a name="see-also"></a>Zobacz też
 [Rozszerzalność debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
