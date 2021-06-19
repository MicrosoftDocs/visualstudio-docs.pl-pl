---
title: Tworzenie niestandardowych procesorów dyrektywy T4 dotyczącej szablonu tekstowego
description: Dowiedz się więcej na temat procesu przekształcania szablonu tekstu i sposobu tworzenia niestandardowego procesora dyrektywy szablonu tekstowego T4.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 59644275f17eac197074351a777959bb1826a5de
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389504"
---
# <a name="create-custom-t4-text-template-directive-processors"></a>Tworzenie niestandardowych procesorów dyrektyw szablonów tekstowych T4

Proces *przekształcania szablonu tekstu* przyjmuje plik szablonu *tekstowego* jako dane wejściowe i generuje plik tekstowy jako dane wyjściowe. Aparat *przekształcania szablonu tekstu* kontroluje proces, a aparat wchodzi w interakcję z  hostem przekształcania szablonu tekstu i co najmniej jednym procesorem dyrektywy szablonu tekstu w celu ukończenia procesu. Aby uzyskać więcej informacji, [zobacz The Text Template Transformation Process (Proces przekształcania szablonu tekstu).](../modeling/the-text-template-transformation-process.md)

Aby utworzyć niestandardowy procesor dyrektywy, należy utworzyć klasę, która dziedziczy z <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> klasy lub <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> .

Różnica między tymi dwoma polega na implementacji minimalnego interfejsu niezbędnego do uzyskania parametrów od użytkownika i wygenerowania kodu, który tworzy <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> plik wyjściowy szablonu. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implementuje wzorzec projektowy requires/provides. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> Obsługuje dwa specjalne parametry: `requires` i `provides` .  Na przykład niestandardowy procesor dyrektywy może akceptować nazwę pliku od użytkownika, otwierać i odczytywać plik, a następnie przechowywać tekst pliku w zmiennej o nazwie `fileText` . Podklasa klasy może przyjmować nazwę pliku od użytkownika jako wartość parametru i nazwę zmiennej, w której ma być zapisywany tekst jako wartość <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> `requires` `provides` parametru. Ten procesor otworzy plik i odczyta go, a następnie przechowa tekst pliku w określonej zmiennej.

Przed wywołaniem niestandardowego procesora dyrektywy z szablonu tekstu w Visual Studio należy go zarejestrować.

Aby uzyskać więcej informacji na temat dodawania klucza rejestru, zobacz [Wdrażanie niestandardowego procesora dyrektywy](../modeling/deploying-a-custom-directive-processor.md).

## <a name="custom-directives"></a>Dyrektywy niestandardowe

Niestandardowa dyrektywa wygląda następująco:

`<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`

Niestandardowego procesora dyrektywy można użyć, gdy chcesz uzyskać dostęp do zewnętrznych danych lub zasobów z szablonu tekstowego.

Różne szablony tekstowe mogą współużytkować funkcje zapewniane przez pojedynczy procesor dyrektywy, dlatego procesory dyrektyw zapewniają sposób czynników kodu do ponownego użycia. Wbudowana dyrektywa jest podobna, ponieważ można jej używać do dzielenia kodu na różne `include` szablony tekstowe. Różnica polega na tym, że wszystkie funkcje zapewniane przez `include` dyrektywę są stałe i nie akceptują parametrów. Jeśli chcesz zapewnić wspólną funkcjonalność szablonu tekstowego i zezwolić szablonowi na podanie parametrów, musisz utworzyć niestandardowy procesor dyrektywy.

Przykłady niestandardowych procesorów dyrektyw mogą być:

- Procesor dyrektywy do zwracania danych z bazy danych, która akceptuje nazwę użytkownika i hasło jako parametry.

- Procesor dyrektywy do otwierania i odczytywania pliku, który akceptuje nazwę pliku jako parametr.

### <a name="principal-parts-of-a-custom-directive-processor"></a>Główne części niestandardowego procesora dyrektywy

Aby opracować procesor dyrektywy, należy utworzyć klasę, która dziedziczy z <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> klasy lub <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> .

Najważniejsze `DirectiveProcessor` metody, które należy zaimplementować, są następujące.

- `bool IsDirectiveSupported(string directiveName)` - Zwraca `true` , jeśli procesor dyrektywy może poradzić sobie z nazwaną dyrektywą.

- `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` - Aparat szablonów wywołuje tę metodę dla każdego wystąpienia dyrektywy w szablonie. Procesor powinien zapisać wyniki.

Po wszystkich wywołaniach metody ProcessDirective() aparat tworzenia szablonów wywoła następujące metody:

- `string[] GetReferencesForProcessingRun()` — Zwraca nazwy zestawów, których wymaga kod szablonu.

- `string[] GetImportsForProcessingRun()` — Zwraca przestrzenie nazw, które mogą być używane w kodzie szablonu.

- `string GetClassCodeForProcessingRun()` — Zwraca kod metod, właściwości i innych deklaracji, których może używać kod szablonu. Najprostszym sposobem na to jest skompilowanie ciągu zawierającego kod W# lub Visual Basic kodu. Aby procesor dyrektywy mógł być wywoływany z szablonu, który używa dowolnego języka CLR, można skonstruować instrukcje jako drzewo CodeDom, a następnie zwrócić wynik serializacji drzewa w języku używanym przez szablon.

- Aby uzyskać więcej informacji, [zobacz Przewodnik: tworzenie niestandardowego procesora dyrektywy](../modeling/walkthrough-creating-a-custom-directive-processor.md).

## <a name="see-also"></a>Zobacz też

- [W artykule Deploy a Custom Directive Processor (Wdrażanie](../modeling/deploying-a-custom-directive-processor.md) niestandardowego procesora dyrektywy) wyjaśniono, jak zarejestrować niestandardowy procesor dyrektywy.
- [Przewodnik: Tworzenie niestandardowego](../modeling/walkthrough-creating-a-custom-directive-processor.md) procesora dyrektywy opisuje sposób tworzenia niestandardowego procesora dyrektywy, rejestrowania i testowania procesora dyrektywy oraz formatowania pliku wyjściowego jako HTML.
