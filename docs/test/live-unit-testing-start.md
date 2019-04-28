---
title: Dowiedz się, jak przetestować kod za pomocą testów jednostkowych na żywo
ms.date: 08/31/2017
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: f27e09cd66c05a10648205850a9547d7b191d2de
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787585"
---
# <a name="get-started-with-live-unit-testing-in-visual-studio"></a>Rozpoczynanie pracy z usługą Live Unit Testing w programie Visual Studio

Po włączeniu opcji Live Unit Testing w rozwiązaniu Visual Studio Live Unit Testing wizualnie przedstawia zakres testu i stan swoich testów. On również dynamicznie testy są wykonywane przy każdej modyfikacji kodu i natychmiast powiadamia użytkownika, gdy zmiany spowodują testy, aby zakończyć się niepowodzeniem.

Live Unit Testing może służyć do testowania rozwiązania przeznaczone dla .NET Framework lub .NET Core. W tym samouczku dowiesz się, jak używać funkcji Live Unit Testing, tworząc bibliotekę klas proste przeznaczonego .NET Standard, a następnie utworzysz Projekt narzędzia MSTest przeznaczonego platformy .NET Core, aby ją przetestować.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

Kompletne rozwiązanie języka C# można pobrać z [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) repozytorium w witrynie GitHub.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

Kompletne rozwiązanie programu Visual Basic można go pobrać ze [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/visual-basic/UtilityLibraries/) repozytorium w witrynie GitHub.

---

## <a name="prerequisites"></a>Wymagania wstępne

Ten samouczek wymaga, że po zainstalowaniu programu Visual Studio Enterprise edition z obciążeniem programu .NET Core 2.0.

## <a name="create-the-solution-and-the-class-library-project"></a>Utwórz rozwiązanie i projekt biblioteki klas

Rozpocznij od utworzenia rozwiązania programu Visual Studio o nazwie `UtilityLibraries` składający się z pojedynczego .NET Standard projekt biblioteki klas, `StringLibrary`. Można napisać `StringLibrary` w języku C# lub Visual Basic.

Rozwiązanie to po prostu kontener dla jednego lub więcej projektów. Aby utworzyć puste rozwiązanie, Otwórz program Visual Studio, a następnie wykonaj następujące czynności:

1. Wybierz **pliku** > **New** > **projektu** menu najwyższego poziomu programu Visual Studio.

1. Typ **rozwiązania** do pola wyszukiwania szablonu, a następnie wybierz **puste rozwiązanie** szablonu.

   ::: moniker range="vs-2017"

   ![** Okna dialogowego Nowy projekt **](./media/lut-start/new-solution.png)

   ::: moniker-end

1. Zakończ tworzenie rozwiązania.

Teraz, po utworzeniu rozwiązania, utworzysz biblioteki klas o nazwie `StringLibrary` zawiera szereg metod rozszerzenia do pracy z ciągami.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `UtilityLibraries` rozwiązań i wybierz pozycję **Dodaj** > **nowy projekt**.

::: moniker range="vs-2017"

2. W **Dodaj nowy projekt** okno dialogowe, węzeł wybierz języka C#, następnie wybierz pozycję **.NET Standard**.

   > [!NOTE]
   > Ponieważ nasza biblioteka jest przeznaczony dla .NET Standard zamiast określonej implementacji .NET, można wywołać z dowolnego implementacji .NET, która obsługuje daną wersję .NET Standard. Aby uzyskać więcej informacji, zobacz [.NET Standard](/dotnet/standard/net-standard).

3. Wybierz **biblioteki klas (.NET Standard)** szablonu w okienku po prawej stronie, a następnie wprowadź `StringLibrary` w **nazwa** pola tekstowego, jak przedstawiono na poniższym rysunku:

   ![** Okna dialogowego Dodawanie nowego projektu **](./media/lut-start/add-project-cs.png)

4. Wybierz **OK** do tworzenia projektu.

::: moniker-end

::: moniker range=">=vs-2019"

