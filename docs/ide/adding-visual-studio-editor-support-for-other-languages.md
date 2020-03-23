---
title: Dodawanie obsługi edytora dla innych języków
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590881"
---
# <a name="add-visual-studio-editor-support-for-other-languages"></a>Dodawanie obsługi edytora programu Visual Studio dla innych języków

Dowiedz się, jak edytor programu Visual Studio obsługuje czytanie i nawigowanie po różnych językach komputerów oraz jak można dodawać obsługę edytora programu Visual Studio dla innych języków.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Kolorowanie składni, uzupełnianie instrukcji i nawigowanie do obsługi

Funkcje w edytorze programu Visual Studio, takie jak kolorowanie składni, uzupełnianie instrukcji (znany również jako IntelliSense) i _Przejdź do_ może ułatwić pisanie, odczytywanie i edytowanie kodu. Poniższy zrzut ekranu przedstawia przykład edytowania skryptu Perla w programie Visual Studio. Składnia jest automatycznie kolorowana. Na przykład uwagi w kodzie są kolorowe na zielono, kod jest czarny, ścieżki są czerwone, a instrukcje są niebieskie. Edytor programu Visual Studio automatycznie stosuje kolorowanie składni do dowolnego języka, który obsługuje. Ponadto po rozpoczęciu wprowadzania znanego słowa kluczowego lub obiektu, zakończenie instrukcji wyświetla listę możliwych instrukcji i obiektów. Uzupełnianie instrukcji może pomóc w szybkim i łatwiejszej pracy kodu.

![Kolorystyka składni w skrypcie Perla](../ide/media/vside_perledit.png)

Program Visual Studio zapewnia obecnie obsługę kolorowania składni i podstawowych instrukcji dla następujących języków przy użyciu [funkcji TextMate Grammars](https://manual.macromates.com/en/language_grammars). Jeśli jednak twojego ulubionego języka nie ma w&mdash;tabeli, nie martw się, możesz go dodać.

|||||||
|-|-|-|-|-|-|
|Bat|F#|Java|Markdown|Rust|Visual Basic|
|Clojure|Przejdź|Javadoc|Obiektowy C|ShaderLab (Płyta shaderlab)|C#|
|CMake|Groovy|JSON|Perl|Kod Powłoki|Visual C++|
|Kod kawowy|HTML|Mniej|Python|SQL|VbNet ( VBNet )|
|CSS|INI|Lua|R|Swift|XML|
|Docker|Jade|Marka|Ruby|TypeScript|YAML|

Oprócz kolorowania składni i podstawowego uzupełniania instrukcji program Visual Studio ma również funkcję o nazwie [Przejdź do](https://blogs.msdn.microsoft.com/benwilli/2015/04/09/visual-studio-tip-3-use-navigate-to/). Ta funkcja umożliwia szybkie wyszukiwanie plików kodu, ścieżek plików i symboli kodu. Visual Studio zapewnia navigate do obsługi następujących języków.

- C#

- C++

- TypeScript

- JavaScript

- Visual Basic

- Przejdź

- Java

- PHP

Wszystkie te typy plików mają funkcje opisane wcześniej, nawet jeśli obsługa danego języka nie została jeszcze zainstalowana. Instalowanie specjalistycznej obsługi niektórych języków może zapewnić dodatkową obsługę języka, taką jak IntelliSense lub inne zaawansowane funkcje językowe, takie jak żarówki.

## <a name="add-support-for-non-supported-languages"></a>Dodawanie obsługi języków nieobjętych obsługą

Program Visual Studio zapewnia obsługę języka w edytorze przy użyciu [TextMate Grammars](https://manual.macromates.com/en/language_grammars). Jeśli twój ulubiony język programowania obecnie nie jest obsługiwany w edytorze&mdash;programu Visual Studio, najpierw wyszukaj w internecie pakiet TextMate dla języka może już istnieć. Jeśli jednak nie możesz go znaleźć, możesz dodać obsługę dla niego samodzielnie, tworząc model pakietu TextMate dla gramatyki i fragmentów języka.

Dodaj wszystkie nowe funkcje TextMate Grammars for Visual Studio w następującym folderze:

*%userprofile%\\.vs\Rozszerzenia*

W obszarze tej ścieżki podstawowej dodaj następujące foldery, jeśli dotyczą one twojej sytuacji:

|Nazwa folderu|Opis|
|-----------------|-----------------|
|\\*\<nazwa języka>*|Folder języka. Zastąp * \<nazwę języka>* nazwą języka. Na przykład *\Matlab*.|
|*\Składnia*|Folder gramatyczny. Zawiera pliki gramatyczne *.json* dla języka, takie jak *Matlab.json*.|
|*\Urywki*|Folder urywki. Zawiera fragmenty kodu języka.|

W systemie Windows *%userprofile%* jest rozpoznawany jako ścieżka: *c:\Użytkownicy\\\<>nazwa użytkownika *. Jeśli folder *Rozszerzenia* nie istnieje w systemie, należy go utworzyć. Jeśli folder już istnieje, zostanie ukryty.

> [!TIP]
> Jeśli masz otwarte pliki w edytorze, musisz je zamknąć i ponownie otworzyć, aby zobaczyć podświetlanie składni po dodaniu poleutyki mate textmate.

Aby uzyskać szczegółowe informacje na temat tworzenia gramatyki mate textmate, zobacz [TextMate - Wprowadzenie do gramatyki języka](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) i [uwagi dotyczące tworzenia gramatyki języka i niestandardowego motywu dla pakietu Textmate](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle).

## <a name="see-also"></a>Zobacz też

- [Dodawanie rozszerzenia Language Server Protocol](../extensibility/adding-an-lsp-extension.md)
- [Przewodnik: tworzenie fragmentu kodu](../ide/walkthrough-creating-a-code-snippet.md)
- [Instruktaż: Zakończenie instrukcji wyświetlania](../extensibility/walkthrough-displaying-statement-completion.md)
