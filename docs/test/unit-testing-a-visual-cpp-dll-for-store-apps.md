---
title: Jak przetestować bibliotekę DLL języka C++ dla aplikacji platformy uniwersalnej systemu Windows
ms.date: 05/01/2019
ms.topic: conceptual
ms.author: corob
manager: jillfra
ms.workload:
- uwp
author: corob-msft
ms.openlocfilehash: 540ff59838343988e7a27f42f8a10d723de1f649
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77274456"
---
# <a name="how-to-test-a-c-dll"></a>Jak przetestować bibliotekę DLL języka C++

W tym temacie opisano jeden ze sposobów tworzenia testów jednostkowych dla biblioteki DLL języka C++ dla aplikacji platformy uniwersalnej systemu Windows (UWP) z platformą testów firmy Microsoft dla języka C++. Biblioteka DLL RooterLib demonstruje niejasne wspomnienia teorii limitu z rachunku, implementując funkcję, która oblicza oszacowanie pierwiastka kwadratowego danej liczby. Biblioteka DLL może następnie zostać uwzględniona w aplikacji platformy uniwersalnej systemu i platformy uniwersalnej systemu, która pokazuje użytkownikowi zabawne rzeczy, które można wykonać za pomocą matematyki.

W tym temacie pokazano, jak używać testowania jednostkowego jako pierwszego kroku w rozwoju. W tym podejściu najpierw napisać metodę testową, która weryfikuje określone zachowanie w systemie, który testujesz, a następnie napisać kod, który przechodzi test. Poprzez wprowadzenie zmian w kolejności następujących procedur, można odwrócić tę strategię, aby najpierw napisać kod, który chcesz przetestować, a następnie napisać testy jednostkowe.

W tym temacie utworzy się również pojedyncze rozwiązanie programu Visual Studio i oddzielne projekty dla testów jednostkowych i biblioteki DLL, które chcesz przetestować. Można również uwzględnić testy jednostkowe bezpośrednio w projekcie biblioteki DLL lub można utworzyć oddzielne rozwiązania dla testów jednostkowych i . Dll. Zobacz [Dodawanie testów jednostkowych do istniejących aplikacji języka C++,](../test/how-to-use-microsoft-test-framework-for-cpp.md) aby uzyskać porady dotyczące struktury, której należy użyć.

## <a name="create-the-solution-and-the-unit-test-project"></a><a name="Create_the_solution_and_the_unit_test_project"></a>Tworzenie rozwiązania i projektu testu jednostkowego

::: moniker range="vs-2019"

