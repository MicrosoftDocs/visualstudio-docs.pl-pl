---
title: Wprowadzenie do edytowania dla C# deweloperów
description: W tym 10-minutowym wprowadzeniu do edytora kodu w programie Visual Studio przedstawiono niektóre sposoby łatwiejszego zapisywania, nawigowania i poznania C# kodu przez program Visual Studio.
ms.custom: seodec18, get-started
ms.date: 11/20/2018
ms.technology: vs-ide-general
ms.topic: tutorial
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5bbca5e46ee83764a6a431ae13829a882b1d859f
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/05/2019
ms.locfileid: "71975162"
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

W C#tym artykule założono, że znasz już program. Jeśli nie, zalecamy zapoznaj się z samouczkiem, takim jak [wprowadzenie do C# i ASP.NET Core w programie Visual Studio](tutorial-aspnet-core.md) .

> [!TIP]
> Aby wykonać kroki opisane w tym artykule, upewnij się, że C# masz wybrane ustawienia dla programu Visual Studio. Aby uzyskać informacje o wybieraniu ustawień dla zintegrowanego środowiska programistycznego (IDE), zobacz [Wybieranie ustawień środowiska](visual-studio-ide.md#select-environment-settings).

## <a name="create-a-new-code-file"></a>Utwórz nowy plik kodu

Rozpocznij, tworząc nowy plik i dodawanie kodu do niego.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio. Naciśnij klawisz **ESC** lub kliknij pozycję **Kontynuuj bez kodu** w oknie uruchamiania, aby otworzyć środowisko programistyczne.

::: moniker-end

2. Z menu **plik** na pasku menu wybierz **Nowy** **plik** >  lub naciśnij **klawisze CTRL**+**N**.

3. W **nowy plik** okno dialogowe, w obszarze **ogólne** kategorii, wybierz **klasy Visual C#** , a następnie wybierz **Otwórz**.

   Nowy plik zostanie otwarty w edytorze za pomocą szkielet klasy C#. (Zwróć uwagę, że firma Microsoft nie ma konieczności tworzenia pełnej projekt programu Visual Studio na uzyskanie niektórych korzyści, że Edytor kodu oferuje; wszystko co potrzebne jest pliku z kodem)!

   ![Plik kodu C# w programie Visual Studio](../media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Używanie fragmentów kodu

Program Visual Studio oferuje przydatne *fragmenty kodu* , umożliwia szybkie i łatwe generowanie najczęściej używane bloki kodu. [Fragmenty kodu](../../ide/code-snippets.md) są dostępne dla różnych języków programowania, w tym C#, Visual Basic i C++. Dodajmy języka C# `void Main` fragment kodu do naszego pliku.

1. Umieść kursor nad końcowego zamykającego nawiasu klamrowego **}** w pliku i wpisz znaki `svm` (który oznacza `static void Main` &mdash;nie martw się zbyt dużo Jeśli nie masz pewności co oznacza to, że).

   Wyskakujące okno dialogowe pojawia się z informacjami o `svm` fragmentu kodu.

   ![Funkcja IntelliSense dla fragmentu kodu w programie Visual Studio](../media/tutorial-intellisense-snippet.png)

1. Naciśnij klawisz **kartę** dwa razy, aby wstawić fragment kodu.

   Zostanie wyświetlony `static void Main()` podpis metody poproś o dodanie Cię do pliku. [Main()](/dotnet/csharp/programming-guide/main-and-command-args/) metodą jest punkt wejścia dla aplikacji w języku C#.

Fragmenty kodu dostępne różnią się w różnych językach programowania. Aby sprawdzić dostępne fragmenty kodu dla danego języka, wybierz opcję **edytuj** > **IntelliSense** > **Wstaw wstawka** lub naciśnij **klawisze Ctrl**+**K**, **Ctrl**+**X**, a następnie wybierz folder Twojego języka. Dla języka C# listy wygląda następująco:

