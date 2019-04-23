---
title: Biblioteki DLL Visual C++ Store aplikacji testów jednostkowych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 24afc90a-8774-4699-ab01-6602a7e6feb2
caps.latest.revision: 15
author: alexhomer1
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 716e6141d9f5ae76773a47b81ae54f5d7b70a9ec
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60104190"
---
# <a name="unit-testing-a-visual-c-dll-for-store-apps"></a>Biblioteki DLL Visual C++ Store aplikacji testów jednostkowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano jeden ze sposobów tworzenia testów jednostkowych dla bibliotek DLL z języka C++ dla aplikacji Windows Store DLL RooterLib pokazuje niejasne chwile teorii limit z calculus poprzez implementację funkcji, który oblicza oszacowanie pierwiastek kwadratowy z podanej liczbie. Biblioteki DLL, następnie mogą być uwzględnione w aplikacji Windows Store, która zawiera użytkownika fun rzeczy, które można wykonać za pomocą matematyczne.  
  
 W tym temacie dowiesz się, jak używać jednostki testowania jako pierwszy krok w rozwoju. W tym podejściu najpierw napisać metodę testową, która sprawdza określone zachowanie w systemie, które testujesz, a następnie napisać kod, który przejdzie test. Wycofanie tej strategii, wprowadzając zmiany kolejności poniższych procedur, w pierwszej operacji zapisu kod, który chcesz przetestować, a następnie napisz testy jednostkowe.  
  
 W tym temacie tworzy również jedno rozwiązanie Visual Studio i oddzielnych projektów dla testów jednostkowych i biblioteki DLL, która ma zostać przetestowana. Możesz również uwzględnić testy jednostkowe bezpośrednio w projekcie biblioteki DLL lub można utworzyć oddzielne rozwiązania dla testów jednostkowych i. BIBLIOTEKI DLL. Zobacz [Dodawanie testów jednostkowych do istniejących aplikacji C++](../test/unit-testing-existing-cpp-applications-with-test-explorer.md) zawiera porady na temat struktury, która do użycia.  
  
