---
title: Dowiedz się, jak testować kod za pomocą testu jednostkowego na żywo
description: Dowiedz się, jak używać Live Unit Testing, tworząc prostą bibliotekę klas, która jest .NET Standard i tworzenie projektu MSTest, który jest przeznaczony dla programu .NET Core w celu jej przetestowania.
ms.custom: SEO-VS-2020
ms.date: 04/03/2020
ms.topic: how-to
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 2270216e7245f20d26df580ad90dc627319adcc1
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798638"
---
# <a name="get-started-with-live-unit-testing"></a>Rozpoczynanie pracy z funkcją Live Unit Testing

Włączenie Live Unit Testing w Visual Studio danych wizualnie przedstawia pokrycie testów i stan testów. Live Unit Testing również dynamicznie wykonuje testy za każdym razem, gdy modyfikujesz kod, i natychmiast powiadamia, gdy zmiany powodują niepowodzenie testów.

Live Unit Testing można używać do testowania rozwiązań, które są .NET Framework lub .NET Core. W tym samouczku dowiesz się, jak używać programu Live Unit Testing, tworząc prostą bibliotekę klas, która jest przeznaczony dla programu .NET Standard, oraz utworzysz projekt MSTest przeznaczony dla programu .NET Core w celu przetestowania go.

Kompletne rozwiązanie w języku C# można pobrać z repozytorium [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) w witrynie GitHub.

## <a name="prerequisites"></a>Wymagania wstępne

Ten samouczek wymaga zainstalowania wersji Visual Studio Enterprise z międzyplatformowym obciążeniem **programistyki platformy .NET Core.**

## <a name="create-the-solution-and-the-class-library-project"></a>Tworzenie rozwiązania i projektu biblioteki klas

Rozpocznij od utworzenia rozwiązania Visual Studio o nazwie UtilityLibraries, które składa się z jednego projektu biblioteki klas .NET Standard, StringLibrary.

Rozwiązanie jest po prostu kontenerem dla co najmniej jednego projektu. Aby utworzyć puste rozwiązanie, otwórz Visual Studio i wykonaj następujące czynności:

1. Wybierz **pozycję**  >  **File New** Project  >  **(Nowy** projekt pliku) z menu Visual Studio najwyższego poziomu.

1. Wpisz **solution** w polu wyszukiwania szablonu, a następnie wybierz szablon **Puste** rozwiązanie. Nadaj **projektowi nazwę UtilityLibraries**.

   ::: moniker range="vs-2017"

   ![Okno dialogowe **Nowy projekt**](./media/lut-start/new-solution.png)

   ::: moniker-end

1. Zakończ tworzenie rozwiązania.

Teraz, po utworzeniu rozwiązania, utworzysz bibliotekę klas o nazwie StringLibrary, która zawiera wiele metod rozszerzeń do pracy z ciągami.

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy rozwiązanie UtilityLibraries i wybierz **polecenie Dodaj** nowy  >  **projekt.**

::: moniker range="vs-2017"

2. W **oknie dialogowym Dodawanie nowego** projektu wybierz węzeł C#, a następnie wybierz **pozycję .NET Standard**.

   > [!NOTE]
   > Ponieważ nasza biblioteka jest .NET Standard a nie określonej implementacji .NET, można ją nazwać z dowolnej implementacji .NET, która obsługuje tę wersję .NET Standard. Aby uzyskać więcej informacji, [zobacz .NET Standard](/dotnet/standard/net-standard).

3. Wybierz szablon **Biblioteka klas (.NET Standard)** w okienku po prawej stronie,  a następnie wprowadź **ciąg StringLibrary** w polu tekstowym Nazwa, jak pokazano na poniższej ilustracji:

   ![Okno dialogowe **Dodawanie nowego projektu**](./media/lut-start/add-project-cs.png)

4. Wybierz przycisk **OK**, aby utworzyć projekt.

::: moniker-end

::: moniker range=">=vs-2019"

