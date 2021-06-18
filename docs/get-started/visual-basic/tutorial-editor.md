---
title: Wprowadzenie do edytowania Visual Basic deweloperów
description: To 10-minutowe wprowadzenie do edytora kodu w programie Visual Studio przedstawia niektóre ze sposobów, w jakie program Visual Studio ułatwia pisanie, nawigowanie i zrozumienie Visual Basic kodu.
ms.custom: seodec18, get-started
ms.date: 11/20/2018
ms.technology: vs-ide-general
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 56f6570b633941c8f7102e245b7668cd31936f83
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308366"
---
# <a name="learn-to-use-the-code-editor-with-visual-basic"></a>Dowiedz się, jak używać edytora kodu z Visual Basic

W tym 10-minutowym wprowadzeniu do edytora kodu w programie Visual Studio dodamy kod do pliku, aby przyjrzeć się niektórym sposobom, w jaki program Visual Studio ułatwia pisanie, nawigowanie i zrozumienie Visual Basic kodu.

::: moniker range="vs-2017"

> [!TIP]
> Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/downloads) Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2022"

> [!TIP]
> Jeśli jeszcze nie zainstalowano programu Visual Studio Preview, przejdź do strony pobierania programu [Visual Studio 2022 (wersja](https://visualstudio.microsoft.com/vs/preview/vs2022) zapoznawcza), aby zainstalować ją bezpłatnie.

::: moniker-end

W tym artykule założono, że znasz już Visual Basic. Jeśli nie, zalecamy, aby najpierw przyjrzeć się samouczkowi, takie jak Rozpoczynanie pracy [Visual Basic w Visual Studio](../../get-started/visual-basic/tutorial-console.md) samouczku.

> [!TIP]
> Aby postępować zgodnie z tym artykułem, upewnij się, że wybrano Visual Basic ustawienia Visual Studio. Aby uzyskać informacje na temat wybierania ustawień zintegrowanego środowiska projektowego (IDE), zobacz [Wybieranie ustawień środowiska](visual-studio-ide.md#select-environment-settings).

## <a name="create-a-new-code-file"></a>Tworzenie nowego pliku kodu

Zacznij od utworzenia nowego pliku i dodania do niego kodu.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio. Naciśnij **klawisz Esc** lub kliknij przycisk Kontynuuj **bez** kodu w oknie uruchamiania, aby otworzyć środowisko projektowe.

::: moniker-end

2. W menu **Plik** na pasku menu wybierz pozycję **Nowy plik.**

3. W **oknie dialogowym Nowy** plik w kategorii **Ogólne** wybierz pozycję klasa Visual Basic , **a** następnie wybierz pozycję **Otwórz**.

   W edytorze zostanie otwarty nowy plik ze szkieletem Visual Basic klasy. (Możesz już zauważyć, że nie musisz tworzyć pełnego projektu Visual Studio, aby uzyskać niektóre korzyści, które oferuje edytor kodu, takie jak wyróżnianie składni. Wszystko, czego potrzebujesz, to plik kodu!

   ![Visual Basic pliku kodu w Visual Studio](media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Używanie fragmentów kodu

Visual Studio udostępnia przydatne *fragmenty* kodu, których można użyć do szybkiego i łatwego generowania często używanych bloków kodu. [Fragmenty kodu są dostępne](../../ide/code-snippets.md) dla różnych języków programowania, w tym Visual Basic, C# i C++. Dodajmy fragment kodu Visual Basic **Sub** do naszego pliku.

1. Umieść kursor nad wierszem o treści `End Class` , i wpisz **sub**.

   Zostanie wyświetlone okno podręczne z informacjami na temat słowa `Sub` kluczowego i sposobu wstawiania **fragmentu kodu Sub.**

   ![Funkcja IntelliSense dla fragmentu kodu w Visual Studio](media/tutorial-intellisense-snippet.png)

1. Naciśnij dwukrotnie klawisz **Tab,** aby wstawić fragment kodu.

   Konspekt procedury Sub `MySub()` jest dodawany do pliku.

Dostępne fragmenty kodu różnią się w zależności od języka programowania. Aby przyjrzeć się dostępnym fragmentom kodu dla Visual Basic, wybierz pozycję Edytuj wstaw fragment kodu  >  **funkcji IntelliSense**(lub naciśnij  >   klawisze **Ctrl** + **K,** **Ctrl** + **X).** Na Visual Basic fragmenty kodu są dostępne dla następujących kategorii:

![Visual Basic listy fragmentów kodu](media/tutorial-code-snippet-list.png)

Istnieją fragmenty kodu do określania, czy plik istnieje na komputerze, zapisu w pliku tekstowym, odczytywania wartości rejestru, wykonywania zapytania SQL, tworzenia pliku [For Each... Następna instrukcja](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)i wiele innych.

## <a name="comment-out-code"></a>Kod komentarza

Pasek narzędzi, który jest wierszem przycisków pod paskiem menu w Visual Studio, może pomóc w produktywności podczas kodzie. Można na przykład przełączać tryb uzupełniania IntelliSense, zwiększać lub zmniejszać wcięcie wiersza lub oznaczać jako komentarz kod, którego nie chcesz kompilować. [(IntelliSense](../../ide/using-intellisense.md) to pomoc w kodowaniu, która wyświetla listę pasujących metod, między innymi). W tej sekcji podamy komentarz do kodu.

![Przyciski paska narzędzi edytora](media/tutorial-editor-toolbar.png)

1. Wklej następujący kod do treści `MySub()` procedury.

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

1. Nie używamy tablicy, ale możemy jej użyć później, więc nie chcemy jej `morewords` całkowicie usuwać. Zamiast tego zajmijmy się komentarzami w tych wierszach. Wybierz całą definicję zamykającego nawiasu klamrowego, a następnie wybierz przycisk Oznacz jako komentarz wybrane `morewords` **wiersze** na pasku narzędzi. Jeśli wolisz używać klawiatury, naciśnij **klawisze Ctrl** + **K,** **Ctrl** + **C**.

   ![Przycisk Wyekseksuj komentarz](media/tutorial-comment-out.png)

   Znak Visual Basic komentarza jest dodawany na początku każdego wybranego wiersza w celu `'` komentarza kodu.

## <a name="collapse-code-blocks"></a>Zwijanie bloków kodu

Możesz zwinąć sekcje kodu, aby skoncentrować się tylko na tych częściach, które Cię interesują. Aby przećwiczyć, `_words` zwińmy tablicę do jednego wiersza kodu. Wybierz małe szare pole ze znakiem minus na marginesie wiersza z znakiem `Dim _words = New String() {` . Lub, jeśli jesteś użytkownikiem klawiatury, umieść kursor w dowolnym miejscu w definicji tablicy i naciśnij **klawisze Ctrl** + **M,** **Ctrl** + **M**.

![Zwijanie przycisku zwijania](media/tutorial-collapse.png)

Blok kodu zwija się tylko do pierwszego wiersza, po którym następuje wielokropek ( `...` ). Aby ponownie rozwinąć blok kodu, kliknij to samo szare pole, w których znajduje się znak plus, lub naciśnij ponownie **klawisze Ctrl** + **M** i **Ctrl** + **M.** Ta funkcja jest [nazywana zwijania](../../ide/outlining.md) i jest szczególnie przydatna w przypadku zwijania długich metod lub całych klas.

## <a name="view-symbol-definitions"></a>Wyświetlanie definicji symboli

Edytor Visual Studio ułatwia sprawdzanie definicji typu, metody itp. Jednym ze sposobów jest przejście do pliku zawierającego definicję, na przykład przez wybranie opcji **Przejdź** do definicji w dowolnym miejscu, do których odwołuje się symbol. Jeszcze szybszym sposobem, aby nie przenosić fokusu od pliku, w który pracujesz, jest użycie funkcji [Podgląd definicji](../../ide/go-to-and-peek-definition.md#peek-definition). Przyjrzyjmy się definicji `String` typu.

1. Kliknij prawym przyciskiem myszy wyraz i `String` wybierz polecenie **Peek Definition (Podgląd definicji)** z menu zawartości. Możesz też nacisnąć **klawisz Alt** + **F12.**

   Zostanie wyświetlone okno podręczne z definicją `String` klasy . Możesz przewijać w oknie podręcznym, a nawet podeglądać definicję innego typu ze podekiem kodu.

   ![Okno Podgląd definicji](media/tutorial-peek-definition.png)

1. Zamknij okno z podglądem definicji, wybierając małe pole z przyciskiem "x" w prawym górnym rogu okna podręcznego.

## <a name="use-intellisense-to-complete-words"></a>Używanie funkcji IntelliSense do dopełniania wyrazów

[IntelliSense](../../ide/using-intellisense.md) to nieoceny zasób podczas kodowania. Może ona wyświetlać informacje o dostępnych członkach typu lub szczegóły parametrów dla różnych przeciążeń metody. Możesz również użyć funkcji IntelliSense, aby zakończyć wyraz po wpisaniu wystarczającej ilości znaków, aby go ujmować. Dodajmy wiersz kodu, aby wydrukować uporządkowane ciągi w oknie konsoli, które jest standardowym miejscem dla danych wyjściowych programu.

1. Poniżej `query` zmiennej zacznij wpisywać następujący kod:

   ```vb
   For Each str In qu
   ```

   Funkcja IntelliSense wyświetla **szybkie informacje o** `query` symbolu.

   ![Uzupełnianie wyrazów funkcji IntelliSense w Visual Studio](media/tutorial-intellisense-completion-list.png)

1. Aby wstawić resztę wyrazu przy użyciu funkcji uzupełniania wyrazów `query` funkcji IntelliSense, naciśnij **klawisz Tab**.

1. Zakończ blok kodu, aby wyglądał jak poniższy kod.

   ```vb
   For Each str In query
       Console.WriteLine(str)
   Next
   ```

## <a name="refactor-a-name"></a>Refaktoryzacja nazwy

Nikt nie otrzymuje kodu po raz pierwszy, a jedną z rzeczy, które trzeba zmienić, jest nazwa zmiennej lub metody. Wypróbujmy funkcję refaktoryzacji [Visual Studio,](../../ide/refactoring-in-visual-studio.md) aby zmienić nazwę `_words` zmiennej na `words` .

1. Umieść kursor na definicji zmiennej i wybierz pozycję Zmień nazwę z menu kontekstowego lub kliknij `_words` prawym przyciskiem myszy. 

   W prawym **górnym** rogu edytora zostanie wyświetlone okno dialogowe Zmień nazwę.

1. Mając nadal `_words` wybraną zmienną, wpisz żądaną nazwę **wyrazów**. Zwróć uwagę, że nazwa odwołania do w `words` zapytaniu również jest automatycznie zmieniana. Przed naciśnięciem **klawisza Enter** lub kliknięciem **przycisku Zastosuj** zaznacz pole wyboru Uwzględnij **komentarze** w **oknie** podręcznym Zmień nazwę.

   ![Zmień nazwę — Okno dialogowe](media/tutorial-rename.png)

1. Naciśnij **klawisz Enter** lub kliknij przycisk **Zastosuj**.

   Nazwy obu wystąpień są zmieniane, a także odwołanie do w `words` `words` komentarzu do kodu.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Dowiedz się więcej o projektach i rozwiązaniach](tutorial-projects-solutions.md)

## <a name="see-also"></a>Zobacz też

- [Fragmenty kodu](../../ide/code-snippets.md)
- [Nawigowanie po kodzie](../../ide/navigating-code.md)
- [Tworzenie konspektu](../../ide/outlining.md)
- [Przejdź do definicji i Zobacz definicję](../../ide/go-to-and-peek-definition.md)
- [Refaktoryzacja](../../ide/refactoring-in-visual-studio.md)
- [Korzystanie z funkcji IntelliSense](../../ide/using-intellisense.md)