## <a name="BKMK_In_this_topic"></a> W tym temacie  
 Ten temat przeprowadzi Cię przez następujące zadania:  
  
 [Tworzenie rozwiązania i projektu testu jednostkowego](#BKMK_Create_the_solution_and_the_unit_test_project)  
  
 [Sprawdź, czy testy zostaną wykonane w Eksploratorze testów](#BKMK_Verify_that_the_tests_run_in_Test_Explorer)  
  
 [Dodaj projekt biblioteki DLL do rozwiązania](#BKMK_Add_the_DLL_project_to_the_solution)  
  
 [Kilka projekt testowy do projektu biblioteki dll](#BKMK_Couple_the_test_project_to_the_dll_project)  
  
 [Iteracyjne Udoskonal testy i nadawać im przekazać](#BKMK_Iteratively_augment_the_tests_and_make_them_pass)  
  
 [Debuguj test niepowodzeniem](#BKMK_Debug_a_failing_test)  
  
 [Refaktoryzacja kodu bez zmieniania testów](#BKMK_Refactor_the_code_without_changing_tests)  
  
## <a name="BKMK_Create_the_solution_and_the_unit_test_project"></a> Tworzenie rozwiązania i projektu testu jednostkowego  
  
1. Na **pliku** menu, wybierz **New**, a następnie wybierz **nowy projekt**.  
  
2. W oknie dialogowym Nowy projekt rozwiń **zainstalowane**, następnie rozwiń **Visual C++** i wybierz polecenie **Windows Store**. Następnie wybierz **Biblioteka testów jednostkowych (Windows Store apps)** z listy szablonów projektu.  
  
     ![Utwórz C&#43; &#43; Biblioteka testów jednostkowych](../test/media/ute-cpp-windows-unittestlib-create.png "UTE_Cpp_windows_UnitTestLib_Create")  
  
3. Nadaj projektowi nazwę `RooterLibTests`; Określ lokalizację; nazwij rozwiązanie `RooterLib`; i upewnij się, że **Utwórz katalog rozwiązania** jest zaznaczone.  
  
     ![Określ nazwę rozwiązania i projektu i lokalizację](../test/media/ute-cpp-windows-unittestlib-createspecs.png "UTE_Cpp_windows_UnitTestLib_CreateSpecs")  
  
4. Otwórz w nowym projekcie **unittest1.cpp**.  
  
     ![unittest1.cpp](../test/media/ute-cpp-windows-unittest1-cpp.png "UTE_Cpp_windows_unittest1_cpp")  
  
     Należy pamiętać o następujących kwestiach:  
  
    - Każdy test jest definiowana za pomocą `TEST_METHOD(YourTestName){...}`.  
  
         Nie trzeba napisać podpis konwencjonalnych funkcji. Podpis jest tworzony za pomocą makra TEST_METHOD. Makro generuje funkcją wystąpienia, która zwraca wartość void. Polecenie to generuje także funkcję statyczną, która zwraca informacje na temat metody testowej. Te informacje temu Eksplorator testów, można znaleźć metody.  
  
    - Metody testowe są pogrupowane według klasy przy użyciu `TEST_CLASS(YourClassName){...}`.  
  
         Gdy testy są uruchamiane, tworzone jest wystąpienie każdej klasy testu. Metody testowe są wywoływane w nieokreślonej kolejności. Można zdefiniować specjalne metody, które są wywoływane przed i po każdym modułu, klasy lub metody. Aby uzyskać więcej informacji, zobacz [korzystanie z Microsoft.VisualStudio.TestTools.CppUnitTestFramework](../test/using-microsoft-visualstudio-testtools-cppunittestframework.md) w bibliotece MSDN.  
  
## <a name="BKMK_Verify_that_the_tests_run_in_Test_Explorer"></a> Sprawdź, czy testy zostaną wykonane w Eksploratorze testów  
  
1. Wstaw kod testu:  
  
    ```cpp  
    TEST_METHOD(TestMethod1)  
    {  
        Assert::AreEqual(1,1);  
    }  
    ```  
  
     Należy zauważyć, że `Assert` klasa udostępnia kilka metod statycznych, których można sprawdzić wyniki za pomocą metod testowych.  
  
2. Na **testu** menu, wybierz **Uruchom** , a następnie wybierz **Uruchom wszystkie**.  
  
     Projekt testowy skompilowane i uruchomione. Zostanie wyświetlone okno Eksploratora testów i test znajduje się w obszarze **testy zakończone powodzeniem**. Okienko podsumowania w dolnej części okna udostępnia dodatkowe szczegóły dotyczące wybranego testu.  
  
     ![Test Explorer](../test/media/ute-cpp-testexplorer-testmethod1.png "UTE_Cpp_TestExplorer_TestMethod1")  
  
## <a name="BKMK_Add_the_DLL_project_to_the_solution"></a> Dodaj projekt biblioteki DLL do rozwiązania  
  
1. W Eksploratorze rozwiązań wybierz nazwę rozwiązania. Z menu skrótów wybierz polecenie **Dodaj**, a następnie **Dodaj nowy projekt**.  
  
     ![Utwórz projekt RooterLib](../test/media/ute-cpp-windows-rooterlib-create.png "UTE_Cpp_windows_RooterLib_Create")  
  
2. W **Dodaj nowy projekt** okna dialogowego wybierz **biblioteki DLL (aplikacje Windows Store)**.  
  
3. Dodaj następujący kod do **RooterLib.h** pliku:  
  
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
  
4. Dodaj ROOTERLIB_EXPORTS symbol w wierszu polecenia.  
  
    1. W Eksploratorze rozwiązań wybierz **RooterLib** projektu, a następnie wybierz **właściwości** z menu skrótów.  
  
         ![Dodawanie definicji symboli preprocesora](../test/media/ute-cpp-windows-addpreprocessorsymbol.png "UTE_Cpp_windows_AddPreprocessorSymbol")  
  
    2. W oknie dialogowym strona właściwości RooterLib rozwiń **właściwości konfiguracji**, rozwiń węzeł **C++** i wybierz polecenie **preprocesora**.  
  
    3. Wybierz  **\<edytujący... >** z **definicje preprocesora** listy, a następnie dodaj `ROOTERLIB_EXPORTS` w oknie dialogowym Definicje preprocesora.  
  
5. Dodaj implementacje minimalne funkcje zadeklarowane. Otwórz **RooterLib.cpp** i Dodaj następujący kod:  
  
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
  
## <a name="BKMK_Couple_the_test_project_to_the_dll_project"></a> Kilka projekt testowy do projektu biblioteki dll  
  
1. Dodaj RooterLib projektu RooterLibTests.  
  
   1. W Eksploratorze rozwiązań wybierz **RooterLibTests** projektu, a następnie wybierz **odwołania...**  menu skrótów.  
  
   2. W oknie dialogowym właściwości projektu RooterLib rozwiń **wspólne właściwości** i wybierz polecenie **szablon i odwołania**.  
  
   3. Wybierz **Dodaj nowe odwołanie...**  
  
   4. W **Dodaj odwołanie** okna dialogowego rozwiń **rozwiązania** , a następnie wybierz **projektów**. Następnie wybierz pozycję **RouterLib** elementu.  
  
2. Uwzględnić plik nagłówka RooterLib w **unittest1.cpp**.  
  
   1. Otwórz **unittest1.cpp**.  
  
   2. Dodaj następujący kod poniżej `#include "CppUnitTest.h"` wiersza:  
  
       ```cpp  
       #include "..\RooterLib\RooterLib.h"  
       ```  
  
3. Dodaj test, który używa funkcji zaimportowane. Dodaj następujący kod do **unittest1.cpp**:  
  
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
  
    Nowy test jest wyświetlany w Eksploratorze testów w **testy nieuruchamiane** węzła.  
  
5. W Eksploratorze testów wybierz **Uruchom wszystkie**.  
  
    ![Podstawowy Test zakończony sukcesem](../test/media/ute-cpp-testexplorer-basictest.png "UTE_Cpp_TestExplorer_BasicTest")  
  
   Mają ustawienie testu i projekty kodu, a następnie zweryfikować, że można uruchomić testy, które uruchamiania funkcji w projekcie kodu. Teraz możesz rozpocząć pisanie rzeczywistych testów i kodu.  
  
## <a name="BKMK_Iteratively_augment_the_tests_and_make_them_pass"></a> Iteracyjne Udoskonal testy i nadawać im przekazać  
  
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
    >  Firma Microsoft zaleca, nie należy zmieniać testy, które zostały przekazane. Zamiast tego Dodaj nowy test, zaktualizować kod, tak aby test zakończy się pomyślnie, a następnie dodaj innego testu, i tak dalej.  
    >   
    >  Użytkownicy zmiany ich wymagań, wyłącz testy, które nie są już prawidłowe. Zapisz nowe testy i ich działania pojedynczo, w taki sam sposób przyrostowego.  
  
2. W Eksploratorze testów wybierz **Uruchom wszystkie**.  
  
3. Test nie powiedzie się.  
  
     ![Kończy się niepowodzeniem RangeTest](../test/media/ute-cpp-testexplorer-rangetest-fail.png "UTE_Cpp_TestExplorer_RangeTest_Fail")  
  
    > [!TIP]
    >  Upewnij się, że każdy test zakończy się niepowodzeniem, natychmiast, po napisaniu go. Dzięki temu można uniknąć łatwe Błąd zapisywania testu, który nigdy nie zakończy się niepowodzeniem.  
  
4. Tak, aby nowy test zakończy się pomyślnie, należy zwiększyć testowany kod. Dodaj następujące polecenie, aby **RooterLib.cpp**:  
  
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
  
5. Skompiluj rozwiązanie, a następnie w Eksploratorze testów wybierz **Uruchom wszystkie**.  
  
     Kod przechodzi oba testy.  
  
> [!TIP]
>  Tworzenie kodu, dodając jeden testów w danym momencie. Upewnij się, że po każdej iteracji kod przechodzi wszystkie testy.  
  
## <a name="BKMK_Debug_a_failing_test"></a> Debuguj test niepowodzeniem  
  
1. Dodaj kolejny test do **unittest1.cpp**:  
  
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
  
2. W Eksploratorze testów wybierz **Uruchom wszystkie**.  
  
    Test nie powiedzie się. Wybierz nazwę testu w Eksploratorze testów. Potwierdzenie nie powiodło się, jest wyróżniona. Komunikat o błędzie jest widoczne w okienku szczegółów w Eksploratorze testów.  
  
    ![Nie powiodło się NegativeRangeTests](../test/media/ute-cpp-testexplorer-negativerangetest-fail.png "UTE_Cpp_TestExplorer_NegativeRangeTest_Fail")  
  
3. Aby zobaczyć, dlaczego test zakończy się niepowodzeniem, krok przy użyciu funkcji:  
  
   1. Ustaw punkt przerwania na początku `SquareRoot` funkcji.  
  
   2. W menu skrótów testów zakończonych niepowodzeniem, wybierz **Debuguj wybrane testy**.  
  
        Po zatrzymaniu w punkcie przerwania Uruchom przejść przez kod.  
  
   3. Dodaj kod, aby **RooterLib.cpp** zostać przechwycony wyjątek:  
  
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
  
   1. W Eksploratorze testów wybierz **Uruchom wszystkie** poprawiony metoda testowa, i upewnij się, że nie zostały wprowadzone regresji.  
  
   Teraz kod przechodzi wszystkie testy.  
  
   ![Kod przechodzi wszystkie testy](../test/media/ute-ult-alltestspass.png "UTE_ULT_AllTestsPass")  
  
## <a name="BKMK_Refactor_the_code_without_changing_tests"></a> Refaktoryzacja kodu bez zmieniania testów  
  
1. Uprość centralnej obliczeń w `SquareRoot` funkcji:  
  
    ```  
    // old code  
    //result = result - (result*result - v)/(2*result);  
    // new code  
    result = (result + v/result) / 2.0;  
  
    ```  
  
2. Wybierz **Uruchom wszystkie** wycofanej metoda testowa, i upewnij się, że nie zostały wprowadzone regresji.  
  
    > [!TIP]
    >  Stabilne zestawy testów jednostkowych dobre daje pewność, że użytkownik nie wprowadzają błędów po zmianie kodu.  
    >   
    >  Zachowaj refaktoryzacji oddzielnie od innych zmian.
