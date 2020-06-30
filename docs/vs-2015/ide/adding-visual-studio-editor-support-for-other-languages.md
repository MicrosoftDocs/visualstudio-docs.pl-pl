---
title: Dodawanie obsługi edytora dla innych języków | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9dbd245edd81907197e23c0d193a01cc07424b4
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548112"
---
# <a name="adding-visual-studio-editor-support-for-other-languages"></a>Dodawanie obsługi innych języków do edytora programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dowiedz się, jak edytor programu Visual Studio obsługuje odczytywanie i nawigowanie w różnych językach komputerowych oraz jak można dodać obsługę edytora programu Visual Studio dla innych języków.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Kolorowanie składni, uzupełnianie instrukcji i przechodzenie do pomocy technicznej
 Funkcje w edytorze programu Visual Studio, takie jak kolorowanie składni, uzupełnianie instrukcji i nawigowanie w usłudze, mogą ułatwić łatwiejsze odczytywanie, tworzenie i edytowanie kodu. Poniższy zrzut ekranu przedstawia przykład edytowania skryptu języka Perl w programie Visual Studio. Składnia jest automatycznie koloru. Na przykład uwagi w kodzie są kolorami zielonymi, kod jest czarny, ścieżki są czerwone, a instrukcje są niebieskie. Edytor programu Visual Studio automatycznie stosuje kolorowanie składni do dowolnego języka, który obsługuje. Ponadto, gdy zaczniesz wprowadzać znane słowo kluczowe lub obiekt języka, uzupełnianie instrukcji wyświetla listę możliwych instrukcji i obiektów. Uzupełnianie instrukcji może ułatwić szybkie i łatwe tworzenie kodu.

 ![Kolorowanie składni w skrypcie języka Perl](../ide/media/vside-perledit.png "VSIDE_PerlEdit")

 Program Visual Studio obecnie zapewnia kolorowanie składni i obsługę uzupełniania podstawowych instrukcji dla następujących języków przy użyciu [gramatyki Deoficerów](https://manual.macromates.com/en/language_grammars). Jeśli Twój ulubiony język nie znajduje się w tabeli, nie martw się — możesz dodać go.

- Technique
- F#
- Java
- Znaczniki języka Markdown
- Rust
- Visual Basic
- Clojure
- Go
- JavaDoc
- Objective-C
- ShaderLab
- C#
- CMake
- Groovy
- JSON
- Języku
- ShellScript
- Visual C++
- CoffeeScript
- HTML
- WCZEŚNIEJSZ
- Python
- SQL
- VBNet
- CSS
- INI
- LUA
- R
- Swift
- XML
- Docker
- Jade
- Marka
- Ruby
- TypeScript
- YAML

 Oprócz kolorowania składni i uzupełniania podstawowych instrukcji, Visual Studio ma również funkcję o nazwie [Przejdź do](https://blogs.msdn.microsoft.com/benwilli/2015/04/09/visual-studio-tip-3-use-navigate-to/). Ta funkcja umożliwia szybkie wyszukiwanie plików kodu, ścieżek plików i symboli kodu. Program Visual Studio oferuje przechodzenie do obsługi następujących języków.

- Przejdź

- Java

- JavaScript

- PHP

- TypeScript

- Visual Basic

- Visual C++

- Visual C#

  Wszystkie te typy plików mają opisane wcześniej funkcje, nawet jeśli obsługa danego języka nie została jeszcze zainstalowana. Zainstalowanie wyspecjalizowanej pomocy technicznej w przypadku niektórych języków może zapewnić obsługę dodatkowych języków, takich jak IntelliSense lub inne zaawansowane funkcje językowe, takie jak żarówki.

## <a name="adding-support-for-non-supported-languages"></a>Dodawanie obsługi dla nieobsługiwanych języków
 Program Visual Studio 2015 Update 1 i jego nowsze wersje zapewniają obsługę języka w edytorze przy użyciu [gramatyki Deautomatyzujj](https://manual.macromates.com/en/language_grammars). Jeśli ulubiony język programowania nie jest obecnie obsługiwany w edytorze programu Visual Studio, należy najpierw przeszukać ten pakiet, który już istnieje w sieci Web. Jeśli nie możesz znaleźć jednego z nich, możesz dodać jego obsługę samodzielnie w programie Visual Studio 2015 Update 1 lub nowszym, tworząc model pakietu deautomatyzujgo dla gramatyki i fragmentów języka.

 Dodaj nowe gramatyki deautomatyzuje dla programu Visual Studio w następującym folderze:

 % USERPROFILE% \\ . vs\Extensions

 W tej ścieżce podstawowej Dodaj następujące foldery, jeśli są one stosowane do danej sytuacji:

|Nazwa folderu|Opis|
|-----------------|-----------------|
|\\*\<language name>*|Folder języka. Zamień *\<language name>* na nazwę języka. Na przykład **\Matlab**.|
|\Syntaxes|Folder gramatyki. Zawiera pliki gramatyce. JSON dla języka, takie jak **Matlab.json**.|
|\Snippets|Folder fragmentów kodu. Zawiera fragmenty kodu dla języka.|

 W systemie Windows% USERPROFILE% jest rozpoznawany jako ścieżka: c:\Users \\ *\<user name>* . Jeśli folder rozszerzeń nie istnieje w systemie, należy go utworzyć. Jeśli folder już istnieje, zostanie on ukryty.

 Aby uzyskać szczegółowe informacje na temat tworzenia gramatyki Details, zobacz Details [— wprowadzenie do gramatyki języka: jak dodać wyróżnioną składnię kodu źródłowego osadzoną w kodzie HTML](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) i [uwagi na temat tworzenia gramatyki języka i niestandardowego motywu dla pakietu](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle)deautomatyzacji.

## <a name="see-also"></a>Zobacz też
 [Visual Studio 2013 przechodzenie do ulepszeń](https://blogs.msdn.microsoft.com/mvpawardprogram/2013/10/22/visual-studio-2013-navigate-to-improvements/) [Instruktaż: Tworzenie](../ide/walkthrough-creating-a-code-snippet.md) [przewodnika po fragmencie kodu: wyświetlanie uzupełniania instrukcji](../extensibility/walkthrough-displaying-statement-completion.md)
