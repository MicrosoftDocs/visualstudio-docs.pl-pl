---
title: Tworzenie niestandardowych procesorów dyrektywy T4 dotyczącej szablonu tekstowego
description: Dowiedz się więcej o procesie transformacji szablonu tekstu i sposobach tworzenia niestandardowego procesora dyrektywy T4.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bf17d2a7e3b38e267f0353f71c7cd83826b141bf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945334"
---
# <a name="create-custom-t4-text-template-directive-processors"></a>Tworzenie niestandardowych procesorów dyrektyw szablonów tekstowych T4

*Proces przekształcania szablonu tekstu* pobiera plik *szablonu tekstu* jako dane wejściowe i tworzy plik tekstowy jako dane wyjściowe. *Aparat transformacji szablonu tekstu* kontroluje proces, a aparat współdziała z hostem transformacji szablonu tekstu i jednym lub wieloma *procesorami dyrektywy* tekstu w celu ukończenia procesu. Aby uzyskać więcej informacji, zobacz [proces przekształcania szablonu tekstu](../modeling/the-text-template-transformation-process.md).

Aby utworzyć niestandardowy procesor dyrektywy, należy utworzyć klasę, która dziedziczy po obu <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> lub <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> .

Różnica między tymi dwoma jest <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> implementacją minimalnego interfejsu, który jest niezbędny do uzyskania parametrów od użytkownika i generowania kodu generującego plik wyjściowy szablonu. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implementuje Wzorzec projektowy wymagane/zapewnia. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> obsługuje dwa specjalne parametry `requires` i `provides` .  Na przykład niestandardowy procesor dyrektywy może akceptować nazwę pliku od użytkownika, otwierać i odczytywać plik, a następnie przechowywać tekst pliku w zmiennej o nazwie `fileText` . Podklasa <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> klasy może przyjmować nazwę pliku od użytkownika jako wartość `requires` parametru i nazwę zmiennej, w której ma być przechowywany tekst jako wartość `provides` parametru programu. Ten procesor otwiera i odczytuje plik, a następnie zapisuje tekst pliku w określonej zmiennej.

Przed wywołaniem niestandardowego procesora dyrektywy z szablonu tekstu w programie Visual Studio, należy go zarejestrować.

Więcej informacji o sposobach dodawania klucza rejestru znajduje się w temacie [wdrażanie niestandardowego procesora dyrektywy](../modeling/deploying-a-custom-directive-processor.md).

## <a name="custom-directives"></a>Dyrektywy niestandardowe

Dyrektywa niestandardowa wygląda następująco:

`<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`

Możesz użyć niestandardowego procesora dyrektywy, gdy chcesz uzyskać dostęp do danych zewnętrznych lub zasobów z szablonu tekstu.

Różne szablony tekstowe mogą współużytkować funkcje, które zapewnia jeden procesor dyrektywy, więc procesory dyrektywy umożliwiają użycie kodu do ponownego użycia. Wbudowana `include` dyrektywa jest podobna, ponieważ można jej użyć do refaktoryzacji kodu i udostępniania jej między różnymi szablonami tekstu. Różnica polega na tym, że każda funkcja, którą `include` zapewnia dyrektywa, jest stała i nie akceptuje parametrów. Aby zapewnić typową funkcjonalność szablonu tekstu i umożliwić szablonowi przekazywanie parametrów, należy utworzyć niestandardowy procesor dyrektywy.

Oto kilka przykładów niestandardowych procesorów dyrektywy:

- Procesor dyrektywy, który zwraca dane z bazy danych, która akceptuje nazwę użytkownika i hasło jako parametry.

- Procesor dyrektywy służący do otwierania i odczytywania pliku, który akceptuje nazwę pliku jako parametr.

### <a name="principal-parts-of-a-custom-directive-processor"></a>Główne części niestandardowego procesora dyrektywy

Aby opracować procesor dyrektywy, należy utworzyć klasę, która dziedziczy po obu <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> lub <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> .

Najważniejsze `DirectiveProcessor` metody, które należy zaimplementować, są następujące.

- `bool IsDirectiveSupported(string directiveName)` -Return `true` , jeśli procesor dyrektywy może zajmować się nazwaną dyrektywą.

- `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` -Aparat szablonu wywołuje tę metodę dla każdego wystąpienia dyrektywy w szablonie. Twój procesor powinien zapisywać wyniki.

Po wszystkich wywołaniach do ProcessDirective () aparat tworzenia szablonów wywoła następujące metody:

- `string[] GetReferencesForProcessingRun()` -Zwraca nazwy zestawów, których wymaga kod szablonu.

- `string[] GetImportsForProcessingRun()` -Zwraca przestrzenie nazw, które mogą być używane w kodzie szablonu.

- `string GetClassCodeForProcessingRun()` -Zwraca kod metod, właściwości i innych deklaracji, które mogą być używane przez kod szablonu. Najprostszym sposobem na to jest skompilowanie ciągu zawierającego kod C# lub Visual Basic. Aby umożliwić wywoływanie procesora dyrektywy z szablonu, który używa dowolnego języka CLR, można skonstruować instrukcje jako drzewo CodeDom, a następnie zwracać wynik serializacji drzewa w języku używanym przez szablon.

- Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie niestandardowego procesora dyrektywy](../modeling/walkthrough-creating-a-custom-directive-processor.md).

## <a name="see-also"></a>Zobacz też

- [Wdrażanie niestandardowego procesora dyrektywy](../modeling/deploying-a-custom-directive-processor.md) wyjaśnia, jak zarejestrować niestandardowy procesor dyrektywy.
- [Przewodnik: Tworzenie niestandardowego procesora dyrektywy](../modeling/walkthrough-creating-a-custom-directive-processor.md) opisuje sposób tworzenia niestandardowego procesora dyrektywy, sposób rejestrowania i testowania procesora dyrektywy oraz formatowania pliku wyjściowego w formacie HTML.
