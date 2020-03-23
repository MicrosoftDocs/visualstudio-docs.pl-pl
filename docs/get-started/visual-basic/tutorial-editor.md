---
title: Wprowadzenie do edycji dla deweloperów języka Visual Basic
description: To 10-minutowe wprowadzenie do edytora kodu w programie Visual Studio pokazuje niektóre ze sposobów, w jakie program Visual Studio ułatwia pisanie, nawigowanie i rozumienie kodu języka Visual Basic.
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "75584611"
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

W tym artykule założono, że znasz już język Visual Basic. Jeśli nie, sugerujemy, aby spojrzeć na samouczek, takich jak [Wprowadzenie do języka Visual Basic w programie Visual Studio](../../get-started/visual-basic/tutorial-console.md) pierwszy.

> [!TIP]
> Aby wykonać wraz z tym artykułem, upewnij się, że ustawienia języka Visual Basic są zaznaczone dla programu Visual Studio. Aby uzyskać informacje na temat wybierania ustawień zintegrowanego środowiska programistycznego (IDE), zobacz [Wybieranie ustawień środowiska](visual-studio-ide.md#select-environment-settings).

## <a name="create-a-new-code-file"></a>Tworzenie nowego pliku kodu

Zacznij od utworzenia nowego pliku i dodania do niego kodu.

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio. Naciśnij **klawisz Esc** lub kliknij przycisk Kontynuuj bez **kodu** w oknie startowym, aby otworzyć środowisko programistyczne.

::: moniker-end

2. Z menu **Plik** na pasku menu wybierz polecenie **Nowy plik**.

3. W oknie dialogowym **Nowy plik** w kategorii **Ogólne** wybierz pozycję Visual **Basic Class**, a następnie wybierz pozycję **Otwórz**.

   Nowy plik zostanie otwarty w edytorze ze szkieletem klasy Visual Basic. (Można już zauważyć, że nie trzeba tworzyć pełny projekt programu Visual Studio, aby uzyskać niektóre korzyści, które oferuje edytor kodu, takie jak wyróżnianie składni. Wszystko, czego potrzebujesz, to plik kodu!)

   ![Plik kodu języka Visual Basic w programie Visual Studio](media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Używanie fragmentów kodu

Visual Studio zawiera przydatne *fragmenty kodu,* których można użyć do szybkiego i łatwego generowania często używanych bloków kodu. [Fragmenty kodu](../../ide/code-snippets.md) są dostępne dla różnych języków programowania, w tym Visual Basic, C#, i C++. Dodajmy fragment kodu **podwładny** języka Visual Basic do naszego pliku.

1. Umieść kursor nad wierszem `End Class`z napisem , i wpisz **sub**.

   Zostanie wyświetlone wyskakujące `Sub` okno dialogowe z informacjami o słowie kluczowym i sposobie wstawienia fragmentu kodu **podrzędnego.**

   ![IntelliSense dla fragmentu kodu w programie Visual Studio](media/tutorial-intellisense-snippet.png)

1. Naciśnij dwukrotnie **klawisz Tab,** aby wstawić fragment kodu.

   Konspekt procedury `MySub()` Sub zostanie dodany do pliku.

Dostępne fragmenty kodu różnią się w zależności od języka programowania. Możesz sprawdzić dostępne fragmenty kodu programu Visual Basic, wybierając **pozycję Edytuj** > **fragment wstawiania** **intellisense** > (lub naciśnij **klawisze Ctrl**+**K**, **Ctrl**+**X**). W przypadku języka Visual Basic fragmenty kodu są dostępne dla następujących kategorii:

![Lista fragmentów kodu języka Visual Basic](media/tutorial-code-snippet-list.png)

Istnieją urywki do określania, czy plik istnieje na komputerze, zapisywania do pliku tekstowego, odczytywania wartości rejestru, wykonywania kwerendy SQL, tworzenia [for each... Następne stwierdzenie](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)i wiele innych.

## <a name="comment-out-code"></a>Skomentuj kod

Pasek narzędzi, który jest wiersz przycisków pod paskiem menu w programie Visual Studio, może pomóc zwiększyć produktywność podczas kodowania. Na przykład można przełączyć tryb ukończenia IntelliSense, zwiększyć lub zmniejszyć wcięcie wiersza lub skomentować kod, który nie ma być kompilowany. [(IntelliSense](../../ide/using-intellisense.md) to pomoc w kodowaniu, która wyświetla listę dopasowujących metod, między innymi.) W tej sekcji pokomentujemy kod.

![Przyciski paska narzędzi edytora](media/tutorial-editor-toolbar.png)

1. Wklej poniższy kod `MySub()` do treści procedury.

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

1. Nie używamy tablicy, `morewords` ale możemy jej użyć później, więc nie chcemy jej całkowicie usunąć. Zamiast tego, skomentujmy te wiersze. Zaznacz całą definicję zamykającego `morewords` nawiasu klamrowego, a następnie wybierz przycisk **Zajmij wybrane linie** na pasku narzędzi. Jeśli wolisz używać klawiatury, naciśnij **klawisze Ctrl**+**K**, **Ctrl**+**C**.

   ![Przycisk Wyjmij komentarz](media/tutorial-comment-out.png)

   Znak `'` komentarza języka Visual Basic jest dodawany na początku każdego zaznaczonego wiersza w celu skomentowania kodu.

## <a name="collapse-code-blocks"></a>Zwijanie bloków kodu

Można zwinąć sekcje kodu, aby skupić się tylko na częściach, które są interesujące dla Ciebie. Aby ćwiczyć, zwińmy tablicę `_words` do jednego wiersza kodu. Wybierz małe szare pole ze znakiem minus wewnątrz niego `Dim _words = New String() {`na marginesie wiersza, który mówi . Lub, jeśli jesteś użytkownikiem klawiatury, umieść kursor w dowolnym miejscu w definicji tablicy i naciśnij **klawisze Ctrl**+**M**, **Ctrl**+**M**.

![Przycisk zwijanie konspektów](media/tutorial-collapse.png)

Blok kodu zwija się tylko do pierwszego wiersza, po którym następuje wielokropek (`...`). Aby ponownie rozwinąć blok kodu, kliknij to samo szare pole, w które ma teraz znak plus, lub ponownie naciśnij **klawisze Ctrl**+**M**, **Ctrl**+**M.** Ta funkcja jest [nazywana tworzeniem przespekk i](../../ide/outlining.md) jest szczególnie przydatna podczas zwijania długich metod lub całych klas.

## <a name="view-symbol-definitions"></a>Wyświetlanie definicji symboli

Edytor programu Visual Studio ułatwia sprawdzanie definicji typu, metody itp. Jednym ze sposobów jest przejście do pliku zawierającego definicję, na przykład wybierając **opcję Przejdź do definicji** w dowolnym miejscu, do którego odwołuje się symbol. Jeszcze szybszym sposobem, który nie odsunie fokus od pliku, w który pracujesz, jest użycie [funkcji Peek Definition](../../ide/go-to-and-peek-definition.md#peek-definition). Zajrzyjmy do definicji `String` typu.

1. Kliknij prawym przyciskiem `String` myszy wyraz i wybierz z menu treści **opcję Peek Definition.** Lub naciśnij **klawisz Alt**+**F12**.

   Pojawi się wyskakujące okno `String` z definicją klasy. Możesz przewijać w wyskakującym oknie, a nawet zajrzeć do definicji innego typu z zaglądanego kodu.

   ![Okno definicji wglądu](media/tutorial-peek-definition.png)

1. Zamknij okno definicji zaglądanego, wybierając małe pole z literą "x" w prawym górnym rogu okna podręcznego.

## <a name="use-intellisense-to-complete-words"></a>Uzupełnianie wyrazów za pomocą funkcji IntelliSense

[IntelliSense](../../ide/using-intellisense.md) jest nieocenionym zasobem podczas kodowania. Może pokazać informacje o dostępnych elementów członkowskich typu lub szczegóły parametru dla różnych przeciążeń metody. Za pomocą programu IntelliSense można również ukończyć słowo po wpisaniu wystarczającej liczby znaków, aby je rozróżnić. Dodajmy wiersz kodu, aby wydrukować uporządkowane ciągi znaków do okna konsoli, które jest standardowym miejscem wyjścia z programu.

1. Poniżej `query` zmiennej zacznij wpisywać następujący kod:

   ```vb
   For Each str In qu
   ```

   Zobaczysz, że program IntelliSense `query` wyświetla szybkie **informacje** o symbolu.

   ![Zakończenie wyrazów IntelliSense w programie Visual Studio](media/tutorial-intellisense-completion-list.png)

1. Aby wstawić resztę `query` wyrazu przy użyciu funkcji uzupełniania wyrazów IntelliSense, naciśnij klawisz **Tab**.

1. Zakończ blok kodu, aby wyglądać jak następujący kod.

   ```vb
   For Each str In query
       Console.WriteLine(str)
   Next
   ```

## <a name="refactor-a-name"></a>Refaktoryzator nazwy

Nikt nie pobiera kodu prawo za pierwszym razem, a jedną z rzeczy, które mogą być trzeba zmienić jest nazwa zmiennej lub metody. Wypróbujmy funkcję [refaktoryzowania](../../ide/refactoring-in-visual-studio.md) programu Visual Studio, `_words` aby `words`zmienić nazwę zmiennej na .

1. Umieść kursor nad definicją `_words` zmiennej i wybierz polecenie Zmień nazwę z menu kontekstowego po **kliknięciu** prawym przyciskiem myszy lub menu kontekstowym.

   W prawym górnym rogu edytora pojawi się wyskakujące okno dialogowe **Zmień nazwę.**

1. Gdy zmienna `_words` jest nadal zaznaczona, wpisz żądaną nazwę **słów**. Należy zauważyć, `words` że odwołanie do kwerendy jest również automatycznie zmieniana. Przed naciśnięciem **klawisza Enter** lub kliknij przycisk **Zastosuj**zaznacz pole wyboru **Dołącz komentarze** w polu podręcznym **Zmień nazwę.**

   ![Zmień nazwę — Okno dialogowe](media/tutorial-rename.png)

1. Naciśnij **klawisz Enter** lub kliknij przycisk **Zastosuj**.

   Oba wystąpienia `words` są zmieniane, a także `words` odwołanie do w komentarzu kodu.

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
