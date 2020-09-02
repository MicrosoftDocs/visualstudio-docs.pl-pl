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
ms.openlocfilehash: c46120c369fa130e83620549ca0bc084a5075f7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "87235150"
---
# <a name="learn-to-use-the-code-editor-with-visual-basic"></a>Dowiedz się, jak używać edytora kodu z Visual Basic

W tym 10-minutowym wprowadzeniu do edytora kodu w programie Visual Studio dodamy kod do pliku, aby zapoznać się z innymi sposobami, w których program Visual Studio ułatwia pisanie, nawigowanie i zrozumienie Visual Basic kodzie.

::: moniker range="vs-2017"

> [!TIP]
> Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.

::: moniker-end

W tym artykule założono, że znasz już Visual Basic. Jeśli nie, zalecamy zapoznaj się z samouczkiem, takim jak [wprowadzenie do Visual Basic w programie Visual Studio](../../get-started/visual-basic/tutorial-console.md) .

> [!TIP]
> Aby postępować zgodnie z tym artykułem, upewnij się, że masz wybrane ustawienia Visual Basic dla programu Visual Studio. Aby uzyskać informacje o wybieraniu ustawień dla zintegrowanego środowiska programistycznego (IDE), zobacz [Wybieranie ustawień środowiska](visual-studio-ide.md#select-environment-settings).

## <a name="create-a-new-code-file"></a>Utwórz nowy plik kodu

Zacznij od utworzenia nowego pliku i dodania do niego kodu.

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

Program Visual Studio oferuje przydatne *fragmenty kodu* , za pomocą których można szybko i łatwo generować często używane bloki kodu. [Fragmenty kodu](../../ide/code-snippets.md) są dostępne dla różnych języków programowania, w tym Visual Basic, C# i C++. Dodajmy do pliku **podrzędny** fragment Visual Basic.

1. Umieść kursor nad wierszem, który brzmi `End Class` , i wpisz **Sub**.

   Zostanie wyświetlone okno dialogowe z informacjami o `Sub` słowie kluczowym i sposobie wstawienia fragmentu kodu **podrzędnego** .

   ![Funkcja IntelliSense dla fragmentu kodu w programie Visual Studio](media/tutorial-intellisense-snippet.png)

1. Naciśnij dwukrotnie klawisz **Tab** , aby wstawić fragment kodu.

   Konspekt procedury Sub `MySub()` zostanie dodany do pliku.

Dostępne fragmenty kodu są różne dla różnych języków programowania. Możesz sprawdzić dostępne fragmenty kodu dla Visual Basic, wybierając pozycję **Edytuj**  >  **IntelliSense**  >  **wstawkę** IntelliSense (lub naciśnij **klawisze CTRL** + **K**, **Ctrl** + **X**). W przypadku Visual Basic są dostępne fragmenty kodu dla następujących kategorii:

![Visual Basic listy fragmentów kodu](media/tutorial-code-snippet-list.png)

Istnieją fragmenty kodu służące do określenia, czy plik istnieje na komputerze, zapisywania do pliku tekstowego, odczytywania wartości rejestru, wykonywania zapytania SQL, tworzenia instrukcji [for each... Następna instrukcja](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)i wiele innych.

## <a name="comment-out-code"></a>Dodawanie komentarza do kodu

Pasek narzędzi, który jest wierszem przycisków na pasku menu w programie Visual Studio, może pomóc zwiększyć produktywność podczas pisania kodu. Można na przykład przełączyć tryb uzupełniania IntelliSense, zwiększyć lub zmniejszyć wcięcie linii lub dodać komentarz do kodu, który nie ma być kompilowany. ([IntelliSense](../../ide/using-intellisense.md) to pomoc dla kodowania, która wyświetla listę zgodnych metod, między innymi). W tej sekcji dodamy komentarz dotyczący kodu.

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

1. Nie używamy `morewords` macierzy, ale możemy jej użyć później, więc nie chcemy jej całkowicie usunąć. Zamiast tego Dodaj komentarz do tych wierszy. Zaznacz całą definicję `morewords` do zamykającego nawiasu klamrowego, a następnie wybierz przycisk Dodaj **komentarz do wybranych linii** na pasku narzędzi. Jeśli wolisz korzystać z klawiatury, naciśnij **klawisze CTRL** + **K**, **Ctrl +** + **C**.

   ![Przycisk komentowania](media/tutorial-comment-out.png)

   Znak komentarza Visual Basic `'` jest dodawany na początku każdego wybranego wiersza w celu dodania komentarza do kodu.

## <a name="collapse-code-blocks"></a>Zwijanie bloków kodu

Możesz zwinąć sekcje kodu, aby skoncentrować się tylko na interesujących Cię częściach. Aby to umożliwić, Zwiń `_words` tablicę do jednego wiersza kodu. Wybierz Małe szare pole ze znakiem minus wewnątrz niego na marginesie wiersza, który wskazuje `Dim _words = New String() {` . Jeśli jesteś użytkownikiem klawiatury, umieść kursor w dowolnym miejscu w definicji tablicy i naciśnij **klawisze CTRL** + **m**, **Ctrl** + **m**.

![Przycisk zwijania konspektu](media/tutorial-collapse.png)

Blok kodu jest zwijany tylko do pierwszego wiersza, a po nim wielokropek ( `...` ). Aby ponownie rozwinąć blok kodu, kliknij szare pole, które ma teraz znak plus, lub naciśnij klawisze **Ctrl** + **m**, **Ctrl** + **m** ponownie. Ta funkcja jest nazywana [tworzeniem konspektu](../../ide/outlining.md) i jest szczególnie przydatna w przypadku zwijania długich metod lub całych klas.

## <a name="view-symbol-definitions"></a>Wyświetl definicje symboli

Edytor programu Visual Studio ułatwia sprawdzanie definicji typu, metody itp. Jednym ze sposobów jest przechodzenie do pliku, który zawiera definicję, na przykład przez wybranie **Przejdź do definicji** wszędzie tam, gdzie znajduje się odwołanie do symbolu. Jeszcze szybszym sposobem, aby nie przenieść fokusu z pliku, w którym pracujesz, jest użycie [definicji wglądu](../../ide/go-to-and-peek-definition.md#peek-definition). Przejdźmy do definicji `String` typu.

1. Kliknij prawym przyciskiem myszy słowo `String` i wybierz polecenie **wgląd do definicji** z menu zawartość. Lub naciśnij klawisze **Alt** + **F12**.

   Zostanie wyświetlone okno podręczne z definicją `String` klasy. Można przewijać w oknie podręcznym, a nawet z dokładnością do definicji innego typu.

   ![Okno definicji wglądu](media/tutorial-peek-definition.png)

1. Zamknij okno Definicja wglądu, wybierając małe pole z symbolem "x" w prawym górnym rogu okna podręcznego.

## <a name="use-intellisense-to-complete-words"></a>Korzystanie z funkcji IntelliSense do uzupełniania wyrazów

[Technologia IntelliSense](../../ide/using-intellisense.md) jest niecennym zasobem podczas kodowania. Można wyświetlić informacje o dostępnych elementach członkowskich typu lub szczegółach parametrów dla różnych przeciążeń metody. Możesz również użyć funkcji IntelliSense, aby zakończyć wyraz po wpisaniu wystarczającej liczby znaków, aby odróżnić go. Dodajmy wiersz kodu, aby drukować uporządkowane ciągi do okna konsoli, który jest standardowym miejscem dla danych wyjściowych z programu.

1. Poniżej `query` zmiennej zacznij pisać następujący kod:

   ```vb
   For Each str In qu
   ```

   Zobaczysz, że IntelliSense wyświetla **szybkie informacje** o `query` symbolu.

   ![Uzupełnianie wyrazów IntelliSense w programie Visual Studio](media/tutorial-intellisense-completion-list.png)

1. Aby wstawić resztę słowa przy `query` użyciu funkcji uzupełniania słów IntelliSense, naciśnij klawisz **Tab**.

1. Zakończ pracę z blokiem kodu, aby wyglądać podobnie do poniższego kodu.

   ```vb
   For Each str In query
       Console.WriteLine(str)
   Next
   ```

## <a name="refactor-a-name"></a>Refaktoryzacja nazwy

Nikt nie pobiera kodu po raz pierwszy, a jedna z rzeczy, które trzeba zmienić, jest nazwą zmiennej lub metody. Wypróbujmy funkcję [refaktoryzacji](../../ide/refactoring-in-visual-studio.md) programu Visual Studio, aby zmienić nazwę `_words` zmiennej na `words` .

1. Umieść kursor nad definicją `_words` zmiennej i wybierz polecenie **Zmień nazwę** w menu kontekstowym lub prawym przyciskiem myszy.

   Okno dialogowe **zmiana nazwy** zostanie wyświetlone w prawym górnym rogu edytora.

1. Po `_words` wybraniu zmiennej wpisz odpowiednie nazwy **wyrazów**. Należy zauważyć, że Nazwa odwołania do `words` zapytania jest również automatycznie zmieniana. Przed naciśnięciem klawisza **Enter** lub kliknięciem przycisku **Zastosuj**zaznacz pole wyboru **Dołącz Komentarze** w oknie podręcznym **Zmień nazwę** .

   ![Zmień nazwę — Okno dialogowe](media/tutorial-rename.png)

1. Naciśnij klawisz **Enter** lub kliknij przycisk **Zastosuj**.

   Oba wystąpienia `words` są nazwy, a także odwołanie do `words` w komentarzu do kodu.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Informacje o projektach i rozwiązaniach](tutorial-projects-solutions.md)

## <a name="see-also"></a>Zobacz też

- [Fragmenty kodu](../../ide/code-snippets.md)
- [Nawiguj po kodzie](../../ide/navigating-code.md)
- [Tworzenie konspektu](../../ide/outlining.md)
- [Przejdź do definicji i Zobacz definicję](../../ide/go-to-and-peek-definition.md)
- [Refaktoryzacja](../../ide/refactoring-in-visual-studio.md)
- [Korzystanie z funkcji IntelliSense](../../ide/using-intellisense.md)
