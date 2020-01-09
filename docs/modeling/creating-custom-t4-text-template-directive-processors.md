---
title: Tworzenie niestandardowych procesorów dyrektywy T4 dotyczącej szablonu tekstowego
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c70aa1853701ef671b7057ad698a0fb63334a1ca
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597181"
---
# <a name="create-custom-t4-text-template-directive-processors"></a>Tworzenie niestandardowych procesorów dyrektyw szablonów tekstowych T4

*Proces przekształcania szablonu tekstu* pobiera plik *szablonu tekstu* jako dane wejściowe i tworzy plik tekstowy jako dane wyjściowe. *Aparat transformacji szablonu tekstu* kontroluje proces, a aparat współdziała z hostem transformacji szablonu tekstu i jednym lub wieloma *procesorami dyrektywy* tekstu w celu ukończenia procesu. Aby uzyskać więcej informacji, zobacz [proces przekształcania szablonu tekstu](../modeling/the-text-template-transformation-process.md).

Aby utworzyć niestandardowy procesor dyrektywy, należy utworzyć klasę, która dziedziczy po obu <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> lub <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

Różnica między tymi dwiema polega na tym, że <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> implementuje minimalny interfejs, który jest niezbędny do uzyskania parametrów od użytkownika i generowania kodu, który tworzy plik wyjściowy szablonu. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implementuje Wzorzec projektowy wymagane/zapewniający. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> obsługuje dwa specjalne parametry, `requires` i `provides`.  Na przykład niestandardowy procesor dyrektywy może akceptować nazwę pliku od użytkownika, otwierać i odczytywać plik, a następnie przechowywać tekst pliku w zmiennej o nazwie `fileText`. Podklasa klasy <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> może przyjmować nazwę pliku od użytkownika jako wartość parametru `requires` i nazwę zmiennej, w której ma być przechowywany tekst jako wartość parametru `provides`. Ten procesor otwiera i odczytuje plik, a następnie zapisuje tekst pliku w określonej zmiennej.

Przed wywołaniem niestandardowego procesora dyrektywy z szablonu tekstu w programie Visual Studio, należy go zarejestrować.

Więcej informacji o sposobach dodawania klucza rejestru znajduje się w temacie [wdrażanie niestandardowego procesora dyrektywy](../modeling/deploying-a-custom-directive-processor.md).

## <a name="custom-directives"></a>Dyrektywy niestandardowe

Dyrektywa niestandardowa wygląda następująco:

`<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`

Możesz użyć niestandardowego procesora dyrektywy, gdy chcesz uzyskać dostęp do danych zewnętrznych lub zasobów z szablonu tekstu.

Różne szablony tekstowe mogą współużytkować funkcje, które zapewnia jeden procesor dyrektywy, więc procesory dyrektywy umożliwiają użycie kodu do ponownego użycia. Wbudowana dyrektywa `include` jest podobna, ponieważ można jej użyć do refaktoryzacji kodu i udostępniania jej między różnymi szablonami tekstu. Różnica polega na tym, że każda funkcja, którą zapewnia dyrektywa `include`, jest stała i nie akceptuje parametrów. Aby zapewnić typową funkcjonalność szablonu tekstu i umożliwić szablonowi przekazywanie parametrów, należy utworzyć niestandardowy procesor dyrektywy.

Oto kilka przykładów niestandardowych procesorów dyrektywy:

- Procesor dyrektywy, który zwraca dane z bazy danych, która akceptuje nazwę użytkownika i hasło jako parametry.

- Procesor dyrektywy służący do otwierania i odczytywania pliku, który akceptuje nazwę pliku jako parametr.

### <a name="principal-parts-of-a-custom-directive-processor"></a>Główne części niestandardowego procesora dyrektywy

Aby opracować procesor dyrektywy, należy utworzyć klasę, która dziedziczy po obu <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> lub <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

Najważniejsze metody `DirectiveProcessor`, które należy zaimplementować, są następujące.

- `bool IsDirectiveSupported(string directiveName)`-Return `true`, jeśli procesor dyrektywy może zajmować się nazwaną dyrektywą.

- `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` — aparat szablonu wywołuje tę metodę dla każdego wystąpienia dyrektywy w szablonie. Twój procesor powinien zapisywać wyniki.

Po wszystkich wywołaniach do ProcessDirective () aparat tworzenia szablonów wywoła następujące metody:

- `string[] GetReferencesForProcessingRun()` — zwraca nazwy zestawów, których wymaga kod szablonu.

- `string[] GetImportsForProcessingRun()` — zwraca przestrzenie nazw, które mogą być używane w kodzie szablonu.

- `string GetClassCodeForProcessingRun()` — zwraca kod metod, właściwości i innych deklaracji, które mogą być używane przez kod szablonu. Najprostszym sposobem na to jest skompilowanie ciągu zawierającego kod C# lub Visual Basic. Aby umożliwić wywoływanie procesora dyrektywy z szablonu, który używa dowolnego języka CLR, można skonstruować instrukcje jako drzewo CodeDom, a następnie zwracać wynik serializacji drzewa w języku używanym przez szablon.

- Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie niestandardowego procesora dyrektywy](../modeling/walkthrough-creating-a-custom-directive-processor.md).

## <a name="see-also"></a>Zobacz także

- [Wdrażanie niestandardowego procesora dyrektywy](../modeling/deploying-a-custom-directive-processor.md) wyjaśnia, jak zarejestrować niestandardowy procesor dyrektywy.
- [Przewodnik: Tworzenie niestandardowego procesora dyrektywy](../modeling/walkthrough-creating-a-custom-directive-processor.md) opisuje sposób tworzenia niestandardowego procesora dyrektywy, sposób rejestrowania i testowania procesora dyrektywy oraz formatowania pliku wyjściowego w formacie HTML.
