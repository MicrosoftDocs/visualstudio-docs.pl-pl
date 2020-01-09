---
title: Dowiedz się, jak testować kod za pomocą testów jednostkowych na żywo
ms.date: 08/31/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 748dfc592fbf7a3b9737e9f418362067b92bb8ff
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594295"
---
# <a name="get-started-with-live-unit-testing"></a>Rozpoczynanie pracy z funkcją Live Unit Testing

Włączenie Live Unit Testing w rozwiązaniu programu Visual Studio wizualne przedstawia pokrycie testów i stan testów. Live Unit Testing również dynamicznie wykonuje testy za każdym razem, gdy modyfikujesz kod i natychmiast powiadomimy, gdy zmiany powodują niepowodzenie testów.

Live Unit Testing może służyć do testowania rozwiązań przeznaczonych dla .NET Framework lub .NET Core. W ramach tego samouczka nauczysz się używać Live Unit Testing przez utworzenie prostej biblioteki klas, która jest przeznaczona dla .NET Standard, i utworzysz projekt MSTest, który jest przeznaczony dla platformy .NET Core w celu przetestowania.

Kompletne rozwiązanie języka C# można pobrać z [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) repozytorium w witrynie GitHub.

## <a name="prerequisites"></a>Wymagania wstępne

Ten samouczek wymaga zainstalowania wersji Visual Studio Enterprise z użyciem obciążenia **międzyplatformowego dla platformy .NET Core** .

## <a name="create-the-solution-and-the-class-library-project"></a>Utwórz rozwiązanie i projekt biblioteki klas

Zacznij od utworzenia rozwiązania programu Visual Studio o nazwie UtilityLibraries, które składa się z pojedynczego projektu biblioteki klas .NET Standard, StringLibrary.

Rozwiązanie to po prostu kontener dla jednego lub więcej projektów. Aby utworzyć puste rozwiązanie, Otwórz program Visual Studio i wykonaj następujące czynności:

1. Wybierz **pliku** > **New** > **projektu** menu najwyższego poziomu programu Visual Studio.

1. Wpisz **rozwiązanie** w polu wyszukiwania szablonu, a następnie wybierz szablon **pustego rozwiązania** .

   ::: moniker range="vs-2017"

   ![** Okna dialogowego Nowy projekt **](./media/lut-start/new-solution.png)

   ::: moniker-end

1. Zakończ tworzenie rozwiązania.

Teraz, po utworzeniu rozwiązania, utworzysz bibliotekę klas o nazwie StringLibrary, która zawiera szereg metod rozszerzających do pracy z ciągami.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie UtilityLibraries i wybierz pozycję **Dodaj** > **Nowy projekt**.

::: moniker range="vs-2017"

2. W **Dodaj nowy projekt** okno dialogowe, węzeł wybierz języka C#, następnie wybierz pozycję **.NET Standard**.

   > [!NOTE]
   > Ponieważ nasza biblioteka jest przeznaczona .NET Standard, a nie do konkretnej implementacji platformy .NET, można ją wywołać z dowolnej implementacji platformy .NET, która obsługuje tę wersję programu .NET Standard. Aby uzyskać więcej informacji, zobacz [.NET Standard](/dotnet/standard/net-standard).

3. Wybierz szablon **Biblioteka klas (.NET standard)** w okienku po prawej stronie, a następnie wprowadź **StringLibrary** w polu tekstowym **Nazwa** , jak pokazano na poniższej ilustracji:

   ![** Okna dialogowego Dodawanie nowego projektu **](./media/lut-start/add-project-cs.png)

4. Wybierz **OK** do tworzenia projektu.

::: moniker-end

::: moniker range=">=vs-2019"

2. Wpisz **Biblioteka klas** w polu wyszukiwania szablonu i szablon wybierz **bibliotekę klas (.NET standard)** . Kliknij przycisk **Dalej**.

   > [!NOTE]
   > Ponieważ nasza biblioteka jest przeznaczona .NET Standard, a nie do konkretnej implementacji platformy .NET, można ją wywołać z dowolnej implementacji platformy .NET, która obsługuje tę wersję programu .NET Standard. Aby uzyskać więcej informacji, zobacz [.NET Standard](/dotnet/standard/net-standard).

3. Nazwij projekt **StringLibrary**.

4. Kliknij przycisk **Utwórz** , aby utworzyć projekt.

::: moniker-end

5. Zastąp wszystkie istniejący kod w oknie Kod następującym kodem:

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   StringLibrary ma trzy metody statyczne:

   - `StartsWithUpper` Zwraca `true` Jeśli ciąg rozpoczyna się od wielkiej litery; w przeciwnym razie zwraca `false`.

   - `StartsWithLower`Zwraca `true` Jeśli ciąg rozpoczyna się od małej litery; w przeciwnym razie zwraca `false`.

   - `HasEmbeddedSpaces` Zwraca `true` Jeśli ciąg zawiera znak spacji osadzonych; w przeciwnym razie zwraca `false`.

