---
title: Pisanie ewaluatora wyrażenia środowiska uruchomieniowego języka wspólnego | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 4e46eaef395a7c66792662b3c5d4b9fbad419dfb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712324"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Pisanie ewaluatora wyrażeń środowiska uruchomieniowego języka wspólnego
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [oceniający wyrażenia CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład oceniającego zarządzane wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Oceniający wyrażenie (EE) jest częścią aparatu debugowania (DE), który obsługuje składni i semantyki języka programowania, który wyprodukował kod jest debugowany. Wyrażenia muszą być oceniane w kontekście języka programowania. Na przykład w niektórych językach wyrażenie "A+B" oznacza "sumę A i B". W innych językach to samo wyrażenie może oznaczać "A lub B". W związku z tym oddzielny EE musi być napisany dla każdego języka programowania, który generuje kod obiektu do debugowania w visual studio IDE.

 Niektóre aspekty pakietu debugowania programu Visual Studio należy interpretować kod w kontekście języka programowania. Na przykład gdy wykonanie zatrzymuje się w punkcie przerwania, wszystkie wyrażenia, które użytkownik wpisał w oknie **czujki,** muszą być oceniane i wyświetlane. Użytkownik może zmienić wartość zmiennej lokalnej, wpisując wyrażenie w oknie **czujki** lub w oknie **Bezpośrednim.**

## <a name="in-this-section"></a>W tej sekcji
 [Wspólne środowisko wykonawcze języka i ocena wyrażeń](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md) W tym artykule wyjaśniono, że podczas integrowania zastrzeżonego języka programowania z ide programu Visual Studio, pisanie EE zdolne do oceny wyrażeń w kontekście języka zastrzeżonego umożliwia kompilowanie do języka pośredniego firmy Microsoft (MSIL) bez pisania aparatu debugowania.

 [Architektura ewaluatora wyrażeń](../../extensibility/debugger/expression-evaluator-architecture.md) W tym artykule omówiono sposób implementacji interfejsów EE wymagane i wywołać wspólnego dostawcy symbolu środowiska wykonawczego języka (SP) i interfejsów spinacza.

 [Rejestrowanie oceniającego wyrażenia](../../extensibility/debugger/registering-an-expression-evaluator.md) Zauważa, że EE musi zarejestrować się jako fabryka klas zarówno w środowisku uruchomieniowym języka wspólnego i środowiska wykonawczego programu Visual Studio.

 [Implementowanie oceniającego wyrażenie](../../extensibility/debugger/implementing-an-expression-evaluator.md) Opisuje, jak proces oceny wyrażenia obejmuje aparat debugowania (DE), dostawca symbolu (SP), obiekt spinacza i oceniający wyrażenie (EE).

 [Pokaż lokalnych](../../extensibility/debugger/displaying-locals.md) Opisuje, jak po wstrzymaniu wykonywania pakiet debugowania wywołuje DE, aby uzyskać listę zmiennych lokalnych i argumentów.

 [Ocena wyrażenia okna zegarka](../../extensibility/debugger/evaluating-a-watch-window-expression.md) Dokumenty, jak pakiet debugowania programu Visual Studio wywołuje DE, aby określić bieżącą wartość każdego wyrażenia na liście obserwowanych.

 [Zmienianie wartości lokalnego](../../extensibility/debugger/changing-the-value-of-a-local.md) Wyjaśnia, że w zmianie wartości lokalnego, każdy wiersz local okna ma skojarzony obiekt, który zawiera nazwę, typ i bieżącą wartość lokalnego.

 [Implementowanie wizualizatorów typów i niestandardowych przejańsków](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md) Wyjaśniono, który interfejs musi zostać zaimplementowany za pomocą którego składnika do obsługi wizualizatorów typów i niestandardowych widzów.

## <a name="see-also"></a>Zobacz też
 [Rozszerzalność debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
