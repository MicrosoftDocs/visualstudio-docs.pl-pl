---
title: Jak przetestować C++ plik DLL dla aplikacji platformy UWP
ms.date: 05/01/2019
ms.topic: conceptual
ms.author: corob
manager: jillfra
ms.workload:
- uwp
author: corob-msft
ms.openlocfilehash: 540ff59838343988e7a27f42f8a10d723de1f649
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2020
ms.locfileid: "77274456"
---
# <a name="how-to-test-a-c-dll"></a>Jak przetestować C++ plik dll

W tym temacie opisano jeden ze sposobów tworzenia testów jednostkowych dla języka C++ bibliotek DLL z aplikacji platformy uniwersalnej Windows (UWP) przy użyciu Frameworka testów firmy Microsoft dla języka C++. Biblioteka DLL RooterLib pokazuje niejasne chwile teorii limit z calculus poprzez implementację funkcji, który oblicza oszacowanie pierwiastek kwadratowy z podanej liczbie. Biblioteki DLL, następnie mógłby być zawarty w aplikacji platformy uniwersalnej systemu Windows, która zawiera użytkownika fun rzeczy, które można wykonać za pomocą matematyczne.

W tym temacie dowiesz się, jak używać jednostki testowania jako pierwszy krok w rozwoju. W tym podejściu najpierw napisać metodę testową, która sprawdza określone zachowanie w systemie, które testujesz, a następnie napisać kod, który przejdzie test. Wycofanie tej strategii, wprowadzając zmiany kolejności poniższych procedur, w pierwszej operacji zapisu kod, który chcesz przetestować, a następnie napisz testy jednostkowe.

W tym temacie tworzy również jedno rozwiązanie Visual Studio i oddzielnych projektów dla testów jednostkowych i biblioteki DLL, która ma zostać przetestowana. Możesz również uwzględnić testy jednostkowe bezpośrednio w projekcie biblioteki DLL lub można utworzyć oddzielne rozwiązania dla testów jednostkowych i. BIBLIOTEKI DLL. Zobacz [Dodawanie testów jednostkowych do C++ istniejących aplikacji](../test/how-to-use-microsoft-test-framework-for-cpp.md) , aby uzyskać wskazówki dotyczące struktury do użycia.

## <a name="Create_the_solution_and_the_unit_test_project"></a>Utwórz rozwiązanie i projekt testu jednostkowego

::: moniker range="vs-2019"

