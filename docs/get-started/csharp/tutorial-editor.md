---
title: Wprowadzenie do edytowania dla C# deweloperów
description: W tym 10-minutowym wprowadzeniu do edytora kodu w programie Visual Studio przedstawiono niektóre sposoby łatwiejszego zapisywania, nawigowania i poznania C# kodu przez program Visual Studio.
ms.custom: seodec18, get-started
ms.date: 11/20/2018
ms.technology: vs-ide-general
ms.topic: tutorial
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 1b5fb79430b081986764f0ee1789f68471667498
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189080"
---
# <a name="learn-to-use-the-code-editor"></a>Dowiedz się, jak używać edytora kodu

W tym 10-minutowym wprowadzeniu do edytora kodu w programie Visual Studio dodamy kod do pliku, aby zapoznać się z innymi sposobami, w których program Visual Studio ułatwia pisanie, nawigowanie i zrozumienie kodu.

::: moniker range="vs-2017"

> [!TIP]
> Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.

::: moniker-end

W C#tym artykule założono, że znasz już program. Jeśli nie, zalecamy zapoznaj się z samouczkiem, takim jak [wprowadzenie do C# i ASP.NET Core w programie Visual Studio](tutorial-aspnet-core.md) .

> [!TIP]
> Aby wykonać kroki opisane w tym artykule, upewnij się, że C# masz wybrane ustawienia dla programu Visual Studio. Aby uzyskać informacje o wybieraniu ustawień dla zintegrowanego środowiska programistycznego (IDE), zobacz [Wybieranie ustawień środowiska](visual-studio-ide.md#select-environment-settings).

## <a name="create-a-new-code-file"></a>Utwórz nowy plik kodu

Zacznij od utworzenia nowego pliku i dodania do niego kodu.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio. Naciśnij klawisz **ESC** lub kliknij pozycję **Kontynuuj bez kodu** w oknie uruchamiania, aby otworzyć środowisko programistyczne.

::: moniker-end

2. Z menu **plik** na pasku menu wybierz polecenie **Nowy** **plik** >  lub naciśnij **klawisze CTRL** +**N**.