2. Typ **biblioteki klas** w polu wyszukiwania szablonu, a następnie wybierz **biblioteki klas (.NET Standard)** szablonu. Kliknij przycisk **Dalej**.

   > [!NOTE]
   > Ponieważ nasza biblioteka jest przeznaczony dla .NET Standard zamiast określonej implementacji .NET, można wywołać z dowolnego implementacji .NET, która obsługuje daną wersję .NET Standard. Aby uzyskać więcej informacji, zobacz [.NET Standard](/dotnet/standard/net-standard).

3. Nadaj projektowi nazwę `StringLibrary`.

4. Kliknij przycisk **Utwórz** do tworzenia projektu.

::: moniker-end

5. Zastąp wszystkie istniejący kod w oknie Kod następującym kodem:

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   `StringLibrary` ma trzy metody statyczne:

   - `StartsWithUpper` Zwraca `true` Jeśli ciąg rozpoczyna się od wielkiej litery; w przeciwnym razie zwraca `false`.

   - `StartsWithLower`Zwraca `true` Jeśli ciąg rozpoczyna się od małej litery; w przeciwnym razie zwraca `false`.

   - `HasEmbeddedSpaces` Zwraca `true` Jeśli ciąg zawiera znak spacji osadzonych; w przeciwnym razie zwraca `false`.

6. Wybierz **kompilacji** > **Kompiluj rozwiązanie** menu najwyższego poziomu programu Visual Studio. Program Visual Studio pomyślnie należy utworzyć bibliotekę.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `UtilityLibraries` rozwiązań i wybierz pozycję **Dodaj** > **nowy projekt**.

::: moniker range="vs-2017"

2. W **Dodaj nowy projekt** okno dialogowe, wybierz węzeł Visual Basic, a następnie wybierz **.NET Standard**.

   > [!NOTE]
   > Ponieważ nasza biblioteka jest przeznaczony dla .NET Standard zamiast określonej implementacji .NET, można wywołać z dowolnego implementacji .NET, która obsługuje daną wersję .NET Standard. Aby uzyskać więcej informacji, zobacz [.NET Standard](/dotnet/standard/net-standard).

3. Wybierz **biblioteki klas (.NET Standard)** szablonu w okienku po prawej stronie, a następnie wprowadź `StringLibrary` w **nazwa** pola tekstowego, jak przedstawiono na poniższym rysunku:

   ![** Okna dialogowego Dodawanie nowego projektu **](./media/lut-start/add-project-vb.png)

4. Wybierz **OK** do tworzenia projektu.

::: moniker-end

::: moniker range=">=vs-2019"

2. Typ **biblioteki klas** w polu wyszukiwania szablonu, a następnie wybierz **biblioteki klas (.NET Standard)** szablonu. Kliknij przycisk **Dalej**.

   > [!NOTE]
   > Ponieważ nasza biblioteka jest przeznaczony dla .NET Standard zamiast określonej implementacji .NET, można wywołać z dowolnego implementacji .NET, która obsługuje daną wersję .NET Standard. Aby uzyskać więcej informacji, zobacz [.NET Standard](/dotnet/standard/net-standard).

3. Nadaj projektowi nazwę `StringLibrary`.

4. Kliknij przycisk **Utwórz** do tworzenia projektu.

::: moniker-end

5. Zastąp wszystkie istniejący kod w oknie Kod następującym kodem:

   [!code-vb[StringLibrary source code](samples/visual-basic/utilitylibraries/stringlibrary/class1.vb)]

   `StringLibrary` ma trzy metody statyczne:

   - `StartsWithUpper` Zwraca `true` Jeśli ciąg rozpoczyna się od wielkiej litery; w przeciwnym razie zwraca `false`.

   - `StartsWithLower`Zwraca `true` Jeśli ciąg rozpoczyna się od małej litery; w przeciwnym razie zwraca `false`.

   - `HasEmbeddedSpaces` Zwraca `true` Jeśli ciąg zawiera znak spacji osadzonych; w przeciwnym razie zwraca `false`.