![Lista fragment kodu języka C#](../media/tutorial-code-snippet-list.png)

Lista zawiera fragmenty kodu do tworzenia [klasy](/dotnet/csharp/programming-guide/classes-and-structs/classes), [Konstruktor](/dotnet/csharp/programming-guide/classes-and-structs/constructors), [dla](/dotnet/csharp/language-reference/keywords/for) pętli, [Jeśli](/dotnet/csharp/language-reference/keywords/if-else) lub [Przełącz](/dotnet/csharp/language-reference/keywords/switch)instrukcji i nie tylko.

## <a name="comment-out-code"></a>Komentarz do kodu

Pasek narzędzi, który jest wiersz przycisków poniżej paska menu w programie Visual Studio, może pomóc zwiększyć produktywność kodowania. Na przykład, można przełączać tryb uzupełniania IntelliSense ([IntelliSense](../../ide/using-intellisense.md) jest pomoc kodowania, który zawiera listę metod, między innymi dopasowania), zwiększ lub Zmniejsz wcięcie wiersza lub kod, który chcesz przekształcić w komentarz skompilować. W tej sekcji firma Microsoft będzie komentarz kodu.

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

1. Nie używamy `morewords` zmienną, ale firma Microsoft może używać go później tak nie chcemy całkowicie usunąć go. Zamiast tego Załóżmy komentarz te wiersze. Zaznacz całą definicję `morewords` do zamknięcia średnikami, a następnie wybierz **komentarz zaznaczonych wierszach** przycisk na pasku narzędzi. Jeśli wolisz użyć klawiatury, naciśnij klawisz **Ctrl**+**K**, **Ctrl**+**C**.

   ![Komentarz przycisku](../media/tutorial-comment-out.png)

   Znaki komentarza C# `//` są dodawane na początku każdego wybranego wiersza, aby przekształcić w komentarz kod.

## <a name="collapse-code-blocks"></a>Zwiń bloki kodu

Nie chcemy wyświetlić pusty [Konstruktor](/dotnet/csharp/programming-guide/classes-and-structs/constructors) dla `Class1` wygenerowany, więc aby uniknąć przeładowania naszych widok kodu, możemy go zwinąć. Wybierz małe pole szarego znakiem minus znajdującym się w nim na marginesie pierwszy wiersz konstruktora. Lub, jeśli jesteś użytkownikiem klawiatury, umieść kursor gdziekolwiek w Konstruktorze kod i naciśnij klawisz **Ctrl**+**M**, **Ctrl**+**M** .

![Przycisk Zwiń konspekt](../media/tutorial-collapse.png)

Blok kodu jest ustawiana na tylko pierwszy wiersz, następuje wielokropek (`...`). Aby rozwinąć blok kodu ponownie, kliknij pole szarego tego samego, który ma teraz znakiem plus lub naciśnij klawisz **Ctrl**+**M**, **Ctrl**+**M**  ponownie. Ta funkcja jest nazywana [konspekt](../../ide/outlining.md) i jest szczególnie przydatne, gdy one zwijanie długie metod lub klas całego.

## <a name="view-symbol-definitions"></a>Wyświetlanie definicji symbolu

Edytor programu Visual Studio można łatwo sprawdzić definicji typu, metody itd. Jednym ze sposobów jest przejście do pliku, który zawiera definicję, na przykład przez wybranie **Przejdź do definicji** lub naciśnięcie klawisza **F12** wszędzie tam, gdzie jest przywoływany symbol. Jeszcze szybszy sposób, który nie zmienia się od pliku pracujesz w jest użycie [Peek Definition](../../ide/go-to-and-peek-definition.md#peek-definition). Umożliwia wgląd w definicji `string` typu.

1. Kliknij prawym przyciskiem myszy na dowolne wystąpienie `string` i wybierz polecenie **Peek Definition** menu zawartości. Lub naciśnij **Alt**+**F12**.

   Okno wyskakujące pojawia się przy użyciu definicji elementu `String` klasy. Można przewijać w oknie podręcznym lub nawet rzut oka na definicję innego typu niż peeked kodu.

   ![Okna definicji wglądu](../media/tutorial-peek-definition.png)

1. Zamknij okno definicji podejrzeć, wybierając pole małych znakiem "x" w prawym górnym rogu okna podręcznego.

## <a name="use-intellisense-to-complete-words"></a>Funkcja IntelliSense są używane do realizowania słów

[Funkcja IntelliSense](../../ide/using-intellisense.md) jest zasobem nieocenione, gdy masz kodowania. Jego można wyświetlić informacje o dostępne elementy członkowskie typu lub szczegóły parametrów dla innego przeciążenia metody. Funkcja IntelliSense umożliwia również Dokończ wyraz, po wpisaniu małej liczby znaków, aby odróżnić go. Dodajmy wiersza kodu, aby wydrukować zamówione ciągi w oknie konsoli, czyli miejsce standardowe dane wyjściowe programu do go.

1. Poniżej `query` zmiennej, wpisz następujący kod:

   ```csharp
   foreach (string str in qu
   ```

   Zobacz IntelliSense dowiesz się, **Quick Info** o `query` symboli.

   ![Uzupełnianie wyrazów w technologii IntelliSense w programie Visual Studio](../media/tutorial-intellisense-completion-list.png)

1. Aby wstawić pozostałe słowa `query` za pomocą funkcji uzupełniania programu word w technologii IntelliSense, naciśnij klawisz **kartę**.

1. Zakończ poza blok kodu, aby wyglądała jak poniższy kod. Można nawet rozwiązaniem, ponownie użyć wstawki kodu programu, wprowadzając `cw` , a następnie naciskając klawisze **kartę** dwa razy, aby wygenerować `Console.WriteLine` kodu.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactor-a-name"></a>Refaktoryzuj nazwę

Nikt nie pobiera kod bezpośrednio po raz pierwszy, a jedną z rzeczy, które trzeba zmienić to nazwa zmiennej lub metody. Spróbujmy programu Visual Studio [zrefaktoryzuj](../../ide/refactoring-in-visual-studio.md) funkcji, aby zmienić nazwę `_words` zmienną `words`.

1. Umieść kursor nad definicji `_words` zmienną i wybierz polecenie **Zmień nazwę** z kliknij prawym przyciskiem myszy lub menu kontekstowego lub naciśnij **Ctrl**+**R**, **Ctrl**+**R**.

   Okno podręczne **Zmień nazwę** okno dialogowe pojawia się u góry bezpośrednio z edytora.

1. Wprowadź żądaną nazwę **wyrazy**. Należy zauważyć, że odwołanie do `words` również automatycznie została zmieniona w zapytaniu. Przed naciśnięciem **Enter**, wybierz opcję **dodawać komentarze** pola wyboru w **Zmień nazwę** okno podręczne.

   ![Zmień nazwę — Okno dialogowe](../media/tutorial-rename.png)

1. Naciśnij klawisz **wprowadź**.

   Oba wystąpienia `words` została zmieniona, a także odwołania do `words` w komentarzu do kodu.

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