6. Wybierz **kompilacji** > **Kompiluj rozwiązanie** menu najwyższego poziomu programu Visual Studio. Kompilacja powinna zakończyć się powodzeniem.

## <a name="create-the-test-project"></a>Utwórz projekt testu

Następnym krokiem jest utworzenie projektu testów jednostkowych w celu przetestowania biblioteki StringLibrary. Utwórz testy jednostkowe, wykonując następujące czynności:

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie UtilityLibraries i wybierz pozycję **Dodaj** > **Nowy projekt**.

::: moniker range="vs-2017"

2. W **Dodaj nowy projekt** okno dialogowe, węzeł wybierz języka C#, następnie wybierz pozycję **platformy .NET Core**.

   > [!NOTE]
   > Nie trzeba pisać testy jednostkowe w tym samym języku co biblioteki klas.

3. Wybierz szablon **projekt testów jednostkowych (.NET Core)** w okienku po prawej stronie, a następnie wprowadź **StringLibraryTests** w polu tekstowym **Nazwa** , jak pokazano na poniższej ilustracji:

   ![** Okna dialogowego Dodawanie nowego projektu ** projektu testu jednostkowego](./media/lut-start/add-unit-test-cs.png)

4. Wybierz **OK** do tworzenia projektu.

::: moniker-end

::: moniker range=">=vs-2019"

2. Wpisz **test jednostkowy** w polu wyszukiwania szablonu, a następnie wybierz szablon **projekt testów jednostkowych (.NET Core)** . Kliknij przycisk **Dalej**.

3. Nazwij projekt **StringLibraryTests**.

4. Kliknij przycisk **Utwórz** , aby utworzyć projekt.

::: moniker-end

   > [!NOTE]
   > Samouczku ułatwiającym rozpoczęcie pracy za pomocą Live Unit Testing szablon testu MSTest. Można również użyć, xUnit i NUnit środowisk testowych.

5. Projekt testu jednostkowego nie może automatycznie korzystać biblioteki klas, który testuje go. Udzielasz dostęp do biblioteki testów przez dodanie odwołania do projektu biblioteki klas. Aby to zrobić, kliknij prawym przyciskiem myszy `StringLibraryTests` projektu, a następnie wybierz **Dodaj** > **odwołania**. W oknie dialogowym **Menedżer odwołań** upewnij się, że karta **rozwiązanie** jest zaznaczona, a następnie wybierz projekt StringLibrary, jak pokazano na poniższej ilustracji.

   ![** Odwołanie Menedżera ** okna dialogowego](./media/lut-start/add-reference.png)

6. Zastąp kod testu jednostkowego standardowy dostarczone przez szablon z następującym kodem:

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

7. Zapisz projekt, wybierając **Zapisz** ikonę na pasku narzędzi.

8. Ponieważ kod testu jednostkowego zawiera niektóre znaki inne niż ASCII, program Visual Studio wyświetla następujące okno dialogowe, aby ostrzec o utracie niektórych znaków, jeśli zapiszesz plik w domyślnym formacie ASCII. Wybierz **Zapisz z kodowaniem inne** przycisku.

   ![Wybierz kodowanie pliku](media/lut-start/ascii-encoding.png)

9. Na liście rozwijanej **kodowanie** w oknie dialogowym **Opcje zapisu zaawansowanego** wybierz opcję **Unicode (UTF-8 bez podpisu)-strona kodowa 65001**, jak pokazano na poniższej ilustracji:

   ![Wybieranie kodowania UTF-8](media/lut-start/utf8-encoding.png)

10. Kompiluj projekt testów jednostkowych, wybierając **kompilacji** > **Kompiluj rozwiązanie** menu najwyższego poziomu programu Visual Studio.

Utworzono bibliotekę klas, a także niektórych testów jednostkowych dla niego. Wymagania wstępne niezbędne do używania funkcji Live Unit Testing został zakończony.

## <a name="enable-live-unit-testing"></a>Włącz Live Unit Testing

Do tej pory mimo że Zapisano testy dla biblioteki klas StringLibrary, nie zostały one wykonane. Live Unit Testing wykonuje je automatycznie po jego włączeniu. Aby to zrobić, wykonaj następujące czynności:

1. Opcjonalnie wybierz okno kod, które zawiera kod dla StringLibrary. Jest to *Class1.cs* projekt C# lub *Class1.vb* dla projektów języka Visual Basic. (Ten krok pozwala wizualnie zbadać wynik testów i zakres pokrycia kodu po włączeniu Live Unit Testing).

