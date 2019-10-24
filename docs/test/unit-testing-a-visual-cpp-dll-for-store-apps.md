---
title: Jak przetestować C++ plik DLL dla aplikacji platformy UWP
ms.date: 05/01/2019
ms.topic: conceptual
ms.author: mblome
manager: jillfra
ms.workload:
- uwp
author: mikeblome
ms.openlocfilehash: 18d8382bcb4f3e348443050e818f0b59c2a18688
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748076"
---
# <a name="how-to-test-a-c-dll"></a>Jak przetestować C++ plik dll

W tym temacie opisano jeden ze sposobów tworzenia testów jednostkowych C++ dla aplikacji DLL for platforma uniwersalna systemu Windows (platformy UWP) przy użyciu platformy Microsoft Test C++Framework dla programu. Biblioteka DLL RooterLib pokazuje niejasne odnoszące się do granicy granicznej z calculus przez implementację funkcji, która oblicza oszacowanie wartości pierwiastek kwadratowy danej liczby. Biblioteka DLL może zostać następnie dołączona do aplikacji platformy UWP, która przedstawia użytkownikowi zabawne rzeczy, które można wykonać za pomocą obliczeń matematycznych.

W tym temacie przedstawiono sposób korzystania z testów jednostkowych jako pierwszego kroku projektowania. W tym podejściu najpierw napiszesz metodę testową, która weryfikuje określone zachowanie w testowanym systemie, a następnie pisze kod, który przekazuje test. Wprowadzając zmiany w kolejności następującej procedury, można odwrócić tę strategię, aby najpierw napisać kod, który ma zostać przetestowany, a następnie napisać testy jednostkowe.

W tym temacie jest również tworzone pojedyncze rozwiązanie programu Visual Studio i oddzielne projekty dla testów jednostkowych i biblioteki DLL, która ma zostać przetestowana. Możesz również uwzględnić testy jednostkowe bezpośrednio w projekcie DLL lub utworzyć oddzielne rozwiązania dla testów jednostkowych i. Bibliotece. Zobacz [Dodawanie testów jednostkowych do C++ istniejących aplikacji](../test/how-to-use-microsoft-test-framework-for-cpp.md) , aby uzyskać wskazówki dotyczące struktury do użycia.

## <a name="Create_the_solution_and_the_unit_test_project"></a>Utwórz rozwiązanie i projekt testu jednostkowego

::: moniker range="vs-2019"

