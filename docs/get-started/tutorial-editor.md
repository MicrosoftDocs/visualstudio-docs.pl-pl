---
title: Wprowadzenie do edycji w edytorze kodu
ms.date: 11/30/2017
ms.technology: vs-ide-general
ms.custom: get-started
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: a0c8122bd08e4eb9af68a0aa70f06cfb18e51469
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "75595270"
---
# <a name="learn-to-use-the-code-editor"></a>Dowiedz się, jak korzystać z edytora kodu

W tym 10-minutowym wprowadzeniu do edytora kodu w programie Visual Studio dodamy kod do pliku, aby przyjrzeć się niektórym sposobom, w jakie program Visual Studio ułatwia pisanie, nawigowanie i rozumienie kodu.

::: moniker range="vs-2017"

> [!TIP]
> Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/downloads) aby zainstalować ją bezpłatnie.

::: moniker-end

W tym artykule założono, że znasz już język programowania. Jeśli nie, sugerujemy, aby najpierw przyjrzeć się jednemu z programów Szybki start, takiemu jak utworzenie aplikacji internetowej z [pythonem](../ide/quickstart-python.md) lub [c#,](../get-started/csharp/tutorial-aspnet-core.md)lub utworzyć aplikację konsoli za pomocą [języka Visual Basic](../ide/quickstart-visual-basic-console.md) lub [C++](/cpp/get-started/tutorial-console-cpp).

## <a name="create-a-new-code-file"></a>Tworzenie nowego pliku kodu

Zacznij od utworzenia nowego pliku i dodania do niego kodu.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio. Naciśnij **klawisz Esc** lub kliknij przycisk Kontynuuj bez **kodu** w oknie startowym, aby otworzyć środowisko programistyczne.

::: moniker-end

2. Z menu **Plik** na pasku menu wybierz polecenie **Nowy** > **plik**.

3. W oknie dialogowym **Nowy plik** w kategorii **Ogólne** wybierz pozycję Klasa języka **Visual C#,** a następnie wybierz pozycję **Otwórz**.

   Nowy plik otwiera się w edytorze ze szkieletem klasy C#. (Zauważ, że nie musimy tworzyć pełnego projektu programu Visual Studio, aby uzyskać niektóre korzyści, które oferuje edytor kodu; wszystko, czego potrzebujesz, to plik kodu!)

   ![Plik kodu języka C# w programie Visual Studio](media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Używanie fragmentów kodu

Visual Studio zawiera przydatne *fragmenty kodu,* których można użyć do szybkiego i łatwego generowania często używanych bloków kodu. [Fragmenty kodu](../ide/code-snippets.md) są dostępne dla różnych języków programowania, w tym C#, Visual Basic i C++. Dodajmy fragment kodu `void Main` języka C# do naszego pliku.

1. Umieść kursor tuż nad ostatecznym nawiasem klamrowym **}** w `svm`pliku i wpisz znaki . (`svm` oznacza `static void Main`; [Main()](/dotnet/csharp/programming-guide/main-and-command-args/) metoda jest punktem wejścia dla aplikacji C#).

   Zostanie wyświetlone wyskakujące `svm` okno dialogowe z informacjami o urywek kodu.

   ![IntelliSense dla fragmentu kodu w programie Visual Studio](media/tutorial-intellisense-snippet.png)

1. Naciśnij dwukrotnie **klawisz Tab,** aby wstawić fragment kodu.

   Zostanie wyświetlony `static void Main()` podpis metody zostanie dodany do pliku.

Dostępne fragmenty kodu różnią się w zależności od języka programowania. Możesz sprawdzić dostępne fragmenty kodu dla swojego języka, wybierając **pozycję Edytuj** > **fragment kodu wstawiania****intellisense,** > a następnie wybierając folder języka. W przypadku języka C#lista wygląda następująco:

![Lista fragmentów kodu języka C#](media/tutorial-code-snippet-list.png)

Lista zawiera fragmenty do tworzenia [klasy,](/dotnet/csharp/programming-guide/classes-and-structs/classes) [konstruktora,](/dotnet/csharp/programming-guide/classes-and-structs/constructors) [for](/dotnet/csharp/language-reference/keywords/for) loop, [instrukcji if](/dotnet/csharp/language-reference/keywords/if-else) lub [switch](/dotnet/csharp/language-reference/keywords/switch) i innych.

## <a name="comment-out-code"></a>Skomentuj kod

Pasek narzędzi, który jest wiersz przycisków pod paskiem menu w programie Visual Studio, może pomóc zwiększyć produktywność podczas kodowania. Na przykład można przełączyć tryb ukończenia IntelliSense[(IntelliSense](../ide/using-intellisense.md) jest pomocą kodowania, która wyświetla listę pasujących metod, między innymi), zwiększyć lub zmniejszyć wcięcie wiersza lub skomentować kod, który nie ma być skompilowany. W tej sekcji pokomentujemy kod.

![Pasek narzędzi edytora](media/tutorial-editor-toolbar.png)

1. Wklej następujący kod `Main()` do treści metody.

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

1. Nie używamy zmiennej, `morewords` ale możemy jej użyć później, więc nie chcemy jej całkowicie usunąć. Zamiast tego, skomentujmy te wiersze. Zaznacz całą definicję końcowego `morewords` średnika, a następnie wybierz przycisk **Zakomentuj wybrane wiersze** na pasku narzędzi. Jeśli wolisz używać klawiatury, naciśnij **klawisze Ctrl**+**K**, **Ctrl**+**C**.

   ![Przycisk Wyjmij komentarz](media/tutorial-comment-out.png)

   Znaki `//` komentarza języka C# są dodawane na początku każdego wybranego wiersza, aby skomentować kod.

## <a name="collapse-code-blocks"></a>Zwijanie bloków kodu

Nie chcemy, aby zobaczyć pusty `Class1` [konstruktor](/dotnet/csharp/programming-guide/classes-and-structs/constructors) dla tego został wygenerowany, więc aby uporządkować nasz widok kodu, zwińmy go. Wybierz małe szare pole ze znakiem minus wewnątrz niego na marginesie pierwszego wiersza konstruktora. Lub, jeśli jesteś użytkownikiem klawiatury, umieść kursor w dowolnym miejscu w kodzie konstruktora i naciśnij **klawisze Ctrl**+**M**, **Ctrl**+**M**.

![Przycisk zwijanie konspektów](media/tutorial-collapse.png)

Blok kodu zwija się tylko do pierwszego wiersza, po którym następuje wielokropek (`...`). Aby ponownie rozwinąć blok kodu, kliknij to samo szare pole, w które ma teraz znak plus, lub ponownie naciśnij **klawisze Ctrl**+**M**, **Ctrl**+**M.** Ta funkcja jest [nazywana tworzeniem przespekk i](../ide/outlining.md) jest szczególnie przydatna podczas zwijania długich metod lub całych klas.

## <a name="view-symbol-definitions"></a>Wyświetlanie definicji symboli

Edytor programu Visual Studio ułatwia sprawdzanie definicji typu, metody itp. Jednym ze sposobów jest przejście do pliku zawierającego definicję, na przykład wybierając **opcję Przejdź do definicji** w dowolnym miejscu, do którego odwołuje się symbol. Jeszcze szybszym sposobem, który nie odsunie fokus od pliku, w który pracujesz, jest użycie [funkcji Peek Definition](../ide/go-to-and-peek-definition.md#peek-definition). Zajrzyjmy do definicji `string` typu.

1. Kliknij prawym przyciskiem `string` myszy dowolne wystąpienie i wybierz z menu treści **opcję Peek Definition.** Lub naciśnij **klawisz Alt**+**F12**.

   Pojawi się wyskakujące okno `String` z definicją klasy. Możesz przewijać w wyskakującym oknie, a nawet zajrzeć do definicji innego typu z zaglądanego kodu.

   ![Okno definicji wglądu](media/tutorial-peek-definition.png)

1. Zamknij okno definicji zaglądanego, wybierając małe pole z literą "x" w prawym górnym rogu okna podręcznego.

## <a name="use-intellisense-to-complete-words"></a>Uzupełnianie wyrazów za pomocą funkcji IntelliSense

[IntelliSense](../ide/using-intellisense.md) jest nieocenionym zasobem podczas kodowania. Może pokazać informacje o dostępnych elementów członkowskich typu lub szczegóły parametru dla różnych przeciążeń metody. Za pomocą programu IntelliSense można również ukończyć słowo po wpisaniu wystarczającej liczby znaków, aby je rozróżnić. Dodajmy wiersz kodu, aby wydrukować uporządkowane ciągi znaków do okna konsoli, które jest standardowym miejscem wyjścia z programu.

1. Poniżej `query` zmiennej zacznij wpisywać następujący kod:

   ```csharp
   foreach (string str in qu
   ```

   Zobaczysz, że program IntelliSense `query` wyświetla szybkie **informacje** o symbolu.

   ![Zakończenie wyrazów IntelliSense w programie Visual Studio](media/tutorial-intellisense-completion-list.png)

1. Aby wstawić resztę `query` wyrazu przy użyciu funkcji uzupełniania wyrazów IntelliSense, naciśnij klawisz **Tab**.

1. Zakończ blok kodu, aby wyglądać jak następujący kod. Można nawet ćwiczyć przy użyciu fragmentów kodu `cw` ponownie, wprowadzając, a `Console.WriteLine` następnie naciskając **tab** dwa razy, aby wygenerować kod.

   ```csharp
   foreach (string str in query)
   {
      Console.WriteLine(str);
   }
   ```

## <a name="refactor-a-name"></a>Refaktoryzator nazwy

Nikt nie pobiera kodu prawo za pierwszym razem, a jedną z rzeczy, które mogą być trzeba zmienić jest nazwa zmiennej lub metody. Wypróbujmy funkcję [refaktoryzowania](../ide/refactoring-in-visual-studio.md) programu Visual Studio, `_words` aby `words`zmienić nazwę zmiennej na .

1. Umieść kursor nad definicją `_words` zmiennej i wybierz polecenie Zmień nazwę z menu kontekstowego lub naciśnij **klawisze** **Ctrl**+**R**, **Ctrl**+**R**.

   W prawym górnym rogu edytora pojawi się wyskakujące okno dialogowe **Zmień nazwę.**

1. Wprowadź żądane **wyrazy**nazwy . Należy zauważyć, `words` że odwołanie do kwerendy jest również automatycznie zmieniana. Przed naciśnięciem **klawisza Enter**zaznacz pole wyboru **Dołącz komentarze** w polu podręcznym **Zmień nazwę.**

   ![Zmień nazwę — Okno dialogowe](media/tutorial-rename.png)

1. Naciśnij **klawisz Enter**.

   Oba wystąpienia `words` zostały zmienione, a także odwołanie `words` do w komentarzu kodu.

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