1. Wybierz **testu** > **Live Unit Testing** > **Start** menu najwyższego poziomu programu Visual Studio.

1. Aktywne testy jednostkowe, która automatycznie uruchamia wszystkie testy uruchomieniu programu Visual Studio.

Po zakończeniu uruchamiania testów, **Eksplorator testów** wyświetla ogólne wyniki i wyników badań indywidualnych. Ponadto okno kodu wyświetla w postaci graficznej pokrycia kodu testu i wyniki testów. Jak pokazano na poniższym obrazie, wszystkie trzy testy zostały wykonane pomyślnie. Pokazano także, że nasze testy zostały omówione wszystkie ścieżki kodu `StartsWithUpper` metody te testy i wszystkie wykonane pomyślnie (które jest wskazywany przez zielony znacznik wyboru "✓"). Na koniec pokazuje, że żadna z innych metod w StringLibrary nie ma pokrycia kodu (który jest wskazywany przez niebieską linię "➖").

![Okno Eksploratora testów i kodu, po uruchomieniu testów jednostkowych na żywo](media/lut-start/lut-results-cs.png)

Również uzyskasz bardziej szczegółowe informacje dotyczące badania pokrycia i wyników testów, wybierając ikonę pokrycia kodu określonego w oknie kodu. Aby zbadać te dane, wykonaj następujące czynności:

1. Kliknij zielony znacznik wyboru w wierszu, który odczytuje `if (String.IsNullOrWhiteSpace(s))` w `StartsWithUpper` metody. Jak widać na poniższej ilustracji, Live Unit Testing wskazuje, że trzy testy pokrywają ten wiersz kodu i że wszystkie zostały wykonane pomyślnie.

   ![Pokrycie kodu dla instrukcji warunkowej "if"](media/lut-start/code-coverage-cs1.png)

1. Kliknij zielony znacznik wyboru w wierszu, który odczytuje `return Char.IsUpper(s[0])` w `StartsWithUpper` metody. Jak widać na poniższej ilustracji, Live Unit Testing wskazuje, że tylko dwa testy obejmują ten wiersz kodu, a wszystkie wykonane pomyślnie.

   ![Pokrycie kodu dla instrukcji return](media/lut-start/code-coverage-cs2.png)

Poważnym problemem, który identyfikuje Live Unit Testing czy pokrycie kodu niekompletne. Będzie ona adresów w następnej sekcji.

## <a name="expand-test-coverage"></a>Rozwiń element pokrycia testu

W tej sekcji możesz rozszerzyć testy jednostek, aby `StartsWithLower` metody. Gdy to zrobisz, Live Unit Testing dynamicznie będzie testować kod.

Aby rozszerzyć pokrycia kodu do `StartsWithLower` metody, wykonaj następujące czynności:

1. Dodaj następujący kod `TestStartsWithLower` i `TestDoesNotStartWithLower` metody służące do pliku z kodem źródłowym projektu testowego:

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. Modyfikowanie `DirectCallWithNullOrEmpty` metody, dodając następujący kod bezpośrednio po wywołaniu [ `Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse` ](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) metody.

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

1. Live Unit Testing automatycznie nowych i zmodyfikowanych: testy są wykonywane podczas modyfikowania kodu źródłowego. Zgodnie z poniższą ilustracją programu **Test Explorer** wszystkie testy, w tym dodawane dwa i te, które zostały zmodyfikowane, zakończyły się powodzeniem.

   ![Eksplorator testów po rozwinięciu pokrycia testu](media/lut-start/test-dynamic.png)

1. Przejdź do okna, które zawiera kod źródłowy dla klasy StringLibrary. Live Unit Testing teraz pokazują nasze pokrycie kodu jest rozszerzony do `StartsWithLower` metody.

    ![Pokrycie kodu dla metody StartsWithLower](media/lut-start/lut-extended-cs.png)

W niektórych przypadkach pomyślne testy w **Eksploratorze testów** mogą być wyszarzone. Oznacza to, że test jest aktualnie wykonywany lub że test nie został uruchomiony ponownie, ponieważ nie wprowadzono żadnych zmian w kodzie, które mogłyby mieć wpływ na test od momentu jego ostatniego wykonania.

Do tej pory wszystkie nasze testy zakończyły się powodzeniem. W następnej sekcji zajmiemy się, jak można obsługiwać niepowodzenia testu.

## <a name="handle-a-test-failure"></a>Uchwyt niepowodzenia testu

W tej sekcji dowiesz się, jak skorzystać Live Unit Testing do identyfikowania, rozwiązywanie problemów i adres niepowodzeń testów. Możesz to zrobić, rozwijając pokrycia testu do `HasEmbeddedSpaces` metody.

