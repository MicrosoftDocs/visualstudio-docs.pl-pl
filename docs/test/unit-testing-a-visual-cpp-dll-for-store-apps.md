---
title: Jak przetestować bibliotekę DLL języka C++ dla aplikacji platformy UWP
description: Dowiedz się, jak tworzyć testy jednostkowe dla biblioteki DLL języka C++ dla aplikacji platforma uniwersalna systemu Windows za pomocą programu Microsoft Test Framework dla języka C++.
ms.custom: SEO-VS-2020
ms.date: 05/01/2019
ms.topic: how-to
ms.author: corob
manager: jmartens
ms.workload:
- uwp
author: corob-msft
ms.openlocfilehash: f1981b3876d2e42e992ef261738da2443edfc114
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2021
ms.locfileid: "112042915"
---
# <a name="how-to-test-a-c-dll"></a>Jak przetestować bibliotekę DLL w języku C++

W tym temacie opisano jeden ze sposobów tworzenia testów jednostkowych dla biblioteki DLL języka C++ dla aplikacji platforma uniwersalna systemu Windows (UWP) za pomocą programu Microsoft Test Framework dla języka C++. Biblioteka DLL RooterLib demonstruje niejasne pamięci teorii limitów z rachunku calculus przez zaimplementowanie funkcji, która oblicza oszacowanie pierwiastek kwadratowy danej liczby. Biblioteka DLL może być następnie dołączona do aplikacji platformy uniwersalnej systemu Windows, która pokazuje użytkownikowi zabawne rzeczy, które można wykonać za pomocą obliczeń matematycznych.

W tym temacie pokazano, jak używać testów jednostkowych jako pierwszego kroku w rozwoju. W tym podejściu najpierw napiszesz metodę testową, która weryfikuje określone zachowanie w testowym systemie, a następnie napiszesz kod, który pomyślnie przejdzie test. Przez wprowadzenie zmian w kolejności poniższych procedur można odwrócić tę strategię, aby najpierw napisać kod, który chcesz przetestować, a następnie napisać testy jednostkowe.

W tym temacie jest również Visual Studio rozwiązanie i oddzielne projekty dla testów jednostkowych i bibliotek DLL, które chcesz przetestować. Testy jednostkowe można również uwzględnić bezpośrednio w projekcie DLL lub utworzyć oddzielne rozwiązania dla testów jednostkowych i .DLL. Aby uzyskać porady dotyczące struktury do użycia, zobacz Dodawanie [testów jednostkowych](../test/how-to-use-microsoft-test-framework-for-cpp.md) do istniejących aplikacji języka C++.

## <a name="create-the-solution-and-the-unit-test-project"></a><a name="Create_the_solution_and_the_unit_test_project"></a> Tworzenie rozwiązania i projektu testu jednostkowego

::: moniker range=">=vs-2019"

