---
title: Dowiedz się, jak przetestować kod za pomocą live unit test
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594295"
---
# <a name="get-started-with-live-unit-testing"></a>Rozpoczynanie pracy z funkcją Live Unit Testing

Po włączeniu testowania jednostek na żywo w rozwiązaniu programu Visual Studio, wizualnie przedstawia pokrycie testu i stan testów. Live Unit Testing również dynamicznie wykonuje testy za każdym razem, gdy modyfikujesz kod i natychmiast powiadamia, gdy zmiany powodują testy nie powiodło się.

Live Unit Testing może służyć do testowania rozwiązań, które są przeznaczone dla platformy .NET Framework lub .NET Core. W tym samouczku dowiesz się używać live unit testing, tworząc prostą bibliotekę klas, która jest przeznaczona dla platformy .NET Standard, a następnie utworzysz projekt MSTest, który jest przeznaczony dla platformy .NET Core, aby go przetestować.

Kompletne rozwiązanie Języka C# można pobrać z repozytorium [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) w usłudze GitHub.

## <a name="prerequisites"></a>Wymagania wstępne

Ten samouczek wymaga zainstalowania wersji programu Visual Studio Enterprise z **wieloplatformowym obciążeniem dewelopera .NET Core.**

## <a name="create-the-solution-and-the-class-library-project"></a>Tworzenie rozwiązania i projektu biblioteki klas

Rozpocznij od utworzenia rozwiązania programu Visual Studio o nazwie UtilityLibraries, który składa się z pojedynczego projektu biblioteki klas .NET Standard, StringLibrary.

Rozwiązanie jest tylko kontenerem dla jednego lub więcej projektów. Aby utworzyć puste rozwiązanie, otwórz program Visual Studio i wykonaj następujące czynności:

1. Wybierz **polecenie Plik** > **nowego** > **projektu** z menu programu Visual Studio najwyższego poziomu.

1. Wpisz **rozwiązanie** w polu wyszukiwania szablonu, a następnie wybierz szablon **Puste rozwiązanie.**

   ::: moniker range="vs-2017"

   ![Okno dialogowe **Nowy projekt**](./media/lut-start/new-solution.png)

   ::: moniker-end

1. Zakończ tworzenie rozwiązania.

Teraz, gdy utworzono rozwiązanie, utworzysz bibliotekę klas o nazwie StringLibrary, która zawiera wiele metod rozszerzenia do pracy z ciągami.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie UtilityLibraries i wybierz pozycję **Dodaj** > **nowy projekt**.

::: moniker range="vs-2017"

2. W oknie dialogowym **Dodawanie nowego projektu** wybierz węzeł C#, a następnie wybierz pozycję **.NET Standard**.

   > [!NOTE]
   > Ponieważ nasza biblioteka jest przeznaczona dla platformy .NET Standard, a nie określonej implementacji platformy .NET, można ją wywołać z dowolnej implementacji platformy .NET obsługującej tę wersję programu .NET Standard. Aby uzyskać więcej informacji, zobacz [.NET Standard](/dotnet/standard/net-standard).

3. Wybierz szablon **Biblioteka klas (.NET Standard)** w prawym okienku i wprowadź **StringLibrary** w polu **tekstowym Nazwa,** jak pokazano na poniższej ilustracji:

   ![Okno dialogowe **Dodaj nowy projekt**](./media/lut-start/add-project-cs.png)

4. Wybierz przycisk **OK**, aby utworzyć projekt.

::: moniker-end

::: moniker range=">=vs-2019"

2. Wpisz **bibliotekę klas** w polu wyszukiwania szablonów, a następnie wybierz szablon **Biblioteka klas (.NET Standard).** Kliknij przycisk **alej**.

   > [!NOTE]
   > Ponieważ nasza biblioteka jest przeznaczona dla platformy .NET Standard, a nie określonej implementacji platformy .NET, można ją wywołać z dowolnej implementacji platformy .NET obsługującej tę wersję programu .NET Standard. Aby uzyskać więcej informacji, zobacz [.NET Standard](/dotnet/standard/net-standard).

3. Nazwij projekt **StringLibrary**.

4. Kliknij **przycisk Utwórz,** aby utworzyć projekt.

::: moniker-end

5. Zastąp cały istniejący kod w oknie kodu następującym kodem:

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   StringLibrary ma trzy metody statyczne:

   - `StartsWithUpper`zwraca, `true` jeśli ciąg zaczyna się od znaku wielkim; w przeciwnym `false`razie zwraca .

   - `StartsWithLower`zwraca, `true` jeśli ciąg zaczyna się od znaku małych liter; w przeciwnym `false`razie zwraca .

   - `HasEmbeddedSpaces`zwraca, `true` jeśli ciąg zawiera osadzony znak odstępu; w przeciwnym `false`razie zwraca .