2. Wpisz **bibliotekę klas** w polu wyszukiwania szablonu, a następnie wybierz szablon Biblioteka klas **(.NET Standard).** Kliknij przycisk **Dalej**.

   > [!NOTE]
   > Ponieważ nasza biblioteka jest .NET Standard a nie określonej implementacji .NET, można ją nazwać z dowolnej implementacji .NET, która obsługuje tę wersję .NET Standard. Aby uzyskać więcej informacji, [zobacz .NET Standard](/dotnet/standard/net-standard).

3. Nadaj **projektowi nazwę StringLibrary**.

4. Kliknij **pozycję Utwórz,** aby utworzyć projekt.

::: moniker-end

5. Zastąp cały istniejący kod w edytorze kodu następującym kodem:

   ```csharp
   using System;

   namespace UtilityLibraries
   {
       public static class StringLibrary
       {
           public static bool StartsWithUpper(this string s)
           {
               if (String.IsNullOrWhiteSpace(s))
                   return false;

               return Char.IsUpper(s[0]);
           }

           public static bool StartsWithLower(this string s)
           {
               if (String.IsNullOrWhiteSpace(s))
                   return false;

               return Char.IsLower(s[0]);
           }

           public static bool HasEmbeddedSpaces(this string s)
           {
               foreach (var ch in s.Trim())
               {
                   if (ch == ' ')
                       return true;
               }
               return false;
           }
       }
   }
   ```

   StringLibrary ma trzy metody statyczne:

   - `StartsWithUpper` Zwraca `true` wartość , jeśli ciąg zaczyna się od wielkich liter; w przeciwnym razie zwraca wartość `false` .

   - `StartsWithLower`Zwraca wartość , jeśli ciąg zaczyna się od małej litery; w przeciwnym razie `true` zwraca wartość `false` .

   - `HasEmbeddedSpaces` Zwraca `true` wartość , jeśli ciąg zawiera osadzony znak odstępu; w przeciwnym razie zwraca wartość `false` .

6. Wybierz **pozycję Build** Build Solution (Skompilowanie rozwiązania do kompilacji) z menu Visual Studio  >   najwyższego poziomu. Kompilacja powinna zakończyć się pomyślnie.

## <a name="create-the-test-project"></a>Tworzenie projektu testowego

Następnym krokiem jest utworzenie projektu testu jednostkowego w celu przetestowania biblioteki StringLibrary. Utwórz testy jednostkowe, wykonując następujące kroki:

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy rozwiązanie UtilityLibraries i wybierz **polecenie Dodaj** nowy  >  **projekt.**

::: moniker range="vs-2017"

2. W **oknie dialogowym Dodawanie nowego** projektu wybierz węzeł C#, a następnie wybierz **pozycję .NET Core.**

   > [!NOTE]
   > Nie trzeba pisać testów jednostkowych w tym samym języku co biblioteka klas.

3. Wybierz szablon **Unit Test Project (.NET Core) w** okienku po prawej  stronie, a następnie wprowadź **ciąg StringLibraryTests** w polu tekstowym Nazwa, jak pokazano na poniższej ilustracji:

   ![Okno dialogowe **Dodawanie nowego projektu** dla projektu testu jednostkowego](./media/lut-start/add-unit-test-cs.png)

4. Wybierz przycisk **OK**, aby utworzyć projekt.

   > [!NOTE]
   > W tym samouczku z wprowadzeniem Live Unit Testing z platformą testową MSTest. Można również użyć platform testowych xUnit i NUnit.

::: moniker-end

::: moniker range=">=vs-2019"

2. Wpisz **test jednostkowy** w polu wyszukiwania szablonu, wybierz **język C#,** a następnie wybierz szablon **Projekt testu jednostkowego** dla programu .NET Core. Kliknij przycisk **Dalej**.

   > [!NOTE]
   > Począwszy od Visual Studio 2019 r. w wersji 16.9 nazwa szablonu projektu MSTest zmieniła się z **MSTest Unit Test Project (.NET Core)** na **Unit Test Project**.

