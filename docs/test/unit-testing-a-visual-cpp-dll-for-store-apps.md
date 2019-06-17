---
title: Jak przetestować biblioteki DLL Visual C++ dla aplikacji platformy uniwersalnej systemu Windows
ms.date: 05/01/2019
ms.topic: conceptual
ms.author: mblome
manager: jillfra
ms.workload:
- uwp
author: mikeblome
ms.openlocfilehash: 723e61f60550230774eb909dfce44d5f91ae7a64
ms.sourcegitcommit: ab06cde69d862440b4277bcd9bf02e7b50593a1b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/13/2019
ms.locfileid: "67132194"
---
# <a name="how-to-test-a-visual-c-dll"></a>Jak przetestować biblioteki DLL Visual C++

W tym temacie opisano jeden ze sposobów tworzenia testów jednostkowych dla języka C++ bibliotek DLL z aplikacji platformy uniwersalnej Windows (UWP) przy użyciu Frameworka testów firmy Microsoft dla języka C++. Biblioteka DLL RooterLib pokazuje niejasne chwile teorii limit z calculus poprzez implementację funkcji, który oblicza oszacowanie pierwiastek kwadratowy z podanej liczbie. Biblioteki DLL, następnie mógłby być zawarty w aplikacji platformy uniwersalnej systemu Windows, która zawiera użytkownika fun rzeczy, które można wykonać za pomocą matematyczne.

 W tym temacie dowiesz się, jak używać jednostki testowania jako pierwszy krok w rozwoju. W tym podejściu najpierw napisać metodę testową, która sprawdza określone zachowanie w systemie, które testujesz, a następnie napisać kod, który przejdzie test. Wycofanie tej strategii, wprowadzając zmiany kolejności poniższych procedur, w pierwszej operacji zapisu kod, który chcesz przetestować, a następnie napisz testy jednostkowe.

 W tym temacie tworzy również jedno rozwiązanie Visual Studio i oddzielnych projektów dla testów jednostkowych i biblioteki DLL, która ma zostać przetestowana. Możesz również uwzględnić testy jednostkowe bezpośrednio w projekcie biblioteki DLL lub można utworzyć oddzielne rozwiązania dla testów jednostkowych i. BIBLIOTEKI DLL. Zobacz [Dodawanie testów jednostkowych do istniejących aplikacji C++](../test/how-to-use-microsoft-test-framework-for-cpp.md) zawiera porady na temat struktury, która do użycia.

## <a name="Create_the_solution_and_the_unit_test_project"></a> Tworzenie rozwiązania i projektu testu jednostkowego

::: moniker range="vs-2019"