6. Wybierz **polecenie Kompilacja** > **rozwiązania kompilacji** z menu programu Visual Studio najwyższego poziomu. Kompilacja powinna zakończyć się pomyślnie.

## <a name="create-the-test-project"></a>Tworzenie projektu testowego

Następnym krokiem jest utworzenie projektu testu jednostkowego w celu przetestowania biblioteki StringLibrary. Utwórz testy jednostkowe, wykonując następujące kroki:

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie UtilityLibraries i wybierz pozycję **Dodaj** > **nowy projekt**.

::: moniker range="vs-2017"

2. W oknie dialogowym **Dodawanie nowego projektu** wybierz węzeł C#, a następnie wybierz pozycję **.NET Core**.

   > [!NOTE]
   > Nie trzeba pisać testy jednostkowe w tym samym języku, co biblioteka klas.

3. Wybierz szablon **Projektu testu jednostkowego (net core)** w prawym okienku i wprowadź **StringLibraryTests** w polu **tekstowym Nazwa,** jak pokazano na poniższej ilustracji:

   ![Okno dialogowe **Dodaj nowy projekt** dla projektu testowego jednostki](./media/lut-start/add-unit-test-cs.png)

4. Wybierz przycisk **OK**, aby utworzyć projekt.

::: moniker-end

::: moniker range=">=vs-2019"

2. Wpisz **test jednostkowy** w polu wyszukiwania szablonu i wybierz szablon **Projektu testu jednostkowego (NET Core).** Kliknij przycisk **alej**.

3. Nazwij projekt **StringLibraryTests**.

4. Kliknij **przycisk Utwórz,** aby utworzyć projekt.

::: moniker-end

   > [!NOTE]
   > Ten samouczek wprowadzenie używa live unit testing z MSTest struktury testów. Można również użyć xUnit i NUnit struktur testowych.

5. Projekt testu jednostkowego nie może automatycznie uzyskać dostępu do biblioteki klas, którą testuje. Możesz dać dostęp do biblioteki testowej, dodając odwołanie do projektu biblioteki klas. Aby to zrobić, kliknij `StringLibraryTests` prawym przyciskiem myszy projekt i wybierz polecenie **Dodaj** > **odwołanie**. W oknie dialogowym **Menedżer odwołań** upewnij się, że jest zaznaczona karta **Rozwiązanie,** i wybierz projekt StringLibrary, jak pokazano na poniższej ilustracji.

   ![Okno dialogowe **Reference Manager**](./media/lut-start/add-reference.png)

6. Wymień kod badania jednostki kotłowej dostarczony przez szablon na następujący kod:

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

7. Zapisz projekt, wybierając ikonę **Zapisz** na pasku narzędzi.

8. Ponieważ kod testu jednostkowego zawiera niektóre znaki inne niż ASCII, program Visual Studio wyświetla następujące okno dialogowe, aby ostrzec, że niektóre znaki zostaną utracone, jeśli zapiszesz plik w domyślnym formacie ASCII. Wybierz przycisk **Zapisz z innym kodowaniem.**

   ![Wybieranie kodowania plików](media/lut-start/ascii-encoding.png)

9. Z listy rozwijanej **Kodowanie** okna dialogowego **Opcje zapisywania z wyprzedzeniem** wybierz pozycję **Unicode (UTF-8 bez podpisu) — Strona kodowa 65001**, jak pokazano na poniższej ilustracji:

   ![Wybór kodowania UTF-8](media/lut-start/utf8-encoding.png)

10. Skompiluj projekt testu jednostkowego, wybierając **build** > **rebuild rozwiązanie** z menu programu Visual Studio najwyższego poziomu.

Utworzono bibliotekę klas, a także niektóre testy jednostkowe dla niego. Ukończono już wstępne przygotowania potrzebne do użycia testów jednostkowych na żywo.

## <a name="enable-live-unit-testing"></a>Włącz testowanie jednostek na żywo

Do tej pory, mimo że napisałeś testy biblioteki klas StringLibrary, nie wykonano ich. Testy jednostkowe na żywo wykonuje je automatycznie po włączeniu go. Aby to zrobić, wykonaj następujące czynności:

1. Opcjonalnie wybierz okno kodu, które zawiera kod stringlibrary. Jest to *Class1.cs* dla projektu C# lub *Class1.vb* dla projektu języka Visual Basic. (Ten krok umożliwia wizualną kontrolę wyników testów i zakresu zakresu kodu po włączeniu testowania jednostek na żywo).

