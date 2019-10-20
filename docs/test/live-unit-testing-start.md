---
title: Dowiedz się, jak testować kod za pomocą testów jednostkowych na żywo
ms.date: 08/31/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a5b136c91873c0af60705ea361a19e53f28e06b0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653056"
---
# <a name="get-started-with-live-unit-testing"></a>Rozpoczynanie pracy z funkcją Live Unit Testing

Włączenie Live Unit Testing w rozwiązaniu programu Visual Studio wizualne przedstawia pokrycie testów i stan testów. Live Unit Testing również dynamicznie wykonuje testy za każdym razem, gdy modyfikujesz kod i natychmiast powiadomimy, gdy zmiany powodują niepowodzenie testów.

Live Unit Testing może służyć do testowania rozwiązań przeznaczonych dla .NET Framework lub .NET Core. W ramach tego samouczka nauczysz się używać Live Unit Testing przez utworzenie prostej biblioteki klas, która jest przeznaczona dla .NET Standard, i utworzysz projekt MSTest, który jest przeznaczony dla platformy .NET Core w celu przetestowania.

Kompletne C# rozwiązanie można pobrać z repozytorium [MicrosoftDocs/VisualStudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) w witrynie GitHub.

## <a name="prerequisites"></a>Wymagania wstępne

Ten samouczek wymaga zainstalowania wersji Visual Studio Enterprise z użyciem obciążenia **międzyplatformowego dla platformy .NET Core** .

## <a name="create-the-solution-and-the-class-library-project"></a>Utwórz rozwiązanie i projekt biblioteki klas

Zacznij od utworzenia rozwiązania programu Visual Studio o nazwie UtilityLibraries, które składa się z pojedynczego projektu biblioteki klas .NET Standard, StringLibrary.

Rozwiązanie to tylko kontener dla jednego lub wielu projektów. Aby utworzyć puste rozwiązanie, Otwórz program Visual Studio i wykonaj następujące czynności:

1. Wybierz pozycję **plik**  > **Nowy**  > **projekt** z menu programu Visual Studio najwyższego poziomu.

1. Wpisz **rozwiązanie** w polu wyszukiwania szablonu, a następnie wybierz szablon **pustego rozwiązania** .

   ::: moniker range="vs-2017"

   ![Okno dialogowe * * Nowy projekt * *](./media/lut-start/new-solution.png)

   ::: moniker-end

1. Zakończ tworzenie rozwiązania.

Teraz, po utworzeniu rozwiązania, utworzysz bibliotekę klas o nazwie StringLibrary, która zawiera szereg metod rozszerzających do pracy z ciągami.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie UtilityLibraries i wybierz pozycję **Dodaj**  > **Nowy projekt**.

::: moniker range="vs-2017"

2. W oknie dialogowym **Dodaj nowy projekt** wybierz C# węzeł, a następnie wybierz pozycję **.NET Standard**.

   > [!NOTE]
   > Ponieważ nasza biblioteka jest przeznaczona .NET Standard, a nie do konkretnej implementacji platformy .NET, można ją wywołać z dowolnej implementacji platformy .NET, która obsługuje tę wersję programu .NET Standard. Aby uzyskać więcej informacji, zobacz [.NET Standard](/dotnet/standard/net-standard).

3. Wybierz szablon **Biblioteka klas (.NET standard)** w okienku po prawej stronie, a następnie wprowadź **StringLibrary** w polu tekstowym **Nazwa** , jak pokazano na poniższej ilustracji:

   ![Okno dialogowe Dodaj nowy projekt * *](./media/lut-start/add-project-cs.png)

4. Wybierz **przycisk OK** , aby utworzyć projekt.

::: moniker-end

::: moniker range=">=vs-2019"

2. Wpisz **Biblioteka klas** w polu wyszukiwania szablonu i szablon wybierz **bibliotekę klas (.NET standard)** . Kliknij przycisk **Dalej**.

   > [!NOTE]
   > Ponieważ nasza biblioteka jest przeznaczona .NET Standard, a nie do konkretnej implementacji platformy .NET, można ją wywołać z dowolnej implementacji platformy .NET, która obsługuje tę wersję programu .NET Standard. Aby uzyskać więcej informacji, zobacz [.NET Standard](/dotnet/standard/net-standard).

3. Nazwij projekt **StringLibrary**.

4. Kliknij przycisk **Utwórz** , aby utworzyć projekt.

::: moniker-end

5. Zamień cały istniejący kod w oknie kodu na następujący kod:

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   StringLibrary ma trzy metody statyczne:

   - `StartsWithUpper` zwraca `true`, jeśli ciąg rozpoczyna się od znaku wielką literą; w przeciwnym razie zwraca `false`.

   - `StartsWithLower`returns `true`, jeśli ciąg rozpoczyna się od małej litery; w przeciwnym razie zwraca `false`.

   - `HasEmbeddedSpaces` zwraca `true`, jeśli ciąg zawiera osadzony znak odstępu; w przeciwnym razie zwraca `false`.

