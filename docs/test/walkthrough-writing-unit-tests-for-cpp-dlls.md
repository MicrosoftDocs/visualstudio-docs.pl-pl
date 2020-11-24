---
title: 'Instrukcje: zapisywanie testów jednostkowych dla bibliotek DLL języka C++'
description: Dowiedz się, jak opracować natywną bibliotekę DLL C++ za pomocą metodologii test-First. Zacznij od utworzenia natywnego projektu testowego.
ms.custom: SEO-VS-2020
ms.date: 06/13/2019
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 178fef548bc52346a78c7f9e4607aad7b1c56f65
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598409"
---
# <a name="how-to-write-unit-tests-for-c-dlls"></a>Instrukcje: zapisywanie testów jednostkowych dla bibliotek DLL języka C++

W tym przewodniku opisano sposób tworzenia natywnej biblioteki DLL języka C++ za pomocą metodologii test-First. Podstawowe kroki są następujące:

1. [Utwórz natywny projekt testowy](#create_test_project). Projekt testowy znajduje się w tym samym rozwiązaniu co projekt biblioteki DLL.

2. [Utwórz projekt DLL](#create_dll_project). W tym instruktażu zostanie utworzona nowa biblioteka DLL, ale procedura testowania istniejącej biblioteki DLL jest podobna.

3. [Uczyń funkcje biblioteki DLL widocznymi dla testów](#make_functions_visible).

4. [Iteracyjnie rozszerza testy](#iterate). Zalecamy cykliczny cykl "czerwony-zielony-Refaktoryzacja", w którym rozwój kodu jest kierowany przez testy.

5. [Debugowanie testów zakończonych niepowodzeniem](#debug). Testy można uruchamiać w trybie debugowania.

6. [Refaktoryzacja przy zachowaniu niezmienionych testów](#refactor). Refaktoryzacja oznacza poprawę struktury kodu bez zmiany jego zachowania zewnętrznego. Można to zrobić, aby zwiększyć wydajność, rozszerzalność lub czytelność kodu. Ponieważ zamiarem nie jest zmiana zachowania, nie należy zmieniać testów podczas zmiany refaktoryzacji kodu. Testy pomagają upewnić się, że nie są wprowadzane usterki podczas refaktoryzacji.

7. [Sprawdź pokrycie](using-code-coverage-to-determine-how-much-code-is-being-tested.md). Testy jednostkowe są bardziej przydatne, gdy wykonują więcej kodu. Można wykryć, które części kodu zostały wykorzystane przez testy.

8. [Izoluj jednostki od zasobów zewnętrznych](using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md). Zazwyczaj Biblioteka DLL jest zależna od innych składników systemu, które tworzysz, takich jak inne biblioteki DLL, bazy danych lub zdalne podsystemy. Warto przetestować każdą jednostkę w izolacji od jej zależności. Składniki zewnętrzne mogą sprawiać, że testy działają wolno. W trakcie programowania inne składniki mogą nie być kompletne.

## <a name="create-a-native-unit-test-project"></a><a name="create_test_project"></a> Utwórz natywny projekt testów jednostkowych

1. W menu **plik** wybierz pozycję **Nowy**  >  **projekt**.

     **Visual Studio 2017 i starsze**: rozwiń węzeł **zainstalowane**  >  **Szablony**  >  **Visual C++**  >  **test**.
     **Visual Studio 2019**: Ustaw **Język** na C++ i wpisz "test" w polu wyszukiwania.

     Wybierz szablon **projektu natywnych testów jednostkowych** lub dowolną zainstalowaną platformę. Jeśli wybierzesz inny szablon, taki jak Google Test lub podwyższanie poziomu. test, podstawowe zasady są takie same, mimo że niektóre szczegóły będą się różnić.

     W tym instruktażu projekt testowy ma nazwę `NativeRooterTest` .

2. W nowym projekcie Sprawdź **UnitTest1. cpp**

     ![Test projektu z KLASą&#95;TESTowego i metodą&#95;testu](../test/media/utecpp2.png)

     Zwróć uwagę, że:

    - Każdy test jest definiowany przy użyciu `TEST_METHOD(YourTestName){...}` .

         Nie trzeba pisać sygnatury funkcji konwencjonalnej. Podpis jest tworzony przez makro TEST_METHOD. Makro generuje funkcję wystąpienia zwracającą typ void. Generuje również funkcję statyczną, która zwraca informacje o metodzie testowej. Te informacje umożliwiają Eksploratorowi testów znalezienie metody.

    - Metody testowe są pogrupowane w klasy przy użyciu `TEST_CLASS(YourClassName){...}` .

         Gdy testy są uruchamiane, tworzone jest wystąpienie każdej klasy testowej. Metody testowe są wywoływane w nieokreślonej kolejności. Można zdefiniować metody specjalne, które są wywoływane przed i po każdym module, klasie lub metodzie.

3. Sprawdź, czy testy są uruchamiane w Eksploratorze testów:

    1. Wstaw kod testu:

        ```cpp
        TEST_METHOD(TestMethod1)
        {
            Assert::AreEqual(1,1);
        }
        ```

         Należy zauważyć, że `Assert` Klasa zawiera kilka metod statycznych, których można użyć do sprawdzenia wyników w metodach testowych.

    2. W menu **test** wybierz polecenie **Uruchom**  >  **wszystkie testy**.

         Test kompiluje i uruchamia.

         Zostanie wyświetlony **Eksplorator testów** .

         Test jest wyświetlany w obszarze **testy zakończone**.

         ![Eksplorator testów jednostkowych z jednym zakończonym testem](../test/media/utecpp04.png)

## <a name="create-a-dll-project"></a><a name="create_dll_project"></a> Tworzenie projektu DLL

::: moniker range="vs-2019"

Poniższe kroki pokazują, jak utworzyć projekt DLL w programie Visual Studio 2019.

1. Utwórz projekt C++ za pomocą **Kreatora pulpitu systemu Windows**: kliknij prawym przyciskiem myszy nazwę rozwiązania w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**  >  **Nowy projekt**. Ustaw **Język** na C++, a następnie wpisz ciąg "Windows" w polu wyszukiwania. Z listy wyników wybierz pozycję **Kreator pulpitu systemu Windows** .

     W tym instruktażu projekt ma nazwę `RootFinder` .

2. Kliknij przycisk **Utwórz**. W następnym oknie dialogowym w obszarze **Typ aplikacji** wybierz **bibliotekę dołączaną dynamicznie (dll)** , a także sprawdź **symbole eksportu**.

     Opcja **Eksportuj symbole** generuje wygodne makro, którego można użyć do zadeklarowania eksportowanych metod.

     ![Kreator projektu C++ ustawiony dla bibliotek DLL i symboli eksportu](../test/media/vs-2019/windows-desktop-project-dll.png)

3. Zadeklaruj wyeksportowaną funkcję w pliku Principal *. h* :

     ![Nowy projekt kodu DLL i plik h z makrami interfejsu API](../test/media/utecpp07.png)

     Deklarator powoduje, że `__declspec(dllexport)` publiczne i chronione składowe klasy są widoczne poza biblioteką DLL. Aby uzyskać więcej informacji, zobacz [using dllimport i dllexport w klasach C++](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes).

4. W pliku Principal *. cpp* Dodaj minimalną treść dla funkcji:

    ```cpp
        // Find the square root of a number.
        double CRootFinder::SquareRoot(double v)
        {
            return 0.0;
        }
    ```

::: moniker-end

::: moniker range="vs-2017"

Poniższe kroki pokazują, jak utworzyć projekt DLL w programie Visual Studio 2017.

1. Utwórz projekt języka C++ przy użyciu szablonu **projektu Win32** .

     W tym instruktażu projekt ma nazwę `RootFinder` .

2. Wybierz opcję **dll** i **Eksportuj symbole** w Kreatorze aplikacji Win32.

     Opcja **Eksportuj symbole** generuje wygodne makro, którego można użyć do zadeklarowania eksportowanych metod.

     ![Kreator projektu C++ ustawiony dla bibliotek DLL i symboli eksportu](../test/media/utecpp06.png)

3. Zadeklaruj wyeksportowaną funkcję w pliku Principal *. h* :

     ![Nowy projekt kodu DLL i plik h z makrami interfejsu API](../test/media/utecpp07.png)

     Deklarator powoduje, że `__declspec(dllexport)` publiczne i chronione składowe klasy są widoczne poza biblioteką DLL. Aby uzyskać więcej informacji, zobacz [using dllimport i dllexport w klasach C++](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes).

4. W pliku Principal *. cpp* Dodaj minimalną treść dla funkcji:

    ```cpp
        // Find the square root of a number.
        double CRootFinder::SquareRoot(double v)
        {
            return 0.0;
        }
    ```

::: moniker-end

## <a name="couple-the-test-project-to-the-dll-project"></a><a name="make_functions_visible"></a> Połącz projekt testowy z projektem DLL

1. Dodaj projekt DLL do odwołań projektu projektu testowego:

   1. Kliknij prawym przyciskiem myszy węzeł projektu testowego w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**  >  **odwołanie**.

   2. W oknie dialogowym **Dodaj odwołanie** wybierz projekt DLL i wybierz pozycję **Dodaj**.

        ![Właściwości projektu C++ | Dodaj nowe odwołanie](../test/media/utecpp09.png)

2. W pliku *. cpp* testu jednostkowego podmiotu zabezpieczeń należy uwzględnić plik *. h* kodu dll:

   ```cpp
   #include "..\RootFinder\RootFinder.h"
   ```

3. Dodaj podstawowy test, który używa wyeksportowanej funkcji:

   ```cpp
   TEST_METHOD(BasicTest)
   {
      CRootFinder rooter;
      Assert::AreEqual(
         // Expected value:
         0.0,
         // Actual value:
         rooter.SquareRoot(0.0),
         // Tolerance:
         0.01,
        // Message:
        L"Basic test failed",
        // Line number - used if there is no PDB file:
        LINE_INFO());
   }
   ```

4. Skompiluj rozwiązanie.

    Nowy test pojawi się w **Eksploratorze testów**.

5. W **Eksploratorze testów** wybierz opcję **Uruchom wszystkie**.

    ![Eksplorator testów jednostkowych &#45; test podstawowy zakończony zakończono](../test/media/utecpp10.png)

   Został skonfigurowany test i projekty kodu i zweryfikowane, że można uruchomić testy, które uruchamiają funkcje w projekcie kodu. Teraz możesz zacząć pisać prawdziwe testy i kod.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a><a name="iterate"></a> Iteracyjnie rozszerza testy i przekazują je

1. Dodaj nowy test:

    ```cpp
    TEST_METHOD(RangeTest)
    {
      CRootFinder rooter;
      for (double v = 1e-6; v < 1e6; v = v * 3.2)
      {
        double actual = rooter.SquareRoot(v*v);
        Assert::AreEqual(v, actual, v/1000);
      }
    }
    ```

    > [!TIP]
    > Zalecamy, aby nie zmieniać testów, które zostały zakończone. Zamiast tego Dodaj nowy test, zaktualizuj kod tak, aby test zakończył się powodzeniem, a następnie Dodaj inny test i tak dalej.
    >
    > Gdy użytkownicy zmienią swoje wymagania, należy wyłączyć testy, które nie są już poprawne. Napisz nowe testy i Przekształć je w jeden raz w ten sam przyrostowy sposób.

2. Skompiluj rozwiązanie, a następnie w **Eksploratorze testów** wybierz opcję **Uruchom wszystkie**.

     Nowy test zakończy się niepowodzeniem.

     ![RangeTest kończy się niepowodzeniem](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Sprawdź, czy każdy test kończy się niepowodzeniem natychmiast po jego zapisaniu. Dzięki temu można uniknąć łatwego błędu podczas pisania testu, który nigdy nie powiedzie się.

3. Popraw kod biblioteki DLL, aby nowe przebiegi testowe:

    ```cpp
    #include <math.h>
    ...
    double CRootFinder::SquareRoot(double v)
    {
      double result = v;
      double diff = v;
      while (diff > result/1000)
      {
        double oldResult = result;
        result = result - (result*result - v)/(2*result);
        diff = abs (oldResult - result);
      }
      return result;
    }
    ```

4. Skompiluj rozwiązanie, a następnie w **Eksploratorze testów** wybierz opcję **Uruchom wszystkie**.

     Oba testy zostały zakończone pomyślnie.

     ![Zakończono Test zakresu &#45; w Eksploratorze testów jednostkowych](../test/media/utecpp12.png)

    > [!TIP]
    > Opracowuj kod przez dodanie testów pojedynczo. Upewnij się, że wszystkie testy są zakończone po każdej iteracji.

## <a name="debug-a-failing-test"></a><a name="debug"></a> Debuguj test zakończony niepowodzeniem

1. Dodaj inny test:

    ```cpp
    #include <stdexcept>
    ...
    // Verify that negative inputs throw an exception.
    TEST_METHOD(NegativeRangeTest)
    {
      wchar_t message[200];
      CRootFinder rooter;
      for (double v = -0.1; v > -3.0; v = v - 0.5)
      {
        try
        {
          // Should raise an exception:
          double result = rooter.SquareRoot(v);

          _swprintf(message, L"No exception for input %g", v);
          Assert::Fail(message, LINE_INFO());
        }
        catch (std::out_of_range ex)
        {
          continue; // Correct exception.
        }
        catch (...)
        {
          _swprintf(message, L"Incorrect exception for %g", v);
          Assert::Fail(message, LINE_INFO());
        }
      }
    }
    ```

2. Skompiluj rozwiązanie i wybierz polecenie **Uruchom wszystkie**.

3. Otwórz (lub kliknij dwukrotnie) Test zakończony niepowodzeniem.

     Niepowodzenie zostało wyróżnione. Komunikat o błędzie jest widoczny w okienku szczegółów w **Eksploratorze testów**.

     ![NegativeRangeTests nie powiodło się](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

4. Aby zobaczyć dlaczego test nie powiedzie się, przechodzenie przez funkcję:

    1. Ustaw punkt przerwania na początku funkcji SquareRoot.

    2. W menu skrótów testu zakończonego niepowodzeniem wybierz **Debuguj wybrane testy**.

         Gdy przebieg zostanie zatrzymany w punkcie przerwania, przejdź do kodu.

5. Wstaw kod w funkcji, którą tworzysz:

    ```cpp

    #include <stdexcept>
    ...
    double CRootFinder::SquareRoot(double v)
    {
        // Validate parameter:
        if (v < 0.0)
        {
          throw std::out_of_range("Can't do square roots of negatives");
        }

    ```

6. Wszystkie testy są teraz zakończone pomyślnie.

   ![Wszystkie testy zakończone powodzeniem](../test/media/ute_ult_alltestspass.png)

::: moniker range="vs-2017"

> [!TIP]
> Jeśli pojedyncze testy nie mają żadnych zależności, które uniemożliwiają ich uruchomienie w dowolnej kolejności, Włącz równoległe wykonywanie testów przy użyciu ![ przycisku wykonaj&#95;parallelicon&#45;mały ](../test/media/ute_parallelicon-small.png) przełącznik na pasku narzędzi. Może to znacznie skrócić czas potrzebny do uruchomienia wszystkich testów.

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> Jeśli pojedyncze testy nie mają żadnych zależności, które uniemożliwiają ich uruchomienie w dowolnej kolejności, Włącz równoległe wykonywanie testów w menu Ustawienia na pasku narzędzi. Może to znacznie skrócić czas potrzebny do uruchomienia wszystkich testów.

::: moniker-end

## <a name="refactor-the-code-without-changing-tests"></a><a name="refactor"></a> Refaktoryzacja kodu bez zmiany testów

1. Uprość Obliczanie centralne w funkcji SquareRoot:

    ```cpp
    // old code:
    //   result = result - (result*result - v)/(2*result);
    // new code:
         result = (result + v/result)/2.0;

    ```

2. Skompiluj rozwiązanie i wybierz pozycję **Uruchom wszystkie**, aby upewnić się, że nie wprowadzono błędu.

    > [!TIP]
    > Dobry zestaw testów jednostkowych daje pewność, że podczas zmiany kodu nie wprowadzono usterek.
    >
    > Kontynuuj refaktoryzację niezależnie od innych zmian.

## <a name="next-steps"></a>Następne kroki

- **Izolacji.** Większość bibliotek DLL jest zależna od innych podsystemów, takich jak bazy danych i inne biblioteki DLL. Te inne składniki są często opracowywane równolegle. Aby zezwolić na wykonywanie testów jednostkowych, gdy inne składniki nie są jeszcze dostępne, musisz zastąpić imitację lub

- **Testy weryfikacyjne kompilacji.** Testy można wykonywać na serwerze kompilacji zespołu w ustalonych odstępach czasu. Gwarantuje to, że usterki nie są wprowadzane podczas integracji pracy kilku członków zespołu.

- **Testy ewidencjonowania.** Można określić, że niektóre testy są wykonywane, zanim każdy członek zespołu sprawdzi kod w kontroli źródła. Zwykle jest to podzestaw kompletnego zestawu testów weryfikacyjnych kompilacji.

   Istnieje również możliwość przydzielenia minimalnego poziomu pokrycia kodu.

## <a name="see-also"></a>Zobacz także

- [Dodawanie testów jednostkowych do istniejących aplikacji C++](../test/how-to-use-microsoft-test-framework-for-cpp.md)
- [Korzystanie z Microsoft.VisualStudio.TestTools.CppUnitTestFramework](how-to-use-microsoft-test-framework-for-cpp.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
- [Przewodnik: Tworzenie i używanie biblioteki dołączanej dynamicznie (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [Importowanie i eksportowanie](/cpp/build/importing-and-exporting)