1. Wybierz **opcję Test** > **Live Unit Testing** > **Start** z menu programu Visual Studio najwyższego poziomu.

1. Visual Studio uruchamia Live Unit Test, który automatycznie uruchamia wszystkie testy.

Po zakończeniu uruchamiania testów **Eksplorator testów** wyświetla zarówno ogólne wyniki, jak i wyniki poszczególnych testów. Ponadto okno kodu graficznie wyświetla zarówno pokrycie kodu testu i wynik testów. Jak pokazano na poniższej ilustracji, wszystkie trzy testy zostały pomyślnie wykonane. Pokazuje również, że nasze testy objęły `StartsWithUpper` wszystkie ścieżki kodu w metodzie, a wszystkie te testy zostały pomyślnie wykonane (co jest oznaczone zielonym znacznikiem wyboru "✓"). Wreszcie, pokazuje, że żadna z innych metod w StringLibrary mają pokrycie kodu (który jest oznaczony niebieską linią "➖").

![Eksplorator testów i okno kodu po uruchomieniu testowania jednostki aktywnej](media/lut-start/lut-results-cs.png)

Można również uzyskać bardziej szczegółowe informacje na temat pokrycia testu i wyniki testów, wybierając ikonę pokrycia określonego kodu w oknie kodu. Aby zbadać ten szczegół, wykonaj następujące czynności:

1. Kliknij zielony znacznik wyboru w wierszu, który odczytuje `if (String.IsNullOrWhiteSpace(s))` się w metodzie. `StartsWithUpper` Jak pokazano na poniższej ilustracji, live unit testing wskazuje, że trzy testy obejmują ten wiersz kodu i że wszystkie zostały wykonane pomyślnie.

   ![Pokrycie kodu instrukcji warunkowej "if"](media/lut-start/code-coverage-cs1.png)

1. Kliknij zielony znacznik wyboru w wierszu, który odczytuje `return Char.IsUpper(s[0])` się w metodzie. `StartsWithUpper` Jak pokazano na poniższej ilustracji, live unit testing wskazuje, że tylko dwa testy obejmują ten wiersz kodu i że wszystkie zostały wykonane pomyślnie.

   ![Pokrycie kodu instrukcji zwrotu](media/lut-start/code-coverage-cs2.png)

Głównym problemem, który identyfikuje live unit testing jest niepełne pokrycie kodu. Zajmiesz się tym w następnej sekcji.

## <a name="expand-test-coverage"></a>Zwiększ zasięg testu

W tej sekcji rozszerzysz testy `StartsWithLower` jednostkowe do metody. Podczas wykonywania tej funkcji testowanie jednostek na żywo będzie dynamicznie nadal testować kod.

Aby rozszerzyć zakres `StartsWithLower` kodu na metodę, wykonaj następujące czynności:

1. Dodaj następujące `TestStartsWithLower` `TestDoesNotStartWithLower` metody do pliku kodu źródłowego testu projektu:

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. Zmodyfikuj `DirectCallWithNullOrEmpty` metodę, dodając następujący [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) kod natychmiast po wywołaniu metody.

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

1. Live Unit Testing automatycznie wykonuje nowe i zmodyfikowane testy podczas modyfikowania kodu źródłowego. Jak pokazano na poniższej ilustracji **Eksploratora testów,** wszystkie testy, w tym dwa dodane i zmodyfikowane, powiodły się.

   ![Eksplorator testów po rozszerzeniu zakresu testu](media/lut-start/test-dynamic.png)

1. Przełącz się do okna, które zawiera kod źródłowy dla StringLibrary klasy. Live Unit Testing pokazuje teraz, że nasz `StartsWithLower` zakres kodu został rozszerzony na metodę.

    ![Pokrycie kodu dla Metody StartsWithLower](media/lut-start/lut-extended-cs.png)

W niektórych przypadkach pomyślne testy w **Eksploratorze testów** mogą być wyszarzone. Oznacza to, że test jest obecnie wykonywany lub że test nie został uruchomiony ponownie, ponieważ nie było żadnych zmian kodu, które mogłyby mieć wpływ na test, ponieważ został ostatnio wykonany.

Do tej pory wszystkie nasze testy zakończyły się sukcesem. W następnej sekcji zbadamy, jak można obsługiwać błąd testu.

## <a name="handle-a-test-failure"></a>Obsługa błędu testu

W tej sekcji dowiesz się, jak za pomocą live unit testing do identyfikowania, rozwiązywania problemów i rozwiązywania błędów testów. Zrobisz to, rozszerzając zakres testu `HasEmbeddedSpaces` do metody.