6. Kliknij prawym przyciskiem myszy nad projektem StringLibrary w **Eksploratora rozwiązań** i wybierz **właściwości**. W **aplikacji** karcie, usuń tekst w **głównej przestrzeni nazw** pola tekstowego, jak przedstawiono na poniższym rysunku. Główna przestrzeń nazw jest definiowany przez [Namespace, instrukcja](/dotnet/visual-basic/language-reference/statements/namespace-statement) w kodzie źródłowym.

   ![Okno dialogowe właściwości projektu dla projektów języka Visual Basic](./media/lut-start/vb-properties.png)

7. Wybierz **kompilacji** > **Kompiluj rozwiązanie** menu najwyższego poziomu programu Visual Studio. Program Visual Studio pomyślnie należy utworzyć bibliotekę.

---

## <a name="create-the-test-project"></a>Utwórz projekt testu

Następnym krokiem jest utworzenie projektu testu jednostkowego do testowania `StringLibrary` biblioteki. Utwórz testy jednostkowe, wykonując następujące czynności:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `UtilityLibraries` rozwiązań i wybierz pozycję **Dodaj** > **nowy projekt**.

::: moniker range="vs-2017"

2. W **Dodaj nowy projekt** okno dialogowe, węzeł wybierz języka C#, następnie wybierz pozycję **platformy .NET Core**.

   > [!NOTE]
   > Nie trzeba pisać testy jednostkowe w tym samym języku co biblioteki klas.

3. Wybierz **projekt testów jednostkowych (.NET Core)** szablonu w okienku po prawej stronie, a następnie wprowadź `StringLibraryTests` w **nazwa** pola tekstowego, jak przedstawiono na poniższym rysunku:

   ![** Okna dialogowego Dodawanie nowego projektu ** projektu testu jednostkowego](./media/lut-start/add-unit-test-cs.png)

4. Wybierz **OK** do tworzenia projektu.

::: moniker-end

::: moniker range=">=vs-2019"

2. Typ **testu jednostkowego** w polu wyszukiwania szablonu, a następnie wybierz **projekt testów jednostkowych (.NET Core)** szablonu. Kliknij przycisk **Dalej**.

3. Nadaj projektowi nazwę `StringLibraryTests`.

4. Kliknij przycisk **Utwórz** do tworzenia projektu.

::: moniker-end

   > [!NOTE]
   > Samouczku ułatwiającym rozpoczęcie pracy za pomocą Live Unit Testing szablon testu MSTest. Można również użyć, xUnit i NUnit środowisk testowych.

5. Projekt testu jednostkowego nie może automatycznie korzystać biblioteki klas, który testuje go. Udzielasz dostęp do biblioteki testów przez dodanie odwołania do projektu biblioteki klas. Aby to zrobić, kliknij prawym przyciskiem myszy `StringLibraryTests` projektu, a następnie wybierz **Dodaj** > **odwołania**. W **Menadżer odwołań** okna dialogowego, upewnij się, że **rozwiązania** karta jest wybrany, a wybierz `StringLibrary` projektu, jak pokazano na poniższej ilustracji.

   ![** Odwołanie Menedżera ** okna dialogowego](./media/lut-start/add-reference.png)

6. Zastąp kod testu jednostkowego standardowy dostarczone przez szablon z następującym kodem:

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

7. Zapisz projekt, wybierając **Zapisz** ikonę na pasku narzędzi.

8. Ponieważ testów jednostkowych kod zawiera znaki spoza zestawu ASCII, Visual Studio wyświetla następujące okno dialogowe w celu otrzymania niektóre znaki zostaną utracone jeśli możemy zapisać plik w formacie ASCII domyślne. Wybierz **Zapisz z kodowaniem inne** przycisku.

   ![Wybierz kodowanie pliku](media/lut-start/ascii-encoding.png)

9. W **kodowanie** listy rozwijanej **zaawansowane opcje zapisywania** okno dialogowe, wybierz **Unicode (UTF-8 bez podpisu) - strona kodowa 65001**, jak pokazano na poniższej ilustracji:

   ![Wybieranie kodowania UTF-8](media/lut-start/utf8-encoding.png)

