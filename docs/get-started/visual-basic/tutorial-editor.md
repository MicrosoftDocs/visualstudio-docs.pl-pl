---
title: Wprowadzenie do edytowania dla deweloperów Visual Basic
description: W tym 10-minutowym wprowadzeniu do edytora kodu w programie Visual Studio przedstawiono niektóre sposoby łatwiejszego zapisywania, nawigowania i interpretowania Visual Basic kodu przez program Visual Studio.
ms.custom: seodec18, get-started
ms.date: 11/20/2018
ms.technology: vs-ide-general
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 695b1600aedb30a9e75a7829af4bac400f069922
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75584611"
---
# <a name="learn-to-use-the-code-editor"></a>Dowiedz się, jak za pomocą edytora kodu

W ramach tego wprowadzenia do edytora kodu w programie Visual Studio 10-minutowe dodamy kod do pliku w celu Spójrz na kilka sposobów, że program Visual Studio sprawia, że pisania, nawigowania i zrozumienie kodu łatwiej.

::: moniker range="vs-2017"

> [!TIP]
> Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) strony, aby zainstalować go za darmo.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads) strony, aby zainstalować go za darmo.

::: moniker-end

W tym artykule założono, że znasz już Visual Basic. Jeśli nie, zalecamy zapoznaj się z samouczkiem, takim jak [wprowadzenie do Visual Basic w programie Visual Studio](../../get-started/visual-basic/tutorial-console.md) .

