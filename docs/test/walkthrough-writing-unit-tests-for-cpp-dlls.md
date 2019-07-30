---
title: 'Instrukcje: Zapisz testy jednostkowe C++ dla bibliotek DLL'
ms.date: 06/13/2019
ms.topic: conceptual
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 1e9e77cd3b6cd02810873127bf9173eac80d7e74
ms.sourcegitcommit: 044bb54cb4552c8f4651feb11d62e52726117e75
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68661908"
---
# <a name="how-to-write-unit-tests-for-c-dlls"></a>Instrukcje: Zapisz testy jednostkowe C++ dla bibliotek DLL

W tym przewodniku opisano sposób tworzenia natywnej C++ biblioteki DLL przy użyciu metodologii test-First. Podstawowe kroki są następujące:

1. [Utwórz natywny projekt testowy](#create_test_project). Projekt testowy znajduje się w tym samym rozwiązaniu co projekt biblioteki DLL.

2. [Utwórz projekt DLL](#create_dll_project). W tym instruktażu zostanie utworzona nowa biblioteka DLL, ale procedura testowania istniejącej biblioteki DLL jest podobna.

3. [Uczyń funkcje biblioteki DLL widocznymi dla testów](#make_functions_visible).

4. [Iteracyjnie rozszerza testy](#iterate). Zalecamy cykliczny cykl "czerwony-zielony-Refaktoryzacja", w którym rozwój kodu jest kierowany przez testy.

5. [Debugowanie testów zakończonych niepowodzeniem](#debug). Testy można uruchamiać w trybie debugowania.

6. [Refaktoryzacja przy zachowaniu niezmienionych testów](#refactor). Refaktoryzacja oznacza poprawę struktury kodu bez zmiany jego zachowania zewnętrznego. Można to zrobić, aby zwiększyć wydajność, rozszerzalność lub czytelność kodu. Ponieważ zamiarem nie jest zmiana zachowania, nie należy zmieniać testów podczas zmiany refaktoryzacji kodu. Testy pomagają upewnić się, że nie są wprowadzane usterki podczas refaktoryzacji.

7. [Sprawdź pokrycie](using-code-coverage-to-determine-how-much-code-is-being-tested.md). Testy jednostkowe są bardziej przydatne, gdy wykonują więcej kodu. Można wykryć, które części kodu zostały wykorzystane przez testy.

8. [Izoluj jednostki od zasobów zewnętrznych](using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md). Zazwyczaj Biblioteka DLL jest zależna od innych składników systemu, które tworzysz, takich jak inne biblioteki DLL, bazy danych lub zdalne podsystemy. Warto przetestować każdą jednostkę w izolacji od jej zależności. Składniki zewnętrzne mogą sprawiać, że testy działają wolno. W trakcie programowania inne składniki mogą nie być kompletne.

## <a name="create_test_project"></a>Utwórz natywny projekt testów jednostkowych

1. Na **pliku** menu, wybierz **New** > **projektu**.

     **Program Visual Studio 2017 i jego wcześniejsze wersje**: Rozwiń >  **test** **wizualizacji C++** **zainstalowanych szablonów** >  . > 
     **Visual Studio 2019**: Ustaw **Język** na C++ i wpisz "test" w polu wyszukiwania.

     Wybierz szablon **projektu natywnych testów jednostkowych** lub dowolną zainstalowaną platformę. Jeśli wybierzesz inny szablon, taki jak Google Test lub podwyższanie poziomu. test, podstawowe zasady są takie same, mimo że niektóre szczegóły będą się różnić.

     W tym instruktażu projekt testowy ma nazwę `NativeRooterTest`.

2. W nowym projekcie Sprawdź **UnitTest1. cpp**

     ![Test projektu z klasą&#95;testową&#95;i metodą testową](../test/media/utecpp2.png)

     Zwróć uwagę, że:

    - Każdy test jest definiowana za pomocą `TEST_METHOD(YourTestName){...}`.

         Nie trzeba napisać podpis konwencjonalnych funkcji. Podpis jest tworzony za pomocą makra TEST_METHOD. Makro generuje funkcją wystąpienia, która zwraca wartość void. Polecenie to generuje także funkcję statyczną, która zwraca informacje na temat metody testowej. Te informacje temu Eksplorator testów, można znaleźć metody.

    - Metody testowe są pogrupowane według klasy przy użyciu `TEST_CLASS(YourClassName){...}`.

         Gdy testy są uruchamiane, tworzone jest wystąpienie każdej klasy testu. Metody testowe są wywoływane w nieokreślonej kolejności. Można zdefiniować specjalne metody, które są wywoływane przed i po każdym modułu, klasy lub metody.

3. Sprawdź, czy testy są uruchamiane w Eksploratorze testów:

    1. Wstaw kod testu:

        ```cpp
        TEST_METHOD(TestMethod1)
        {
            Assert::AreEqual(1,1);
        }
        ```

         Należy zauważyć, że `Assert` klasa udostępnia kilka metod statycznych, których można sprawdzić wyniki za pomocą metod testowych.

    2. W menu **test** wybierz polecenie **Uruchom** > **wszystkie testy**.

         Test kompiluje i uruchamia.

         Zostanie wyświetlony **Eksplorator testów** .

         Test jest wyświetlany w obszarze **testy zakończone**.

         ![Eksplorator testów jednostkowych z jednym zakończonym testem](../test/media/utecpp04.png)

## <a name="create_dll_project"></a>Tworzenie projektu DLL

::: moniker range="vs-2019"

Poniższe kroki pokazują, jak utworzyć projekt DLL w programie Visual Studio 2019.

1. Utwórz C++ projekt za pomocą **Kreatora pulpitu systemu Windows**: Kliknij prawym przyciskiem myszy nazwę rozwiązania w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj** > **Nowy projekt**. Ustaw **Język** na C++ , a następnie wpisz ciąg "Windows" w polu wyszukiwania. Z listy wyników wybierz pozycję **Kreator pulpitu systemu Windows** .

     W tym instruktażu projekt ma nazwę `RootFinder`.

2. Naciśnij pozycję **Utwórz**. W następnym oknie dialogowym w obszarze **Typ aplikacji** wybierz **bibliotekę dołączaną dynamicznie (dll)** , a także sprawdź **symbole eksportu**.

     Opcja **Eksportuj symbole** generuje wygodne makro, którego można użyć do zadeklarowania eksportowanych metod.

     ![C++Kreator projektu ustawiony dla bibliotek DLL i symboli eksportu](../test/media/vs-2019/windows-desktop-project-dll.png)

3. Zadeklaruj wyeksportowaną funkcję w pliku Principal *. h* :

     ![Nowy projekt kodu DLL i plik h z makrami interfejsu API](../test/media/utecpp07.png)

     Deklarator `__declspec(dllexport)` powoduje, że publiczne i chronione składowe klasy są widoczne poza biblioteką DLL. Aby uzyskać więcej informacji, zobacz [using dllimport i dllexport C++ w klasach](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes).

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

1. Utwórz C++ projekt przy użyciu szablonu **projektu Win32** .

     W tym instruktażu projekt ma nazwę `RootFinder`.

2. Wybierz opcję **dll** i **Eksportuj symbole** w Kreatorze aplikacji Win32.

     Opcja **Eksportuj symbole** generuje wygodne makro, którego można użyć do zadeklarowania eksportowanych metod.

     ![C++Kreator projektu ustawiony dla bibliotek DLL i symboli eksportu](../test/media/utecpp06.png)

3. Zadeklaruj wyeksportowaną funkcję w pliku Principal *. h* :

     ![Nowy projekt kodu DLL i plik h z makrami interfejsu API](../test/media/utecpp07.png)

     Deklarator `__declspec(dllexport)` powoduje, że publiczne i chronione składowe klasy są widoczne poza biblioteką DLL. Aby uzyskać więcej informacji, zobacz [using dllimport i dllexport C++ w klasach](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes).

4. W pliku Principal *. cpp* Dodaj minimalną treść dla funkcji:

    ```cpp
        // Find the square root of a number.
        double CRootFinder::SquareRoot(double v)
        {
            return 0.0;
        }
    ```

::: moniker-end

## <a name="make_functions_visible"></a>Połącz projekt testowy z projektem DLL

1. Dodaj projekt DLL do odwołań projektu projektu testowego:

   1. Kliknij prawym przyciskiem myszy węzeł projektu testu w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj** > **odwołania**.

   2. W oknie dialogowym **Dodaj odwołanie** wybierz projekt DLL i wybierz pozycję **Dodaj**.

        ![C++Właściwości projektu | Dodaj nowe odwołanie](../test/media/utecpp09.png)

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

5. W **Eksplorator testów**, wybierz **Uruchom wszystkie**.

    ![Test podstawowego Eksploratora &#45; testów jednostkowych zakończonych niepowodzeniem](../test/media/utecpp10.png)

   Mają ustawienie testu i projekty kodu, a następnie zweryfikować, że można uruchomić testy, które uruchamiania funkcji w projekcie kodu. Teraz możesz rozpocząć pisanie rzeczywistych testów i kodu.

## <a name="iterate"></a> Iteracyjne Udoskonal testy i nadawać im przekazać

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
    > Firma Microsoft zaleca, nie należy zmieniać testy, które zostały przekazane. Zamiast tego Dodaj nowy test, zaktualizować kod, tak aby test zakończy się pomyślnie, a następnie dodaj innego testu, i tak dalej.
    >
    > Użytkownicy zmiany ich wymagań, wyłącz testy, które nie są już prawidłowe. Zapisz nowe testy i ich działania pojedynczo, w taki sam sposób przyrostowego.

2. Skompiluj rozwiązanie, a następnie w **Eksploratorze testów**wybierz opcję **Uruchom wszystkie**.

     Nowy test zakończy się niepowodzeniem.

     ![RangeTest kończy się niepowodzeniem](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Upewnij się, że każdy test zakończy się niepowodzeniem, natychmiast, po napisaniu go. Dzięki temu można uniknąć łatwe Błąd zapisywania testu, który nigdy nie zakończy się niepowodzeniem.

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

4. Kompiluj rozwiązanie, a następnie w polu **Eksplorator testów**, wybierz **Uruchom wszystkie**.

     Kod przechodzi oba testy.

     ![Test zakresu Eksploratora &#45; testów jednostkowych zakończonych](../test/media/utecpp12.png)

    > [!TIP]
    > Tworzenie kodu, dodając jeden testów w danym momencie. Upewnij się, że po każdej iteracji kod przechodzi wszystkie testy.

## <a name="debug"></a> Debuguj test niepowodzeniem

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

     Potwierdzenie nie powiodło się, jest wyróżniona. Komunikat o błędzie jest widoczny w okienku szczegółów **Eksplorator testów**.

     ![NegativeRangeTests nie powiodło się.](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

4. Aby zobaczyć, dlaczego test zakończy się niepowodzeniem, krok przy użyciu funkcji:

    1. Ustaw punkt przerwania na początku funkcji SquareRoot.

    2. W menu skrótów testów zakończonych niepowodzeniem, wybierz **Debuguj wybrane testy**.

         Po zatrzymaniu w punkcie przerwania Uruchom przejść przez kod.

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

6. Teraz kod przechodzi wszystkie testy.

   ![Kod przechodzi wszystkie testy](../test/media/ute_ult_alltestspass.png)

::: moniker range="vs-2017"

> [!TIP]
> Jeśli pojedyncze testy nie mają żadnych zależności, które uniemożliwiają ich uruchomienie w dowolnej kolejności, należy włączyć równoległe wykonywanie testów ![za&#95;pomocą&#45;przycisku](../test/media/ute_parallelicon-small.png) przełączania wykonaj parallelicon mały przełącznik na pasku narzędzi. Może to znacznie zmniejszyć czas poświęcony na uruchamianie wszystkich testów.

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> Jeśli pojedyncze testy nie mają żadnych zależności, które uniemożliwiają ich uruchomienie w dowolnej kolejności, Włącz równoległe wykonywanie testów w menu Ustawienia na pasku narzędzi. Może to znacznie zmniejszyć czas poświęcony na uruchamianie wszystkich testów.

::: moniker-end

## <a name="refactor"></a> Refaktoryzacja kodu bez zmieniania testów

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
    > Zachowaj refaktoryzacji oddzielnie od innych zmian.

## <a name="next-steps"></a>Następne kroki

- **Izolacji.** Większość bibliotek DLL jest zależna od innych podsystemów, takich jak bazy danych i inne biblioteki DLL. Te inne składniki są często opracowywane równolegle. Aby zezwolić na wykonywanie testów jednostkowych, gdy inne składniki nie są jeszcze dostępne, musisz zastąpić imitację lub

- **Testy weryfikacyjne kompilacji.** Testy można wykonywać na serwerze kompilacji zespołu w ustalonych odstępach czasu. Gwarantuje to, że usterki nie są wprowadzane podczas integracji pracy kilku członków zespołu.

- **Testy ewidencjonowania.** Można określić, że niektóre testy są wykonywane, zanim każdy członek zespołu sprawdzi kod w kontroli źródła. Zwykle jest to podzestaw kompletnego zestawu testów weryfikacyjnych kompilacji.

   Istnieje również możliwość przydzielenia minimalnego poziomu pokrycia kodu.

## <a name="see-also"></a>Zobacz także

- [Dodawanie testów jednostkowych do C++ istniejących aplikacji](../test/how-to-use-microsoft-test-framework-for-cpp.md)
- [Korzystanie z elementu Microsoft.VisualStudio.TestTools.CppUnitTestFramework](how-to-use-microsoft-test-framework-for-cpp.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
- [Przewodnik: Tworzenie i używanie biblioteki dołączanej dynamicznieC++()](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [Importowanie i eksportowanie](/cpp/build/importing-and-exporting)