1. Dodaj następującą metodę do pliku testu:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

1. Gdy test zostanie wykonany, Live Unit Testing wskazuje, że metoda `TestHasEmbeddedSpaces` nie zakończyła się niepowodzeniem, jak pokazano na poniższym obrazie:

   ![Eksplorator testów zgłasza test zakończony niepowodzeniem](media/lut-start/test-failure.png)

1. Wybierz okno, które wyświetla kod biblioteki. Live Unit Testing ma rozwinięte pokrycie kodu dla metody `HasEmbeddedSpaces`. Również raporty niepowodzenia testu, dodając czerwony znak "🞩" do wierszy objętych testy zakończone niepowodzeniem.

1. Umieść kursor nad wiersz z `HasEmbeddedSpaces` podpis metody. Live Unit Testing wyświetla etykietkę narzędzia, która zgłasza, że metoda jest objęta jednym testem, jak pokazano na poniższej ilustracji:

   ![Live Unit Testing informacji na testach zakończonych niepowodzeniem](media/lut-start/test-failure-info-cs.png)

1. Wybierz nieudane **TestHasEmbeddedSpaces** testu. Live Unit Testing udostępnia wiele opcji, takich jak uruchamianie wszystkich testów, uruchamianie wybranych testów, debugowanie wszystkich testów i debugowanie wybranych testów, jak pokazano na poniższej ilustracji:

   ![Opcje Live Unit Testing dla testu zakończonego niepowodzeniem](media/lut-start/test-failure-options.png)

1. Wybierz **Debuguj zaznaczone** do debugowania testów zakończonych niepowodzeniem.

1. Program Visual Studio uruchamia test w trybie debugowania.

   Test przypisuje każdy ciąg w tablicy do zmiennej o nazwie `phrase` i przekazuje ją do metody `HasEmbeddedSpaces`. Wykonanie programu wstrzymuje i wywołuje czasu debugera pierwsze wyrażenie asercji jest `false`. Na poniższej ilustracji przedstawiono okno dialogowe wyjątku, które wynika z nieoczekiwanej wartości w wywołaniu metody [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) .

   ![Okno dialogowe wyjątku Live Unit Testing](media/lut-start/exception-dialog-cs.png)

   Ponadto wszystkie narzędzia debugowania udostępniane przez program Visual Studio są dostępne, aby pomóc nam w rozwiązywaniu problemów z testem zakończonym niepowodzeniem, jak pokazano na poniższej ilustracji:

   ![Narzędzia debugowania programu Visual Studio](media/lut-start/debugging-tools-cs.png)

   Zwróć uwagę, w **Autos** okna, wartość `phrase` zmienna jest "Name\tDescription", czyli drugiego elementu tablicy. Metoda testowa oczekuje `HasEmbeddedSpaces` do zwrócenia `true` przekazanej tego ciągu; zamiast tego zwraca `false`. Oczywiście nie rozpoznaje "\t", znak tabulacji jako osadzona spacja.

1. Wybierz **debugowania** > **Kontynuuj**, naciśnij klawisz **F5**, lub kliknij przycisk **Kontynuuj** przycisk na pasku narzędzi, aby kontynuować wykonywanie Test program. Ponieważ wystąpił nieobsługiwany wyjątek, test kończy się.
Zapewnia to za mało informacji dla badań wstępnych usterki. Albo `TestHasEmbeddedSpaces` (procedury testu) wprowadzone niepoprawne założeń lub `HasEmbeddedSpaces` niepoprawnie rozpoznać wszystkich osadzonych spacje.

1. Aby zdiagnozować i rozwiązać ten problem, Zacznij od metody `StringLibrary.HasEmbeddedSpaces`. Przyjrzyj się porównanie w `HasEmbeddedSpaces` metody. Traktuje nim osadzona spacja to U + 0020. Jednak standardu Unicode obejmuje szereg innych znaków spacji. Sugeruje to, że kod biblioteki niepoprawnie jest sprawdzane pod kątem znak odstępu.

1. Zamień na wywołanie w celu porównania równości <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> metody:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. Live Unit Testing automatycznie ponownie uruchamia nieudaną metodę testową i aktualizuje wyniki w oknie kodu i w **Eksploratorze testów**, jak pokazano na poniższej ilustracji:

    ![Pomyślne testowanie HasEmbeddedSpaces](media/lut-start/test-success-cs.png)

## <a name="see-also"></a>Zobacz także

- [Live Unit Testing w programie Visual Studio](live-unit-testing.md)
- [Live Unit Testing — często zadawane pytania](live-unit-testing-faq.md)