Zacznij od utworzenia nowego projektu testowego. W menu **plik** wybierz **Nowy** **projekt** > . W oknie dialogowym **Tworzenie nowego projektu** wpisz "test" w polu wyszukiwania, a następnie ustaw **Język** na C++. Następnie wybierz pozycję **aplikacja testów jednostkowych (uniwersalna systemu Windows)** z listy szablonów projektu.

   ![Utwórz nowy projekt testu platformy UWP](media/vs-2019/cpp-new-uwp-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"

Zacznij od utworzenia nowego projektu testowego. W menu **plik** wybierz **Nowy** **projekt** > . W oknie dialogowym **Nowy projekt** rozwiń węzeł **zainstalowane**  >  **C++ Wizualizacja** i wybierz pozycję **Windows Universal**. Następnie wybierz pozycję **aplikacja testów jednostkowych (uniwersalna systemu Windows)** z listy szablonów projektu.

::: moniker-end

1. W oknie dialogowym Nowy projekt rozwiń węzeł **zainstalowane**  > **Wizualizacja C++**  i wybierz pozycję **Windows Universal**. Następnie wybierz pozycję **aplikacja testów jednostkowych (uniwersalna systemu Windows)** z listy szablonów projektu.

2. Nadaj projektowi nazwę `RooterLibTests`; Określ lokalizację; Nazwij rozwiązanie `RooterLib`; Upewnij się, że jest zaznaczone pole wyboru **Utwórz katalog dla rozwiązania** .

     ![Określ rozwiązanie i nazwę projektu i lokalizację](../test/media/ute_cpp_windows_unittestlib_createspecs.png)

3. W nowym projekcie Otwórz **UnitTest1. cpp**.

     ![UnitTest1. cpp](../test/media/ute_cpp_windows_unittest1_cpp.png)

     Należy pamiętać o następujących kwestiach:

    - Każdy test jest definiowany przy użyciu `TEST_METHOD(YourTestName){...}`.

         Nie trzeba pisać sygnatury funkcji konwencjonalnej. Podpis jest tworzony przez makro TEST_METHOD. Makro generuje funkcję wystąpienia zwracającą typ void. Generuje również funkcję statyczną, która zwraca informacje o metodzie testowej. Te informacje umożliwiają Eksploratorowi testów znalezienie metody.

    - Metody testowe są pogrupowane w klasy przy użyciu `TEST_CLASS(YourClassName){...}`.

         Gdy testy są uruchamiane, tworzone jest wystąpienie każdej klasy testowej. Metody testowe są wywoływane w nieokreślonej kolejności. Można zdefiniować metody specjalne, które są wywoływane przed i po każdym module, klasie lub metodzie. Aby uzyskać więcej informacji, zobacz [using Microsoft. VisualStudio. TestTools. CppUnitTestFramework](how-to-use-microsoft-test-framework-for-cpp.md).

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

     Projekt testowy zostanie skompilowany i uruchomiony. Zostanie wyświetlone okno **Eksplorator testów** , a test zostanie wyświetlony na liście **zakończonych testów**. Okienko **Podsumowanie** u dołu okna zawiera dodatkowe szczegółowe informacje o wybranym teście.

     ![Eksplorator testów](../test/media/ute_cpp_testexplorer_testmethod1.png)

## <a name="Add_the_DLL_project_to_the_solution"></a>Dodawanie projektu DLL do rozwiązania

::: moniker range="vs-2019"

W **Eksplorator rozwiązań**wybierz nazwę rozwiązania. Z menu skrótów wybierz polecenie **Dodaj**, a następnie **Nowy projekt**. W oknie dialogowym **Dodawanie nowego projektu** Ustaw **Język** na C++ i wpisz "dll" w polu wyszukiwania. Z listy wyników wybierz pozycję **aplikacja testów jednostkowych (Universal Windows- C++/CX)** .

![Tworzenie projektu RooterLib](../test/media/vs-2019/cpp-new-uwp-test-project-vs2019.png)

::: moniker-end

::: moniker range="vs-2017"
W **Eksplorator rozwiązań**wybierz nazwę rozwiązania. Z menu skrótów wybierz polecenie **Dodaj**, a następnie **Nowy projekt**.

![Tworzenie projektu RooterLib](../test/media/ute_cpp_windows_rooterlib_create.png)

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

     Komentarze wyjaśniają blok ifdef nie tylko dla dewelopera biblioteki DLL, ale do każdego, kto odwołuje się do biblioteki DLL w projekcie. Symbol ROOTERLIB_EXPORTS można dodać do wiersza polecenia przy użyciu właściwości projektu biblioteki DLL.

     Klasa `CRooterLib` deklaruje konstruktora i metodę `SqareRoot` szacowania.

3. Dodaj symbol ROOTERLIB_EXPORTS do wiersza polecenia.

    1. W **Eksplorator rozwiązań**wybierz projekt **RooterLib** , a następnie wybierz polecenie **Właściwości** z menu skrótów.

         ![Dodaj definicję symbolu preprocesora](../test/media/ute_cpp_windows_addpreprocessorsymbol.png)

    2. Na **stronie właściwości RooterLib** rozwiń węzeł **Właściwości konfiguracji**, rozwiń **C++** i wybierz **preprocesor**.

    3. Wybierz **\<Edit... >** z listy **Definicje preprocesora** , a następnie Dodaj `ROOTERLIB_EXPORTS` do okna dialogowego **Definicje preprocesora** .

4. Dodaj minimalne implementacje zadeklarowanych funkcji. Otwórz *RooterLib. cpp* i Dodaj następujący kod:

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

1. Dodaj RooterLib do projektu RooterLibTests.

   1. W **Eksplorator rozwiązań**wybierz projekt **RooterLibTests** , a następnie wybierz pozycję **Dodaj**  > **odwołanie** w menu skrótów.

   1. W oknie dialogowym **Dodaj odwołanie** wybierz pozycję **projekty**. Następnie wybierz element **RouterLib** .

2. Dołącz plik nagłówka RooterLib w *UnitTest1. cpp*.

   1. Otwórz *UnitTest1. cpp*.

   2. Dodaj następujący kod do `#include "CppUnitTest.h"` wiersza:

       ```cpp
       #include "..\RooterLib\RooterLib.h"
       ```

3. Dodaj test, który używa zaimportowanej funkcji. Dodaj następujący kod do *UnitTest1. cpp*:

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

    ![Test podstawowy zakończony zakończono](../test/media/ute_cpp_testexplorer_basictest.png)

   Został skonfigurowany test i projekty kodu i zweryfikowane, że można uruchomić testy, które uruchamiają funkcje w projekcie kodu. Teraz możesz zacząć pisać prawdziwe testy i kod.

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
    > Zalecamy, aby nie zmieniać testów, które zostały zakończone. Zamiast tego Dodaj nowy test, zaktualizuj kod tak, aby test zakończył się powodzeniem, a następnie Dodaj inny test i tak dalej.
    >
    > Gdy użytkownicy zmienią swoje wymagania, należy wyłączyć testy, które nie są już poprawne. Napisz nowe testy i Przekształć je w jeden raz w ten sam przyrostowy sposób.

2. W **Eksploratorze testów**wybierz opcję **Uruchom wszystkie**.

3. Test zakończy się niepowodzeniem.

     ![RangeTest kończy się niepowodzeniem](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Sprawdź, czy każdy test kończy się niepowodzeniem natychmiast po jego zapisaniu. Dzięki temu można uniknąć łatwego błędu podczas pisania testu, który nigdy nie powiedzie się.

4. Podnieś poziom testowanego kodu, tak aby nowe testy zostały przekazane. Dodaj następujący do *RooterLib. cpp*:

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

     Oba testy zostały zakończone pomyślnie.

> [!TIP]
> Opracowuj kod przez dodanie testów pojedynczo. Upewnij się, że wszystkie testy są zakończone po każdej iteracji.

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

    Test zakończy się niepowodzeniem. Wybierz nazwę testu w **Eksploratorze testów**. Niepowodzenie zostało wyróżnione. Komunikat o błędzie jest widoczny w okienku szczegółów w **Eksploratorze testów**.

    ![NegativeRangeTests nie powiodło się](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

3. Aby zobaczyć dlaczego test nie powiedzie się, przechodzenie przez funkcję:

   1. Ustaw punkt przerwania na początku funkcji `SquareRoot`.

   2. W menu skrótów testu zakończonego niepowodzeniem wybierz **Debuguj wybrane testy**.

        Gdy przebieg zostanie zatrzymany w punkcie przerwania, przejdź do kodu.

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

   Wszystkie testy są teraz zakończone pomyślnie.

   ![Wszystkie testy zakończone powodzeniem](../test/media/ute_ult_alltestspass.png)

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
    > Stabilny zestaw dobrych testów jednostkowych daje pewność, że podczas zmiany kodu nie wprowadzono usterek.
    >
    > Kontynuuj refaktoryzację niezależnie od innych zmian.