Rozpocznij od utworzenia nowego projektu testu. Na **pliku** menu, wybierz **New** > **projektu**. W **Utwórz nowy projekt** okno dialogowe, w polu wyszukiwania wpisz "test", a następnie ustaw **języka** do C++. Następnie wybierz **aplikacji testów jednostkowych (Windows Universal)** z listy szablonów projektu.

   ![Tworzenie nowego projektu testowego platformy uniwersalnej systemu Windows](media/vs-2019/cpp-new-uwp-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

Rozpocznij od utworzenia nowego projektu testu. Na **pliku** menu, wybierz **New** > **projektu**. W **nowy projekt** okna dialogowego, rozwiń węzeł **zainstalowane** > **Visual C++**  i wybierz polecenie **Windows Universal**. Następnie wybierz **aplikacji testów jednostkowych (Windows Universal)** z listy szablonów projektu.

::: moniker-end

1. W oknie dialogowym Nowy projekt rozwiń **zainstalowane** > **Visual C++** i wybierz polecenie **Windows Universal**. Następnie wybierz **aplikacji testów jednostkowych (Windows Universal)** z listy szablonów projektu.

2. Nadaj projektowi nazwę `RooterLibTests`; Określ lokalizację; nazwij rozwiązanie `RooterLib`; i upewnij się, że **Utwórz katalog rozwiązania** jest zaznaczone.

     ![Określ nazwę rozwiązania i projektu i lokalizacji](../test/media/ute_cpp_windows_unittestlib_createspecs.png)

3. Otwórz w nowym projekcie **unittest1.cpp**.

     ![unittest1.cpp](../test/media/ute_cpp_windows_unittest1_cpp.png)

     Należy pamiętać o następujących kwestiach:

    - Każdy test jest definiowana za pomocą `TEST_METHOD(YourTestName){...}`.

         Nie trzeba napisać podpis konwencjonalnych funkcji. Podpis jest tworzony za pomocą makra TEST_METHOD. Makro generuje funkcją wystąpienia, która zwraca wartość void. Polecenie to generuje także funkcję statyczną, która zwraca informacje na temat metody testowej. Te informacje temu Eksplorator testów, można znaleźć metody.

    - Metody testowe są pogrupowane według klasy przy użyciu `TEST_CLASS(YourClassName){...}`.

         Gdy testy są uruchamiane, tworzone jest wystąpienie każdej klasy testu. Metody testowe są wywoływane w nieokreślonej kolejności. Można zdefiniować specjalne metody, które są wywoływane przed i po każdym modułu, klasy lub metody. Aby uzyskać więcej informacji, zobacz [korzystanie z Microsoft.VisualStudio.TestTools.CppUnitTestFramework](how-to-use-microsoft-test-framework-for-cpp.md).

## <a name="Verify_that_the_tests_run_in_Test_Explorer"></a> Sprawdź, czy testy zostaną wykonane w Eksploratorze testów

1. Wstaw kod testu:

    ```cpp
    TEST_METHOD(TestMethod1)
    {
        Assert::AreEqual(1,1);
    }
    ```

     Należy zauważyć, że `Assert` klasa udostępnia kilka metod statycznych, których można sprawdzić wyniki za pomocą metod testowych.

2. Na **testu** menu, wybierz **Uruchom** , a następnie wybierz **Uruchom wszystkie**.

     Projekt testowy skompilowane i uruchomione. **Eksploratora testów** zostanie wyświetlone okno i test znajduje się w obszarze **testy zakończone powodzeniem**. **Podsumowanie** okienku u dołu okna udostępnia dodatkowe szczegóły dotyczące wybranego testu.

     ![Eksplorator testów](../test/media/ute_cpp_testexplorer_testmethod1.png)

## <a name="Add_the_DLL_project_to_the_solution"></a> Dodaj projekt biblioteki DLL do rozwiązania

::: moniker range="vs-2019"

W **Eksploratora rozwiązań**, wybierz nazwę rozwiązania. Z menu skrótów wybierz polecenie **Dodaj**, a następnie **nowy projekt**. W **Dodaj nowy projekt** okno dialogowe, zestaw **języka** do C++ i w polu wyszukiwania wpisz "DLL". Z listy wyników wybierz **aplikacji testów jednostkowych (Windows Universal - C++/CX)** .

![Utwórz projekt RooterLib](../test/media/vs-2019/cpp-new-uwp-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"
W **Eksploratora rozwiązań**, wybierz nazwę rozwiązania. Z menu skrótów wybierz polecenie **Dodaj**, a następnie **nowy projekt**.

![Utwórz projekt RooterLib](../test/media/ute_cpp_windows_rooterlib_create.png)

::: moniker-end

1. W **Dodaj nowy projekt** okna dialogowego wybierz **biblioteki DLL (platformy uwp)** .

2. Dodaj następujący kod do *RooterLib.h* pliku:

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

     `CRooterLib` Klasa deklaruje Konstruktor i `SqareRoot` metoda narzędzie do szacowania.

3. Dodaj ROOTERLIB_EXPORTS symbol w wierszu polecenia.

    1. W **Eksploratora rozwiązań**, wybierz **RooterLib** projektu, a następnie wybierz **właściwości** z menu skrótów.

         ![Dodawanie definicji symboli preprocesora](../test/media/ute_cpp_windows_addpreprocessorsymbol.png)

    2. W **strona właściwości RooterLib** okna dialogowego rozwiń **właściwości konfiguracji**, rozwiń węzeł **C++** i wybierz polecenie **preprocesora**.

    3. Wybierz  **\<edytujący... >** z **definicje preprocesora** listy, a następnie dodaj `ROOTERLIB_EXPORTS` w **definicje preprocesora** okno dialogowe.

4. Dodaj implementacje minimalne funkcje zadeklarowane. Otwórz *RooterLib.cpp* i Dodaj następujący kod:

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

## <a name="make_the_dll_functions_visible_to_the_test_code"></a> Uwidacznianie funkcji dll z kodem testu

1. Dodaj RooterLib projektu RooterLibTests.

   1. W **Eksploratora rozwiązań**, wybierz **RooterLibTests** projektu, a następnie wybierz **Dodaj** > **odwołania** na skrót menu.

   1. W **Dodaj odwołanie** okna dialogowego wybierz **projektów**. Następnie wybierz pozycję **RouterLib** elementu.

2. Uwzględnić plik nagłówka RooterLib w *unittest1.cpp*.

   1. Otwórz *unittest1.cpp*.

   2. Dodaj następujący kod poniżej `#include "CppUnitTest.h"` wiersza:

       ```cpp
       #include "..\RooterLib\RooterLib.h"
       ```

3. Dodaj test, który używa funkcji zaimportowane. Dodaj następujący kod do *unittest1.cpp*:

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

    Nowy test jest wyświetlany w **Eksploratora testów** w **testy nieuruchamiane** węzła.

5. W **Eksplorator testów**, wybierz **Uruchom wszystkie**.

    ![Podstawowy Test zakończony pomyślnie](../test/media/ute_cpp_testexplorer_basictest.png)

   Mają ustawienie testu i projekty kodu, a następnie zweryfikować, że można uruchomić testy, które uruchamiania funkcji w projekcie kodu. Teraz możesz rozpocząć pisanie rzeczywistych testów i kodu.

## <a name="Iteratively_augment_the_tests_and_make_them_pass"></a> Iteracyjne Udoskonal testy i nadawać im przekazać

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

2. W **Eksplorator testów**, wybierz **Uruchom wszystkie**.

3. Test nie powiedzie się.

     ![RangeTest kończy się niepowodzeniem](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Upewnij się, że każdy test zakończy się niepowodzeniem, natychmiast, po napisaniu go. Dzięki temu można uniknąć łatwe Błąd zapisywania testu, który nigdy nie zakończy się niepowodzeniem.

4. Tak, aby nowy test zakończy się pomyślnie, należy zwiększyć testowany kod. Dodaj następujące polecenie, aby *RooterLib.cpp*:

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

5. Kompiluj rozwiązanie, a następnie w polu **Eksplorator testów**, wybierz **Uruchom wszystkie**.

     Kod przechodzi oba testy.

> [!TIP]
> Tworzenie kodu, dodając jeden testów w danym momencie. Upewnij się, że po każdej iteracji kod przechodzi wszystkie testy.

## <a name="Debug_a_failing_test"></a> Debuguj test niepowodzeniem

1. Dodaj kolejny test do *unittest1.cpp*:

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

2. W **Eksplorator testów**, wybierz **Uruchom wszystkie**.

    Test nie powiedzie się. Wybierz nazwę testu w **Eksploratora testów**. Potwierdzenie nie powiodło się, jest wyróżniona. Komunikat o błędzie jest widoczny w okienku szczegółów **Eksplorator testów**.

    ![NegativeRangeTests nie powiodło się.](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

3. Aby zobaczyć, dlaczego test zakończy się niepowodzeniem, krok przy użyciu funkcji:

   1. Ustaw punkt przerwania na początku `SquareRoot` funkcji.

   2. W menu skrótów testów zakończonych niepowodzeniem, wybierz **Debuguj wybrane testy**.

        Po zatrzymaniu w punkcie przerwania Uruchom przejść przez kod.

   3. Dodaj kod, aby *RooterLib.cpp* zostać przechwycony wyjątek:

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

   1. W **Eksploratora testów**, wybierz **Uruchom wszystkie** poprawiony metoda testowa, i upewnij się, że nie zostały wprowadzone regresji.

   Teraz kod przechodzi wszystkie testy.

   ![Kod przechodzi wszystkie testy](../test/media/ute_ult_alltestspass.png)

## <a name="Refactor_the_code_without_changing_tests"></a> Refaktoryzacja kodu bez zmieniania testów

1. Uprość centralnej obliczeń w `SquareRoot` funkcji:

    ```csharp
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;
    ```

2. Wybierz **Uruchom wszystkie** wycofanej metoda testowa, i upewnij się, że nie zostały wprowadzone regresji.

    > [!TIP]
    > Stabilne zestawy testów jednostkowych dobre daje pewność, że użytkownik nie wprowadzają błędów po zmianie kodu.
    >
    > Zachowaj refaktoryzacji oddzielnie od innych zmian.