1. Dodaj następującą metodę do pliku testowego:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

1. Po wykonaniu testu, live unit testing `TestHasEmbeddedSpaces` wskazuje, że metoda nie powiodła się, jak pokazano na poniższej ilustracji:

   ![Eksplorator testów zgłaszacy nieudany test](media/lut-start/test-failure.png)

1. Wybierz okno, w które wyświetla kod biblioteki. Live Unit Testing rozszerzył zakres `HasEmbeddedSpaces` kodu do metody. Zgłasza również błąd testu, dodając🞩czerwony " " do wierszy objętych niepowodzeniem testów.

1. Umieść wskaźnik myszy `HasEmbeddedSpaces` na wierszu z podpisem metody. Live Unit Testing wyświetla etykietkę narzędzia, która informuje, że metoda jest objęta jednym testem, jak pokazano na poniższej ilustracji:

   ![Informacje o testach jednostkowych na żywo w nieudanym teście](media/lut-start/test-failure-info-cs.png)

1. Wybierz test **TestHasEmbeddedSpaces.** Live Unit Testing oferuje szereg opcji, takich jak uruchamianie wszystkich testów, uruchamianie wybranych testów, debugowanie wszystkich testów i debugowanie wybranych testów, jak pokazano na poniższej ilustracji:

   ![Opcje testowania jednostek na żywo dla testu nie powiodło się](media/lut-start/test-failure-options.png)

1. Wybierz **opcję Debugowanie wybrane,** aby debugować test nie powiódł się.

1. Visual Studio wykonuje test w trybie debugowania.

   Test przypisuje każdy ciąg w tablicy `phrase` do zmiennej `HasEmbeddedSpaces` o nazwie i przekazuje go do metody. Wykonanie programu wstrzymuje i wywołuje debuger `false`przy pierwszym wywołaniu assert. Okno dialogowe wyjątku, które [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) wynika z nieoczekiwanej wartości w wywołaniu metody jest wyświetlany na poniższej ilustracji.

   ![Okno dialogowe wyjątku testowania jednostek na żywo](media/lut-start/exception-dialog-cs.png)

   Ponadto wszystkie narzędzia debugowania, które udostępnia program Visual Studio są dostępne, aby pomóc nam w rozwiązywaniu problemów z naszym nieudanym testem, jak pokazano na poniższej ilustracji:

   ![Narzędzia debugowania programu Visual Studio](media/lut-start/debugging-tools-cs.png)

   W oknie **Autos** należy zauważyć, `phrase` że wartością zmiennej jest "Name\tDescription", która jest drugim elementem tablicy. Metoda testowa `HasEmbeddedSpaces` oczekuje, `true` że powróci po przekazaniu tego ciągu; zamiast tego zwraca `false`. Widocznie nie rozpoznaje "\t", znaku karty, jako osadzonej przestrzeni.

1. Wybierz opcję > **Debuguj kontynuuj**, naciśnij **klawisz F5**lub kliknij przycisk **Kontynuuj** na pasku narzędzi, aby kontynuować wykonywanie programu testowego. **Debug** Ponieważ wystąpił nieobsługiowany wyjątek, test kończy się.
Zapewnia to wystarczające informacje do wstępnego dochodzenia w sprawie błędu. Albo `TestHasEmbeddedSpaces` (procedura testowa) wykonane nieprawidłowe `HasEmbeddedSpaces` założenie lub nie poprawnie rozpoznać wszystkie osadzone spacje.

1. Aby zdiagnozować i rozwiązać problem, zacznij od `StringLibrary.HasEmbeddedSpaces` metody. Spójrz na porównanie `HasEmbeddedSpaces` w metodzie. Uważa, że osadzona przestrzeń jest U + 0020. Jednak Standard Unicode zawiera wiele innych znaków spacji. Sugeruje to, że kod biblioteki niepoprawnie przetestowane dla znaku odstępu.

1. Zastąp porównanie równości <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> wywołaniem metody:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. Live Unit Testing automatycznie ponownie przeprowadza nieudaną metodę testową i aktualizuje wyniki w oknie kodu i w **Eksploratorze testów**, jak pokazano na poniższej ilustracji:

    ![Udany test HasEmbeddedSpaces](media/lut-start/test-success-cs.png)

## <a name="see-also"></a>Zobacz też

- [Testowanie jednostek na żywo w programie Visual Studio](live-unit-testing.md)
- [Testy jednostek na żywo Często zadawane pytania](live-unit-testing-faq.md)
