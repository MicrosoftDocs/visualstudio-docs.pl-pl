---
title: 'Jak: Pisanie testów jednostkowych dla bibliotek DLL języka C++'
ms.date: 06/13/2019
ms.topic: conceptual
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: 752a2bb53e25954824a1400ee178cd0cbf4adcf2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77275425"
---
# <a name="how-to-write-unit-tests-for-c-dlls"></a>Jak: Pisanie testów jednostkowych dla bibliotek DLL języka C++

W tym instruktażu opisano sposób tworzenia natywnej biblioteki DLL języka C++ przy użyciu metodologii najpierw testowej. Podstawowe kroki są następujące:

1. [Utwórz natywny projekt testowy](#create_test_project). Projekt testowy znajduje się w tym samym rozwiązaniu co projekt DLL.

2. [Tworzenie projektu biblioteki DLL](#create_dll_project). W tym instruktażu tworzy nową bibliotekę DLL, ale procedura testowania istniejącej biblioteki DLL jest podobna.

3. [Spraw, aby funkcje biblioteki DLL były widoczne dla testów.](#make_functions_visible)

4. [Iteratively rozszerzyć testy](#iterate). Zaleca się cykl "red-green-refaktoryzator", w którym rozwój kodu jest prowadzony przez testy.

5. [Testy niedają debugowania](#debug). Testy można uruchamiać w trybie debugowania.

6. [Refaktoryzator przy zachowaniu testów bez zmian](#refactor). Refaktoryzowanie oznacza poprawę struktury kodu bez zmiany jego zachowania zewnętrznego. Można to zrobić, aby zwiększyć wydajność, rozszerzalność lub czytelność kodu. Ponieważ intencją nie jest zmiana zachowania, nie należy zmieniać testów podczas dokonywania refaktoryzacji zmiany w kodzie. Testy pomagają upewnić się, że nie wprowadzasz błędów podczas refaktoryzacji.

7. [Sprawdź zasięg](using-code-coverage-to-determine-how-much-code-is-being-tested.md). Testy jednostkowe są bardziej przydatne, gdy wykonują więcej kodu. Można odkryć, które części kodu zostały użyte przez testy.

8. [Izoluj jednostki od zasobów zewnętrznych](using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md). Zazwyczaj biblioteka DLL jest zależna od innych składników systemu, który tworzysz, takich jak inne biblioteki DLL, bazy danych lub zdalne podsystemy. Jest to przydatne do testowania każdej jednostki w izolacji od jej zależności. Komponenty zewnętrzne mogą sprawić, że testy będą działać wolno. Podczas programowania inne składniki mogą nie być kompletne.

## <a name="create-a-native-unit-test-project"></a><a name="create_test_project"></a>Tworzenie projektu testu jednostkowego natywnego

1. W menu **Plik** wybierz polecenie **Nowy** > **projekt**.

     **Visual Studio 2017 i starsze**: Rozwiń **zainstalowane** > **szablony** > **Visual C++** > **Test**.
     **Visual Studio 2019**: Ustaw **język** na C++ i wpisz "test" w polu wyszukiwania.

     Wybierz szablon **projektu testu jednostki natywnej** lub dowolną zainstalowaną strukturę. Jeśli wybierzesz inny szablon, taki jak Google Test lub Boost.Test, podstawowe zasady są takie same, chociaż niektóre szczegóły będą się różnić.

     W tym instruktażu projekt `NativeRooterTest`testowy nosi nazwę .

2. W nowym projekcie należy sprawdzić **unittest1.cpp**

     ![Projekt testowy z TEST&#95;CLASS i TEST&#95;METHOD](../test/media/utecpp2.png)

     Należy zauważyć, że:

    - Każdy test jest `TEST_METHOD(YourTestName){...}`definiowany za pomocą programu .

         Nie trzeba pisać podpisu funkcji konwencjonalnych. Podpis jest tworzony przez TEST_METHOD makra. Makro generuje funkcję wystąpienia, która zwraca void. Generuje również funkcję statyczną, która zwraca informacje o metodzie testowej. Te informacje umożliwiają eksploratorowi testów znalezienie metody.

    - Metody testowe są pogrupowane w klasy przy użyciu . `TEST_CLASS(YourClassName){...}`

         Po uruchomieniu testów tworzone jest wystąpienie każdej klasy testowej. Metody testowe są wywoływane w nieokreślonej kolejności. Można zdefiniować specjalne metody, które są wywoływane przed i po każdym module, klasy lub metody.

3. Sprawdź, czy testy są uruchamiane w Eksploratorze testów:

    1. Wstaw kod testowy:

        ```cpp
        TEST_METHOD(TestMethod1)
        {
            Assert::AreEqual(1,1);
        }
        ```

         Należy zauważyć, że `Assert` klasa zawiera kilka metod statycznych, które można użyć do weryfikacji wyników w metodach testowych.

    2. W menu **Test** wybierz polecenie **Uruchom** > **wszystkie testy**.

         Test tworzy i uruchamia.

         Pojawi się **Eksplorator testów.**

         Test pojawi się w obszarze **Testy zdań**.

         ![Eksplorator testów jednostkowych z jednym zdawanym testem](../test/media/utecpp04.png)

## <a name="create-a-dll-project"></a><a name="create_dll_project"></a>Tworzenie projektu biblioteki DLL

::: moniker range="vs-2019"

Poniższe kroki pokazują, jak utworzyć projekt biblioteki DLL w programie Visual Studio 2019.

1. Tworzenie projektu w języku C++ za pomocą **Kreatora pulpitu systemu Windows**: Kliknij prawym przyciskiem myszy nazwę rozwiązania w **Eksploratorze rozwiązań** i wybierz pozycję **Dodaj** > **nowy projekt**. Ustaw **język** na C++, a następnie wpisz "windows" w polu wyszukiwania. Z listy wyników wybierz **Kreatora pulpitu systemu Windows.**

     W tym instruktażu projekt `RootFinder`nosi nazwę .

2. Kliknij przycisk **Utwórz**. W następnym oknie dialogowym w obszarze **Typ aplikacji** wybierz pozycję **Biblioteka łączy dynamicznych (biblioteka dll),** a także zaznacz pozycję **Eksportuj symbole**.

     Opcja **Eksportuj symbole** generuje wygodne makro, którego można użyć do deklarowania eksportowanych metod.

     ![Kreator projektu języka C++ ustawiony dla bibliotek DLL i symboli eksportu](../test/media/vs-2019/windows-desktop-project-dll.png)

3. Zadeklaruj wyeksportowane funkcje w głównym pliku *h:*

     ![Nowy projekt kodu DLL i plik h z makrami API](../test/media/utecpp07.png)

     Deklarator `__declspec(dllexport)` powoduje, że publiczne i chronione elementy członkowskie klasy być widoczne poza biblioteką DLL. Aby uzyskać więcej informacji, zobacz [Korzystanie z dllimport i dllexport w klasach C++.](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes)

4. W głównym pliku *.cpp* dodaj minimalną treść dla funkcji:

    ```cpp
        // Find the square root of a number.
        double CRootFinder::SquareRoot(double v)
        {
            return 0.0;
        }
    ```

::: moniker-end

::: moniker range="vs-2017"

Poniższe kroki pokazują, jak utworzyć projekt biblioteki DLL w programie Visual Studio 2017.

1. Utwórz projekt W++ przy użyciu szablonu **projektu Win32.**

     W tym instruktażu projekt `RootFinder`nosi nazwę .

2. Wybierz **bibliotekę DLL** i **symbole eksportu** w Kreatorze aplikacji Win32.

     Opcja **Eksportuj symbole** generuje wygodne makro, którego można użyć do deklarowania eksportowanych metod.

     ![Kreator projektu języka C++ ustawiony dla bibliotek DLL i symboli eksportu](../test/media/utecpp06.png)

3. Zadeklaruj wyeksportowane funkcje w głównym pliku *h:*

     ![Nowy projekt kodu DLL i plik h z makrami API](../test/media/utecpp07.png)

     Deklarator `__declspec(dllexport)` powoduje, że publiczne i chronione elementy członkowskie klasy być widoczne poza biblioteką DLL. Aby uzyskać więcej informacji, zobacz [Korzystanie z dllimport i dllexport w klasach C++.](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes)

4. W głównym pliku *.cpp* dodaj minimalną treść dla funkcji:

    ```cpp
        // Find the square root of a number.
        double CRootFinder::SquareRoot(double v)
        {
            return 0.0;
        }
    ```

::: moniker-end

## <a name="couple-the-test-project-to-the-dll-project"></a><a name="make_functions_visible"></a>Połącz projekt testowy z projektem DLL

1. Dodaj projekt biblioteki DLL do odwołań do projektu testowego:

   1. Kliknij prawym przyciskiem myszy węzeł projektu testowego w **Eksploratorze rozwiązań** i wybierz polecenie **Dodaj** > **odwołanie**.

   2. W oknie dialogowym **Dodawanie odwołania** wybierz projekt biblioteki DLL i wybierz pozycję **Dodaj**.

        ![Właściwości projektu C++ | Dodaj nowe odwołanie](../test/media/utecpp09.png)

2. W głównym pliku testowym jednostki *.cpp* dołącz plik *.h* kodu DLL:

   ```cpp
   #include "..\RootFinder\RootFinder.h"
   ```

3. Dodaj test podstawowy, który używa wyeksportowanego przycisku funkcji:

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

5. W **Eksploratorze testów**wybierz pozycję **Uruchom wszystko**.

    ![Przebieg testu jednostkowego &#45; test podstawowy](../test/media/utecpp10.png)

   Skonfigurowano projekty testów i kodu i zweryfikowano, że można uruchomić testy, które uruchamiają funkcje w projekcie kodu. Teraz możesz zacząć pisać prawdziwe testy i kod.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a><a name="iterate"></a>Iteratively zwiększyć testy i uczynić je przejść

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
    > Zaleca się, aby nie zmieniać testów, które przeszły. Zamiast tego dodaj nowy test, zaktualizuj kod, aby test przebiegł pomyślnie, a następnie dodaj kolejny test i tak dalej.
    >
    > Gdy użytkownicy zmienią swoje wymagania, wyłącz testy, które nie są już poprawne. Napisz nowe testy i spraw, aby działały po kolei, w ten sam przyrostowy sposób.

2. Skompiluj rozwiązanie, a następnie w **Eksploratorze testów**wybierz pozycję **Uruchom wszystko**.

     Nowy test kończy się niepowodzeniem.

     ![Test rangetest kończy się niepowodzeniem](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Sprawdź, czy każdy test nie powiedzie się natychmiast po jego zapisaniu. Pomaga to uniknąć łatwego błędu pisania testu, który nigdy nie kończy się niepowodzeniem.

3. Popraw swój kod DLL, tak aby nowy test przebiegał pomyślnie:

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

4. Skompiluj rozwiązanie, a następnie w **Eksploratorze testów**wybierz pozycję **Uruchom wszystko**.

     Oba testy przechodzą.

     ![Przebieg testu jednostkowego &#45; przebiegu testów](../test/media/utecpp12.png)

    > [!TIP]
    > Opracowanie kodu przez dodanie testów po jednym na raz. Upewnij się, że wszystkie testy przechodzą po każdej iteracji.

## <a name="debug-a-failing-test"></a><a name="debug"></a>Debugowanie testu nie po awarii

1. Dodaj kolejny test:

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

2. Zbuduj rozwiązanie i wybierz **pozycję Uruchom wszystko**.

3. Otwórz (lub kliknij dwukrotnie) test nieu powiodła się.

     Twierdzenie nie powiodło się jest wyróżniony. Komunikat o błędzie jest widoczny w okienku szczegółów **Eksploratora testów**.

     ![Testy NegativeRangeTests nie powiodły się](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

4. Aby zobaczyć, dlaczego test nie powiedzie się, krok po kroku funkcji:

    1. Ustaw punkt przerwania na początku SquareRoot funkcji.

    2. W menu skrótów testu nie powiodło się wybierz polecenie **Debugowanie wybranych testów**.

         Gdy run zatrzymuje się w punkcie przerwania, krok po kroku kodu.

5. Wstaw kod do funkcji, którą tworzysz:

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

6. Wszystkie testy teraz przechodzą.

   ![Wszystkie testy przechodzą zdać](../test/media/ute_ult_alltestspass.png)

::: moniker range="vs-2017"

> [!TIP]
> Jeśli poszczególne testy nie mają żadnych zależności, które uniemożliwiają ich uruchamianie ![w dowolnej kolejności, włącz równoległe wykonanie](../test/media/ute_parallelicon-small.png) testu za pomocą ute&#95;parallelicon&#45;mały przycisk przełączania na pasku narzędzi. Może to znacznie skrócić czas pracy wszystkich testów.

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> Jeśli poszczególne testy nie mają żadnych zależności, które uniemożliwiają ich uruchamianie w dowolnej kolejności, włącz równoległe wykonanie testu w menu ustawień paska narzędzi. Może to znacznie skrócić czas pracy wszystkich testów.

::: moniker-end

## <a name="refactor-the-code-without-changing-tests"></a><a name="refactor"></a>Refaktoryzuje kod bez zmiany testów

1. Uprość centralne obliczenie w funkcji Kwadratroot:

    ```cpp
    // old code:
    //   result = result - (result*result - v)/(2*result);
    // new code:
         result = (result + v/result)/2.0;

    ```

2. Skompiluj rozwiązanie i wybierz **pozycję Uruchom wszystko**, aby upewnić się, że nie wprowadzono błędu.

    > [!TIP]
    > Dobry zestaw testów jednostkowych daje pewność, że nie wprowadzono błędów po zmianie kodu.
    >
    > Zachowaj refaktoryzowania oddzielnie od innych zmian.

## <a name="next-steps"></a>Następne kroki

- **Izolacji.** Większość bibliotek DLL jest zależna od innych podsystemów, takich jak bazy danych i inne biblioteki DLL. Te inne składniki są często opracowywane równolegle. Aby umożliwić przeprowadzanie testów jednostkowych, gdy inne komponenty nie są jeszcze dostępne, należy zastąpić

- **Kompilacja testów weryfikacyjnych.** Testy mogą być wykonywane na serwerze kompilacji zespołu w ustalonych odstępach czasu. Gwarantuje to, że błędy nie są wprowadzane, gdy praca kilku członków zespołu jest zintegrowany.

- **Testy kontrolne.** Można zalecić, że niektóre testy są wykonywane, zanim każdy członek zespołu sprawdza kod do kontroli źródła. Zazwyczaj jest to podzbiór pełnego zestawu testów weryfikacji kompilacji.

   Można również zalecić minimalny poziom pokrycia kodu.

## <a name="see-also"></a>Zobacz też

- [Dodawanie testów jednostkowych do istniejących aplikacji języka C++](../test/how-to-use-microsoft-test-framework-for-cpp.md)
- [Korzystanie z Microsoft.VisualStudio.TestTools.CppUnitTestFramework](how-to-use-microsoft-test-framework-for-cpp.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
- [Przewodnik: Tworzenie i używanie biblioteki łączy dynamicznych (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [Import i eksport](/cpp/build/importing-and-exporting)