3. Nadaj **projektowi nazwę StringLibraryTests i** kliknij przycisk **Next (Dalej).**

4. Wybierz zalecaną platformę docelową (.NET Core 3.1) lub .NET 5, a następnie wybierz pozycję **Utwórz.**

   > [!NOTE]
   > W tym samouczku z wprowadzeniem Live Unit Testing z platformą testową MSTest. Można również użyć platform testowych xUnit i NUnit.

::: moniker-end

5. Projekt testu jednostkowego nie może automatycznie uzyskać dostępu do testowej biblioteki klas. Dostęp do biblioteki testowej można udzielić, dodając odwołanie do projektu biblioteki klas. W tym celu kliknij prawym przyciskiem myszy projekt `StringLibraryTests` i wybierz polecenie Dodaj   >  **odwołanie**. W **oknie dialogowym Menedżer**  odwoływać się upewnij się, że wybrano kartę Rozwiązanie, a następnie wybierz projekt StringLibrary, jak pokazano na poniższej ilustracji.

   ![Okno dialogowe **Menedżer odów**](./media/lut-start/add-reference.png)

6. Zastąp kod testu jednostkowego podany w szablonie następującym kodem:

   ```csharp
   using System;
   using Microsoft.VisualStudio.TestTools.UnitTesting;
   using UtilityLibraries;

   namespace StringLibraryTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestStartsWithUpper()
           {
               // Tests that we expect to return true.
               string[] words = { "Alphabet", "Zebra", "ABC", "Αθήνα", "Москва" };
               foreach (var word in words)
               {
                   bool result = word.StartsWithUpper();
                   Assert.IsTrue(result,
                                 $"Expected for '{word}': true; Actual: {result}");
               }
           }

           [TestMethod]
           public void TestDoesNotStartWithUpper()
           {
               // Tests that we expect to return false.
               string[] words = { "alphabet", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                                  "1234", ".", ";", " " };
               foreach (var word in words)
               {
                   bool result = word.StartsWithUpper();
                   Assert.IsFalse(result,
                                  $"Expected for '{word}': false; Actual: {result}");
               }
           }

           [TestMethod]
           public void DirectCallWithNullOrEmpty()
           {
               // Tests that we expect to return false.
               string[] words = { String.Empty, null };
               foreach (var word in words)
               {
                   bool result = StringLibrary.StartsWithUpper(word);
                   Assert.IsFalse(result,
                                  $"Expected for '{(word == null ? "<null>" : word)}': " +
                                  $"false; Actual: {result}");
               }
           }
       }
   }
   ```

7. Zapisz projekt, wybierając **ikonę Zapisz** na pasku narzędzi.

   Ponieważ kod testu jednostkowego zawiera znaki inne niż ASCII, zostanie wyświetlone następujące okno dialogowe z ostrzeżeniem, że niektóre znaki zostaną utracone w przypadku zapisania pliku w domyślnym formacie ASCII.

8. Wybierz przycisk **Zapisz z innym kodowaniem.**

   ![Wybieranie kodowania pliku](media/lut-start/ascii-encoding.png)

9. Na **liście rozwijanej** Kodowanie  okna dialogowego Zaawansowane opcje zapisywania wybierz pozycję **Unicode (UTF-8 bez podpisu) — Codepage 65001,** jak pokazano na poniższej ilustracji:

   ![Wybieranie kodowania UTF-8](media/lut-start/utf8-encoding.png)

10. Skompiluj projekt testu jednostkowego, wybierając pozycję **Kompiluj** ponownie rozwiązanie z menu Visual Studio  >   najwyższego poziomu.

Utworzono bibliotekę klas, a także kilka testów jednostkowych dla tej biblioteki. Ukończono wstępne informacje potrzebne do korzystania z Live Unit Testing.

## <a name="enable-live-unit-testing"></a>Włącz Live Unit Testing