> [!TIP]
> Aby postępować zgodnie z tym artykułem, upewnij się, że masz wybrane ustawienia Visual Basic dla programu Visual Studio. Aby uzyskać informacje o wybieraniu ustawień dla zintegrowanego środowiska programistycznego (IDE), zobacz [Wybieranie ustawień środowiska](visual-studio-ide.md#select-environment-settings).

## <a name="create-a-new-code-file"></a>Utwórz nowy plik kodu

Rozpocznij, tworząc nowy plik i dodawanie kodu do niego.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio. Naciśnij klawisz **ESC** lub kliknij pozycję **Kontynuuj bez kodu** w oknie uruchamiania, aby otworzyć środowisko programistyczne.

::: moniker-end

2. Z menu **plik** na pasku menu wybierz polecenie **nowy plik**.

3. W oknie dialogowym **nowy plik** w obszarze Kategoria **ogólne** wybierz pozycję **Visual Basic Klasa**, a następnie wybierz pozycję **Otwórz**.

   Nowy plik zostanie otwarty w edytorze z szkieletem klasy Visual Basic. (Można już zauważyć, że nie trzeba tworzyć pełnego projektu programu Visual Studio, aby uzyskać pewne korzyści, które oferuje Edytor kodu, takie jak wyróżnianie składni. Wszystko, co jest potrzebne, jest plikiem kodu!)

   ![Visual Basic pliku kodu w programie Visual Studio](media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Używanie fragmentów kodu

Program Visual Studio oferuje przydatne *fragmenty kodu* , umożliwia szybkie i łatwe generowanie najczęściej używane bloki kodu. [Fragmenty kodu](../../ide/code-snippets.md) są dostępne dla różnych języków programowania, w tym Visual Basic C#, i C++. Dodajmy do pliku **podrzędny** fragment Visual Basic.

1. Umieść kursor nad wierszem, który brzmi `End Class`, a następnie wpisz **Sub**.

   Zostanie wyświetlone okno dialogowe z informacjami dotyczącymi słowa kluczowego `Sub` i sposobu wstawienia fragmentu kodu **podrzędnego** .

   ![Funkcja IntelliSense dla fragmentu kodu w programie Visual Studio](media/tutorial-intellisense-snippet.png)

1. Naciśnij klawisz **kartę** dwa razy, aby wstawić fragment kodu.

   Do pliku zostanie dodany kontur procedury podrzędnej `MySub()`.

Fragmenty kodu dostępne różnią się w różnych językach programowania. Możesz sprawdzić dostępne fragmenty kodu dla Visual Basic, wybierając pozycję **edytuj** > **IntelliSense** > **Wstaw** wstawkę (lub naciśnij **klawisze CTRL**+**K**, **Ctrl**+**X**). W przypadku Visual Basic są dostępne fragmenty kodu dla następujących kategorii:

![Visual Basic listy fragmentów kodu](media/tutorial-code-snippet-list.png)

Istnieją fragmenty kodu służące do określenia, czy plik istnieje na komputerze, zapisywania do pliku tekstowego, odczytywania wartości rejestru, wykonywania zapytania SQL, tworzenia instrukcji [for each... Następna instrukcja](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)i wiele innych.

## <a name="comment-out-code"></a>Komentarz do kodu

Pasek narzędzi, który jest wiersz przycisków poniżej paska menu w programie Visual Studio, może pomóc zwiększyć produktywność kodowania. Można na przykład przełączyć tryb uzupełniania IntelliSense, zwiększyć lub zmniejszyć wcięcie linii lub dodać komentarz do kodu, który nie ma być kompilowany. ([IntelliSense](../../ide/using-intellisense.md) to pomoc dla kodowania, która wyświetla listę zgodnych metod, między innymi). W tej sekcji dodamy komentarz dotyczący kodu.

![Przyciski paska narzędzi edytora](media/tutorial-editor-toolbar.png)

1. Wklej następujący kod do treści procedury `MySub()`.

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

1. Nie używamy tablicy `morewords`, ale możemy jej użyć później, więc nie chcemy jej całkowicie usunąć. Zamiast tego Załóżmy komentarz te wiersze. Zaznacz całą definicję `morewords` do zamykającego nawiasu klamrowego, a następnie wybierz przycisk Dodaj **komentarz do wybranych linii** na pasku narzędzi. Jeśli wolisz użyć klawiatury, naciśnij klawisz **Ctrl**+**K**, **Ctrl**+**C**.

   ![Komentarz przycisku](media/tutorial-comment-out.png)

   Visual Basic znak komentarza `'` jest dodawany do początku każdego zaznaczonego wiersza w celu dodania komentarza do kodu.

## <a name="collapse-code-blocks"></a>Zwiń bloki kodu

Możesz zwinąć sekcje kodu, aby skoncentrować się tylko na interesujących Cię częściach. Aby to umożliwić, Zwiń tablicę `_words` do jednego wiersza kodu. Wybierz Małe szare pole ze znakiem minus wewnątrz niego na marginesie linii, która mówi `Dim _words = New String() {`. Jeśli jesteś użytkownikiem klawiatury, umieść kursor w dowolnym miejscu w definicji tablicy i naciśnij **klawisze ctrl**+**m**, **Ctrl**+**m**.

![Przycisk Zwiń konspekt](media/tutorial-collapse.png)

Blok kodu jest ustawiana na tylko pierwszy wiersz, następuje wielokropek (`...`). Aby rozwinąć blok kodu ponownie, kliknij pole szarego tego samego, który ma teraz znakiem plus lub naciśnij klawisz **Ctrl**+**M**, **Ctrl**+**M**  ponownie. Ta funkcja jest nazywana [konspekt](../../ide/outlining.md) i jest szczególnie przydatne, gdy one zwijanie długie metod lub klas całego.

## <a name="view-symbol-definitions"></a>Wyświetlanie definicji symbolu

Edytor programu Visual Studio ułatwia sprawdzanie definicji typu, metody itp. Jednym ze sposobów jest przechodzenie do pliku, który zawiera definicję, na przykład przez wybranie **Przejdź do definicji** wszędzie tam, gdzie znajduje się odwołanie do symbolu. Jeszcze szybszy sposób, który nie zmienia się od pliku pracujesz w jest użycie [Peek Definition](../../ide/go-to-and-peek-definition.md#peek-definition). Umożliwia wgląd w definicji `String` typu.

1. Kliknij prawym przyciskiem myszy słowo `String` a następnie wybierz polecenie **Podgląd definicji** z menu zawartość. Lub naciśnij **Alt**+**F12**.

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

1. Umieść kursor nad definicją zmiennej `_words` i wybierz polecenie **Zmień nazwę** w menu kontekstowym lub prawym przyciskiem myszy.

   Okno podręczne **Zmień nazwę** okno dialogowe pojawia się u góry bezpośrednio z edytora.

1. Gdy zmienna `_words` nadal zaznaczona, wpisz odpowiednią nazwę **wyrazów**. Należy zauważyć, że odwołanie do `words` również automatycznie została zmieniona w zapytaniu. Przed naciśnięciem klawisza **Enter** lub kliknięciem przycisku **Zastosuj**zaznacz pole wyboru **Dołącz Komentarze** w oknie podręcznym **Zmień nazwę** .

   ![Zmień nazwę — Okno dialogowe](media/tutorial-rename.png)

1. Naciśnij klawisz **Enter** lub kliknij przycisk **Zastosuj**.

   Należy zmienić nazwy obu wystąpień `words`, a także odwołanie do `words` w komentarzu do kodu.

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
