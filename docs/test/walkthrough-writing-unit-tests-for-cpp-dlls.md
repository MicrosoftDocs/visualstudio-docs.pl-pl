---
title: Pisano testy jednostkowe dla bibliotek DLL języka C++
description: Dowiedz się, jak opracowywać natywną bibliotekę DLL języka C++ przy użyciu metodologii "najpierw test". Rozpocznij od utworzenia natywnego projektu testowego.
ms.custom: SEO-VS-2020
ms.date: 06/13/2019
ms.topic: how-to
ms.author: corob
manager: markl
ms.workload:
- cplusplus
author: corob-msft
ms.openlocfilehash: cfdc580b94760cb0c5160918210ba6c3dd8fa2f6
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2021
ms.locfileid: "112042928"
---
# <a name="how-to-write-unit-tests-for-c-dlls"></a>Pisano testy jednostkowe dla bibliotek DLL języka C++

W tym przewodniku opisano sposób tworzenia natywnej biblioteki DLL języka C++ przy użyciu metodologii "najpierw test". Podstawowe kroki są następujące:

1. [Utwórz natywny projekt testowy](#create_test_project). Projekt testowy znajduje się w tym samym rozwiązaniu co projekt DLL.

2. [Utwórz projekt DLL.](#create_dll_project) Ten przewodnik tworzy nową bibliotekę DLL, ale procedura testowania istniejącej biblioteki DLL jest podobna.

3. [Ujmij funkcje DLL jako widoczne dla testów](#make_functions_visible).

4. [Iteracyjnie rozszerzają testy](#iterate). Zalecamy cykl "refaktoryzacja czerwony-zielony", w którym opracowywanie kodu jest prowadzone przez testy.

5. [Debugowanie testów, które się nie popełniły.](#debug) Testy można uruchamiać w trybie debugowania.

6. [Refaktoryzacja przy zachowaniu niezmienionych testów.](#refactor) Refaktoryzacja oznacza poprawę struktury kodu bez zmiany jego zachowania zewnętrznego. Można to zrobić, aby zwiększyć wydajność, rozszerzalność lub czytelność kodu. Ponieważ celem nie jest zmiana zachowania, nie należy zmieniać testów podczas zmiany refaktoryzacji kodu. Testy pomagają upewnić się, że podczas refaktoryzacji nie wprowadzono usterek.

7. [Sprawdź pokrycie](using-code-coverage-to-determine-how-much-code-is-being-tested.md). Testy jednostkowe są bardziej przydatne podczas wykonywania większej części kodu. Możesz dowiedzieć się, które części kodu zostały użyte w testach.

8. [Odizoluj jednostki od zasobów zewnętrznych.](using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md) Zazwyczaj biblioteka DLL jest zależna od innych składników systemu, które opracowujesz, takich jak inne biblioteki DLL, bazy danych lub podsystemy zdalne. Warto przetestować każdą jednostkę w izolacji od jej zależności. Składniki zewnętrzne mogą wolno uruchamiać testy. Podczas opracowywania pozostałe składniki mogą nie być kompletne.

## <a name="create-a-native-unit-test-project"></a><a name="create_test_project"></a> Tworzenie natywnego projektu testu jednostkowego

1. W menu **File (Plik)** wybierz pozycję New Project   >  **(Nowy projekt).**

     **Visual Studio 2017 i starsze:** Rozwiń zainstalowane **szablony,** Visual C++  >    >    >  **test.**
     **Visual Studio 2019:** ustaw język **na** C++ i wpisz "test" w polu wyszukiwania.

     Wybierz szablon **Native Unit Test Project (Natywny projekt testu** jednostkowego) lub wybierz preferowaną platformę. Jeśli wybierzesz inny szablon, taki jak Google Test lub Boost.Test, podstawowe zasady są takie same, chociaż niektóre szczegóły będą się różnić.

     W tym przewodniku projekt testowy nosi nazwę `NativeRooterTest` .

2. W nowym projekcie sprawdź **unittest1.cpp**

     ![Test project with TEST&#95;CLASS and TEST&#95;METHOD](../test/media/utecpp2.png)

     Zwróć uwagę, że:

    - Każdy test jest definiowany przy użyciu metody `TEST_METHOD(YourTestName){...}` .

         Nie trzeba pisać konwencjonalnej sygnatury funkcji. Podpis jest tworzony przez TEST_METHOD. Makro generuje funkcję wystąpienia, która zwraca wartość void. Generuje również funkcję statyczną, która zwraca informacje o metodzie testowej. Te informacje umożliwiają eksploratorowi testów znalezienie metody .

    - Metody testowe są pogrupowane w klasy przy użyciu metody `TEST_CLASS(YourClassName){...}` .

         Po uruchomieniu testów tworzone jest wystąpienie każdej klasy testowej. Metody testowe są wywoływane w nieokreślonym porządku. Możesz zdefiniować specjalne metody wywoływane przed i po każdym module, klasie lub metodzie.

3. Sprawdź, czy testy są uruchamiane w Eksploratorze testów:

    1. Wstaw kod testowy:

        ```cpp
        TEST_METHOD(TestMethod1)
        {
            Assert::AreEqual(1,1);
        }
        ```

         Zwróć `Assert` uwagę, że klasa udostępnia kilka metod statycznych, których można użyć do zweryfikowania wyników w metodach testowych.

    2. W menu **Test** wybierz polecenie **Uruchom**  >  **wszystkie testy.**

         Test jest kompilowany i uruchamiany.

         **Zostanie wyświetlony Eksplorator** testów.

         Test zostanie wyświetlony w obszarze **Testy pomyślnie przekazane.**

         ![Eksplorator testów jednostkowych z jednym pomyślnie przekazanym testem](../test/media/utecpp04.png)

## <a name="create-a-dll-project"></a><a name="create_dll_project"></a> Tworzenie projektu DLL

::: moniker range=">=vs-2019"

Poniższe kroki pokazują, jak utworzyć projekt DLL w programie Visual Studio 2019.

1. Utwórz projekt języka C++ za pomocą Kreatora pulpitu systemu **Windows:** kliknij prawym przyciskiem myszy nazwę rozwiązania w Eksplorator rozwiązań **a** następnie wybierz **polecenie Dodaj**  >  **nowy projekt.** Ustaw pozycję **Język** na C++, a następnie wpisz "windows" w polu wyszukiwania. Wybierz **pozycję Kreator pulpitu systemu Windows** z listy wyników.

     W tym przewodniku projekt nosi nazwę `RootFinder` .

2. Kliknij przycisk **Utwórz**. W następnym oknie dialogowym w obszarze **Typ aplikacji wybierz** pozycję Dynamic Link Library **(dll),** a następnie zaznacz **pole wyboru Eksportuj symbole**.

     Opcja **Eksportuj symbole** generuje wygodne makro, które służy do deklarowania wyeksportowanych metod.

     ![Zestaw kreatora projektu języka C++ dla bibliotek DLL i symboli eksportu](../test/media/vs-2019/windows-desktop-project-dll.png)

3. Zadeklaruj wyeksportowaną funkcję w pliku *h podmiotu* zabezpieczeń:

     ![Nowy projekt kodu DLL i plik h z makrami interfejsu API](../test/media/utecpp07.png)

     Deklarator `__declspec(dllexport)` powoduje, że publiczne i chronione składowe klasy są widoczne poza biblioteką DLL. Aby uzyskać więcej informacji, zobacz [Using dllimport and dllexport in C++ Classes (Używanie dllimport i dllexport w klasach języka C++).](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes)

4. W pliku *cpp podmiotu* zabezpieczeń dodaj minimalną treść funkcji:

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

1. Utwórz projekt języka C++ przy użyciu **szablonu Projekt Win32.**

     W tym przewodniku projekt nosi nazwę `RootFinder` .

2. Wybierz **pozycję DLL** i **eksportuj symbole** w Kreatorze aplikacji Win32.

     Opcja **Eksportuj symbole** generuje wygodne makro, które służy do deklarowania wyeksportowanych metod.

     ![Zestaw kreatora projektu języka C++ dla bibliotek DLL i symboli eksportu](../test/media/utecpp06.png)

3. Zadeklaruj wyeksportowaną funkcję w pliku *h podmiotu* zabezpieczeń:

     ![Nowy projekt kodu DLL i plik h z makrami interfejsu API](../test/media/utecpp07.png)

     Deklarator `__declspec(dllexport)` powoduje, że publiczne i chronione składowe klasy są widoczne poza biblioteką DLL. Aby uzyskać więcej informacji, zobacz [Using dllimport and dllexport in C++ Classes (Używanie dllimport i dllexport w klasach języka C++).](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes)

4. W pliku *cpp podmiotu* zabezpieczeń dodaj minimalną treść funkcji:

    ```cpp
        // Find the square root of a number.
        double CRootFinder::SquareRoot(double v)
        {
            return 0.0;
        }
    ```

::: moniker-end

## <a name="couple-the-test-project-to-the-dll-project"></a><a name="make_functions_visible"></a> Paruj projekt testowy z projektem DLL

1. Dodaj projekt DLL do odwołań projektu testowego:

   1. Kliknij prawym przyciskiem myszy węzeł projektu testowego w **programie Eksplorator rozwiązań** a następnie wybierz **polecenie Dodaj**  >  **odwołanie**.

   2. W **oknie dialogowym Dodawanie** odwołania wybierz projekt DLL, a następnie wybierz pozycję **Dodaj**.

        ![Właściwości projektu w języku C++ | Dodawanie nowego odwołania](../test/media/utecpp09.png)

2. W pliku cpp testu jednostkowego *jednostki* uwzględnij *plik h* kodu DLL:

   ```cpp
   #include "..\RootFinder\RootFinder.h"
   ```

3. Dodaj podstawowy test, który używa wyeksportowanych funkcji:

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

    Nowy test zostanie wyświetlony w **Eksploratorze testów.**

5. W **Eksploratorze testów** wybierz **pozycję Uruchom wszystko.**

    ![Test jednostkowy Eksploratora &#45; test podstawowy został pomyślnie przekazany](../test/media/utecpp10.png)

   Masz już zestaw testów i projekty kodu oraz sprawdzono, że można uruchamiać testy, które uruchamiają funkcje w projekcie kodu. Teraz możesz zacząć pisać prawdziwe testy i kod.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a><a name="iterate"></a> Iteracyjnie rozszerzają testy i sprawiają, że są one pass

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
    > Nie zaleca się zmieniania testów, które zostały pomyślnie przeprowadzone. Zamiast tego dodaj nowy test, zaktualizuj kod tak, aby test przebiegł pomyślnie, a następnie dodaj kolejny test i tak dalej.
    >
    > Gdy użytkownicy zmienią swoje wymagania, wyłącz testy, które nie są już poprawne. Napisz nowe testy i spraw, aby działały po jednym na raz, w ten sam sposób przyrostowy.

2. Skompilowanie rozwiązania, a następnie w **Eksploratorze testów** wybierz **pozycję Uruchom wszystko.**

     Nowy test kończy się niepowodzeniem.

     ![Test RangeTest kończy się niepowodzeniem](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Sprawdź, czy każdy test kończy się niepowodzeniem natychmiast po jego napisano. Pozwala to uniknąć prostego błędu podczas pisania testu, który nigdy nie zakończy się niepowodzeniem.

3. Ulepsz kod biblioteki DLL, aby nowy test przebiegł pomyślnie:

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

4. Skompilować rozwiązanie, a następnie w **Eksploratorze testów** wybierz **pozycję Uruchom wszystko.**

     Oba testy zostały zmieściły się.

     ![Test zakresu testów jednostkowych &#45; test został pomyślnie przekazany](../test/media/utecpp12.png)

    > [!TIP]
    > Opracuj kod, dodając testy po jednym na raz. Upewnij się, że wszystkie testy przechodzą testy po każdej iteracji.

## <a name="debug-a-failing-test"></a><a name="debug"></a> Debugowanie testu po awarii

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

2. Skompilowanie rozwiązania i wybranie opcji **Uruchom wszystko.**

3. Otwórz (lub kliknij dwukrotnie) test, który zakończył się niepowodzeniem.

     Potwierdzenie, które zakończyło się niepowodzeniem, jest wyróżnione. Komunikat o błędzie jest widoczny w okienku szczegółów **Eksploratora testów.**

     ![Niepowodzenie testów NegativeRangeTests](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

4. Aby zobaczyć, dlaczego test kończy się niepowodzeniem, zapoznaj się z funkcją :

    1. Ustaw punkt przerwania na początku funkcji SquareRoot.

    2. W menu skrótów testu, który zakończył się niepowodzeniem, wybierz pozycję **Debuguj wybrane testy.**

         Gdy przebieg zostanie zatrzymany w punkcie przerwania, należy przejść przez kod.

5. Wstaw kod w programowej funkcji:

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

6. Wszystkie testy teraz się pominą.

   ![Wszystkie testy zostały zmieściły się](../test/media/ute_ult_alltestspass.png)

::: moniker range="vs-2017"

> [!TIP]
> Jeśli poszczególne testy nie mają zależności uniemożliwiających ich uruchamianie w dowolnej kolejności, włącz równoległe wykonywanie testów za pomocą zrzutu ekranu przedstawiający przycisk przełączania równoległego wykonywania testów na pasku narzędzi ![ Eksploratora testów. Po wybraniu tego przycisku testy będą uruchamiane równolegle.](../test/media/ute_parallelicon-small.png) na pasku narzędzi. Może to znacznie skrócić czas uruchamiania wszystkich testów.

::: moniker-end

::: moniker range=">=vs-2019"

> [!TIP]
> Jeśli poszczególne testy nie mają zależności, które uniemożliwiają ich uruchamianie w dowolnej kolejności, włącz równoległe wykonywanie testów w menu ustawień paska narzędzi. Może to znacznie skrócić czas uruchamiania wszystkich testów.

::: moniker-end

## <a name="refactor-the-code-without-changing-tests"></a><a name="refactor"></a> Refaktoryzacja kodu bez zmiany testów

1. Uprość centralne obliczenie w funkcji SquareRoot:

    ```cpp
    // old code:
    //   result = result - (result*result - v)/(2*result);
    // new code:
         result = (result + v/result)/2.0;

    ```

2. Skompilowanie rozwiązania i wybranie opcji **Uruchom wszystko,** aby upewnić się, że nie wprowadzono błędu.

    > [!TIP]
    > Dobry zestaw testów jednostkowych daje pewność, że nie wprowadzono usterek podczas zmiany kodu.
    >
    > Refaktoryzacja należy oddzielić od innych zmian.

## <a name="next-steps"></a>Następne kroki

- **Izolacji.** Większość bibliotek DLL jest zależna od innych podsystemów, takich jak bazy danych i inne biblioteki DLL. Te inne składniki są często opracowywane równolegle. Aby umożliwić przeprowadzanie testów jednostkowych, gdy inne składniki nie są jeszcze dostępne, należy zastąpić makietę lub

- **Tworzenie testów weryfikacyjnych.** Testy na serwerze kompilacji twojego zespołu mogą być przeprowadzane w określonych odstępach czasu. Gwarantuje to, że usterki nie zostaną wprowadzone, gdy praca kilku członków zespołu jest zintegrowana.

- **Testy kontrolne.** Możesz wymuś, aby niektóre testy zostały wykonane przed sprawdzeniem kodu przez każdego członka zespołu w kontroli źródła. Zazwyczaj jest to podzbiór pełnego zestawu testów weryfikacji kompilacji.

   Można również określić minimalny poziom pokrycia kodu.

## <a name="see-also"></a>Zobacz też

- [Dodawanie testów jednostkowych do istniejących aplikacji C++](../test/how-to-use-microsoft-test-framework-for-cpp.md)
- [Korzystanie z Microsoft.VisualStudio.TestTools.CppUnitTestFramework](how-to-use-microsoft-test-framework-for-cpp.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
- [Przewodnik: Tworzenie i używanie biblioteki dołączanej dynamicznie (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [Importowanie i eksportowanie](/cpp/build/importing-and-exporting)