Do tej pory, mimo że zostały napisane testy dla biblioteki klas StringLibrary, nie zostały wykonane. Live Unit Testing są automatycznie wykonywane po włączeniu. W tym celu wykonaj następujące czynności:

1. Opcjonalnie wybierz okno edytora kodu zawierające kod dla stringLibrary. Jest to klasa *Class1.cs* dla projektu języka C# lub *Klasa1.vb* dla Visual Basic projektu. (Ten krok umożliwia wizualne sprawdzenie wyniku testów i zakresu pokrycia kodu po włączeniu funkcji Live Unit Testing).

1. Wybierz **pozycję** Live Unit Testing Start z menu Visual Studio  >    >   najwyższego poziomu.

1. Visual Studio test jednostkowy na żywo, który automatycznie uruchamia wszystkie testy.

::: moniker range="vs-2017"
Po zakończeniu uruchamiania testów Eksplorator **testów** wyświetla zarówno ogólne wyniki, jak i wyniki poszczególnych testów. Ponadto okno edytora kodu wyświetla graficznie zarówno pokrycie kodu testowego, jak i wynik testów. Jak pokazano na poniższej ilustracji, wszystkie trzy testy zostały wykonane pomyślnie. Pokazuje również, że nasze testy obejmowały wszystkie ścieżki kodu w metodzie i wszystkie te testy zostały wykonane pomyślnie (co jest oznaczone zielonym znakiem wyboru `StartsWithUpper` "";"). Na koniec pokazuje, że żadna z innych metod w stringLibrary nie ma pokrycia kodu (co jest oznaczone niebieską linią "➖").

![Okno Eksplorator testów i edytor kodu po rozpoczęciu testów jednostkowych na żywo](media/lut-start/lut-results-cs.png)
::: moniker-end
::: moniker range=">=vs-2019&quot;
Po zakończeniu uruchamiania testów **Live Unit Testing** zarówno ogólne wyniki, jak i wyniki poszczególnych testów. Ponadto w oknie edytora kodu są wyświetlane graficznie zarówno pokrycie kodu testowego, jak i wyniki testów. Jak pokazano na poniższej ilustracji, wszystkie trzy testy zostały wykonane pomyślnie. Pokazuje również, że nasze testy obejmowały wszystkie ścieżki kodu w metodzie i wszystkie te testy zostały wykonane pomyślnie (co jest oznaczone zielonym znakiem wyboru `StartsWithUpper` &quot;&quot;;"). Na koniec pokazuje, że żadna z innych metod w stringLibrary nie ma pokrycia kodu (co jest oznaczone niebieską linią "➖").

![Eksplorator testów na żywo i okno edytora kodu po rozpoczęciu testów jednostkowych na żywo](media/lut-start/vs-2019/lut-results-cs.png)
::: moniker-end

Możesz również uzyskać bardziej szczegółowe informacje na temat pokrycia testów i wyników testów, wybierając określoną ikonę pokrycia kodu w oknie edytora kodu. Aby zbadać te szczegóły, wykonaj następujące czynności:

1. Kliknij zielony znacznik wyboru w wierszu, który `if (String.IsNullOrWhiteSpace(s))` odczytuje metodę `StartsWithUpper` . Jak pokazano na poniższej ilustracji, Live Unit Testing, że trzy testy obejmują ten wiersz kodu i że wszystkie zostały wykonane pomyślnie.

   ![Pokrycie kodu dla instrukcji warunkowej "if"](media/lut-start/code-coverage-cs1.png)

1. Kliknij zielony znacznik wyboru w wierszu, który `return Char.IsUpper(s[0])` odczytuje metodę `StartsWithUpper` . Jak pokazano na poniższej ilustracji, Live Unit Testing, że tylko dwa testy obejmują ten wiersz kodu i że wszystkie zostały wykonane pomyślnie.

   ![Pokrycie kodu dla instrukcji return](media/lut-start/code-coverage-cs2.png)

Głównym problemem, który Live Unit Testing, jest niepełne pokrycie kodu. Ten temat zostanie rozwiązany w następnej sekcji.

## <a name="expand-test-coverage"></a>Rozszerzanie pokrycia testu

W tej sekcji rozszerzysz testy jednostkowe na `StartsWithLower` metodę . Chociaż to zrobisz, Live Unit Testing będzie dynamicznie kontynuować testowanie kodu.

Aby rozszerzyć pokrycie kodu na `StartsWithLower` metodę , wykonaj następujące czynności:

1. Dodaj następujące metody `TestStartsWithLower` i do pliku kodu `TestDoesNotStartWithLower` źródłowego testu projektu:

   :::code language="csharp" source="../test/samples/snippets/csharp/lut-start/unittest2.cs" id="Snippet1":::

1. `DirectCallWithNullOrEmpty`Zmodyfikuj metodę, dodając następujący kod bezpośrednio po wywołaniu [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) metody .

   :::code language="csharp" source="../test/samples/snippets/csharp/lut-start/unittest2.cs" id="Snippet2":::

1. Live Unit Testing automatycznie wykonuje nowe i zmodyfikowane testy podczas modyfikowania kodu źródłowego. Jak pokazano na poniższej ilustracji, wszystkie testy, w tym dwa dodane i zmodyfikowane testy, zakończyły się pomyślnie.

   ::: moniker range="vs-2017"
   ![Eksplorator testów po rozwinięciu pokrycia testu](media/lut-start/test-dynamic.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Eksplorator testów na żywo po rozwinięciu pokrycia testu](media/lut-start/vs-2019/test-dynamic.png)
   ::: moniker-end

1. Przejdź do okna zawierającego kod źródłowy klasy StringLibrary. Live Unit Testing teraz, że pokrycie kodu jest rozszerzone na `StartsWithLower` metodę .

    ![Pokrycie kodu dla metody StartsWithLower](media/lut-start/lut-extended-cs.png)

W niektórych przypadkach pomyślne testy w **Eksploratorze testów** mogą być wyszarowane. Oznacza to, że test jest obecnie wykonywany lub że test nie został uruchomiony ponownie, ponieważ nie ma żadnych zmian kodu, które miałyby wpływ na test od czasu jego ostatniego wykonania.

Do tej pory wszystkie nasze testy zakończyły się pomyślnie. W następnej sekcji sprawdzimy, jak można obsłużyć niepowodzenie testu.

## <a name="handle-a-test-failure"></a>Obsługa błędu testu

W tej sekcji dowiesz się, jak za pomocą narzędzia Live Unit Testing identyfikować i rozwiązywać problemy z błędami testów oraz rozwiązywać problemy. W tym celu rozszerzysz pokrycie testów do `HasEmbeddedSpaces` metody .

1. Dodaj następującą metodę do pliku testowego:

   :::code language="csharp" source="../test/samples/snippets/csharp/lut-start/unittest2.cs" id="Snippet3":::

1. Po wykonaniu testu Live Unit Testing, że metoda zakończyła się niepowodzeniem, jak pokazano na `TestHasEmbeddedSpaces` poniższej ilustracji:

   ::: moniker range="vs-2017"
   ![Eksplorator testów zgłasza test, który zakończył się niepowodzeniem](media/lut-start/test-failure.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Eksplorator testów na żywo zgłasza test, który zakończył się niepowodzeniem](media/lut-start/vs-2019/test-failure.png)
   ::: moniker-end

1. Wybierz okno, w którym zostanie wyświetlony kod biblioteki. Live Unit Testing rozszerzono pokrycie kodu do `HasEmbeddedSpaces` metody . Raportuje również niepowodzenie testu przez dodanie czerwonego "" do wierszy 🞩 objętych niepowodzeniem testów.

1. Umieść kursor nad wierszem przy użyciu `HasEmbeddedSpaces` podpisu metody. Live Unit Testing zostanie wyświetlona etykietka narzędzia z raportem, że metoda jest objęta jednym testem, jak pokazano na poniższej ilustracji:

   ![Live Unit Testing informacji o teście, który zakończył się niepowodzeniem](media/lut-start/test-failure-info-cs.png)

1. Wybierz test **TestHasEmbeddedSpaces,** który zakończył się niepowodzeniem. Live Unit Testing udostępnia kilka opcji, takich jak uruchamianie wszystkich testów i debugowanie wszystkich testów, jak pokazano na poniższej ilustracji:

   ::: moniker range="vs-2017"
   ![Live Unit Testing opcje dla testu po awarii](media/lut-start/test-failure-options.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Live Unit Testing opcje dla testu po awarii](media/lut-start/vs-2019/test-failure-options.png)
   ::: moniker-end

1. Wybierz **pozycję Debuguj** wszystko, aby debugować test, który zakończył się niepowodzeniem.

1. Visual Studio wykonuje test w trybie debugowania.

   Test przypisuje każdy ciąg w tablicy do zmiennej o nazwie `phrase` i przekazuje go do metody `HasEmbeddedSpaces` . Wykonywanie programu wstrzymuje i wywołuje debuger przy pierwszym wyrażeniu potwierdzenia `false` . Okno dialogowe wyjątku, które wynika z nieoczekiwanej wartości w [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) wywołaniu metody, jest pokazane na poniższej ilustracji.

   ![okno dialogowe Live Unit Testing wyjątku](media/lut-start/exception-dialog-cs.png)

   Ponadto dostępne są wszystkie narzędzia do debugowania Visual Studio, które ułatwiają rozwiązywanie problemów z testem po awarii, jak pokazano na poniższej ilustracji:

   ![Visual Studio debugowania](media/lut-start/debugging-tools-cs.png)

   Zwróć uwagę, że w oknie **Autos** wartość zmiennej to `phrase` "Name\tDescription", która jest drugim elementem tablicy. Metoda testowa oczekuje `HasEmbeddedSpaces` zwrócenia wartości , gdy zostanie przekazany ten ciąg. Zamiast `true` tego zwraca wartość `false` . Oczywiście nie rozpoznaje znaku tabuły "\t" jako osadzonego miejsca.

1. Wybierz **pozycję Kontynuuj**  >  **debugowanie,** naciśnij klawisz **F5** lub kliknij przycisk **Kontynuuj** na pasku narzędzi, aby kontynuować wykonywanie programu testowego. Ponieważ wystąpił nieobsługiwany wyjątek, test zostaje zakończony.
Zapewnia to wystarczającą ilość informacji do wstępnego badania usterki. Albo `TestHasEmbeddedSpaces` (procedura testowa) podjęła niepoprawne założenie, albo `HasEmbeddedSpaces` nie rozpoznaje prawidłowo wszystkich osadzonych spacji.

1. Aby zdiagnozować i rozwiązać problem, zacznij od `StringLibrary.HasEmbeddedSpaces` metody . Przyjrzyj się porównaniu w `HasEmbeddedSpaces` metodzie . Uważa, że osadzone miejsce to U+0020. Jednak standard Unicode zawiera kilka innych znaków spacji. Sugeruje to, że kod biblioteki został niepoprawnie przetestowany pod kątem znaku odstępu.

1. Zastąp porównanie równości wywołaniem <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> metody :

   :::code language="csharp" source="../test/samples/snippets/csharp/lut-start/program2.cs" id="Snippet1":::

1. Live Unit Testing automatycznie ponownie uruchamia metodę testu, która zakończyła się niepowodzeniem.

   Live Unit Testing zostaną wyświetlone zaktualizowane wyniki, które są również wyświetlane w oknie edytora kodu.

## <a name="see-also"></a>Zobacz też

- [Live Unit Testing w Visual Studio](live-unit-testing.md)
- [Live Unit Testing często zadawanych pytań](live-unit-testing-faq.yml)
