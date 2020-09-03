---
title: Testowanie jednostkowe Visual C++ DLL dla aplikacji ze sklepu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 24afc90a-8774-4699-ab01-6602a7e6feb2
caps.latest.revision: 15
author: alexhomer1
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d5f86eb40e1401f98a4c66d0b971fb006762cc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659692"
---
# <a name="unit-testing-a-visual-c-dll-for-store-apps"></a>Testowanie jednostkowe Visual C++ DLL dla aplikacji ze sklepu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano jeden ze sposobów tworzenia testów jednostkowych dla bibliotek DLL języka C++ dla aplikacji ze sklepu Windows. Biblioteka DLL RooterLib pokazuje niejasne informacje o limicie teoretycznym od calculus przez implementację funkcji, która oblicza oszacowanie wartości pierwiastek kwadratowy danej liczby. Biblioteka DLL może zostać następnie dołączona do aplikacji ze sklepu Windows, która przedstawia użytkownikowi zabawne rzeczy, które można wykonać za pomocą obliczeń matematycznych.

 W tym temacie przedstawiono sposób korzystania z testów jednostkowych jako pierwszego kroku projektowania. W tym podejściu najpierw napiszesz metodę testową, która weryfikuje określone zachowanie w testowanym systemie, a następnie pisze kod, który przekazuje test. Wprowadzając zmiany w kolejności następującej procedury, można odwrócić tę strategię, aby najpierw napisać kod, który ma zostać przetestowany, a następnie napisać testy jednostkowe.

 W tym temacie jest również tworzone pojedyncze rozwiązanie programu Visual Studio i oddzielne projekty dla testów jednostkowych i biblioteki DLL, która ma zostać przetestowana. Możesz również uwzględnić testy jednostkowe bezpośrednio w projekcie DLL lub utworzyć oddzielne rozwiązania dla testów jednostkowych i. Bibliotece. Zobacz [Dodawanie testów jednostkowych do istniejących aplikacji C++](../test/unit-testing-existing-cpp-applications-with-test-explorer.md) , aby uzyskać wskazówki dotyczące struktury do użycia.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> W tym temacie
 Ten temat przeprowadzi Cię przez następujące zadania:

 [Utwórz rozwiązanie i projekt testu jednostkowego](#BKMK_Create_the_solution_and_the_unit_test_project)

 [Sprawdź, czy testy są uruchamiane w Eksploratorze testów](#BKMK_Verify_that_the_tests_run_in_Test_Explorer)

 [Dodawanie projektu DLL do rozwiązania](#BKMK_Add_the_DLL_project_to_the_solution)

 [Połącz projekt testowy z projektem dll](#BKMK_Couple_the_test_project_to_the_dll_project)

 [Iteracyjnie rozszerza testy i przekazują je](#BKMK_Iteratively_augment_the_tests_and_make_them_pass)

 [Debuguj test zakończony niepowodzeniem](#BKMK_Debug_a_failing_test)

 [Refaktoryzacja kodu bez zmiany testów](#BKMK_Refactor_the_code_without_changing_tests)

## <a name="create-the-solution-and-the-unit-test-project"></a><a name="BKMK_Create_the_solution_and_the_unit_test_project"></a> Utwórz rozwiązanie i projekt testu jednostkowego

1. W menu **plik** wybierz pozycję **Nowy**, a następnie wybierz pozycję **Nowy projekt**.

2. W oknie dialogowym Nowy projekt rozwiń węzeł **zainstalowane**, rozwiń węzeł **Visual C++** i wybierz pozycję **Sklep Windows**. Następnie wybierz pozycję **Biblioteka testów jednostkowych (aplikacje ze sklepu Windows)** z listy szablonów projektu.

     ![Tworzenie biblioteki testów jednostkowych C&#43;&#43; ](../test/media/ute-cpp-windows-unittestlib-create.png "UTE_Cpp_windows_UnitTestLib_Create")

3. Nazwij projekt `RooterLibTests` ; Określ lokalizację; Nadaj nazwę rozwiązaniu i upewnij się, `RooterLib` że jest zaznaczone pole wyboru **Utwórz katalog dla rozwiązania** .

     ![Określ rozwiązanie i nazwę projektu i lokalizację](../test/media/ute-cpp-windows-unittestlib-createspecs.png "UTE_Cpp_windows_UnitTestLib_CreateSpecs")

4. W nowym projekcie Otwórz **UnitTest1. cpp**.

     ![UnitTest1. cpp](../test/media/ute-cpp-windows-unittest1-cpp.png "UTE_Cpp_windows_unittest1_cpp")

     Należy pamiętać, że:

    - Każdy test jest definiowany przy użyciu `TEST_METHOD(YourTestName){...}` .

         Nie trzeba pisać sygnatury funkcji konwencjonalnej. Podpis jest tworzony przez makro TEST_METHOD. Makro generuje funkcję wystąpienia zwracającą typ void. Generuje również funkcję statyczną, która zwraca informacje o metodzie testowej. Te informacje umożliwiają Eksploratorowi testów znalezienie metody.

    - Metody testowe są pogrupowane w klasy przy użyciu `TEST_CLASS(YourClassName){...}` .

         Gdy testy są uruchamiane, tworzone jest wystąpienie każdej klasy testowej. Metody testowe są wywoływane w nieokreślonej kolejności. Można zdefiniować metody specjalne, które są wywoływane przed i po każdym module, klasie lub metodzie. Aby uzyskać więcej informacji, zobacz [using Microsoft. VisualStudio. TestTools. CppUnitTestFramework](../test/using-microsoft-visualstudio-testtools-cppunittestframework.md) w bibliotece MSDN.

## <a name="verify-that-the-tests-run-in-test-explorer"></a><a name="BKMK_Verify_that_the_tests_run_in_Test_Explorer"></a> Sprawdź, czy testy są uruchamiane w Eksploratorze testów

1. Wstaw kod testu:

    ```cpp
    TEST_METHOD(TestMethod1)
    {
        Assert::AreEqual(1,1);
    }
    ```

     Należy zauważyć, że `Assert` Klasa zawiera kilka metod statycznych, których można użyć do sprawdzenia wyników w metodach testowych.

2. W menu **test** wybierz polecenie **Uruchom** , a następnie wybierz polecenie **Uruchom wszystkie**.

     Projekt testowy zostanie skompilowany i uruchomiony. Zostanie wyświetlone okno Eksplorator testów, a test zostanie wyświetlony na liście **zakończonych testów**. Okienko Podsumowanie u dołu okna zawiera dodatkowe szczegółowe informacje o wybranym teście.

     ![Eksplorator testów](../test/media/ute-cpp-testexplorer-testmethod1.png "UTE_Cpp_TestExplorer_TestMethod1")

## <a name="add-the-dll-project-to-the-solution"></a><a name="BKMK_Add_the_DLL_project_to_the_solution"></a> Dodawanie projektu DLL do rozwiązania

1. W Eksplorator rozwiązań wybierz nazwę rozwiązania. Z menu skrótów wybierz polecenie **Dodaj**, a następnie **Dodaj nowy projekt**.

     ![Tworzenie projektu RooterLib](../test/media/ute-cpp-windows-rooterlib-create.png "UTE_Cpp_windows_RooterLib_Create")

2. W oknie dialogowym **Dodaj nowy projekt** wybierz pozycję **dll (aplikacje ze sklepu Windows)**.

3. Dodaj następujący kod do pliku **RooterLib. h** :

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

     Komentarze wyjaśniają blok ifdef nie tylko dla dewelopera biblioteki DLL, ale do każdego, kto odwołuje się do biblioteki DLL w projekcie. Możesz dodać symbol ROOTERLIB_EXPORTS do wiersza polecenia, używając właściwości projektu biblioteki DLL.

     `CRooterLib`Klasa deklaruje konstruktora i `SqareRoot` metodę szacowania.

4. Dodaj symbol ROOTERLIB_EXPORTS do wiersza polecenia.

    1. W Eksplorator rozwiązań wybierz projekt **RooterLib** , a następnie wybierz polecenie **Właściwości** z menu skrótów.

         ![Dodaj definicję symbolu preprocesora](../test/media/ute-cpp-windows-addpreprocessorsymbol.png "UTE_Cpp_windows_AddPreprocessorSymbol")

    2. Na stronie właściwości RooterLib rozwiń węzeł **Właściwości konfiguracji**, rozwiń węzeł **C++** i wybierz **preprocesor**.

    3. Wybierz **\<Edit...>** z listy **Definicje preprocesora** , a następnie Dodaj w oknie `ROOTERLIB_EXPORTS` dialogowym Definicje preprocesora.

5. Dodaj minimalne implementacje zadeklarowanych funkcji. Otwórz **RooterLib. cpp** i Dodaj następujący kod:

    ```
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

## <a name="couple-the-test-project-to-the-dll-project"></a><a name="BKMK_Couple_the_test_project_to_the_dll_project"></a> Połącz projekt testowy z projektem dll

1. Dodaj RooterLib do projektu RooterLibTests.

   1. W Eksplorator rozwiązań wybierz projekt **RooterLibTests** , a następnie wybierz **odwołania...** w menu skrótów.

   2. W oknie dialogowym właściwości projektu RooterLib rozwiń węzeł **wspólne właściwości** i wybierz pozycję **Struktura i odwołania**.

   3. Wybierz pozycję **Dodaj nowe odwołanie..** .

   4. W oknie dialogowym **Dodawanie odwołania** rozwiń węzeł **rozwiązanie** , a następnie wybierz pozycję **projekty**. Następnie wybierz element **RouterLib** .

2. Dołącz plik nagłówka RooterLib w **UnitTest1. cpp**.

   1. Otwórz **UnitTest1. cpp**.

   2. Dodaj następujący kod do `#include "CppUnitTest.h"` wiersza:

       ```cpp
       #include "..\RooterLib\RooterLib.h"
       ```

3. Dodaj test, który używa zaimportowanej funkcji. Dodaj następujący kod do **UnitTest1. cpp**:

   ```
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

    Nowy test zostanie wyświetlony w Eksploratorze testów w węźle **nie uruchomiono testy** .

5. W Eksploratorze testów wybierz opcję **Uruchom wszystkie**.

    ![Test podstawowy zakończony zakończono](../test/media/ute-cpp-testexplorer-basictest.png "UTE_Cpp_TestExplorer_BasicTest")

   Został skonfigurowany test i projekty kodu i zweryfikowane, że można uruchomić testy, które uruchamiają funkcje w projekcie kodu. Teraz możesz zacząć pisać prawdziwe testy i kod.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a><a name="BKMK_Iteratively_augment_the_tests_and_make_them_pass"></a> Iteracyjnie rozszerza testy i przekazują je

1. Dodaj nowy test:

    ```
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
    > Zalecamy, aby nie zmieniać testów, które zostały zakończone. Zamiast tego Dodaj nowy test, zaktualizuj kod tak, aby test zakończył się powodzeniem, a następnie Dodaj inny test i tak dalej.
    >
    >  Gdy użytkownicy zmienią swoje wymagania, należy wyłączyć testy, które nie są już poprawne. Napisz nowe testy i Przekształć je w jeden raz w ten sam przyrostowy sposób.

2. W Eksploratorze testów wybierz opcję **Uruchom wszystkie**.

3. Test zakończy się niepowodzeniem.

     ![RangeTest kończy się niepowodzeniem](../test/media/ute-cpp-testexplorer-rangetest-fail.png "UTE_Cpp_TestExplorer_RangeTest_Fail")

    > [!TIP]
    > Sprawdź, czy każdy test kończy się niepowodzeniem natychmiast po jego zapisaniu. Dzięki temu można uniknąć łatwego błędu podczas pisania testu, który nigdy nie powiedzie się.

4. Podnieś poziom testowanego kodu, tak aby nowe testy zostały przekazane. Dodaj następujący do **RooterLib. cpp**:

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

5. Skompiluj rozwiązanie, a następnie w Eksploratorze testów wybierz opcję **Uruchom wszystkie**.

     Oba testy zostały zakończone pomyślnie.

> [!TIP]
> Opracowuj kod przez dodanie testów pojedynczo. Upewnij się, że wszystkie testy są zakończone po każdej iteracji.

## <a name="debug-a-failing-test"></a><a name="BKMK_Debug_a_failing_test"></a> Debuguj test zakończony niepowodzeniem

1. Dodaj inny test do **UnitTest1. cpp**:

   ```
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

2. W Eksploratorze testów wybierz opcję **Uruchom wszystkie**.

    Test zakończy się niepowodzeniem. Wybierz nazwę testu w Eksploratorze testów. Niepowodzenie zostało wyróżnione. Komunikat o błędzie jest widoczny w okienku szczegółów w Eksploratorze testów.

    ![NegativeRangeTests nie powiodło się](../test/media/ute-cpp-testexplorer-negativerangetest-fail.png "UTE_Cpp_TestExplorer_NegativeRangeTest_Fail")

3. Aby zobaczyć dlaczego test nie powiedzie się, przechodzenie przez funkcję:

   1. Ustaw punkt przerwania na początku `SquareRoot` funkcji.

   2. W menu skrótów testu zakończonego niepowodzeniem wybierz **Debuguj wybrane testy**.

        Gdy przebieg zostanie zatrzymany w punkcie przerwania, przejdź do kodu.

   3. Dodaj kod do **RooterLib. cpp** , aby przechwycić wyjątek:

       ```
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

   1. W Eksploratorze testów wybierz opcję **Uruchom wszystkie** , aby przetestować poprawioną metodę i upewnić się, że regresja nie została wprowadzona.

   Wszystkie testy są teraz zakończone pomyślnie.

   ![Wszystkie testy zakończone powodzeniem](../test/media/ute-ult-alltestspass.png "UTE_ULT_AllTestsPass")

## <a name="refactor-the-code-without-changing-tests"></a><a name="BKMK_Refactor_the_code_without_changing_tests"></a> Refaktoryzacja kodu bez zmiany testów

1. Uprość Obliczanie centralne w `SquareRoot` funkcji:

    ```
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;

    ```

2. Wybierz opcję **Uruchom wszystkie** , aby przetestować metodę refaktoryzacji i upewnić się, że regresja nie została wprowadzona.

    > [!TIP]
    > Stabilny zestaw dobrych testów jednostkowych daje pewność, że podczas zmiany kodu nie wprowadzono usterek.
    >
    >  Kontynuuj refaktoryzację niezależnie od innych zmian.
