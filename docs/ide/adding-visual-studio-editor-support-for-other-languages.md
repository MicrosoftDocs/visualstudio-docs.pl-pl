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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d4fafaf9356d8862808e1ac6ad125207d71769b5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590881"
---
# <a name="add-visual-studio-editor-support-for-other-languages"></a>Dodaj obsługę innych języków w edytorze programu Visual Studio

Informacje na temat jak edytor programu Visual Studio obsługuje odczytu ani nawigować przez inny komputer języków i jak dodać obsługę innych języków w edytorze programu Visual Studio.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Kolorowanie składni, uzupełniania instrukcji i przejdź do pomocy technicznej

Funkcje w edytorze programu Visual Studio, takie jak kolorowania składni, uzupełniania instrukcji (znany także jako IntelliSense) i _przejdź do_ pomoże Ci łatwiej zapisu, odczytu i edytować kod. Poniższy zrzut ekranu przedstawia przykład edytowanie skryptu Perl w programie Visual Studio. Składnia jest automatycznie w trybie kolorowym. Na przykład uwagi w kodzie mają kolor zielony, kod jest czarny, ścieżki są oznaczone kolorem czerwonym i instrukcje są niebieski. Edytor programu Visual Studio automatycznie stosuje kolorowania składni dowolnego języka programowania go obsługuje. Ponadto po rozpoczęciu wprowadź słowo kluczowe języka znane lub obiekt, uzupełniania instrukcji Wyświetla listę możliwych instrukcji i obiektów. Uzupełnianie instrukcji pomaga napisać kod szybciej i łatwiej.

![Kolorowanie składni w skrypcie języka Perl](../ide/media/vside_perledit.png)

Program Visual Studio zawiera obecnie kolorowania składni i uzupełniania instrukcji podstawowe obsługę następujących języków przy użyciu [Gramatyk TextMate](https://manual.macromates.com/en/language_grammars). Jeśli ulubiony język nie znajduje się w tabeli, nie martw się&mdash;można go dodać.

|||||||
|-|-|-|-|-|-|
|Bat|Język F#|Java|Markdown|Rust|Język Visual Basic|
|Clojure|Przejdź|JavaDoc|Objective-C|ShaderLab|Język C#|
|CMake|Groovy|JSON|Perl|ShellScript|Visual C++|
|CoffeeScript|HTML|MNIEJ|Python|SQL|VBNet|
|{1&gt;CSS&lt;1}|INI|LUA|R|Swift|{1&gt;XML&lt;1}|
|Docker|Jade|Tworzenie|Ruby|TypeScript|YAML|

Oprócz kolorowania składni i uzupełniania instrukcji podstawowych programu Visual Studio ma również funkcję o nazwie [przejdź do](https://blogs.msdn.microsoft.com/benwilli/2015/04/09/visual-studio-tip-3-use-navigate-to/). Ta funkcja umożliwia szybkie wyszukiwanie plików kodu, ścieżek plików i symboli kodu. Visual Studio zawiera przejdź do pomocy technicznej dla następujących języków.

- Język C#

- C++

- TypeScript

- JavaScript

- Język Visual Basic

- Przejdź

- Java

- PHP

Wszystkie typy plików mają funkcje opisane wcześniej nawet wtedy, gdy pomoc techniczna dla danego języka nie został jeszcze zainstalowany. Instalowanie obsługi wyspecjalizowane w przypadku niektórych języków może dostarczyć obsługę dodatkowych języków, takich jak technologia IntelliSense i inne funkcje zaawansowane języka, takie jak żarówki.

## <a name="add-support-for-non-supported-languages"></a>Dodano obsługę języków nieobsługiwanych

Program Visual Studio zapewnia obsługę języka w edytorze przy użyciu [gramatyki Deautomatyzujj](https://manual.macromates.com/en/language_grammars). Jeśli ulubiony język programowania nie jest obecnie obsługiwany w edytorze programu Visual Studio, najpierw Przeszukaj&mdash;sieci Web, a pakiet deautomatyzuj dla tego języka już istnieje. Jeśli nie możesz znaleźć jednego z nich, możesz samodzielnie dodać do niego pomoc techniczną, tworząc model pakietu deautomatyzujgo dla gramatyki języka i fragmentów kodu.

Dodaj wszystkie nowe Gramatyk TextMate dla programu Visual Studio w następującym folderze:

*% userprofile %\\. vs\Extensions*

W tej ścieżce podstawowej Dodaj następujące foldery, jeśli mają zastosowanie do Twojej sytuacji:

|Nazwa folderu|Opis|
|-----------------|-----------------|
|\\ *\<Nazwa języka >*|Folder języka. Zastąp  *\<Nazwa języka >* nazwą języka. Na przykład *\Matlab*.|
|*\Syntaxes*|Folder gramatyki. Zawiera gramatykę *.json* plików dla języka, takich jak *Matlab.json*.|
|*\Snippets*|Folder fragmentów kodu. Zawiera fragmenty kodu dla języka.|

W Windows *% userprofile %* jest rozpoznawana jako ścieżka: *c:\Users\\\<nazwa użytkownika >* . Jeśli folder *rozszerzeń* nie istnieje w systemie, należy go utworzyć. Jeśli folder już istnieje, zostanie on ukryty.

> [!TIP]
> Jeśli w edytorze znajdują się jakieś pliki, musisz je zamknąć i ponownie otworzyć, aby wyświetlić wyróżnianie składni po dodaniu gramatyki.

Aby uzyskać szczegółowe informacje na temat tworzenia gramatyki Details, zobacz detailion [-Introduction to Languages](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) i [uwagi na temat tworzenia gramatyki języka i motywu niestandardowego dla pakietu](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle)details.

## <a name="see-also"></a>Zobacz także

- [Dodawanie rozszerzenia protokołu serwera języka](../extensibility/adding-an-lsp-extension.md)
- [Przewodnik: tworzenie fragmentu kodu](../ide/walkthrough-creating-a-code-snippet.md)
- [Przewodnik: Wyświetlanie uzupełniania](../extensibility/walkthrough-displaying-statement-completion.md)