Zacznij od utworzenia nowego projektu testowego. W menu **Plik** wybierz polecenie **Nowy** > **projekt**. W oknie **dialogowym Utwórz nowy projekt** wpisz "test" w polu wyszukiwania, a następnie ustaw **język** na C++. Następnie wybierz aplikację **testu jednostkowego (Universal Windows)** z listy szablonów projektów.

   ![Tworzenie nowego projektu testowego platformy uniwersalnej systemuśpiłtnego](media/vs-2019/cpp-new-uwp-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

Zacznij od utworzenia nowego projektu testowego. W menu **Plik** wybierz polecenie **Nowy** > **projekt**. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Zainstalowany** > **program Visual C++** i wybierz pozycję System Windows **Universal**. Następnie wybierz aplikację **testu jednostkowego (Universal Windows)** z listy szablonów projektów.

::: moniker-end

1. W oknie dialogowym Nowy projekt rozwiń węzeł **Zainstalowany** > **program Visual C++** i wybierz pozycję System Windows **Universal**. Następnie wybierz aplikację **testu jednostkowego (Universal Windows)** z listy szablonów projektów.

2. Nazwij `RooterLibTests`projekt ; określić lokalizację; nazwa roztworu; `RooterLib` i upewnij się, że **pole wyboru Utwórz katalog dla rozwiązania.**

     ![Określanie nazwy i lokalizacji rozwiązania i projektu](../test/media/ute_cpp_windows_unittestlib_createspecs.png)

3. W nowym projekcie otwórz **unittest1.cpp**.

     ![unittest1.cpp](../test/media/ute_cpp_windows_unittest1_cpp.png)

     Należy pamiętać, że:

    - Każdy test jest `TEST_METHOD(YourTestName){...}`definiowany za pomocą programu .

         Nie trzeba pisać podpisu funkcji konwencjonalnych. Podpis jest tworzony przez TEST_METHOD makra. Makro generuje funkcję wystąpienia, która zwraca void. Generuje również funkcję statyczną, która zwraca informacje o metodzie testowej. Te informacje umożliwiają eksploratorowi testów znalezienie metody.

    - Metody testowe są pogrupowane w klasy przy użyciu . `TEST_CLASS(YourClassName){...}`

         Po uruchomieniu testów tworzone jest wystąpienie każdej klasy testowej. Metody testowe są wywoływane w nieokreślonej kolejności. Można zdefiniować specjalne metody, które są wywoływane przed i po każdym module, klasy lub metody. Aby uzyskać więcej informacji, zobacz [Korzystanie z programu Microsoft.VisualStudio.TestTools.CppUnitTestFramework](how-to-use-microsoft-test-framework-for-cpp.md).

## <a name="verify-that-the-tests-run-in-test-explorer"></a><a name="Verify_that_the_tests_run_in_Test_Explorer"></a>Sprawdź, czy testy są uruchamiane w Eksploratorze testów

1. Wstaw kod testowy:

    ```cpp
    TEST_METHOD(TestMethod1)
    {
        Assert::AreEqual(1,1);
    }
    ```

     Należy zauważyć, że `Assert` klasa zawiera kilka metod statycznych, które można użyć do weryfikacji wyników w metodach testowych.

2. W menu **Test** wybierz polecenie **Uruchom,** a następnie wybierz polecenie **Uruchom wszystko**.

     Projekt testowy tworzy i uruchamia. Zostanie wyświetlone okno **Eksploratora testów,** a test zostanie wyświetlony w obszarze **Testy przeszły**. Okienko **Podsumowanie** w dolnej części okna zawiera dodatkowe szczegóły dotyczące wybranego testu.

     ![Eksplorator testów](../test/media/ute_cpp_testexplorer_testmethod1.png)

## <a name="add-the-dll-project-to-the-solution"></a><a name="Add_the_DLL_project_to_the_solution"></a>Dodawanie projektu biblioteki DLL do rozwiązania

::: moniker range="vs-2019"

W **Eksploratorze rozwiązań**wybierz nazwę rozwiązania. Z menu skrótów wybierz polecenie **Dodaj**, a następnie **pozycję Nowy projekt**. W oknie **dialogowym Dodaj nowy projekt** ustaw **język** na C++ i wpisz "DLL" w polu wyszukiwania. Z listy wyników wybierz **pozycję Unit Test App (Universal Windows - C++/CX).**

![Tworzenie projektu RooterLib](../test/media/vs-2019/cpp-new-uwp-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"
W **Eksploratorze rozwiązań**wybierz nazwę rozwiązania. Z menu skrótów wybierz polecenie **Dodaj**, a następnie **pozycję Nowy projekt**.

![Tworzenie projektu RooterLib](../test/media/ute_cpp_windows_rooterlib_create.png)

::: moniker-end

1. W oknie dialogowym **Dodawanie nowego projektu** wybierz pozycję **DLL (aplikacje platformy uniwersalnej systemu Windows).**

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

     Komentarze wyjaśniają blok ifdef nie tylko deweloperowi biblioteki DLL, ale każdemu, kto odwołuje się do biblioteki DLL w swoim projekcie. Symbol ROOTERLIB_EXPORTS można dodać do wiersza polecenia przy użyciu właściwości projektu biblioteki DLL.

     Klasa `CRooterLib` deklaruje konstruktora `SqareRoot` i estymatora metody.

3. Dodaj symbol ROOTERLIB_EXPORTS do wiersza polecenia.

    1. W **Eksploratorze rozwiązań**wybierz projekt **RooterLib,** a następnie wybierz polecenie Właściwości z menu **skrótów.**

         ![Dodawanie definicji symbolu preprocesora](../test/media/ute_cpp_windows_addpreprocessorsymbol.png)

    2. W oknie dialogowym **Strona właściwości RooterLib** rozwiń węzeł **Właściwości konfiguracji**, rozwiń węzeł **C++** i wybierz pozycję **Preprocesor**.

    3. Z listy **Definicje preprocesora** wybierz `ROOTERLIB_EXPORTS` ** \<pozycję Edytuj...>,** a następnie dodaj okno **dialogowe Definicje preprocesora.**

4. Dodaj minimalne implementacje zadeklarowanych funkcji. Otwórz *plik RooterLib.cpp* i dodaj następujący kod:

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

## <a name="make-the-dll-functions-visible-to-the-test-code"></a><a name="make_the_dll_functions_visible_to_the_test_code"></a>Uwidocznić funkcje dll w kodzie testowym

1. Dodaj RooterLib do projektu RooterLibTests.

   1. W **Eksploratorze rozwiązań**wybierz projekt **RooterLibTests,** a następnie w menu skrótów wybierz polecenie **Dodaj** > **odwołanie.**

   1. W oknie dialogowym **Dodawanie odwołania** wybierz pozycję **Projekty**. Następnie wybierz element **RouterLib.**

2. Dołącz plik nagłówka RooterLib w *pliku unittest1.cpp*.

   1. Otwórz *unittest1.cpp*.

   2. Dodaj ten kod `#include "CppUnitTest.h"` poniżej wiersza:

       ```cpp
       #include "..\RooterLib\RooterLib.h"
       ```

3. Dodaj test, który używa importowanej funkcji. Dodaj następujący kod do *unittest1.cpp:*

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

    Nowy test pojawia się w **Eksploratorze testów** w węźle **Nie uruchamiaj testów.**

5. W **Eksploratorze testów**wybierz pozycję **Uruchom wszystko**.

    ![Test podstawowy zdawany test](../test/media/ute_cpp_testexplorer_basictest.png)

   Skonfigurowano projekty testów i kodu i zweryfikowano, że można uruchomić testy, które uruchamiają funkcje w projekcie kodu. Teraz możesz zacząć pisać prawdziwe testy i kod.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a><a name="Iteratively_augment_the_tests_and_make_them_pass"></a>Iteratively zwiększyć testy i uczynić je przejść

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
    > Zaleca się, aby nie zmieniać testów, które przeszły. Zamiast tego dodaj nowy test, zaktualizuj kod, aby test przebiegł pomyślnie, a następnie dodaj kolejny test i tak dalej.
    >
    > Gdy użytkownicy zmienią swoje wymagania, wyłącz testy, które nie są już poprawne. Napisz nowe testy i spraw, aby działały po kolei, w ten sam przyrostowy sposób.

2. W **Eksploratorze testów**wybierz pozycję **Uruchom wszystko**.

3. Test zakończy się niepowodzeniem.

     ![Test rangetest kończy się niepowodzeniem](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Sprawdź, czy każdy test nie powiedzie się natychmiast po jego zapisaniu. Pomaga to uniknąć łatwego błędu pisania testu, który nigdy nie kończy się niepowodzeniem.

4. Popraw kod w ramach testu, tak aby nowy test przebiegał pomyślnie. Dodaj następujące elementy do *pliku RooterLib.cpp:*

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

5. Skompiluj rozwiązanie, a następnie w **Eksploratorze testów**wybierz pozycję **Uruchom wszystko**.

     Oba testy przechodzą.

> [!TIP]
> Opracowanie kodu przez dodanie testów po jednym na raz. Upewnij się, że wszystkie testy przechodzą po każdej iteracji.

## <a name="debug-a-failing-test"></a><a name="Debug_a_failing_test"></a>Debugowanie testu nie po awarii

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

2. W **Eksploratorze testów**wybierz pozycję **Uruchom wszystko**.

    Test zakończy się niepowodzeniem. Wybierz nazwę testu w **Eksploratorze testów**. Twierdzenie nie powiodło się jest wyróżniony. Komunikat o błędzie jest widoczny w okienku szczegółów **Eksploratora testów**.

    ![Testy NegativeRangeTests nie powiodły się](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

3. Aby zobaczyć, dlaczego test nie powiedzie się, krok po kroku funkcji:

   1. Ustaw punkt przerwania na `SquareRoot` początku funkcji.

   2. W menu skrótów testu nie powiodło się wybierz polecenie **Debugowanie wybranych testów**.

        Gdy run zatrzymuje się w punkcie przerwania, krok po kroku kodu.

   3. Dodaj kod do *RooterLib.cpp,* aby złapać wyjątek:

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

   1. W **Eksploratorze testów**wybierz opcję **Uruchom wszystko,** aby przetestować poprawioną metodę i upewnij się, że nie wprowadzono regresji.

   Wszystkie testy teraz przechodzą.

   ![Wszystkie testy przechodzą zdać](../test/media/ute_ult_alltestspass.png)

## <a name="refactor-the-code-without-changing-tests"></a><a name="Refactor_the_code_without_changing_tests"></a>Refaktoryzuje kod bez zmiany testów

1. Uprość centralne `SquareRoot` obliczenia w funkcji:

    ```csharp
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;
    ```

2. Wybierz **pozycję Uruchom wszystko,** aby przetestować metodę refaktoryzowania i upewnij się, że nie wprowadzono regresji.

    > [!TIP]
    > Stabilny zestaw dobrych testów jednostkowych daje pewność, że nie wprowadzono błędów po zmianie kodu.
    >
    > Zachowaj refaktoryzowania oddzielnie od innych zmian.
