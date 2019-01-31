---
title: Wprowadzenie do edycji dla deweloperów programu Visual Basic
description: To wprowadzenie 10-minutowe do edytora kodu w programie Visual Studio zawiera kilka sposobów, że Visual Studio wprowadza pisania, nawigowania i zrozumienie kodu języka Visual Basic jest łatwiejsze.
ms.custom: seodec18, get-started
ms.date: 11/20/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: tutorial
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: b2183b12f1614adf7939c17b3e260cebb1c3238b
ms.sourcegitcommit: 9866740aec05d1a3a5dc3b4b6d2ceaeecbd3fc29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55424489"
---
# <a name="learn-to-use-the-code-editor"></a>Dowiedz się, jak za pomocą edytora kodu

W ramach tego wprowadzenia do edytora kodu w programie Visual Studio 10-minutowe dodamy kod do pliku w celu Spójrz na kilka sposobów, że program Visual Studio sprawia, że pisania, nawigowania i zrozumienie kodu łatwiej.

> [!TIP]
> Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

W tym artykule przyjęto założenie, że już znasz Visual Basic. Jeśli nie masz, Sugerujemy, zobacz samouczek takich jak [wprowadzenie do języka Visual Basic w programie Visual Studio](../../get-started/visual-basic/tutorial-console.md) pierwszy.

