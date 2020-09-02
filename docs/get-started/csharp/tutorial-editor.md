---
title: Wprowadzenie do edytowania dla deweloperów języka C#
description: W tym 10-minutowym wprowadzeniu do edytora kodu w programie Visual Studio przedstawiono niektóre sposoby łatwiejszego zapisywania, nawigowania i interpretowania kodu w języku C#.
ms.custom: seodec18, get-started
ms.date: 11/20/2018
ms.technology: vs-ide-general
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8122f42fb5d2ec4c31ec553407b644e59e9f4418
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88248286"
---
# <a name="learn-to-use-the-code-editor-with-c"></a>Dowiedz się, jak używać edytora kodu języka C\#

W tym 10-minutowym wprowadzeniu do edytora kodu w programie Visual Studio dodamy kod do pliku, aby zapoznać się z innymi sposobami, w których program Visual Studio ułatwia pisanie, nawigowanie i zrozumienie kodu w języku C#.

::: moniker range="vs-2017"

> [!TIP]
> Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.

::: moniker-end

W tym artykule założono, że znasz już język C#. Jeśli nie, zalecamy zapoznaj się z samouczkiem, takim jak [wprowadzenie do języka C# i ASP.NET Core w programie Visual Studio](tutorial-aspnet-core.md) .

> [!TIP]
> Aby wykonać kroki opisane w tym artykule, upewnij się, że masz wybrane ustawienia języka C# dla programu Visual Studio. Aby uzyskać informacje o wybieraniu ustawień dla zintegrowanego środowiska programistycznego (IDE), zobacz [Wybieranie ustawień środowiska](visual-studio-ide.md#select-environment-settings).

## <a name="create-a-new-code-file"></a>Utwórz nowy plik kodu

Zacznij od utworzenia nowego pliku i dodania do niego kodu.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio. Naciśnij klawisz **ESC** lub kliknij pozycję **Kontynuuj bez kodu** w oknie uruchamiania, aby otworzyć środowisko programistyczne.

::: moniker-end

2. Z menu **plik** na pasku menu wybierz polecenie **Nowy**  >  **plik**lub naciśnij **klawisze CTRL** + **N**.