10. Kompiluj projekt testów jednostkowych, wybierając **kompilacji** > **Kompiluj rozwiązanie** menu najwyższego poziomu programu Visual Studio.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `UtilityLibraries` rozwiązań i wybierz pozycję **Dodaj** > **nowy projekt**.

::: moniker range="vs-2017"

2. W **Dodaj nowy projekt** okno dialogowe, wybierz węzeł Visual Basic, a następnie wybierz **platformy .NET Core**.

   > [!NOTE]
   > Nie trzeba pisać testy jednostkowe w tym samym języku co biblioteki klas.

3. Wybierz **projekt testów jednostkowych (.NET Core)** szablonu w okienku po prawej stronie, a następnie wprowadź `StringLibraryTests` w **nazwa** pola tekstowego, jak przedstawiono na poniższym rysunku:

   ![** Okna dialogowego Dodawanie nowego projektu ** dla testu jednostkowego](./media/lut-start/add-unit-test-vb.png)

4. Wybierz **OK** do tworzenia projektu.

::: moniker-end

::: moniker range=">=vs-2019"

2. Typ **testu jednostkowego** w polu wyszukiwania szablonu, a następnie wybierz **projekt testów jednostkowych (.NET Core)** szablonu. Kliknij przycisk **Dalej**.

3. Nadaj projektowi nazwę `StringLibraryTests`.

4. Kliknij przycisk **Utwórz** do tworzenia projektu.

::: moniker-end

   > [!NOTE]
   > Samouczku ułatwiającym rozpoczęcie pracy za pomocą Live Unit Testing szablon testu MSTest. Można również użyć, xUnit i NUnit środowisk testowych.

5. Projekt testu jednostkowego nie może automatycznie korzystać biblioteki klas, który testuje go. Udzielasz dostęp do biblioteki testów przez dodanie odwołania do projektu biblioteki klas. Aby to zrobić, kliknij prawym przyciskiem myszy `StringLibraryTests` projektu, a następnie wybierz **Dodaj** > **odwołania**. W **Menadżer odwołań** okna dialogowego, upewnij się, że **rozwiązania** karta jest wybrany, a wybierz `StringLibrary` projektu, jak pokazano na poniższej ilustracji.

   ![** Odwołanie Menedżera ** okna dialogowego](./media/lut-start/add-reference.png)

6. Zastąp kod testu jednostkowego standardowy dostarczone przez szablon z następującym kodem:

   [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest1.vb)]

7. Zapisz projekt, wybierając **Zapisz** ikonę na pasku narzędzi.

8. Ponieważ testów jednostkowych kod zawiera znaki spoza zestawu ASCII, Visual Studio wyświetla następujące okno dialogowe w celu otrzymania niektóre znaki zostaną utracone jeśli możemy zapisać plik w formacie ASCII domyślne. Wybierz **Zapisz z kodowaniem inne** przycisku.

   ![Wybierz kodowanie pliku](media/lut-start/ascii-encoding.png)

9. W **kodowanie** listy rozwijanej **zaawansowane opcje zapisywania** okno dialogowe, wybierz **Unicode (UTF-8 bez podpisu) - strona kodowa 65001**, jak pokazano na poniższej ilustracji:

   ![Wybieranie kodowania UTF-8](media/lut-start/utf8-encoding.png)

10. Kompiluj projekt testów jednostkowych przez **kompilacji** > **Kompiluj rozwiązanie** menu najwyższego poziomu programu Visual Studio.

---

Utworzono bibliotekę klas, a także niektórych testów jednostkowych dla niego. Wymagania wstępne niezbędne do używania funkcji Live Unit Testing został zakończony.

## <a name="enable-live-unit-testing"></a>Włącz Live Unit Testing

Jeśli, mimo że napisanych testów dla `StringLibrary` biblioteki klas, które jeszcze nie zostało wykonane je. Live Unit Testing wykonuje je automatycznie po jego włączeniu. Aby to zrobić, wykonaj następujące czynności:

1. Opcjonalnie wybierz w oknie kodu, który zawiera kod `StringLibrary`. Jest to *Class1.cs* projekt C# lub *Class1.vb* dla projektów języka Visual Basic. (Ten krok pozwala wizualnie badać wyników testów i zakresu pokrycia kodu, po włączeniu Live Unit Testing.)

1. Wybierz **testu** > **Live Unit Testing** > **Start** menu najwyższego poziomu programu Visual Studio.

1. Aktywne testy jednostkowe, która automatycznie uruchamia wszystkie testy uruchomieniu programu Visual Studio.

Po zakończeniu uruchamiania testów, **Eksplorator testów** wyświetla ogólne wyniki i wyników badań indywidualnych. Ponadto okno kodu wyświetla w postaci graficznej pokrycia kodu testu i wyniki testów. Jak pokazano na poniższej ilustracji, wszystkie trzy testy zostały wykonane pomyślnie. Pokazano także, że nasze testy zostały omówione wszystkie ścieżki kodu `StartsWithUpper` metody te testy i wszystkie wykonane pomyślnie (które jest wskazywany przez zielony znacznik wyboru "✓"). Na koniec pokazuje, że żadna z innych metod w `StringLibrary` mają pokrycie kodu, (który jest wskazywany przez linię "➖").

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

