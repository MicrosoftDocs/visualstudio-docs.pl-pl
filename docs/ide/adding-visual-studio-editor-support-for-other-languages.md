---
title: Dodaj dla innych języków pomoc techniczna do edytora
ms.date: 11/04/2016
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7ae0b2f606b4fe04ad390712f48ac1e06ff9bb86
ms.sourcegitcommit: 283f2dbce044a18e9f6ac6398f6fc78e074ec1ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2019
ms.locfileid: "65805329"
---
# <a name="add-visual-studio-editor-support-for-other-languages"></a>Dodaj obsługę innych języków w edytorze programu Visual Studio

Informacje na temat jak edytor programu Visual Studio obsługuje odczytu ani nawigować przez inny komputer języków i jak dodać obsługę innych języków w edytorze programu Visual Studio.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Kolorowanie składni, uzupełniania instrukcji i przejdź do pomocy technicznej

Funkcje w edytorze programu Visual Studio, takie jak kolorowania składni, uzupełniania instrukcji (znany także jako IntelliSense) i _przejdź do_ pomoże Ci łatwiej zapisu, odczytu i edytować kod. Poniższy zrzut ekranu przedstawia przykład edytowanie skryptu Perl w programie Visual Studio. Składnia jest automatycznie w trybie kolorowym. Na przykład uwagi w kodzie mają kolor zielony, kod jest czarny, ścieżki są oznaczone kolorem czerwonym i instrukcje są niebieski. Edytor programu Visual Studio automatycznie stosuje kolorowania składni dowolnego języka programowania go obsługuje. Ponadto po rozpoczęciu wprowadź słowo kluczowe języka znane lub obiekt, uzupełniania instrukcji Wyświetla listę możliwych instrukcji i obiektów. Uzupełnianie instrukcji pomaga napisać kod szybciej i łatwiej.

![Kolorowanie składni w skrypcie języka Perl](../ide/media/vside_perledit.png)

Program Visual Studio zawiera obecnie kolorowania składni i uzupełniania instrukcji podstawowe obsługę następujących języków przy użyciu [Gramatyk TextMate](https://manual.macromates.com/en/language_grammars). Jeśli w tabeli nie jest ulubionego języka, jednak nie martw się&mdash;można go dodać.

|||||||
|-|-|-|-|-|-|
|Bat|F#|Java|Markdown|Rust|Visual Basic|
|Clojure|Z rzeczywistym użyciem|JavaDoc|Objective-C|ShaderLab|C#|
|Narzędzia CMake|Groovy|JSON|Perl|ShellScript|Visual C++|
|CoffeeScript|HTML|MNIEJ|Python|SQL|VBNet|
|CSS|INI|LUA|R|Swift|XML|
|Docker|Jade|Wprowadź|Ruby|TypeScript|YAML|

Oprócz kolorowania składni i uzupełniania instrukcji podstawowych programu Visual Studio ma również funkcję o nazwie [przejdź do](https://blogs.msdn.microsoft.com/benwilli/2015/04/09/visual-studio-tip-3-use-navigate-to/). Ta funkcja umożliwia szybkie wyszukiwanie plików kodu, ścieżki do plików i symbole kodu. Visual Studio zawiera przejdź do pomocy technicznej dla następujących języków.

- C#

- C++

- TypeScript

- JavaScript

- Visual Basic

- Z rzeczywistym użyciem

- Java

- PHP

Wszystkie typy plików mają funkcje opisane wcześniej nawet wtedy, gdy pomoc techniczna dla danego języka nie został jeszcze zainstalowany. Instalowanie obsługi wyspecjalizowane w przypadku niektórych języków może dostarczyć obsługę dodatkowych języków, takich jak technologia IntelliSense i inne funkcje zaawansowane języka, takie jak żarówki.

## <a name="add-support-for-non-supported-languages"></a>Dodano obsługę języków nieobsługiwanych

Program Visual Studio zapewnia obsługę języka w edytorze za pomocą [Gramatyk TextMate](https://manual.macromates.com/en/language_grammars). Jeśli w ulubionym języku programowania nie jest obecnie obsługiwane w edytorze programu Visual Studio, najpierw należy wyszukać w sieci web&mdash;TextMate pakiet dla języka może już istnieć. Jeśli nie znajdziesz, jednak można dodać obsługę dla niego samodzielnie przez tworzenie modelu pakietu TextMate gramatyki języka i fragmenty kodu.

Dodaj wszystkie nowe Gramatyk TextMate dla programu Visual Studio w następującym folderze:

*% userprofile %\\. vs\Extensions*

W ramach tej ścieżki podstawowej należy dodać następujące foldery, jeśli mają one zastosowanie do danej sytuacji:

|Nazwa folderu|Opis|
|-----------------|-----------------|
|\\*\<Nazwa języka >*|Folder języka. Zastąp  *\<Nazwa języka >* nazwą języka. Na przykład *\Matlab*.|
|*\Syntaxes*|Folder gramatyki. Zawiera gramatykę *.json* plików dla języka, takich jak *Matlab.json*.|
|*\Snippets*|Folder fragmentów kodu. Zawiera fragmenty kodu dla języka.|

W Windows *% userprofile %* jest rozpoznawana jako ścieżka: *c:\Users\\\<nazwa użytkownika >*. Jeśli *rozszerzenia* folder nie istnieje w systemie, musisz go utworzyć. Jeśli folder już istnieje, zostanie on ukryty.

> [!TIP]
> W przypadku wszystkich plików, Otwórz w edytorze musisz zamknąć i ponownie otworzyć je, aby wyświetlić, wyróżnianie składni, po dodaniu gramatyki TextMate.

Aby uzyskać szczegółowe informacje o sposobie tworzenia gramatyki TextMate, zobacz [TextMate — wprowadzenie do języka gramatyki](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) i [informacje na temat tworzenia gramatyki języka i motywu niestandardowego dla pakietu Textmate](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle).

## <a name="see-also"></a>Zobacz także

- [Dodawanie rozszerzenia protokołu Language Server Protocol](../extensibility/adding-an-lsp-extension.md)
- [Przewodnik: Tworzenie fragmentu kodu](../ide/walkthrough-creating-a-code-snippet.md)
- [Przewodnik: Wyświetlanie uzupełniania instrukcji](../extensibility/walkthrough-displaying-statement-completion.md)