3. W oknie dialogowym **nowy plik** w obszarze Kategoria **Ogólne** wybierz pozycję **Klasa Visual C#**, a następnie wybierz polecenie **Otwórz**.

   Nowy plik zostanie otwarty w edytorze z szkieletem klasy C#. (Zwróć uwagę, że nie musimy tworzyć pełnego projektu programu Visual Studio, aby uzyskać pewne korzyści, które oferuje Edytor kodu; wszystko, co jest potrzebne, jest plikiem kodu!)

   ![Plik kodu C# w programie Visual Studio](../media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Używanie fragmentów kodu

Program Visual Studio oferuje przydatne *fragmenty kodu* , za pomocą których można szybko i łatwo generować często używane bloki kodu. [Fragmenty kodu](../../ide/code-snippets.md) są dostępne dla różnych języków programowania, w tym C#, Visual Basic i C++. Dodajmy `void Main` fragment kodu C# do naszego pliku.

1. Umieść kursor tuż nad ostatnim zamykającym nawiasem klamrowym ( **) w pliku** , a następnie wpisz znaki `svm` (co `static void Main` &mdash; oznacza, że nie jest to zbyt duże, jeśli nie wiesz, co to znaczy).

   Zostanie wyświetlone okno dialogowe z informacjami o `svm` fragmencie kodu.

   ![Funkcja IntelliSense dla fragmentu kodu w programie Visual Studio](../media/tutorial-intellisense-snippet.png)

1. Naciśnij dwukrotnie klawisz **Tab** , aby wstawić fragment kodu.

   Zostanie wyświetlony `static void Main()` podpis metody dodany do pliku. Metoda [Main ()](/dotnet/csharp/programming-guide/main-and-command-args/) jest punktem wejścia dla aplikacji języka C#.

Dostępne fragmenty kodu są różne dla różnych języków programowania. Możesz obejrzeć dostępne fragmenty kodu dla danego języka, wybierając opcję **Edytuj**  >  **IntelliSense**  >  **wstawkę** IntelliSense lub naciskając **klawisze CTRL** + **K**, **Ctrl** + **X**, a następnie wybierając folder języka. Dla języka C# lista wygląda następująco:

![Lista fragmentów kodu w języku C#](../media/tutorial-code-snippet-list.png)

Lista zawiera fragmenty kodu służące do tworzenia [klas](/dotnet/csharp/programming-guide/classes-and-structs/classes), [Konstruktor](/dotnet/csharp/programming-guide/classes-and-structs/constructors), pętla [for](/dotnet/csharp/language-reference/keywords/for) , instrukcja [if](/dotnet/csharp/language-reference/keywords/if-else) lub [Switch](/dotnet/csharp/language-reference/keywords/switch) itd.

## <a name="comment-out-code"></a>Dodawanie komentarza do kodu

Pasek narzędzi, który jest wierszem przycisków na pasku menu w programie Visual Studio, może pomóc zwiększyć produktywność podczas pisania kodu. Można na przykład przełączyć tryb uzupełniania IntelliSense ([IntelliSense](../../ide/using-intellisense.md) to pomoc dla kodu, która wyświetla listę zgodnych metod, między innymi), zwiększyć lub zmniejszyć wcięcie linii albo dodać komentarz do kodu, który nie ma być kompilowany. W tej sekcji dodamy komentarz dotyczący kodu.

![Pasek narzędzi edytora](../media/tutorial-editor-toolbar.png)

1. Wklej następujący kod do `Main()` treści metody.

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

1. Nie używamy `morewords` zmiennej, ale możemy jej użyć później, więc nie chcemy jej całkowicie usunąć. Zamiast tego Dodaj komentarz do tych wierszy. Zaznacz całą definicję `morewords` do zamykającego średnika, a następnie wybierz przycisk Dodaj komentarz do **wybranych linii** na pasku narzędzi. Jeśli wolisz korzystać z klawiatury, naciśnij **klawisze CTRL** + **K**, **Ctrl +** + **C**.

   ![Przycisk komentowania](../media/tutorial-comment-out.png)

   Znaki komentarza w języku C# `//` są dodawane na początku każdego zaznaczonego wiersza w celu dodania komentarza do kodu.

## <a name="collapse-code-blocks"></a>Zwijanie bloków kodu

Nie chcemy zobaczyć pustego [konstruktora](/dotnet/csharp/programming-guide/classes-and-structs/constructors) dla, `Class1` który został wygenerowany, więc aby nie zaśmiecać naszego widoku kodu, przejdźmy do niego. Wybierz Małe szare pole ze znakiem minus wewnątrz niego na marginesie pierwszego wiersza konstruktora. Jeśli jesteś użytkownikiem klawiatury, umieść kursor w dowolnym miejscu w kodzie konstruktora i naciśnij klawisze **Ctrl** + **m**, **Ctrl** + **m**.

![Przycisk zwijania konspektu](../media/tutorial-collapse.png)

Blok kodu jest zwijany tylko do pierwszego wiersza, a po nim wielokropek ( `...` ). Aby ponownie rozwinąć blok kodu, kliknij szare pole, które ma teraz znak plus, lub naciśnij klawisze **Ctrl** + **m**, **Ctrl** + **m** ponownie. Ta funkcja jest nazywana [tworzeniem konspektu](../../ide/outlining.md) i jest szczególnie przydatna w przypadku zwijania długich metod lub całych klas.

## <a name="view-symbol-definitions"></a>Wyświetl definicje symboli

Edytor programu Visual Studio ułatwia sprawdzanie definicji typu, metody itp. Jednym ze sposobów jest przejście do pliku, który zawiera definicję, na przykład przez wybranie **Przejdź do definicji** lub naciśnięcie klawisza **F12** wszędzie tam, gdzie jest przywoływany symbol. Jeszcze szybszym sposobem, aby nie przenieść fokusu z pliku, w którym pracujesz, jest użycie [definicji wglądu](../../ide/go-to-and-peek-definition.md#peek-definition). Przejdźmy do definicji `string` typu.

1. Kliknij prawym przyciskiem myszy dowolne wystąpienie `string` i wybierz z menu zawartość polecenie **wgląd do definicji** . Lub naciśnij klawisze **Alt** + **F12**.

   Zostanie wyświetlone okno podręczne z definicją `String` klasy. Można przewijać w oknie podręcznym, a nawet z dokładnością do definicji innego typu.

   ![Okno definicji wglądu](../media/tutorial-peek-definition.png)

1. Zamknij okno Definicja wglądu, wybierając małe pole z symbolem "x" w prawym górnym rogu okna podręcznego.

## <a name="use-intellisense-to-complete-words"></a>Korzystanie z funkcji IntelliSense do uzupełniania wyrazów

[Technologia IntelliSense](../../ide/using-intellisense.md) jest niecennym zasobem podczas kodowania. Można wyświetlić informacje o dostępnych elementach członkowskich typu lub szczegółach parametrów dla różnych przeciążeń metody. Możesz również użyć funkcji IntelliSense, aby zakończyć wyraz po wpisaniu wystarczającej liczby znaków, aby odróżnić go. Dodajmy wiersz kodu, aby drukować uporządkowane ciągi do okna konsoli, który jest standardowym miejscem dla danych wyjściowych z programu.

1. Poniżej `query` zmiennej zacznij pisać następujący kod:

   ```csharp
   foreach (string str in qu
   ```

   Zobaczysz, że IntelliSense wyświetla **szybkie informacje** o `query` symbolu.

   ![Uzupełnianie wyrazów IntelliSense w programie Visual Studio](../media/tutorial-intellisense-completion-list.png)

1. Aby wstawić resztę słowa przy `query` użyciu funkcji uzupełniania słów IntelliSense, naciśnij klawisz **Tab**.

1. Zakończ pracę z blokiem kodu, aby wyglądać podobnie do poniższego kodu. Możesz nawet użyć ponownie wstawek kodu, wprowadzając `cw` i naciskając dwukrotnie klawisz **Tab** , aby wygenerować `Console.WriteLine` kod.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactor-a-name"></a>Refaktoryzacja nazwy

Nikt nie pobiera kodu po raz pierwszy, a jedna z rzeczy, które trzeba zmienić, jest nazwą zmiennej lub metody. Wypróbujmy funkcję [refaktoryzacji](../../ide/refactoring-in-visual-studio.md) programu Visual Studio, aby zmienić nazwę `_words` zmiennej na `words` .

1. Umieść kursor nad definicją `_words` zmiennej, a następnie wybierz polecenie **Zmień nazwę** w menu kontekstowym lub prawym przyciskiem myszy lub naciśnij **klawisze CTRL** + **r**, **Ctrl** + **r**.

   Okno dialogowe **zmiana nazwy** zostanie wyświetlone w prawym górnym rogu edytora.

1. Wprowadź odpowiednie nazwy **wyrazów**. Należy zauważyć, że Nazwa odwołania do `words` zapytania jest również automatycznie zmieniana. Przed naciśnięciem klawisza **Enter**zaznacz pole wyboru **Dołącz Komentarze** w oknie podręcznym **zmiany nazwy** .

   ![Zmień nazwę — Okno dialogowe](../media/tutorial-rename.png)

1.  Naciśnij klawisz **Enter**.

   Zmieniono nazwę obu wystąpień `words` , a także odwołanie do `words` w komentarzu do kodu.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Informacje o projektach i rozwiązaniach](../tutorial-projects-solutions.md)

## <a name="see-also"></a>Zobacz też

- [Fragmenty kodu](../../ide/code-snippets.md)
- [Nawiguj po kodzie](../../ide/navigating-code.md)
- [Tworzenie konspektu](../../ide/outlining.md)
- [Przejdź do definicji i Zobacz definicję](../../ide/go-to-and-peek-definition.md)
- [Refaktoryzacja](../../ide/refactoring-in-visual-studio.md)
- [Korzystanie z funkcji IntelliSense](../../ide/using-intellisense.md)
