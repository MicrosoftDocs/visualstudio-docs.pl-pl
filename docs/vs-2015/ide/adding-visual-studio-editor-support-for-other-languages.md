---
title: Dodawanie Obsługa edytora dla innych języków | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax colorization
- IntelliSense
- IDE, navigation
- documents [Visual Studio], navigation
- TextMate bundle
- TextMate language grammar
- language support
ms.assetid: d78c43ee-4ef2-42e5-984e-d137de4e7e92
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 366ec5de66c3070e30d7d4f98662732a7892437b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54758818"
---
# <a name="adding-visual-studio-editor-support-for-other-languages"></a>Dodawanie obsługi innych języków w edytorze programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Informacje na temat jak edytor programu Visual Studio obsługuje odczytu ani nawigować przez inny komputer języków i jak dodać obsługę innych języków w edytorze programu Visual Studio.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Kolorowanie składni, uzupełniania instrukcji i przejdź do pomocy technicznej
 Funkcje w edytorze programu Visual Studio, takie jak kolorowania składni, uzupełniania instrukcji i przejdź do może pomóc Ci łatwo odczytywać, tworzyć i edytować kod. Poniższy zrzut ekranu przedstawia przykład edytowanie skryptu Perl w programie Visual Studio. Składnia jest automatycznie w trybie kolorowym. Na przykład uwagi w kodzie mają kolor zielony, kod jest czarny, ścieżki są oznaczone kolorem czerwonym i instrukcje są niebieski. Edytor programu Visual Studio automatycznie stosuje kolorowania składni dowolnego języka programowania go obsługuje. Ponadto po rozpoczęciu wprowadź słowo kluczowe języka znane lub obiekt, uzupełniania instrukcji Wyświetla listę możliwych instrukcji i obiektów. Uzupełnianie instrukcji mogą pomóc tworzyć kod szybciej i łatwiej.

 ![Kolorowanie składni w skrypcie języka Perl](../ide/media/vside-perledit.png "VSIDE_PerlEdit")

 Program Visual Studio zawiera obecnie kolorowania składni i uzupełniania instrukcji podstawowe obsługę następujących języków przy użyciu [Gramatyk TextMate](https://manual.macromates.com/en/language_grammars). Jeśli tabela nie ma ulubionego języka, jednak nie martw się — możesz dodać go.

|||||||
|-|-|-|-|-|-|
|Bat|F#|Java|Markdown|Rust|Visual Basic|
|Clojure|Z rzeczywistym użyciem|JavaDoc|Objective-C|ShaderLab|Visual C#|
|Narzędzia CMake|Groovy|JSON|Perl|ShellScript|Visual C++|
|CoffeeScript|HTML|MNIEJ|Python|SQL|VBNet|
|CSS|INI|LUA|R|Swift|XML|
|Docker|Jade|Wprowadź|Ruby|TypeScript|YAML|

 Oprócz kolorowania składni i uzupełniania instrukcji podstawowych programu Visual Studio ma również funkcję o nazwie [przejdź do](https://blogs.msdn.microsoft.com/benwilli/2015/04/09/visual-studio-tip-3-use-navigate-to/). Ta funkcja umożliwia szybkie wyszukiwanie plików kodu, ścieżki do plików i symbole kodu. Visual Studio zawiera przejdź do pomocy technicznej dla następujących języków.

- Z rzeczywistym użyciem

- Java

- JavaScript

- PHP

- TypeScript

- Visual Basic

- Visual C++

- Visual C#

  Wszystkie typy plików mają funkcje opisane wcześniej nawet wtedy, gdy pomoc techniczna dla danego języka nie został jeszcze zainstalowany. Instalowanie obsługi wyspecjalizowane w przypadku niektórych języków może dostarczyć obsługę dodatkowych języków, takich jak technologia IntelliSense i inne funkcje zaawansowane języka, takie jak żarówki.

## <a name="adding-support-for-non-supported-languages"></a>Dodano obsługę języków nieobsługiwanych
 Visual Studio 2015 Update 1 i nowsze wersje zapewniają obsługę języka w edytorze za pomocą [Gramatyk TextMate](https://manual.macromates.com/en/language_grammars). Jeśli w ulubionym języku programowania nie jest obecnie obsługiwane w edytorze programu Visual Studio, najpierw wyszukać w sieci web - pakiet TextMate języka może już istnieć. Jeśli nie znajdziesz, jednak można dodać obsługę dla niego samodzielnie w Visual Studio 2015 Update 1 lub nowszy, tworząc modelu pakietu TextMate gramatyki języka i fragmenty kodu.

 Dodaj wszystkie nowe Gramatyk TextMate dla programu Visual Studio w następującym folderze:

 % userprofile %\\. vs\Extensions

 W ramach tej ścieżki podstawowej należy dodać następujące foldery, jeśli mają one zastosowanie do konkretnej sytuacji:

|Nazwa folderu|Opis|
|-----------------|-----------------|
|\\*\<Nazwa języka >*|Folder języka. Zastąp  *\<Nazwa języka >* nazwą języka. Na przykład **\Matlab**.|
|\Syntaxes|Folder gramatyki. Zawiera pliki .json gramatyki języka, takich jak **Matlab.json**.|
|\Snippets|Folder fragmentów kodu. Zawiera fragmenty kodu dla języka.|

 W Windows, % userprofile % jest rozpoznawana jako ścieżka: c:\Users\\*\<nazwa użytkownika >*. Jeśli folder rozszerzenia nie istnieje w systemie, należy go utworzyć. Jeśli folder już istnieje, zostanie on ukryty.

 Aby uzyskać szczegółowe informacje o sposobie tworzenia gramatyki TextMate, zobacz [TextMate — wprowadzenie do gramatyki języka: Jak dodawać, wyróżnianie składni kodu źródłowego osadzonych w kodzie HTML](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) i [informacje na temat tworzenia gramatyki języka i motywu niestandardowego dla pakietu Textmate](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle).

## <a name="see-also"></a>Zobacz też
 [Visual Studio 2013, przejdź do ulepszenia](https://blogs.msdn.microsoft.com/mvpawardprogram/2013/10/22/visual-studio-2013-navigate-to-improvements/) [instruktażu: Creating a Code Snippet](../ide/walkthrough-creating-a-code-snippet.md) [instruktażu: Wyświetlanie uzupełniania instrukcji](../extensibility/walkthrough-displaying-statement-completion.md)