> [!TIP]
> Aby skorzystać z tego artykułu, upewnij się, że wybrano dla programu Visual Studio ustawienia języka Visual Basic. Aby dowiedzieć się, jak wybranie ustawienia dla zintegrowanego środowiska programistycznego (IDE), zobacz [wybierz ustawienia środowiska](visual-studio-ide.md#select-environment-settings).

## <a name="create-a-new-code-file"></a>Utwórz nowy plik kodu

Rozpocznij, tworząc nowy plik i dodawanie kodu do niego.

1. Otwórz program Visual Studio i **pliku** menu na pasku menu wybierz opcję **nowy plik**.

1. W **nowy plik** okno dialogowe, w obszarze **ogólne** kategorii, wybierz **klasy Visual Basic**, a następnie wybierz **Otwórz**.

   Nowy plik zostanie otwarty w edytorze za pomocą szkielet klasa Visual Basic. (Można już zauważysz, że nie trzeba utworzyć pełny projekt programu Visual Studio na uzyskanie niektórych korzyści oferowanych przez Edytor kodu, takich jak wyróżnianie składni. Wymagany jest plik kodu!)

   ![Plik kodu języka Visual Basic w programie Visual Studio](media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Używanie fragmentów kodu

Program Visual Studio oferuje przydatne *fragmenty kodu* , umożliwia szybkie i łatwe generowanie najczęściej używane bloki kodu. [Fragmenty kodu](../../ide/code-snippets.md) są dostępne dla różnych języków programowania, w tym Visual Basic C#i C++. Dodajmy języka Visual Basic **Sub** fragment kodu do naszego pliku.

1. Umieść kursor nad wierszem, który mówi `End Class`i wpisz **sub**.

   Wyskakujące okno dialogowe pojawia się z informacjami o `Sub` — słowo kluczowe i sposób wstawiania **Sub** fragmentu kodu.

   ![Funkcja IntelliSense dla fragmentu kodu w programie Visual Studio](media/tutorial-intellisense-snippet.png)

1. Naciśnij klawisz **kartę** dwa razy, aby wstawić fragment kodu.

   Konspekt dla procedury Sub `MySub()` jest dodawany do pliku.

Fragmenty kodu dostępne różnią się w różnych językach programowania. Można przyjrzeć się fragmentów kodu dostępne dla języka Visual Basic, wybierając **Edytuj** > **IntelliSense** > **Wstaw fragment kodu** (lub naciśnij  **CTRL**+**K**, **Ctrl**+**X**). Dla języka Visual Basic fragmenty kodu są dostępne w ramach następujących kategorii:

![Lista fragment kodu języka Visual Basic](media/tutorial-code-snippet-list.png)

Istnieją fragmentów kodu do określania, jeśli plik istnieje na komputerze, zapisywania do pliku tekstowego, odczytać wartości rejestru, wykonywanie zapytania SQL, tworząc [For Each... Następna instrukcja](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)i wiele innych.

## <a name="comment-out-code"></a>Komentarz do kodu

Pasek narzędzi, który jest wiersz przycisków poniżej paska menu w programie Visual Studio, może pomóc zwiększyć produktywność kodowania. Na przykład możesz można Przełącz tryb uzupełniania IntelliSense, zwiększyć Zmniejsz wcięcie wiersza lub przekształcić w komentarz kod, nie chcesz skompilować. ([IntelliSense](../../ide/using-intellisense.md) jest pomoc kodowania, który zawiera listę metod, między innymi dopasowania.) W tej sekcji firma Microsoft będzie komentarz kodu.

![Przyciski paska narzędzi edytora](media/tutorial-editor-toolbar.png)

1. Wklej następujący kod do `MySub()` treści procedury.

   ```vb
   ' _words is a string array that we'll sort alphabetically
   Dim _words = New String() {
   "the",
   "quick",
   "brown",
   "fox",
   "jumps"
   }

   Dim morewords = New String() {
   "over",
   "the",
   "lazy",
   "dog"
   }

   Dim query = From word In _words
               Order By word.Length
               Select word
   ```

1. Nie używamy `morewords` tablicy, ale firma Microsoft może używać go później tak nie chcemy całkowicie usunąć go. Zamiast tego Załóżmy komentarz te wiersze. Zaznacz całą definicję `morewords` do nawias zamykający nawias klamrowy, a następnie wybierz **komentarz zaznaczonych wierszach** przycisk na pasku narzędzi. Jeśli wolisz użyć klawiatury, naciśnij klawisz **Ctrl**+**K**, **Ctrl**+**C**.

   ![Komentarz przycisku](media/tutorial-comment-out.png)

   Znak komentarz języka Visual Basic `'` zostanie dodany na początku każdego wybranego wiersza, aby przekształcić w komentarz kod.

## <a name="collapse-code-blocks"></a>Zwiń bloki kodu

Można zwinąć fragmentów kodu, aby skoncentrować się tylko na części, które Cię interesują. Praktyczne, możemy Zwiń `_words` tablicy do jednego wiersza kodu. Wybierz małe pole szarego znakiem minus znajdującym się w nim na marginesie wiersz, który jest wyświetlany komunikat `Dim _words = New String() {`. Lub, jeśli jesteś użytkownikiem klawiatury, umieść kursor gdziekolwiek w definicji tablicy i naciśnij klawisz **Ctrl**+**M**, **Ctrl**+**M** .

![Przycisk Zwiń konspekt](media/tutorial-collapse.png)

Blok kodu jest ustawiana na tylko pierwszy wiersz, następuje wielokropek (`...`). Aby rozwinąć blok kodu ponownie, kliknij pole szarego tego samego, który ma teraz znakiem plus lub naciśnij klawisz **Ctrl**+**M**, **Ctrl**+**M**  ponownie. Ta funkcja jest nazywana [konspekt](../../ide/outlining.md) i jest szczególnie przydatne, gdy one zwijanie długie metod lub klas całego.

## <a name="view-symbol-definitions"></a>Wyświetlanie definicji symbolu

Edytor programu Visual Studio można łatwo sprawdzić definicji typu, metody itd. Jednym ze sposobów jest przejdź do pliku, który zawiera definicję, na przykład wybierając **przejdź do definicji** dowolnym odwołuje się do symbolu. Jeszcze szybszy sposób, który nie zmienia się od pliku pracujesz w jest użycie [Peek Definition](../../ide/go-to-and-peek-definition.md#peek-definition). Umożliwia wgląd w definicji `String` typu.

1. Kliknij prawym przyciskiem myszy na słowo `String` i wybierz polecenie **Peek Definition** menu zawartości. Lub naciśnij **Alt**+**F12**.

   Okno wyskakujące pojawia się przy użyciu definicji elementu `String` klasy. Można przewijać w oknie podręcznym lub nawet rzut oka na definicję innego typu niż peeked kodu.

   ![Okna definicji wglądu](media/tutorial-peek-definition.png)

1. Zamknij okno definicji podejrzeć, wybierając pole małych znakiem "x" w prawym górnym rogu okna podręcznego.

## <a name="use-intellisense-to-complete-words"></a>Funkcja IntelliSense są używane do realizowania słów

[Funkcja IntelliSense](../../ide/using-intellisense.md) jest zasobem nieocenione, gdy masz kodowania. Jego można wyświetlić informacje o dostępne elementy członkowskie typu lub szczegóły parametrów dla innego przeciążenia metody. Funkcja IntelliSense umożliwia również Dokończ wyraz, po wpisaniu małej liczby znaków, aby odróżnić go. Dodajmy wiersza kodu, aby wydrukować zamówione ciągi w oknie konsoli, czyli miejsce standardowe dane wyjściowe programu do go.

1. Poniżej `query` zmiennej, wpisz następujący kod:

   ```vb
   For Each str In qu
   ```

   Zobacz IntelliSense dowiesz się, **Quick Info** o `query` symboli.

   ![Uzupełnianie wyrazów w technologii IntelliSense w programie Visual Studio](media/tutorial-intellisense-completion-list.png)

1. Aby wstawić pozostałe słowa `query` za pomocą funkcji uzupełniania programu word w technologii IntelliSense, naciśnij klawisz **kartę**.

1. Zakończ poza blok kodu, aby wyglądała jak poniższy kod.

   ```vb
   For Each str In query
       Console.WriteLine(str)
   Next
   ```

## <a name="refactor-a-name"></a>Refaktoryzuj nazwę

Nikt nie pobiera kod bezpośrednio po raz pierwszy, a jedną z rzeczy, które trzeba zmienić to nazwa zmiennej lub metody. Spróbujmy programu Visual Studio [zrefaktoryzuj](../../ide/refactoring-in-visual-studio.md) funkcji, aby zmienić nazwę `_words` zmienną `words`.

1. Umieść kursor nad definicji `_words` zmiennej i wybierz polecenie **Zmień nazwę** w menu kliknij prawym przyciskiem myszy lub kontekstu.

   Okno podręczne **Zmień nazwę** okno dialogowe pojawia się u góry bezpośrednio z edytora.

1. Za pomocą zmiennej `_words` nadal zaznaczone, wpisz odpowiednią nazwę **wyrazy**. Należy zauważyć, że odwołanie do `words` również automatycznie została zmieniona w zapytaniu. Przed naciśnięciem **Enter** lub kliknij przycisk **Zastosuj**, wybierz opcję **dodawać komentarze** pola wyboru w **Zmień nazwę** okno podręczne.

   ![Zmień nazwę — Okno dialogowe](media/tutorial-rename.png)

1. Naciśnij klawisz **Enter** lub kliknij przycisk **Zastosuj**.

   Oba wystąpienia `words` zostały zmienione, a także odwołania do `words` w komentarzu do kodu.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Dowiedz się więcej o projekty i rozwiązania](tutorial-projects-solutions.md)

## <a name="see-also"></a>Zobacz także

- [Fragmenty kodu](../../ide/code-snippets.md)
- [Przechodzenie do kodu](../../ide/navigating-code.md)
- [Obramowanie](../../ide/outlining.md)
- [Polecenia Przejdź do definicji i Zobacz definicję](../../ide/go-to-and-peek-definition.md)
- [Refaktoryzacja](../../ide/refactoring-in-visual-studio.md)
- [Korzystanie z funkcji IntelliSense](../../ide/using-intellisense.md)