![Okno Eksploratora testów i kodu, po uruchomieniu testów jednostkowych na żywo](media/lut-start/lut-results-cs.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

![Okno Eksploratora testów i kodu, po uruchomieniu testów jednostkowych na żywo](media/lut-start/lut-results-vb.png)

---

Również uzyskasz bardziej szczegółowe informacje dotyczące badania pokrycia i wyników testów, wybierając ikonę pokrycia kodu określonego w oknie kodu. Aby zbadać te dane, wykonaj następujące czynności:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Kliknij zielony znacznik wyboru w wierszu, który odczytuje `if (String.IsNullOrWhiteSpace(s))` w `StartsWithUpper` metody. Jak pokazano na poniższej ilustracji, Live Unit Testing wskazuje, że trzy testy obejmują ten wiersz kodu i że wszystkie zostały wykonane pomyślnie.

   ![Pokrycie kodu dla instrukcji warunkowej "if"](media/lut-start/code-coverage-cs1.png)

1. Kliknij zielony znacznik wyboru w wierszu, który odczytuje `return Char.IsUpper(s[0])` w `StartsWithUpper` metody. Jak pokazano na poniższej ilustracji, Live Unit Testing wskazuje, że tylko dwa badania obejmują ten wiersz kodu i że wszystkie zostały wykonane pomyślnie.

   ![Pokrycie kodu dla instrukcji return](media/lut-start/code-coverage-cs2.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Kliknij zielony znacznik wyboru w wierszu, który odczytuje `If (String.IsNullOrWhiteSpace(s)) Then` w `StartsWithUpper` metody. Jak pokazano na poniższej ilustracji, Live Unit Testing wskazuje, że trzy testy obejmują ten wiersz kodu i że wszystkie zostały wykonane pomyślnie.

   ![Pokrycie kodu dla instrukcji warunkowej "If"](media/lut-start/code-coverage-vb1.png)

1. Kliknij zielony znacznik wyboru w wierszu, który odczytuje `Return Char.IsUpper(s(0))` w `StartsWithUpper` metody. Jak pokazano na poniższej ilustracji, Live Unit Testing wskazuje, że tylko dwa badania obejmują ten wiersz kodu i że wszystkie zostały wykonane pomyślnie.

   ![Pokrycie kodu dla instrukcji return](media/lut-start/code-coverage-vb2.png)

---

Poważnym problemem, który identyfikuje Live Unit Testing czy pokrycie kodu niekompletne. Będzie ona adresów w następnej sekcji.

## <a name="expand-test-coverage"></a>Rozwiń element pokrycia testu

W tej sekcji możesz rozszerzyć testy jednostek, aby `StartsWithLower` metody. Gdy to zrobisz, Live Unit Testing dynamicznie będzie testować kod.

Aby rozszerzyć pokrycia kodu do `StartsWithLower` metody, wykonaj następujące czynności:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Dodaj następujący kod `TestStartsWithLower` i `TestDoesNotStartWithLower` metody służące do pliku z kodem źródłowym projektu testowego:

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. Modyfikowanie `DirectCallWithNullOrEmpty` metody, dodając następujący kod bezpośrednio po wywołaniu [ `Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse` ](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) metody.

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

1. Live Unit Testing automatycznie nowych i zmodyfikowanych: testy są wykonywane podczas modyfikowania kodu źródłowego. Jak poniższy rysunek **Eksplorator testów** pokazuje, wszystkie testy w tym dwóch zostały dodane i ten, który został zmodyfikowany, zakończyły się powodzeniem.

   ![Pokrycie testów w Eksploratorze testów po rozwinięciu.](media/lut-start/test-dynamic.png)

1. Przejdź do okna, który zawiera kod źródłowy `StringLibrary` klasy. Live Unit Testing teraz pokazują nasze pokrycie kodu jest rozszerzony do `StartsWithLower` metody.

    ![Pokrycie kodu dla metody StartsWithLower](media/lut-start/lut-extended-cs.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Dodaj następujący kod `TestStartsWithLower` i `TestDoesNotStartWithLower` metody służące do pliku z kodem źródłowym projektu testowego:

    [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest2.vb#1)]

1. Modyfikowanie `DirectCallWithNullOrEmpty` metody, dodając następujący kod bezpośrednio po wywołaniu [ `Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse` ](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) metody.

    [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest2.vb#2)]

1. Live Unit Testing automatycznie nowych i zmodyfikowanych: testy są wykonywane podczas modyfikowania kodu źródłowego. Jak poniższy rysunek **Eksplorator testów** pokazuje, wszystkie testy w tym dwóch zostały dodane i ten, który został zmodyfikowany, zakończyły się powodzeniem.

   ![Pokrycie testów w Eksploratorze testów po rozwinięciu.](media/lut-start/test-dynamic.png)

1. Przejdź do okna, który zawiera kod źródłowy `StringLibrary` klasy. Live Unit Testing teraz pokazują nasze pokrycie kodu jest rozszerzony do `StartsWithLower` metody.

    ![Pokrycie kodu dla StartsWithLower](media/lut-start/lut-extended-vb.png)

---

W niektórych przypadkach testy zakończone powodzeniem w **Eksplorator testów** może być nieaktywny. Wskazuje, czy test jest w trakcie wykonywania, lub czy test nie został uruchomiony ponownie, ponieważ została zmian nie kodu, które mogło mieć wpływ na test od czasu ostatniego został wykonany.

Do tej pory wszystkie nasze testy zakończyły się powodzeniem. W następnej sekcji zajmiemy się, jak można obsługiwać niepowodzenia testu.

## <a name="handle-a-test-failure"></a>Uchwyt niepowodzenia testu

W tej sekcji dowiesz się, jak skorzystać Live Unit Testing do identyfikowania, rozwiązywanie problemów i adres niepowodzeń testów. Możesz to zrobić, rozwijając pokrycia testu do `HasEmbeddedSpaces` metody.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Dodaj następującą metodę do pliku testu:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

1. Podczas wykonywania testu, Live Unit Testing wskazuje, że `TestHasEmbeddedSpaces` metody nie powiodło się, jak przedstawiono na poniższym rysunku:

   ![Eksplorator testów raportowania testów zakończonych niepowodzeniem.](media/lut-start/test-failure.png)

1. Wybierz okno, które wyświetla kod biblioteki. Należy pamiętać, że Live Unit Testing została rozszerzona pokrycia kodu do `HasEmbeddedSpaces` metody. Również raporty niepowodzenia testu, dodając czerwony znak "🞩" do wierszy objętych testy zakończone niepowodzeniem.

1. Umieść kursor nad wiersz z `HasEmbeddedSpaces` podpis metody. Live Unit Testing wyświetla etykietkę narzędzia, która zgłasza, że metoda jest objęta jeden test, jak przedstawiono na poniższym rysunku:

   ![Live Unit Testing informacje na temat testów zakończonych niepowodzeniem.](media/lut-start/test-failure-info-cs.png)

1. Wybierz nieudane **TestHasEmbeddedSpaces** testu. Pamiętaj, że Live Unit Testing zapewnia kilka opcji, takich jak uruchamianie wszystkich testów, wybierz testów, debugowanie wszystkich testów i debugowanie testów, jako wybrana Poniższa ilustracja przedstawia:

   ![Live Unit Testing opcje dla testów zakończonych niepowodzeniem.](media/lut-start/test-failure-options.png)

1. Wybierz **Debuguj zaznaczone** do debugowania testów zakończonych niepowodzeniem.

1. Program Visual Studio uruchamia test w trybie debugowania. Naszym teście każdego ciągu w tablicy jest przypisywany do zmiennej o nazwie `phrase` i przekazuje go do `HasEmbeddedSpaces` metody. Wykonanie programu wstrzymuje i wywołuje czasu debugera pierwsze wyrażenie asercji jest `false`. Okno dialogowe wyjątku, która wynika z nieoczekiwaną wartość w [ `Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue` ](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) wywołania metody jest wyświetlany na poniższej ilustracji.

   ![Live Unit Testing okno dialogowe wyjątku.](media/lut-start/exception-dialog-cs.png)

   Ponadto wszystkie narzędzia debugowania, które program Visual Studio są dostępne pomóc nam w rozwiązaniu naszym teście nie powiodło się, jak przedstawiono na poniższym rysunku:

   ![Narzędzia debugowania programu Visual Studio.](media/lut-start/debugging-tools-cs.png)

   Zwróć uwagę, w **Autos** okna, wartość `phrase` zmienna jest "Name\tDescription", czyli drugiego elementu tablicy. Metoda testowa oczekuje `HasEmbeddedSpaces` do zwrócenia `true` przekazanej tego ciągu; zamiast tego zwraca `false`. Oczywiście nie rozpoznaje "\t", znak tabulacji jako osadzona spacja.

1. Wybierz **debugowania** > **Kontynuuj**, naciśnij klawisz **F5**, lub kliknij przycisk **Kontynuuj** przycisk na pasku narzędzi, aby kontynuować wykonywanie Test program. Ponieważ wystąpił nieobsługiwany wyjątek, test kończy się.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Dodaj następującą metodę do pliku testu:

    [!code-vb[The TestHasEmbeddedSpaces test method](samples/snippets/visual-basic/lut-start/unittest2.vb#3)]

1. Podczas wykonywania testu, Live Unit Testing wskazuje, że `TestHasEmbeddedSpaces` metody nie powiodło się, jak przedstawiono na poniższym rysunku:

   ![Eksplorator testów raportowania testów zakończonych niepowodzeniem.](media/lut-start/test-failure.png)

1. Wybierz okno, które wyświetla kod biblioteki. Należy pamiętać, że Live Unit Testing została rozszerzona pokrycia kodu do `HasEmbeddedSpaces` metody. Również raporty niepowodzenia testu, dodając czerwony znak "🞩" do wierszy objętych testy zakończone niepowodzeniem.

1. Umieść kursor nad wiersz z `HasEmbeddedSpaces` podpis metody. Live Unit Testing wyświetla etykietkę narzędzia, która zgłasza, że metoda jest objęta jeden test, jak przedstawiono na poniższym rysunku:

   ![Live Unit Testing informacje na temat testów zakończonych niepowodzeniem.](media/lut-start/test-failure-info-vb.png)

1. Wybierz nieudane **TestHasEmbeddedSpaces** testu. Pamiętaj, że Live Unit Testing zapewnia wiele opcji, takich jak uruchamianie wszystkich testów, uruchamiania wybranych testów, debugowanie wszystkich testów i debugowanie testów, jako wybrana Poniższa ilustracja przedstawia:

   ![Live Unit Testing opcje dla testów zakończonych niepowodzeniem.](media/lut-start/test-failure-options.png)

1. Wybierz **Debuguj zaznaczone** do debugowania testów zakończonych niepowodzeniem.

1. Program Visual Studio uruchamia test w trybie debugowania. Naszym teście każdego ciągu w tablicy jest przypisywany do zmiennej o nazwie `phrase` i przekazuje go do `HasEmbeddedSpaces` metody. Wykonanie programu wstrzymuje i wywołuje czasu debugera pierwsze wyrażenie asercji jest `false`. Okno dialogowe wyjątku, która wynika z nieoczekiwaną wartość w [ `Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue` ](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) wywołania metody jest wyświetlany na poniższej ilustracji.

   ![Live Unit Testing okno dialogowe wyjątku.](media/lut-start/exception-dialog-vb.png)

   Ponadto wszystkie narzędzia debugowania, które program Visual Studio są dostępne pomóc nam w rozwiązaniu naszym teście nie powiodło się, jak przedstawiono na poniższym rysunku:

   ![Narzędzia debugowania programu Visual Studio.](media/lut-start/debugging-tools-vb.png)

   Zwróć uwagę, w **Autos** okna, wartość `phrase` zmienna jest "Name" + vbTab + "Description", czyli drugiego elementu tablicy. Metoda testowa oczekuje `HasEmbeddedSpaces` do zwrócenia `true` przekazanej tego ciągu; zamiast tego zwraca `false`. Oczywiście nie rozpoznaje znak tabulacji jako osadzona spacja.

1. Wybierz **debugowania** > **Kontynuuj**, naciśnij klawisz **F5**, lub kliknij przycisk **Kontynuuj** przycisk na pasku narzędzi, aby kontynuować wykonywanie Test program. Ponieważ wystąpił nieobsługiwany wyjątek, test kończy się.

---

Zapewnia to za mało informacji dla badań wstępnych usterki. Albo `TestHasEmbeddedSpaces` (procedury testu) wprowadzone niepoprawne założeń lub `HasEmbeddedSpaces` niepoprawnie rozpoznać wszystkich osadzonych spacje. Aby zdiagnozować i rozwiązać ten problem, zacznij od `StringLibrary.HasEmbeddedSpaces` metody:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Przyjrzyj się porównanie w `HasEmbeddedSpaces` metody. Traktuje nim osadzona spacja to U + 0020. Jednak standardu Unicode obejmuje szereg innych znaków spacji. Sugeruje to, że kod biblioteki niepoprawnie jest sprawdzane pod kątem znak odstępu.

1. Zamień na wywołanie w celu porównania równości <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> metody:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. Live Unit Testing umożliwia ponowne wykonanie metody testów zakończonych niepowodzeniem i automatycznie aktualizuje wyniki w oknie kodu, a w **Eksploratora testów**, jak pokazano na poniższej ilustracji:

    ![Pomyślnego testowego HasEmbeddedSpaces.](media/lut-start/test-success-cs.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Przyjrzyj się porównanie w `HasEmbeddedSpaces` metody. Traktuje nim osadzona spacja to U + 0020. Jednak standardu Unicode obejmuje szereg innych znaków spacji. Sugeruje to, że kod biblioteki niepoprawnie jest sprawdzane pod kątem znak odstępu.

1. Zamień na wywołanie w celu porównania równości <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> metody:

    [!code-vb[The TestHasEmbeddedSpaces test method](samples/snippets/visual-basic/lut-start/class2.vb#1)]

1. Live Unit Testing automatycznie ponownie uruchamia metody testów zakończonych niepowodzeniem i aktualizuje wyniki w oknie kodu, a w **Eksploratora testów**, jak pokazano na poniższej ilustracji:

    ![Pomyślnego testowego HasEmbeddedSpaces.](media/lut-start/test-success-vb.png)

---

## <a name="see-also"></a>Zobacz także

- [Live Unit Testing w programie Visual Studio](live-unit-testing.md)
- [Live Unit Testing — często zadawane pytania](live-unit-testing-faq.md)