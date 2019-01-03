---
title: Tworzenie niestandardowych procesorów dyrektywy T4 dotyczącej szablonu tekstowego
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, custom directive processors
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 5db3772b782af666023f39fd833e18ba2092c176
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989153"
---
# <a name="creating-custom-t4-text-template-directive-processors"></a>Tworzenie niestandardowych procesorów dyrektywy T4 dotyczącej szablonu tekstowego

*Proces przekształcania szablonu tekstowego* przyjmuje *szablon tekstowy* pliku jako dane wejściowe i tworzy plik tekstowy jako dane wyjściowe. *Aparatu przekształceń szablonu tekstu* kontroli procesu i aparat współdziała z hosta przekształcania szablonu tekstu i co najmniej jeden szablon tekstowy *procesorów dyrektyw* do ukończenia proces. Aby uzyskać więcej informacji, zobacz [proces przekształcania szablonu tekstowego](../modeling/the-text-template-transformation-process.md).

Aby utworzyć niestandardowy procesor dyrektywy, należy utworzyć klasę, która dziedziczy z <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> lub <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

Różnica między tymi dwoma dotyczy <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> implementuje interfejs minimalne, które są niezbędne, można pobrać parametrów od użytkownika, a także o generowaniu kodu, który tworzy plik wyjściowy szablonu. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> implementuje wzorzec projektowy wymaga/udostępnia. <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> obsługuje dwa parametry specjalne, `requires` i `provides`.  Na przykład niestandardowy procesor dyrektywy może Zaakceptuj nazwy pliku od użytkownika, Otwórz i odczytać pliku, a następnie zapisać go w pliku w zmiennej o nazwie `fileText`. Podklasa klasy <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> klasy może potrwać nazwy pliku od użytkownika jako wartość `requires` parametr i nazwę zmiennej do przechowywania tekstu jako wartość `provides` parametru. Tego procesora będzie otworzyć i odczytać plik i następnie zapisać go w pliku w określonej zmiennej.

Przed wywołaniem niestandardowy procesor dyrektywy z szablonu tekstu w programie Visual Studio, należy zarejestrować.

Aby uzyskać więcej informacji o tym, jak dodać klucz rejestru, zobacz [wdrażanie niestandardowego procesora dyrektywy](../modeling/deploying-a-custom-directive-processor.md).

## <a name="custom-directives"></a>Dyrektywy niestandardowej

Niestandardowej dyrektywy wygląda następująco:

`<#@ MyDirective Processor="MyDirectiveProcessor" parameter1="value1" ... #>`

Jeśli chcesz uzyskać dostęp do danych zewnętrznych lub zasobów z szablonu tekstu, można użyć niestandardowego procesora dyrektywy.

Szablony tekstowe różnych udostępnić funkcje, które zapewnia pojedynczy procesor dyrektywy, więc procesorów dyrektyw umożliwiają współczynnik kodu do ponownego wykorzystania. Wbudowane `include` dyrektywa jest podobny, ponieważ służy do wziąć pod uwagę kod i udostępnij go wśród szablonów inny tekst. Różnica jest to, że żadnej funkcji, która `include` zapewnia dyrektywa jest stała i nie akceptuje parametrów. Jeśli chcesz zapewnić typowe funkcje szablonu tekstu i umożliwić szablonu w celu przekazania parametrów, należy utworzyć niestandardowy procesor dyrektywy.

Przykładowe niestandardowe procesory dyrektyw może być:

-   Procesor dyrektywy, aby zwrócić dane z bazy danych, która przyjmuje jako parametry nazwę użytkownika i hasło.

-   Procesor dyrektywy, aby otworzyć i przeczytać plik, który przyjmuje nazwę pliku jako parametr.

### <a name="principal-parts-of-a-custom-directive-processor"></a>Podmiot zabezpieczeń części niestandardowego procesora dyrektywy

Aby opracować procesor dyrektywy, należy utworzyć klasę, która dziedziczy z <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor> lub <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.

Najważniejsze `DirectiveProcessor` dostępne są następujące metody, które należy zaimplementować.

-   `bool IsDirectiveSupported(string directiveName)` -Return `true` Jeśli procesor dyrektywy poradzenie sobie z dyrektywy o nazwie.

-   `void ProcessDirective (string directiveName, IDictionary<string, string> arguments)` Aparatu szablonów wywołuje tę metodę dla każdego wystąpienia dyrektywy w szablonie. Procesor należy zapisać wyniki.

Po wszystkie wywołania element ProcessDirective() aparatu tworzenia szablonów będzie wywoływać tych metod:

-   `string[] GetReferencesForProcessingRun()` -Zwraca nazwy zestawów, których wymaga kod szablonu.

-   `string[] GetImportsForProcessingRun()` -Przywrócić przestrzenie nazw, który może służyć kod szablonu.

-   `string GetClassCodeForProcessingRun()` -Zwrócić kod metody, właściwości i innych deklaracji, używających kod szablonu. W tym celu najłatwiej do tworzenia ciąg zawierający w języku C# lub kod języka Visual Basic. Aby procesor dyrektywy może być wywoływana z szablonu, który korzysta z dowolnego języka środowiska CLR, można skonstruować oświadczeń jako drzewo CodeDom, a następnie powróć wynik serializacji drzewa w język używany przez szablon.

-   Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie niestandardowego procesora dyrektywy](../modeling/walkthrough-creating-a-custom-directive-processor.md).

## <a name="see-also"></a>Zobacz także

- [Wdrażanie niestandardowego procesora dyrektywy](../modeling/deploying-a-custom-directive-processor.md) wyjaśnia, jak zarejestrować niestandardowy procesor dyrektywy.
- [Przewodnik: Tworzenie niestandardowego procesora dyrektywy](../modeling/walkthrough-creating-a-custom-directive-processor.md) opisano, jak utworzyć niestandardowy procesor dyrektywy, jak się zarejestrować i przetestować procesor dyrektywy i jak sformatować plik wyjściowy w formacie HTML.