6. Wybierz opcję **kompiluj**  > **Kompiluj rozwiązanie** z menu programu Visual Studio najwyższego poziomu. Kompilacja powinna zakończyć się powodzeniem.

## <a name="create-the-test-project"></a>Tworzenie projektu testowego

Następnym krokiem jest utworzenie projektu testów jednostkowych w celu przetestowania biblioteki StringLibrary. Utwórz testy jednostkowe, wykonując następujące czynności:

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie UtilityLibraries i wybierz pozycję **Dodaj**  > **Nowy projekt**.

::: moniker range="vs-2017"

2. W oknie dialogowym **Dodaj nowy projekt** wybierz C# węzeł, a następnie wybierz pozycję **.NET Core**.

   > [!NOTE]
   > Nie musisz pisać testów jednostkowych w tym samym języku co Biblioteka klas.

3. Wybierz szablon **projekt testów jednostkowych (.NET Core)** w okienku po prawej stronie, a następnie wprowadź **StringLibraryTests** w polu tekstowym **Nazwa** , jak pokazano na poniższej ilustracji:

   ![Okno dialogowe programu * * Dodawanie nowego projektu * * dla projektu testów jednostkowych](./media/lut-start/add-unit-test-cs.png)

4. Wybierz **przycisk OK** , aby utworzyć projekt.

::: moniker-end

::: moniker range=">=vs-2019"

2. Wpisz **test jednostkowy** w polu wyszukiwania szablonu, a następnie wybierz szablon **projekt testów jednostkowych (.NET Core)** . Kliknij przycisk **Dalej**.

3. Nazwij projekt **StringLibraryTests**.

4. Kliknij przycisk **Utwórz** , aby utworzyć projekt.

::: moniker-end

   > [!NOTE]
   > Ten samouczek wprowadzający używa Live Unit Testing z platformą testową MSTest. Można również użyć platform testowych xUnit i NUnit.

5. Projekt testu jednostkowego nie może automatycznie uzyskać dostępu do biblioteki klas, która jest testowana. Możesz nadać dostęp do biblioteki testowej, dodając odwołanie do projektu biblioteki klas. Aby to zrobić, kliknij prawym przyciskiem myszy projekt `StringLibraryTests` i wybierz polecenie **dodaj**  > **odwołanie**. W oknie dialogowym **Menedżer odwołań** upewnij się, że karta **rozwiązanie** jest zaznaczona, a następnie wybierz projekt StringLibrary, jak pokazano na poniższej ilustracji.

   ![Okno dialogowe * * odwołanie Manager * *](./media/lut-start/add-reference.png)

6. Zastąp standardowy kod testu jednostkowego dostarczony przez szablon następującym kodem:

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

7. Zapisz projekt, wybierając ikonę **Zapisz** na pasku narzędzi.

8. Ponieważ kod testu jednostkowego zawiera niektóre znaki inne niż ASCII, program Visual Studio wyświetla następujące okno dialogowe, aby ostrzec o utracie niektórych znaków, jeśli zapiszesz plik w domyślnym formacie ASCII. Wybierz przycisk **Zapisz z innym kodowaniem** .

   ![Wybierz Kodowanie pliku](media/lut-start/ascii-encoding.png)

9. Na liście rozwijanej **kodowanie** w oknie dialogowym **Opcje zapisu zaawansowanego** wybierz opcję **Unicode (UTF-8 bez podpisu)-strona kodowa 65001**, jak pokazano na poniższej ilustracji:

   ![Wybieranie kodowania UTF-8](media/lut-start/utf8-encoding.png)

10. Kompiluj projekt testu jednostkowego, wybierając pozycję **kompilacja**  > **Skompiluj ponownie rozwiązanie** z menu programu Visual Studio najwyższego poziomu.

Utworzono bibliotekę klas, a także niektóre testy jednostkowe. Zakończono już czynności wstępne potrzebne do korzystania z Live Unit Testing.

## <a name="enable-live-unit-testing"></a>Włącz Live Unit Testing

Do tej pory mimo że Zapisano testy dla biblioteki klas StringLibrary, nie zostały one wykonane. Live Unit Testing wykonuje je automatycznie po jej włączeniu. Aby to zrobić, wykonaj następujące czynności:

1. Opcjonalnie wybierz okno kod, które zawiera kod dla StringLibrary. Jest to *Class1.cs* dla C# projektu lub *Class1. vb* dla projektu Visual Basic. (Ten krok pozwala wizualnie zbadać wynik testów i zakres pokrycia kodu po włączeniu Live Unit Testing).