Zacznij od utworzenia nowego projektu testowego. W menu **plik** wybierz **Nowy** **projekt** > . W oknie dialogowym **Tworzenie nowego projektu** wpisz "test" w polu wyszukiwania, a następnie ustaw **Język** na C++. Następnie wybierz pozycję **aplikacja testów jednostkowych (uniwersalna systemu Windows)** z listy szablonów projektu.

   ![Utwórz nowy projekt testu platformy UWP](media/vs-2019/cpp-new-uwp-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

Zacznij od utworzenia nowego projektu testowego. W menu **plik** wybierz **Nowy** **projekt** > . W oknie dialogowym **Nowy projekt** rozwiń węzeł **zainstalowane** >  **C++ Wizualizacja** i wybierz pozycję **Windows Universal**. Następnie wybierz pozycję **aplikacja testów jednostkowych (uniwersalna systemu Windows)** z listy szablonów projektu.

::: moniker-end

1. W oknie dialogowym Nowy projekt rozwiń węzeł **zainstalowane** > **Wizualizacja C++**  i wybierz pozycję **Windows Universal**. Następnie wybierz pozycję **aplikacja testów jednostkowych (uniwersalna systemu Windows)** z listy szablonów projektu.

2. Nadaj projektowi nazwę `RooterLibTests`; Określ lokalizację; Nazwij rozwiązanie `RooterLib`; Upewnij się, że jest zaznaczone pole wyboru **Utwórz katalog dla rozwiązania** .

     ![Określ nazwę rozwiązania i projektu i lokalizacji](../test/media/ute_cpp_windows_unittestlib_createspecs.png)

3. W nowym projekcie Otwórz **UnitTest1. cpp**.

     ![unittest1.cpp](../test/media/ute_cpp_windows_unittest1_cpp.png)

     Należy pamiętać, że:

    - Każdy test jest definiowany przy użyciu `TEST_METHOD(YourTestName){...}`.

         Nie trzeba napisać podpis konwencjonalnych funkcji. Podpis jest tworzony za pomocą makra TEST_METHOD. Makro generuje funkcją wystąpienia, która zwraca wartość void. Polecenie to generuje także funkcję statyczną, która zwraca informacje na temat metody testowej. Te informacje temu Eksplorator testów, można znaleźć metody.

    - Metody testowe są pogrupowane w klasy przy użyciu `TEST_CLASS(YourClassName){...}`.

         Gdy testy są uruchamiane, tworzone jest wystąpienie każdej klasy testu. Metody testowe są wywoływane w nieokreślonej kolejności. Można zdefiniować specjalne metody, które są wywoływane przed i po każdym modułu, klasy lub metody. Aby uzyskać więcej informacji, zobacz [using Microsoft. VisualStudio. TestTools. CppUnitTestFramework](how-to-use-microsoft-test-framework-for-cpp.md).

## <a name="Verify_that_the_tests_run_in_Test_Explorer"></a>Sprawdź, czy testy są uruchamiane w Eksploratorze testów

1. Wstaw kod testu:

    ```cpp
    TEST_METHOD(TestMethod1)
    {
        Assert::AreEqual(1,1);
    }
    ```

     Należy zauważyć, że Klasa `Assert` dostarcza kilka metod statycznych, których można użyć do sprawdzenia wyników w metodach testowych.

2. W menu **test** wybierz polecenie **Uruchom** , a następnie wybierz polecenie **Uruchom wszystkie**.

     Projekt testowy skompilowane i uruchomione. Zostanie wyświetlone okno **Eksplorator testów** , a test zostanie wyświetlony na liście **zakończonych testów**. Okienko **Podsumowanie** u dołu okna zawiera dodatkowe szczegółowe informacje o wybranym teście.

     ![Eksplorator testów](../test/media/ute_cpp_testexplorer_testmethod1.png)

## <a name="Add_the_DLL_project_to_the_solution"></a>Dodawanie projektu DLL do rozwiązania

::: moniker range="vs-2019"

W **Eksplorator rozwiązań**wybierz nazwę rozwiązania. Z menu skrótów wybierz polecenie **Dodaj**, a następnie **Nowy projekt**. W oknie dialogowym **Dodawanie nowego projektu** Ustaw **Język** na C++ i wpisz "dll" w polu wyszukiwania. Z listy wyników wybierz pozycję **aplikacja testów jednostkowych (Universal Windows- C++/CX)** .

![Utwórz projekt RooterLib](../test/media/vs-2019/cpp-new-uwp-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"
W **Eksplorator rozwiązań**wybierz nazwę rozwiązania. Z menu skrótów wybierz polecenie **Dodaj**, a następnie **Nowy projekt**.

![Utwórz projekt RooterLib](../test/media/ute_cpp_windows_rooterlib_create.png)

::: moniker-end

1. W oknie dialogowym **Dodaj nowy projekt** wybierz pozycję **dll (aplikacje platformy UWP)** .

2. Dodaj następujący kod do pliku *RooterLib. h* :

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

     Zostało wyjaśnione w komentarzach blok ifdef nie tylko do deweloperów biblioteki dll, ale dla każdego, kto odwołuje się do biblioteki DLL w projekcie. Możesz dodać ROOTERLIB_EXPORTS symbol do wiersza polecenia przy użyciu właściwości projektu biblioteki dll.

     Klasa `CRooterLib` deklaruje konstruktora i metodę `SqareRoot` szacowania.

3. Dodaj ROOTERLIB_EXPORTS symbol w wierszu polecenia.

    1. W **Eksplorator rozwiązań**wybierz projekt **RooterLib** , a następnie wybierz polecenie **Właściwości** z menu skrótów.

         ![Dodawanie definicji symboli preprocesora](../test/media/ute_cpp_windows_addpreprocessorsymbol.png)

    2. Na **stronie właściwości RooterLib** rozwiń węzeł **Właściwości konfiguracji**, rozwiń **C++** i wybierz **preprocesor**.

    3. Wybierz **\<Edytuj... >** z listy **Definicje preprocesora** , a następnie Dodaj `ROOTERLIB_EXPORTS` do okna dialogowego **Definicje preprocesora** .

4. Dodaj implementacje minimalne funkcje zadeklarowane. Otwórz *RooterLib. cpp* i Dodaj następujący kod:

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

## <a name="make_the_dll_functions_visible_to_the_test_code"></a>Uczyń funkcje biblioteki DLL widocznymi dla kodu testu

1. Dodaj RooterLib projektu RooterLibTests.

   1. W **Eksplorator rozwiązań**wybierz projekt **RooterLibTests** , a następnie wybierz pozycję **Dodaj** > **odwołanie** w menu skrótów.

   1. W oknie dialogowym **Dodaj odwołanie** wybierz pozycję **projekty**. Następnie wybierz element **RouterLib** .

2. Dołącz plik nagłówka RooterLib w *UnitTest1. cpp*.

   1. Otwórz *UnitTest1. cpp*.

   2. Dodaj następujący kod do `#include "CppUnitTest.h"` wiersza:

       ```cpp
       #include "..\RooterLib\RooterLib.h"
       ```

3. Dodaj test, który używa funkcji zaimportowane. Dodaj następujący kod do *UnitTest1. cpp*:

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

    Nowy test zostanie wyświetlony w **Eksploratorze testów** w węźle **nie uruchomiono testy** .

5. W **Eksploratorze testów**wybierz opcję **Uruchom wszystkie**.

    ![Podstawowy Test zakończony pomyślnie](../test/media/ute_cpp_testexplorer_basictest.png)

   Mają ustawienie testu i projekty kodu, a następnie zweryfikować, że można uruchomić testy, które uruchamiania funkcji w projekcie kodu. Teraz możesz rozpocząć pisanie rzeczywistych testów i kodu.

## <a name="Iteratively_augment_the_tests_and_make_them_pass"></a>Iteracyjnie rozszerza testy i przekazują je

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
    > Firma Microsoft zaleca, nie należy zmieniać testy, które zostały przekazane. Zamiast tego Dodaj nowy test, zaktualizować kod, tak aby test zakończy się pomyślnie, a następnie dodaj innego testu, i tak dalej.
    >
    > Użytkownicy zmiany ich wymagań, wyłącz testy, które nie są już prawidłowe. Zapisz nowe testy i ich działania pojedynczo, w taki sam sposób przyrostowego.

2. W **Eksploratorze testów**wybierz opcję **Uruchom wszystkie**.

3. Test nie powiedzie się.

     ![RangeTest kończy się niepowodzeniem](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Upewnij się, że każdy test zakończy się niepowodzeniem, natychmiast, po napisaniu go. Dzięki temu można uniknąć łatwe Błąd zapisywania testu, który nigdy nie zakończy się niepowodzeniem.

4. Tak, aby nowy test zakończy się pomyślnie, należy zwiększyć testowany kod. Dodaj następujący do *RooterLib. cpp*:

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

5. Skompiluj rozwiązanie, a następnie w **Eksploratorze testów**wybierz opcję **Uruchom wszystkie**.

     Kod przechodzi oba testy.

> [!TIP]
> Tworzenie kodu, dodając jeden testów w danym momencie. Upewnij się, że po każdej iteracji kod przechodzi wszystkie testy.

## <a name="Debug_a_failing_test"></a>Debuguj test zakończony niepowodzeniem

1. Dodaj inny test do *UnitTest1. cpp*:

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

2. W **Eksploratorze testów**wybierz opcję **Uruchom wszystkie**.

    Test nie powiedzie się. Wybierz nazwę testu w **Eksploratorze testów**. Potwierdzenie nie powiodło się, jest wyróżniona. Komunikat o błędzie jest widoczny w okienku szczegółów w **Eksploratorze testów**.

    ![NegativeRangeTests nie powiodło się.](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

3. Aby zobaczyć, dlaczego test zakończy się niepowodzeniem, krok przy użyciu funkcji:

   1. Ustaw punkt przerwania na początku funkcji `SquareRoot`.

   2. W menu skrótów testu zakończonego niepowodzeniem wybierz **Debuguj wybrane testy**.

        Po zatrzymaniu w punkcie przerwania Uruchom przejść przez kod.

   3. Dodaj kod do *RooterLib. cpp* , aby przechwycić wyjątek:

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

   1. W **Eksploratorze testów**wybierz opcję **Uruchom wszystkie** , aby przetestować poprawioną metodę i upewnić się, że regresja nie została wprowadzona.

   Teraz kod przechodzi wszystkie testy.

   ![Kod przechodzi wszystkie testy](../test/media/ute_ult_alltestspass.png)

## <a name="Refactor_the_code_without_changing_tests"></a>Refaktoryzacja kodu bez zmiany testów

1. Uprość Obliczanie centralne w funkcji `SquareRoot`:

    ```csharp
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;
    ```

2. Wybierz opcję **Uruchom wszystkie** , aby przetestować metodę refaktoryzacji i upewnić się, że regresja nie została wprowadzona.

    > [!TIP]
    > Stabilne zestawy testów jednostkowych dobre daje pewność, że użytkownik nie wprowadzają błędów po zmianie kodu.
    >
    > Zachowaj refaktoryzacji oddzielnie od innych zmian.
