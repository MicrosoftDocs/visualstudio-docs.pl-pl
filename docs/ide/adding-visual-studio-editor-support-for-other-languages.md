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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4e43325a6d749653c063c06f2c1c10c69f708da9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647794"
---
# <a name="add-visual-studio-editor-support-for-other-languages"></a>Dodaj obsługę edytora programu Visual Studio dla innych języków

Dowiedz się, jak edytor programu Visual Studio obsługuje odczytywanie i nawigowanie w różnych językach komputerowych oraz jak można dodać obsługę edytora programu Visual Studio dla innych języków.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Kolorowanie składni, uzupełnianie instrukcji i przechodzenie do pomocy technicznej

Funkcje w edytorze programu Visual Studio, takie jak kolorowanie składni, uzupełnianie instrukcji (nazywane także technologią IntelliSense) i _nawigowanie w usłudze_ ułatwiają łatwiejsze pisanie, odczytywanie i edytowanie kodu. Poniższy zrzut ekranu przedstawia przykład edytowania skryptu języka Perl w programie Visual Studio. Składnia jest automatycznie koloru. Na przykład uwagi w kodzie są kolorami zielonymi, kod jest czarny, ścieżki są czerwone, a instrukcje są niebieskie. Edytor programu Visual Studio automatycznie stosuje kolorowanie składni do dowolnego języka, który obsługuje. Ponadto, gdy zaczniesz wprowadzać znane słowo kluczowe lub obiekt języka, uzupełnianie instrukcji wyświetla listę możliwych instrukcji i obiektów. Uzupełnianie instrukcji ułatwia szybkie i łatwe pisanie kodu.

![Kolorowanie składni w skrypcie języka Perl](../ide/media/vside_perledit.png)

Program Visual Studio obecnie zapewnia kolorowanie składni i obsługę uzupełniania podstawowych instrukcji dla następujących języków przy użyciu [gramatyki Deoficerów](https://manual.macromates.com/en/language_grammars). Jeśli ulubiony język nie znajduje się w tabeli, ale nie martw się, &mdash;you może go dodać.

|||||||
|-|-|-|-|-|-|
|Technique|F#|Java|Promocji|Rust|Visual Basic|
|Clojure|Udać|JavaDoc|Objective-C|ShaderLab|C#|
|CMake|Groovy|JSON|Języku|ShellScript|Visual C++|
|CoffeeScript|HTML|WCZEŚNIEJSZ|Python|SQL|VBNet|
|CSS|INI|LUA|R|Adres|XML|
|Docker|Jade|SprawdY|Dopisek|TypeScript|YAML|

Oprócz kolorowania składni i uzupełniania podstawowych instrukcji, Visual Studio ma również funkcję o nazwie [Przejdź do](https://blogs.msdn.microsoft.com/benwilli/2015/04/09/visual-studio-tip-3-use-navigate-to/). Ta funkcja umożliwia szybkie wyszukiwanie plików kodu, ścieżek plików i symboli kodu. Program Visual Studio oferuje przechodzenie do obsługi następujących języków.

- C#

- C++

- TypeScript

- JavaScript

- Visual Basic

- Udać

- Java

- Obsługa

Wszystkie te typy plików mają opisane wcześniej funkcje, nawet jeśli obsługa danego języka nie została jeszcze zainstalowana. Zainstalowanie wyspecjalizowanej pomocy technicznej w przypadku niektórych języków może zapewnić obsługę dodatkowych języków, takich jak IntelliSense lub inne zaawansowane funkcje językowe, takie jak żarówki.

## <a name="add-support-for-non-supported-languages"></a>Dodawanie obsługi dla nieobsługiwanych języków

Program Visual Studio zapewnia obsługę języka w edytorze przy użyciu [gramatyki Deautomatyzujj](https://manual.macromates.com/en/language_grammars). Jeśli ulubiony język programowania nie jest obecnie obsługiwany w edytorze programu Visual Studio, należy najpierw przeszukać pakiet narzędzia Web &mdash;a textoficer dla tego języka. Jeśli nie możesz znaleźć jednego z nich, możesz samodzielnie dodać do niego pomoc techniczną, tworząc model pakietu deautomatyzujgo dla gramatyki języka i fragmentów kodu.

Dodaj nowe gramatyki deautomatyzuje dla programu Visual Studio w następującym folderze:

*% USERPROFILE% \\. vs\Extensions*

W tej ścieżce podstawowej Dodaj następujące foldery, jeśli mają zastosowanie do Twojej sytuacji:

|Nazwa folderu|Opis|
|-----------------|-----------------|
|\\ *nazwę \<language >*|Folder języka. Zastąp *\<language nazwę >* nazwą języka. Na przykład *\Matlab*.|
|*\Syntaxes*|Folder gramatyki. Zawiera pliki gramatyce *. JSON* dla języka, takie jak *MATLAB. JSON*.|
|*\Snippets*|Folder fragmentów kodu. Zawiera fragmenty kodu dla języka.|

W systemie Windows *% USERPROFILE%* jest rozpoznawana jako ścieżka: *c:\Users \\ \<user > nazwy*. Jeśli folder *rozszerzeń* nie istnieje w systemie, należy go utworzyć. Jeśli folder już istnieje, zostanie on ukryty.

> [!TIP]
> Jeśli w edytorze znajdują się jakieś pliki, musisz je zamknąć i ponownie otworzyć, aby wyświetlić wyróżnianie składni po dodaniu gramatyki.

Aby uzyskać szczegółowe informacje na temat tworzenia gramatyki Details, zobacz detailion [-Introduction to Languages](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) i [uwagi na temat tworzenia gramatyki języka i motywu niestandardowego dla pakietu](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle)details.

## <a name="see-also"></a>Zobacz także

- [Dodawanie rozszerzenia protokołu serwera języka](../extensibility/adding-an-lsp-extension.md)
- [Przewodnik: tworzenie fragmentu kodu](../ide/walkthrough-creating-a-code-snippet.md)
- [Przewodnik: Wyświetlanie instrukcji wyświetlania](../extensibility/walkthrough-displaying-statement-completion.md)