1. Wybierz pozycję **testuj**  > **Live Unit Testing**  > **Rozpocznij** od menu programu Visual Studio najwyższego poziomu.

1. Program Visual Studio uruchamia test jednostkowy na żywo, który automatycznie uruchamia wszystkie testy.

Po zakończeniu wykonywania testów w **Eksploratorze testów** są wyświetlane zarówno wyniki ogólne, jak i wynik poszczególnych testów. Ponadto okno kod wyświetla graficznie zarówno pokrycie kodu testu, jak i wynik dla testów. Jak pokazano na poniższym obrazie, wszystkie trzy testy zostały wykonane pomyślnie. Pokazuje również, że nasze testy pokryte wszystkie ścieżki kodu w metodzie `StartsWithUpper` i wszystkie testy wykonane pomyślnie (które są wskazywane przez zielony znacznik wyboru "✓"). Na koniec pokazuje, że żadna z innych metod w StringLibrary nie ma pokrycia kodu (który jest wskazywany przez niebieską linię "➖").

![Eksplorator testów i okno kodu po rozpoczęciu testów jednostkowych na żywo](media/lut-start/lut-results-cs.png)

Możesz również uzyskać bardziej szczegółowe informacje na temat pokrycia testów i wyników testów, wybierając konkretną ikonę pokrycia kodu w oknie kod. Aby przejrzeć te szczegóły, wykonaj następujące czynności:

1. Kliknij zielony znacznik wyboru w wierszu, który odczytuje `if (String.IsNullOrWhiteSpace(s))` w `StartsWithUpper` metodzie. Jak widać na poniższej ilustracji, Live Unit Testing wskazuje, że trzy testy pokrywają ten wiersz kodu i że wszystkie zostały wykonane pomyślnie.

   ![Pokrycie kodu dla instrukcji warunkowej "If"](media/lut-start/code-coverage-cs1.png)

1. Kliknij zielony znacznik wyboru w wierszu, który odczytuje `return Char.IsUpper(s[0])` w `StartsWithUpper` metodzie. Jak widać na poniższej ilustracji, Live Unit Testing wskazuje, że tylko dwa testy obejmują ten wiersz kodu, a wszystkie wykonane pomyślnie.

   ![Pokrycie kodu dla instrukcji return](media/lut-start/code-coverage-cs2.png)

Głównym problemem, który Live Unit Testing identyfikuje, jest niepełne pokrycie kodu. Podasz ten adres w następnej sekcji.

## <a name="expand-test-coverage"></a>Rozwiń pokrycie testu

W tej sekcji rozszerzy testy jednostkowe na metodę `StartsWithLower`. Gdy to zrobisz, Live Unit Testing będzie dynamicznie kontynuować testowanie kodu.

Aby zwiększyć pokrycie kodu do metody `StartsWithLower`, wykonaj następujące czynności:

1. Dodaj następujące `TestStartsWithLower` i metody `TestDoesNotStartWithLower` do pliku kodu źródłowego testu projektu:

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. Zmodyfikuj metodę `DirectCallWithNullOrEmpty`, dodając następujący kod bezpośrednio po wywołaniu metody [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) .

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

1. Live Unit Testing automatycznie wykonuje nowe i zmodyfikowane testy podczas modyfikacji kodu źródłowego. Zgodnie z poniższą ilustracją programu **Test Explorer** wszystkie testy, w tym dodawane dwa i te, które zostały zmodyfikowane, zakończyły się powodzeniem.

   ![Eksplorator testów po rozwinięciu pokrycia testu](media/lut-start/test-dynamic.png)

1. Przejdź do okna, które zawiera kod źródłowy dla klasy StringLibrary. Live Unit Testing teraz pokazuje, że nasze pokrycie kodu jest rozszerzone do metody `StartsWithLower`.

    ![Pokrycie kodu dla metody StartsWithLower](media/lut-start/lut-extended-cs.png)

W niektórych przypadkach pomyślne testy w **Eksploratorze testów** mogą być wyszarzone. Oznacza to, że test jest aktualnie wykonywany lub że test nie został uruchomiony ponownie, ponieważ nie wprowadzono żadnych zmian w kodzie, które mogłyby mieć wpływ na test od momentu jego ostatniego wykonania.

Do tej pory wszystkie nasze testy zakończyły się powodzeniem. W następnej sekcji sprawdzimy, jak można obsłużyć niepowodzenie testu.

## <a name="handle-a-test-failure"></a>Obsługuj niepowodzenie testu

W tej sekcji dowiesz się, jak używać Live Unit Testing do identyfikowania, rozwiązywania problemów i testowania błędów testów. Można to zrobić przez zwiększenie pokrycia testu do metody `HasEmbeddedSpaces`.