3. W oknie dialogowym **nowy plik** w obszarze Kategoria **Ogólne** wybierz pozycję **Klasa wizualizacji C#** , a następnie wybierz polecenie **Otwórz**.

   Nowy plik zostanie otwarty w edytorze z szkieletem C# klasy. (Zwróć uwagę, że nie musimy tworzyć pełnego projektu programu Visual Studio, aby uzyskać pewne korzyści, które oferuje Edytor kodu; wszystko, co jest potrzebne, jest plikiem kodu!)

   ![C#plik kodu w programie Visual Studio](../media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Używanie fragmentów kodu

Program Visual Studio oferuje przydatne *fragmenty kodu* , za pomocą których można szybko i łatwo generować często używane bloki kodu. [Fragmenty kodu](../../ide/code-snippets.md) są dostępne dla różnych języków programowania, takich C#jak, Visual Basic i C++. Dodajmy fragment C# `void Main` do pliku.

1. Umieść kursor tuż nad ostatnim zamykającym nawiasem klamrowym () w pliku i wpisz znaki `svm` (co oznacza, że `static void Main` &mdash;don nie **martw się,** Jeśli nie wiesz, co to znaczy).

   Zostanie wyświetlone okno dialogowe z informacjami o `svm` fragmencie kodu.

   ![Funkcja IntelliSense dla fragmentu kodu w programie Visual Studio](../media/tutorial-intellisense-snippet.png)

1. Naciśnij dwukrotnie klawisz **Tab** , aby wstawić fragment kodu.

   Zostanie wyświetlony podpis metody `static void Main()` dodany do pliku. Metoda [Main ()](/dotnet/csharp/programming-guide/main-and-command-args/) jest punktem wejścia dla C# aplikacji.

Dostępne fragmenty kodu są różne dla różnych języków programowania. Aby sprawdzić dostępne fragmenty kodu dla danego języka, wybierz opcję **edytuj**  > **IntelliSense**  > **Wstaw** wstawka lub naciśnij **kombinację klawiszy CTRL** +**K**, **Ctrl** +**X**, a następnie wybierz pozycję folder Twojego języka. W C#przypadku, lista wygląda następująco:

![C#Lista fragmentów kodu](../media/tutorial-code-snippet-list.png)

Lista zawiera fragmenty kodu służące do tworzenia [klas](/dotnet/csharp/programming-guide/classes-and-structs/classes), [Konstruktor](/dotnet/csharp/programming-guide/classes-and-structs/constructors), pętla [for](/dotnet/csharp/language-reference/keywords/for) , instrukcja [if](/dotnet/csharp/language-reference/keywords/if-else) lub [Switch](/dotnet/csharp/language-reference/keywords/switch) itd.

## <a name="comment-out-code"></a>Dodawanie komentarza do kodu

Pasek narzędzi, który jest wierszem przycisków na pasku menu w programie Visual Studio, może pomóc zwiększyć produktywność podczas pisania kodu. Można na przykład przełączyć tryb uzupełniania IntelliSense ([IntelliSense](../../ide/using-intellisense.md) to pomoc dla kodu, która wyświetla listę zgodnych metod, między innymi), zwiększyć lub zmniejszyć wcięcie linii albo dodać komentarz do kodu, który nie ma być kompilowany. W tej sekcji dodamy komentarz dotyczący kodu.

![Pasek narzędzi edytora](../media/tutorial-editor-toolbar.png)

1. Wklej następujący kod do treści metody `Main()`.

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

1. Nie używamy zmiennej `morewords`, ale możemy jej użyć później, więc nie chcemy jej całkowicie usunąć. Zamiast tego Dodaj komentarz do tych wierszy. Zaznacz całą definicję `morewords` do zamykającego średnika, a następnie wybierz przycisk Dodaj **komentarz do wybranych linii** na pasku narzędzi. Jeśli wolisz korzystać z klawiatury, naciśnij klawisz **ctrl** +**K**, **Ctrl** +**C**.

   ![Przycisk komentowania](../media/tutorial-comment-out.png)

   Znaki C# komentarza `//` są dodawane na początku każdego wybranego wiersza w celu dodania komentarza do kodu.

## <a name="collapse-code-blocks"></a>Zwijanie bloków kodu

Nie chcemy zobaczyć pustego [konstruktora](/dotnet/csharp/programming-guide/classes-and-structs/constructors) dla `Class1`, który został wygenerowany, więc aby nie zasłaniać naszego widoku kodu, przyjrzyjmy go. Wybierz Małe szare pole ze znakiem minus wewnątrz niego na marginesie pierwszego wiersza konstruktora. Jeśli jesteś użytkownikiem klawiatury, umieść kursor w dowolnym miejscu w kodzie konstruktora i naciśnij **klawisze ctrl** +**m**, **Ctrl** +**m**.

![Przycisk zwijania konspektu](../media/tutorial-collapse.png)

Blok kodu jest zwijany tylko do pierwszego wiersza, a po nim wielokropek (`...`). Aby ponownie rozwinąć blok kodu, kliknij szare pole, w którym znajduje się znak plusa, lub naciśnij klawisze **ctrl** +**m**, **Ctrl** +**m** ponownie. Ta funkcja jest nazywana [tworzeniem konspektu](../../ide/outlining.md) i jest szczególnie przydatna w przypadku zwijania długich metod lub całych klas.

## <a name="view-symbol-definitions"></a>Wyświetl definicje symboli

Edytor programu Visual Studio ułatwia sprawdzanie definicji typu, metody itp. Jednym ze sposobów jest przejście do pliku, który zawiera definicję, na przykład przez wybranie **Przejdź do definicji** lub naciśnięcie klawisza **F12** wszędzie tam, gdzie jest przywoływany symbol. Jeszcze szybszym sposobem, aby nie przenieść fokusu z pliku, w którym pracujesz, jest użycie [definicji wglądu](../../ide/go-to-and-peek-definition.md#peek-definition). Przejdźmy do definicji typu `string`.

1. Kliknij prawym przyciskiem myszy dowolne wystąpienie `string` a następnie wybierz polecenie **wgląd do definicji** z menu zawartość. Lub naciśnij klawisz **Alt** +**F12**.

   Zostanie wyświetlone okno podręczne z definicją klasy `String`. Można przewijać w oknie podręcznym, a nawet z dokładnością do definicji innego typu.

   ![Okno definicji wglądu](../media/tutorial-peek-definition.png)

1. Zamknij okno Definicja wglądu, wybierając małe pole z symbolem "x" w prawym górnym rogu okna podręcznego.

## <a name="use-intellisense-to-complete-words"></a>Korzystanie z funkcji IntelliSense do uzupełniania wyrazów

[Technologia IntelliSense](../../ide/using-intellisense.md) jest niecennym zasobem podczas kodowania. Można wyświetlić informacje o dostępnych elementach członkowskich typu lub szczegółach parametrów dla różnych przeciążeń metody. Możesz również użyć funkcji IntelliSense, aby zakończyć wyraz po wpisaniu wystarczającej liczby znaków, aby odróżnić go. Dodajmy wiersz kodu, aby drukować uporządkowane ciągi do okna konsoli, który jest standardowym miejscem dla danych wyjściowych z programu.

1. Poniżej zmiennej `query` Zacznij wpisywać następujący kod:

   ```csharp
   foreach (string str in qu
   ```

   Zobaczysz, że IntelliSense wyświetla **szybkie informacje** o symbolu `query`.

   ![Uzupełnianie wyrazów IntelliSense w programie Visual Studio](../media/tutorial-intellisense-completion-list.png)

1. Aby wstawić resztę słowa `query` przy użyciu funkcji uzupełniania wyrazów IntelliSense, naciśnij klawisz **Tab**.

1. Zakończ pracę z blokiem kodu, aby wyglądać podobnie do poniższego kodu. Możesz nawet użyć ponownie wstawek kodu, wprowadzając `cw` a następnie naciskając dwukrotnie klawisz **Tab** w celu wygenerowania kodu `Console.WriteLine`.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactor-a-name"></a>Refaktoryzacja nazwy

Nikt nie pobiera kodu po raz pierwszy, a jedna z rzeczy, które trzeba zmienić, jest nazwą zmiennej lub metody. Wypróbujmy funkcję [refaktoryzacji](../../ide/refactoring-in-visual-studio.md) programu Visual Studio, aby zmienić nazwę zmiennej `_words` na `words`.

1. Umieść kursor nad definicją zmiennej `_words` i wybierz polecenie **Zmień nazwę** w menu kontekstowym lub kliknij prawym przyciskiem myszy lub naciśnij klawisze **Ctrl**+**R**, **Ctrl**+**R**.

   Okno dialogowe **zmiana nazwy** zostanie wyświetlone w prawym górnym rogu edytora.

1. Wprowadź odpowiednie nazwy **wyrazów**. Należy zauważyć, że Nazwa odwołania do `words` w zapytaniu jest również automatycznie zmieniana. Przed naciśnięciem klawisza **Enter**zaznacz pole wyboru **Dołącz Komentarze** w oknie podręcznym **zmiany nazwy** .

   ![Zmień nazwę — Okno dialogowe](../media/tutorial-rename.png)

1. Naciśnij klawisz **Enter**.

   Zmieniono nazwę obu wystąpień `words`, a także odwołanie do `words` w komentarzu do kodu.

## <a name="next-steps"></a>Następne kroki

> [!div class="nextstepaction"]
> [Informacje o projektach i rozwiązaniach](../tutorial-projects-solutions.md)

## <a name="see-also"></a>Zobacz także

- [Fragmenty kodu](../../ide/code-snippets.md)
- [Nawiguj po kodzie](../../ide/navigating-code.md)
- [Obramowanie](../../ide/outlining.md)
- [Polecenia Przejdź do definicji i Zobacz definicję](../../ide/go-to-and-peek-definition.md)
- [Refaktoryzacja](../../ide/refactoring-in-visual-studio.md)
- [Korzystanie z funkcji IntelliSense](../../ide/using-intellisense.md)