Rozpocznij od utworzenia nowego projektu testowego. W menu **File (Plik)** wybierz pozycję New Project   >  **(Nowy projekt).** W **oknie dialogowym Create a New Project (Tworzenie** nowego projektu) wpisz "test" w polu wyszukiwania, a następnie ustaw **pozycję Language (Język) na** C++. Następnie wybierz **pozycję Aplikacja testów jednostkowych (uniwersalny system Windows)** z listy szablonów projektów.

   ![Tworzenie nowego projektu testowego platformy uniwersalnej systemu Windows](media/vs-2019/cpp-new-uwp-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

Rozpocznij od utworzenia nowego projektu testowego. W menu **File (Plik)** wybierz pozycję New Project   >  **(Nowy projekt).** W **oknie dialogowym Nowy projekt** rozwiń pozycję **Zainstalowane**  >  **Visual C++** i wybierz pozycję **Aplikacje uniwersalne systemu Windows.** Następnie wybierz **pozycję Aplikacja testów jednostkowych (uniwersalny system Windows)** z listy szablonów projektów.

::: moniker-end

1. W oknie dialogowym Nowy projekt rozwiń pozycję **Zainstalowane**  >  **Visual C++** wybierz pozycję **Aplikacje uniwersalne systemu Windows.** Następnie wybierz **pozycję Aplikacja testów jednostkowych (uniwersalny system Windows)** z listy szablonów projektów.

2. Nadaj projektowi nazwę ; określ lokalizację; nazwij rozwiązanie i upewnij się, że zaznaczono pole create `RooterLibTests` `RooterLib` directory for solution (Utwórz **katalog** dla rozwiązania).

     ![Określanie nazwy i lokalizacji rozwiązania oraz projektu](../test/media/ute_cpp_windows_unittestlib_createspecs.png)

3. W nowym projekcie otwórz **unittest1.cpp**.

     ![unittest1.cpp](../test/media/ute_cpp_windows_unittest1_cpp.png)

     Należy pamiętać, że:

    - Każdy test jest definiowany przy użyciu metody `TEST_METHOD(YourTestName){...}` .

         Nie trzeba pisać konwencjonalnego podpisu funkcji. Podpis jest tworzony przez TEST_METHOD. Makro generuje funkcję wystąpienia, która zwraca wartość void. Generuje również funkcję statyczną, która zwraca informacje o metodzie testowej. Te informacje umożliwiają eksploratorowi testów znalezienie metody .

    - Metody testowe są pogrupowane w klasy przy użyciu metody `TEST_CLASS(YourClassName){...}` .

         Po uruchomieniu testów tworzone jest wystąpienie każdej klasy testowej. Metody testowe są wywoływane w nieokreślonym porządku. Można zdefiniować specjalne metody wywoływane przed i po każdym module, klasie lub metodzie. Aby uzyskać więcej informacji, zobacz [Using Microsoft.VisualStudio.TestTools.CppUnitTestFramework](how-to-use-microsoft-test-framework-for-cpp.md).

## <a name="verify-that-the-tests-run-in-test-explorer"></a><a name="Verify_that_the_tests_run_in_Test_Explorer"></a> Sprawdzanie, czy testy są uruchamiane w Eksploratorze testów

1. Wstaw kod testowy:

    ```cpp
    TEST_METHOD(TestMethod1)
    {
        Assert::AreEqual(1,1);
    }
    ```

     Zwróć uwagę, `Assert` że klasa udostępnia kilka metod statycznych, których można użyć do zweryfikowania wyników w metodach testowych.

2. W menu **Test** wybierz pozycję **Uruchom,** a następnie wybierz **pozycję Uruchom wszystko.**

     Projekt testowy jest kompilowany i uruchamiany. Zostanie **wyświetlone okno Eksplorator** testów, a test zostanie wyświetlony w obszarze Testy pomyślnie **przekazane.** Okienko **Podsumowanie** w dolnej części okna zawiera dodatkowe szczegóły dotyczące wybranego testu.

     ![Eksplorator testów](../test/media/ute_cpp_testexplorer_testmethod1.png)

## <a name="add-the-dll-project-to-the-solution"></a><a name="Add_the_DLL_project_to_the_solution"></a> Dodawanie projektu DLL do rozwiązania

::: moniker range=">=vs-2019"

W **Eksplorator rozwiązań** wybierz nazwę rozwiązania. Z menu skrótów wybierz pozycję **Dodaj**, a następnie **pozycję Nowy projekt.** W **oknie dialogowym Dodawanie nowego projektu** ustaw pozycję **Język** na C++ i wpisz "DLL" w polu wyszukiwania. Z listy wyników wybierz pozycję **Aplikacja testów jednostkowych (uniwersalny system Windows — C++/CX).**

![Tworzenie projektu RooterLib](../test/media/vs-2019/cpp-new-uwp-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"
W **Eksplorator rozwiązań** wybierz nazwę rozwiązania. Z menu skrótów wybierz pozycję **Dodaj**, a następnie **pozycję Nowy projekt.**

![Tworzenie projektu RooterLib](../test/media/ute_cpp_windows_rooterlib_create.png)

::: moniker-end

1. W **oknie dialogowym Dodawanie nowego** projektu wybierz pozycję **DLL (aplikacje platformy UWP).**

2. Dodaj następujący kod do pliku *RooterLib.h:*

    ```cpp
    // The following ifdef block is the standard way of creating macros which make exporting
    // from a DLL simpler. All files within this DLL are compiled with the ROOTERLIB_EXPORTS
    // symbol defined on the command line. This symbol should not be defined on any project
    // that uses this DLL. This way any other project whose source files include this file see
    // ROOTERLIB_API functions as being imported from a DLL, whereas this DLL sees symbols
    // defined with this macro as being exported.
    #ifdef ROOTERLIB_EXPORTS
    #define ROOTERLIB_API  __declspec(dllexport)
    #else
    #define ROOTERLIB_API __declspec(dllimport)
    #endif //ROOTERLIB_EXPORTS

    class ROOTERLIB_API CRooterLib {
    public:
        CRooterLib(void);
        double SquareRoot(double v);
    };
    ```

     Komentarze wyjaśniają blok ifdef nie tylko deweloperowi biblioteki dll, ale także każdemu, kto odwołuje się do biblioteki DLL w projekcie. Symbol ROOTERLIB_EXPORTS można dodać do wiersza polecenia przy użyciu właściwości projektu biblioteki DLL.

     Klasa `CRooterLib` deklaruje konstruktor i `SqareRoot` metodę szacowania.

3. Dodaj symbol ROOTERLIB_EXPORTS do wiersza polecenia.

    1. W **Eksplorator rozwiązań** wybierz projekt **RooterLib,** a następnie wybierz pozycję **Właściwości** z menu skrótów.

         ![Dodawanie definicji symbolu preprocesora](../test/media/ute_cpp_windows_addpreprocessorsymbol.png)

    2. W **oknie dialogowym Strona właściwości RooterLib** rozwiń **pozycję** Właściwości konfiguracji, rozwiń pozycję **C++** i wybierz **pozycję Preprocesor**.

    3. Wybierz **\<Edit...>** pozycję z listy **Definicje preprocesora,** a następnie dodaj w oknie dialogowym `ROOTERLIB_EXPORTS` **Definicje preprocesora.**

4. Dodanie minimalnych implementacji zadeklarowanych funkcji. Otwórz *katalog RooterLib.cpp* i dodaj następujący kod:

    ```cpp
    // constructor
    CRooterLib::CRooterLib()
    {
    }

    // Find the square root of a number.
    double CRooterLib::SquareRoot(double v)
    {
        return 0.0;
    }

    ```

## <a name="make-the-dll-functions-visible-to-the-test-code"></a><a name="make_the_dll_functions_visible_to_the_test_code"></a> Ujmij funkcje dll w kod testowy

1. Dodaj rooterLib do projektu RooterLibTests.

   1. W **Eksplorator rozwiązań** wybierz projekt **RooterLibTests,** a następnie wybierz pozycję **Dodaj** odwołanie w  >   menu skrótów.

   1. W **oknie dialogowym Dodawanie** odwołania wybierz pozycję **Projekty**. Następnie wybierz **element RouterLib.**

2. Dołącz plik nagłówka RooterLib w pliku *unittest1.cpp.*

   1. Otwórz *unittest1.cpp*.

   2. Dodaj ten kod pod `#include "CppUnitTest.h"` wierszem :

       ```cpp
       #include "..\RooterLib\RooterLib.h"
       ```

3. Dodaj test, który używa zaimportowanych funkcji. Dodaj następujący kod do *unittest1.cpp:*

   ```cpp
   TEST_METHOD(BasicTest)
   {
       CRooterLib rooter;
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

    Nowy test zostanie wyświetlony w **Eksploratorze testów** w **węźle Nie uruchamiaj testów.**

5. W **Eksploratorze testów** wybierz **pozycję Uruchom wszystko.**

    ![Test podstawowy minął](../test/media/ute_cpp_testexplorer_basictest.png)

   Po skonfigurowaniu testu i projektów kodu zweryfikowano, że można uruchamiać testy, które uruchamiają funkcje w projekcie kodu. Teraz możesz rozpocząć pisanie rzeczywistych testów i kodu.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a><a name="Iteratively_augment_the_tests_and_make_them_pass"></a> Iteracyjnie rozszerzają testy i sprawiają, że są one pass

1. Dodaj nowy test:

    ```cpp
    TEST_METHOD(RangeTest)
    {
        CRooterLib rooter;
        for (double v = 1e-6; v < 1e6; v = v * 3.2)
        {
            double expected = v;
            double actual = rooter.SquareRoot(v*v);
            double tolerance = expected/1000;
            Assert::AreEqual(expected, actual, tolerance);
        }
    };
    ```

    > [!TIP]
    > Zalecamy, aby nie zmieniać testów, które przeszły pomyślnie. Zamiast tego dodaj nowy test, zaktualizuj kod tak, aby test przebiegł pomyślnie, a następnie dodaj kolejny test i tak dalej.
    >
    > Gdy użytkownicy zmienią swoje wymagania, wyłącz testy, które nie są już poprawne. Napisz nowe testy i spraw, aby działały po jednym na raz, w ten sam przyrostowy sposób.

2. W **Eksploratorze testów** wybierz **pozycję Uruchom wszystko.**

3. Test kończy się niepowodzeniem.

     ![Test RangeTest kończy się niepowodzeniem](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Sprawdź, czy każdy test kończy się niepowodzeniem natychmiast po jego napisano. Pozwala to uniknąć prostego błędu podczas pisania testu, który nigdy nie zakończy się niepowodzeniem.

4. Ulepsz testowy kod, aby nowy test przebiegł pomyślnie. Dodaj następujący kod do *katalogu RooterLib.cpp:*

    ```cpp
    #include <math.h>
    ...
    // Find the square root of a number.
    double CRooterLib::SquareRoot(double v)
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

5. Skompilować rozwiązanie, a następnie w **Eksploratorze testów** wybierz **pozycję Uruchom wszystko.**

     Oba testy zostały zmieściły się.

> [!TIP]
> Opracuj kod, dodając testy po jednym na raz. Upewnij się, że wszystkie testy przechodzą po każdej iteracji.

## <a name="debug-a-failing-test"></a><a name="Debug_a_failing_test"></a> Debugowanie testu po awarii

1. Dodaj kolejny test do *unittest1.cpp:*

   ```cpp
   // Verify that negative inputs throw an exception.
    TEST_METHOD(NegativeRangeTest)
    {
      wchar_t message[200];
      CRooterLib rooter;
      for (double v = -0.1; v > -3.0; v = v - 0.5)
      {
        try
        {
          // Should raise an exception:
          double result = rooter.SquareRoot(v);

          swprintf_s(message, L"No exception for input %g", v);
          Assert::Fail(message, LINE_INFO());
        }
        catch (std::out_of_range ex)
        {
          continue; // Correct exception.
        }
        catch (...)
        {
          swprintf_s(message, L"Incorrect exception for %g", v);
          Assert::Fail(message, LINE_INFO());
        }
      }
   };
   ```

2. W **Eksploratorze testów** wybierz **pozycję Uruchom wszystko.**

    Test kończy się niepowodzeniem. Wybierz nazwę testu w **Eksploratorze testów.** Potwierdzenie, które zakończyło się niepowodzeniem, jest wyróżnione. Komunikat o błędzie jest widoczny w okienku szczegółów **Eksploratora testów.**

    ![Niepowodzenie testów NegativeRangeTests](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

3. Aby zobaczyć, dlaczego test kończy się niepowodzeniem, zapoznaj się z funkcją :

   1. Ustaw punkt przerwania na początku `SquareRoot` funkcji.

   2. W menu skrótów testu, który zakończył się niepowodzeniem, wybierz pozycję **Debuguj wybrane testy.**

        Gdy przebieg zatrzymuje się w punkcie przerwania, należy przejść przez kod.

   3. Dodaj kod do *rooterLib.cpp,* aby przechwyć wyjątek:

       ```cpp
       #include <stdexcept>
       ...
       double CRooterLib::SquareRoot(double v)
       {
           //Validate the input parameter:
           if (v < 0.0)
           {
             throw std::out_of_range("Can't do square roots of negatives");
           }
       ...

       ```

   1. W **Eksploratorze testów** wybierz **pozycję Uruchom** wszystko, aby przetestować poprawioną metodę i upewnić się, że nie wprowadzono regresji.

   Wszystkie testy zostały teraz zmieściły się.

   ![Wszystkie testy przebiegają](../test/media/ute_ult_alltestspass.png)

## <a name="refactor-the-code-without-changing-tests"></a><a name="Refactor_the_code_without_changing_tests"></a> Refaktoryzacja kodu bez zmiany testów

1. Uproszczenie centralnych obliczeń w `SquareRoot` funkcji:

    ```csharp
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;
    ```

2. Wybierz **pozycję Uruchom wszystko,** aby przetestować refaktoryzowana metodę i upewnić się, że nie wprowadzono regresji.

    > [!TIP]
    > Stabilny zestaw dobrych testów jednostkowych daje pewność, że nie wprowadzono usterek podczas zmiany kodu.
    >
    > Refaktoryzacja należy oddzielić od innych zmian.