1. Dodaj następującą metodę do pliku testowego:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

1. Gdy test zostanie wykonany, Live Unit Testing wskazuje, że metoda `TestHasEmbeddedSpaces` nie zakończyła się niepowodzeniem, jak pokazano na poniższym obrazie:

   ![Eksplorator testów zgłasza test zakończony niepowodzeniem](media/lut-start/test-failure.png)

1. Wybierz okno, w którym jest wyświetlany kod biblioteki. Live Unit Testing ma rozwinięte pokrycie kodu dla metody `HasEmbeddedSpaces`. Zgłasza również niepowodzenie testu poprzez dodanie czerwonego "🞩" do linii objętych niepowodzeniem testów.

1. Umieść kursor nad wierszem za pomocą sygnatury metody `HasEmbeddedSpaces`. Live Unit Testing wyświetla etykietkę narzędzia, która zgłasza, że metoda jest objęta jednym testem, jak pokazano na poniższej ilustracji:

   ![Live Unit Testing informacji na testach zakończonych niepowodzeniem](media/lut-start/test-failure-info-cs.png)

1. Wybierz test **TestHasEmbeddedSpaces** zakończony niepowodzeniem. Live Unit Testing udostępnia wiele opcji, takich jak uruchamianie wszystkich testów, uruchamianie wybranych testów, debugowanie wszystkich testów i debugowanie wybranych testów, jak pokazano na poniższej ilustracji:

   ![Opcje Live Unit Testing dla testu zakończonego niepowodzeniem](media/lut-start/test-failure-options.png)

1. Wybierz pozycję **Debuguj zaznaczone** , aby debugować test zakończony niepowodzeniem.

1. Program Visual Studio wykonuje test w trybie debugowania.

   Test przypisuje każdy ciąg w tablicy do zmiennej o nazwie `phrase` i przekazuje ją do metody `HasEmbeddedSpaces`. Wykonywanie programu jest wstrzymywane i wywołuje debuger przy pierwszym `false` wyrażenia potwierdzenia. Na poniższej ilustracji przedstawiono okno dialogowe wyjątku, które wynika z nieoczekiwanej wartości w wywołaniu metody [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) .

   ![Okno dialogowe wyjątku Live Unit Testing](media/lut-start/exception-dialog-cs.png)

   Ponadto wszystkie narzędzia debugowania udostępniane przez program Visual Studio są dostępne, aby pomóc nam w rozwiązywaniu problemów z testem zakończonym niepowodzeniem, jak pokazano na poniższej ilustracji:

   ![Narzędzia debugowania programu Visual Studio](media/lut-start/debugging-tools-cs.png)

   Zwróć uwagę, że w oknie **samochody** wartość zmiennej `phrase` jest "Name\tDescription", która jest drugim elementem tablicy. Metoda testowa oczekuje, że `HasEmbeddedSpaces` zwrócić `true`, gdy przeszedł ten ciąg; Zamiast tego zwraca `false`. W oczywisty sposób nie rozpoznaje "\t" znaku tabulacji jako obszaru osadzonego.

1. Wybierz pozycję **debuguj**  > **kontynuować**, naciśnij klawisz **F5**lub kliknij przycisk **Kontynuuj** na pasku narzędzi, aby kontynuować wykonywanie programu testowego. Ponieważ wystąpił nieobsługiwany wyjątek, test zakończy się.
Zapewnia to wystarczającą ilość informacji na potrzeby wstępnego badania błędu. Każda `TestHasEmbeddedSpaces` (procedura testowa) wprowadziła nieprawidłowe założenie lub `HasEmbeddedSpaces` nie rozpoznaje prawidłowo wszystkich osadzonych miejsc.

1. Aby zdiagnozować i rozwiązać ten problem, Zacznij od metody `StringLibrary.HasEmbeddedSpaces`. Przyjrzyj się porównaniu w `HasEmbeddedSpaces` metodzie. Uważa, że przestrzeń osadzona ma być U + 0020. Standard Unicode zawiera jednak kilka innych znaków spacji. Sugeruje to, że kod biblioteki został niepoprawnie przetestowany pod kątem znaku odstępu.

1. Zastąp porównanie równości wywołaniem metody <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName>:

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. Live Unit Testing automatycznie ponownie uruchamia nieudaną metodę testową i aktualizuje wyniki w oknie kodu i w **Eksploratorze testów**, jak pokazano na poniższej ilustracji:

    ![Pomyślne testowanie HasEmbeddedSpaces](media/lut-start/test-success-cs.png)

## <a name="see-also"></a>Zobacz także

- [Live Unit Testing w programie Visual Studio](live-unit-testing.md)
- [Live Unit Testing często zadawane pytania](live-unit-testing-faq.md)