---
title: Wprowadzenie do edytowania w edytorze kodu
description: Dowiedz się, jak za pomocą edytora kodu Visual Studio dodawać kod do pliku, a także jak pisać kod, przechodzić do niego i refaktoryzować go.
ms.date: 11/30/2017
ms.technology: vs-ide-general
ms.custom:
- vs-acquisition
- get-started
- SEO-VS-2020
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 0ce656c43dd04ab91bd3fd34dcd01dbad27cc644
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386452"
---
# <a name="learn-to-use-the-code-editor"></a>Dowiedz się, jak używać edytora kodu

W tym 10-minutowym wprowadzeniu do edytora kodu w programie Visual Studio dodamy kod do pliku, aby przyjrzeć się niektórym sposobom, Visual Studio ułatwia pisanie, nawigowanie i zrozumienie kodu.

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
> Jeśli jeszcze nie zainstalowano programu Visual Studio 2022 (wersja zapoznawcza), przejdź do strony pobierania programu [Visual Studio 2022 Preview,](https://visualstudio.microsoft.com/vs/preview/vs2022) aby zainstalować ją bezpłatnie.

::: moniker-end

W tym artykule założono, że znasz już język programowania. Jeśli nie, zalecamy, aby najpierw przyjrzeć się jednem z przewodników Szybki start dotyczących programowania, takim jak tworzenie aplikacji internetowej przy użyciu języka [Python](../ide/quickstart-python.md) lub [C#](../get-started/csharp/tutorial-aspnet-core.md)albo tworzenie aplikacji konsolowej przy użyciu języka [Visual Basic](../ide/quickstart-visual-basic-console.md) lub [C++.](/cpp/get-started/tutorial-console-cpp)

## <a name="create-a-new-code-file"></a>Tworzenie nowego pliku kodu

Zacznij od utworzenia nowego pliku i dodania do niego kodu.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio. Naciśnij **klawisz Esc** lub kliknij przycisk Kontynuuj **bez** kodu w oknie uruchamiania, aby otworzyć środowisko projektowe.

::: moniker-end

2. W menu **Plik** na pasku menu wybierz pozycję **Nowy**  >  **plik.**

3. W **oknie dialogowym Nowy** plik w kategorii **Ogólne** wybierz pozycję Visual C# Class (Klasa **Visual C#),** a następnie wybierz pozycję **Open (Otwórz).**

   W edytorze zostanie otwarty nowy plik ze szkieletem klasy C#. (Zwróć uwagę, że nie musimy tworzyć pełnego projektu Visual Studio, aby uzyskać niektóre korzyści zapewniane przez edytor kodu. Wystarczy tylko plik kodu).

   ![Plik kodu C# w Visual Studio](media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Używanie fragmentów kodu

Visual Studio udostępnia przydatne *fragmenty* kodu, których można użyć do szybkiego i łatwego generowania często używanych bloków kodu. [Fragmenty kodu są dostępne](../ide/code-snippets.md) dla różnych języków programowania, w tym C#, Visual Basic i C++. Dodajmy fragment kodu w języku C# `void Main` do naszego pliku.

1. Umieść kursor tuż nad zamykającym nawiasem klamrowym **}** w pliku i wpisz znaki `svm` . ( `svm` oznacza ; metoda `static void Main` [Main()](/dotnet/csharp/programming-guide/main-and-command-args/) jest punktem wejścia dla aplikacji języka C#).

   Zostanie wyświetlone okno podręczne z informacjami o `svm` fragmencie kodu.

   ![Funkcja IntelliSense dla fragmentu kodu w Visual Studio](media/tutorial-intellisense-snippet.png)

1. Naciśnij dwukrotnie klawisz **Tab,** aby wstawić fragment kodu.

   Zobaczysz, `static void Main()` że sygnatura metody jest dodawana do pliku.

Dostępne fragmenty kodu różnią się w zależności od języka programowania. Możesz przyjrzeć się dostępnym fragmentom kodu dla swojego języka, wybierając pozycję **Edytuj** wstaw fragment kodu  >  **funkcji IntelliSense,** a następnie wybierając  >  folder języka. W przypadku języka C# lista wygląda następująco:

![Lista fragmentów kodu w języku C#](media/tutorial-code-snippet-list.png)

Lista zawiera fragmenty kodu służące do tworzenia [klasy](/dotnet/csharp/programming-guide/classes-and-structs/classes), [konstruktora](/dotnet/csharp/programming-guide/classes-and-structs/constructors), [pętli for,](/dotnet/csharp/language-reference/keywords/for) [instrukcji if](/dotnet/csharp/language-reference/keywords/if-else) lub [switch](/dotnet/csharp/language-reference/keywords/switch) i nie tylko.

## <a name="comment-out-code"></a>Kod komentarza

Pasek narzędzi, który jest wierszem przycisków pod paskiem menu w Visual Studio, może pomóc w produktywności podczas kodzie. Można na przykład przełączać tryb uzupełniania IntelliSense[(IntelliSense](../ide/using-intellisense.md) to pomoc w kodowaniu, która wyświetla między innymi listę pasujących metod), zwiększać lub zmniejszać wcięcie wiersza lub oznaczać jako komentarz kod, którego nie chcesz kompilować. W tej sekcji podamy komentarz do kodu.

![Pasek narzędzi edytora](media/tutorial-editor-toolbar.png)

1. Wklej następujący kod do treści `Main()` metody.

    ```csharp
    // _words is a string array that we'll sort alphabetically
    string[] _words = {
        "the",
        "quick",
        "brown",
        "fox",
        "jumps"
    };

    string[] morewords = {
        "over",
        "the",
        "lazy",
        "dog"
    };

    IEnumerable<string> query = from word in _words
                                orderby word.Length
                                select word;
    ```

1. Nie używamy zmiennej , ale możemy jej użyć później, więc nie chcemy jej `morewords` całkowicie usuwać. Zamiast tego zajmijmy się komentarzami w tych wierszach. Wybierz całą definicję do zamykającego średnika, a następnie wybierz przycisk Oznacz jako komentarz wybrane `morewords` **wiersze** na pasku narzędzi. Jeśli wolisz używać klawiatury, naciśnij **klawisze Ctrl** + **K,** **Ctrl** + **C**.

   ![Przycisk Wyekseksuj komentarz](media/tutorial-comment-out.png)

   Znaki komentarza w języku C# są dodawane na początku każdego wybranego wiersza w celu `//` komentarza kodu.

## <a name="collapse-code-blocks"></a>Zwijanie bloków kodu

Nie chcemy widzieć pustego [](/dotnet/csharp/programming-guide/classes-and-structs/constructors) konstruktora dla tego, który został wygenerowany, więc aby usunąć ten widok `Class1` kodu, zwińmy go. Wybierz małe szare pole ze znakiem minus na marginesie pierwszego wiersza konstruktora. Lub, jeśli jesteś użytkownikiem klawiatury, umieść kursor w dowolnym miejscu w kodzie konstruktora i naciśnij **klawisze Ctrl** + **M,** **Ctrl** + **M**.

![Zwijanie przycisku zwijania](media/tutorial-collapse.png)

Blok kodu zwija się tylko do pierwszego wiersza, po którym następuje wielokropek ( `...` ). Aby ponownie rozwinąć blok kodu, kliknij to samo szare pole, w których znajduje się znak plus, lub naciśnij ponownie **klawisze Ctrl** + **M** i **Ctrl** + **M.** Ta funkcja jest [nazywana zwijania](../ide/outlining.md) i jest szczególnie przydatna w przypadku zwijania długich metod lub całych klas.

## <a name="view-symbol-definitions"></a>Wyświetlanie definicji symboli

Edytor Visual Studio ułatwia sprawdzanie definicji typu, metody itp. Jednym ze sposobów jest przejście do pliku zawierającego definicję, na przykład przez wybranie opcji **Przejdź** do definicji w dowolnym miejscu, do których odwołuje się symbol. Jeszcze szybszym sposobem, aby nie przenosić fokusu od pliku, w który pracujesz, jest użycie funkcji [Podgląd definicji](../ide/go-to-and-peek-definition.md#peek-definition). Przyjrzyjmy się definicji `string` typu.

1. Kliknij prawym przyciskiem myszy dowolne wystąpienie elementu i `string` wybierz polecenie **Peek Definition (Podgląd definicji)** z menu zawartości. Możesz też nacisnąć **klawisz Alt** + **F12.**

   Zostanie wyświetlone okno podręczne z definicją `String` klasy . Możesz przewijać w oknie podręcznym, a nawet podeglądać definicję innego typu ze podekiem kodu.

   ![Okno Podgląd definicji](media/tutorial-peek-definition.png)

1. Zamknij okno z podglądem definicji, wybierając małe pole z przyciskiem "x" w prawym górnym rogu okna podręcznego.

## <a name="use-intellisense-to-complete-words"></a>Używanie funkcji IntelliSense do dopełniania wyrazów

[IntelliSense](../ide/using-intellisense.md) to nieoceny zasób podczas kodowania. Może ona wyświetlać informacje o dostępnych członkach typu lub szczegóły parametrów dla różnych przeciążeń metody. Możesz również użyć funkcji IntelliSense, aby zakończyć wyraz po wpisaniu wystarczającej ilości znaków, aby go ujmować. Dodajmy wiersz kodu, aby wydrukować uporządkowane ciągi w oknie konsoli, które jest standardowym miejscem dla danych wyjściowych programu.

1. Poniżej `query` zmiennej zacznij wpisywać następujący kod:

   ```csharp
   foreach (string str in qu
   ```

   Funkcja IntelliSense wyświetla **szybkie informacje o** `query` symbolu.

   ![Uzupełnianie wyrazów funkcji IntelliSense w Visual Studio](media/tutorial-intellisense-completion-list.png)

1. Aby wstawić resztę wyrazu przy użyciu funkcji uzupełniania wyrazów `query` funkcji IntelliSense, naciśnij **klawisz Tab**.

1. Zakończ blok kodu, aby wyglądał jak poniższy kod. Możesz nawet ponownie ćwiczyć korzystanie z fragmentów kodu, wprowadzając, a następnie naciskając dwukrotnie klawisz `cw` **Tab,** aby wygenerować `Console.WriteLine` kod.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactor-a-name"></a>Refaktoryzacja nazwy

Nikt nie otrzymuje kodu po raz pierwszy, a jedną z rzeczy, które trzeba zmienić, jest nazwa zmiennej lub metody. Wypróbujmy funkcję refaktoryzacji [Visual Studio,](../ide/refactoring-in-visual-studio.md) aby zmienić nazwę `_words` zmiennej na `words` .

1. Umieść kursor na definicji zmiennej i wybierz polecenie Zmień nazwę z menu kontekstowego lub kliknij prawym przyciskiem myszy albo naciśnij `_words` **klawisze Ctrl**  + **R,** **Ctrl** + **R**.

   W prawym **górnym** rogu edytora zostanie wyświetlone okno dialogowe Zmień nazwę.

1. Wprowadź żądane słowa **nazwy**. Zwróć uwagę, że nazwa odwołania do w `words` zapytaniu również jest automatycznie zmieniana. Przed naciśnięciem **klawisza Enter** zaznacz pole wyboru **Uwzględnij komentarze** w **oknie** podręcznym Zmień nazwę.

   ![Zmień nazwę — Okno dialogowe](media/tutorial-rename.png)

1.  Naciśnij klawisz **Enter**.

   Nazwy obu wystąpień zostały zmienione, a także odwołanie do w `words` `words` komentarzu do kodu.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Dowiedz się więcej o projektach i rozwiązaniach](../get-started/tutorial-projects-solutions.md)

## <a name="see-also"></a>Zobacz też

- [Fragmenty kodu](../ide/code-snippets.md)
- [Nawigowanie po kodzie](../ide/navigating-code.md)
- [Tworzenie konspektu](../ide/outlining.md)
- [Przejdź do definicji i Zobacz definicję](../ide/go-to-and-peek-definition.md)
- [Refaktoryzacja](../ide/refactoring-in-visual-studio.md)
- [Korzystanie z funkcji IntelliSense](../ide/using-intellisense.md)
