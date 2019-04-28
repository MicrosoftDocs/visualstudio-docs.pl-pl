---
title: Pisanie testów jednostkowych dla języka C-C++ za pomocą Frameworka testów jednostkowych firmy Microsoft dla języka C++ | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 4f4b5f10-7314-4725-8c6e-e72f52eff918
caps.latest.revision: 16
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d532234e50177222c3165638c0d77a8bd7c1b142
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437965"
---
# <a name="writing-unit-tests-for-cc-with-the-microsoft-unit-testing-framework-for-c"></a>Framework testów jednostkowych firmy Microsoft dla języka C++ pozwala pisać testy jednostkowe dla projektów języka C++.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio można utworzyć testy jednostkowe dla niezarządzanego kodu napisanego w języku C++. Niezarządzany kod jest czasami określane jako kodu natywnego.  
  
 Poniższa procedura zawiera podstawowe informacje, które ułatwi rozpoczęcie pracy. Nowsze sekcje zawierają przewodnik, który opisuje czynności, które bardziej szczegółowo.  
  
### <a name="to-write-unit-tests-for-an-unmanaged-code-dll"></a>Do pisania testów jednostkowych dla niezarządzanego kodu biblioteki DLL  
  
1. Użyj **natywnego projektu testowego** szablonu w celu utworzenia oddzielnego projektu programu Visual Studio dla testów.  
  
     Projekt zawiera przykładowy kod testu.  
  
2. Udostępnić biblioteki DLL dla projektu testowego:  
  
    - `#include` `.h` pliku, który zawiera deklaracje zewnętrzne dostępne funkcje biblioteki DLL.  
  
         `.h` Plik powinien zawierać deklaracje funkcji oznaczone `_declspec(dllimport)`. Alternatywnie możesz wyeksportować metody przy użyciu plików DEF. Aby uzyskać więcej informacji, zobacz [importowanie i eksportowanie](http://msdn.microsoft.com/library/7c44c2aa-2117-4cec-9615-a65bfd3f8f7b).  
  
         Testy jednostkowe mogą uzyskiwać dostęp tylko funkcje, które są eksportowane z biblioteki DLL w ramach testu.  
  
    - Dodaj projekt biblioteki DLL do odwołań projektu testowego:  
  
         W **właściwości** projektu testowego, rozwiń węzeł **wspólne właściwości**, **szablon i odwołania**i wybierz polecenie **Dodaj odwołanie**.  
  
3. W projekcie testowym Tworzenie klas testowych i metod testowych przy użyciu makra testu i Asercja klasy w następujący sposób:  
  
    ```cpp  
    #include "stdafx.h"  
    #include <CppUnitTest.h>  
    #include "..\MyProjectUnderTest\MyCodeUnderTest.h"  
    using namespace Microsoft::VisualStudio::CppUnitTestFramework;  
    TEST_CLASS(TestClassName)  
    {  
    public:  
      TEST_METHOD(TestMethodName)  
      {  
        // Run a function under test here.  
        Assert::AreEqual(expectedValue, actualValue, L"message", LINE_INFO());  
      }  
    }  
    ```  
  
    - `Assert` zawiera kilka funkcji statycznych, których można użyć, aby sprawdzić wynik testu.  
  
    - `LINE_INFO()` Parametr jest opcjonalny. W przypadkach, w przypadku, gdy nie ma żadnego pliku PDB, umożliwia ona modułu uruchamiającego testy w celu zidentyfikowania lokalizacji błędu.  
  
    - Można także napisać instalacyjne i czyszczące metod testowych. Aby uzyskać więcej informacji, otwórz definicję `TEST_METHOD` makro, i przeczytaj komentarze w CppUnitTest.h  
  
    - Nie można zagnieździć klas testowych.  
  
4. Aby uruchomić testy, należy użyć narzędzia Eksplorator testów:  
  
    1. Na **widoku** menu, wybierz **Windows inne**, **Eksplorator testów**.  
  
    2. Twórz rozwiązania Visual Studio.  
  
    3. W Eksploratorze testów wybierz **Uruchom wszystkie**.  
  
    4. Aby zbadać każde badanie bardziej szczegółowo w Eksploratorze testów:  
  
        1. Wybierz nazwę testu, aby zobaczyć więcej szczegółów, takich jak awaria wiadomości i ślad stosu.  
  
        2. Otwórz nazwa testu (na przykład przez dwukrotne kliknięcie), aby przejść do lokalizacji błędu lub kod testu.  
  
        3. W menu skrótów dla testu wybierz **Debuguj wybrany Test** do uruchomienia testu w debugerze.  
  
## <a name="walkthrough"></a> Wskazówki: Tworzenie niezarządzaną biblioteką DLL za pomocą narzędzia Eksplorator testów  
 Możliwość dostosowania tego przewodnika w celu tworzenia własnych biblioteki DLL. Główne kroki są następujące:  
  
1. [Utwórz projekt testu natywnych](#unitTestProject). Testy są tworzone w osobnym projekcie z biblioteki DLL, który tworzysz.  
  
2. [Utwórz projekt biblioteki DLL](#createDllProject). Ten poradnik tworzy DLL, nowe, ale procedura testowania istniejącej biblioteki DLL jest podobny.  
  
3. [Uwidacznianie funkcji DLL testów](#coupleProjects).  
  
4. [Iteracyjne Udoskonal testy](#iterate). Firma Microsoft zaleca cyklu "ruch zrefaktoryzuj red zielony", w którym tworzenia kodu zostanie przeprowadzony przez testy.  
  
5. [Debugowanie w przypadku braku testy](#debug). Można uruchomić testy w trybie debugowania.  
  
6. [Refaktoryzuj podczas utrzymanie testów bez zmian](#refactor). Refaktoryzacja oznacza, że poprawy struktury kodu bez zmiany zachowania zewnętrznych. Możesz to zrobić w celu poprawy wydajności, rozszerzalność i czytelności kodu. Ponieważ zamiar nie należy zmieniać zachowanie, nie zmieniaj testów podczas wprowadzania zmian refaktoryzacji w kodzie. Testy pomoc, upewnij się, że nie wprowadzają błędów podczas są refaktoryzacji. Można więc wprowadzić takie zmiany, bez obaw znacznie więcej niż Jeśli nie masz testy.  
  
7. [Sprawdź pokrycia](https://msdn.microsoft.com/library/fc8hec9e.aspx). Testy jednostkowe są bardziej użyteczne, gdy korzystają oni z kodu. Może odnajdywać, które części kodu były używane przez testy.  
  
8. [Izolowanie jednostki z zasobami zewnętrznymi](https://msdn.microsoft.com/library/hh549174.aspx). Zazwyczaj Biblioteka DLL jest zależny od innych składników systemu, które tworzysz, takich jak inne biblioteki dll, bazy danych lub zdalnego podsystemów. Warto przetestować każda jednostka w izolacji od jego zależności. Składniki zewnętrzne, można wprowadzić testy spowolnienie działania. Podczas tworzenia aplikacji inne składniki mogą być niekompletne.  
  
### <a name="unitTestProject"></a> Utwórz natywny projekt testów jednostkowych  
  
1. Na **pliku** menu, wybierz **New**, **projektu**.  
  
     W oknie dialogowym Rozwiń **zainstalowane**, **szablony**, **Visual C++**, **testu**.  
  
     Wybierz **natywnego projektu testowego** szablonu.  
  
     W tym przewodniku nosi nazwę projektu testowego `NativeRooterTest`.  
  
     ![Tworzenie C&#43; &#43; projektu testu jednostkowego](../test/media/utecpp01.png "UteCpp01")  
  
2. W nowym projekcie, należy sprawdzić **unittest1.cpp**  
  
     ![Projekt testowy z TESTEM&#95;klasy i testowania&#95;metoda](../test/media/utecpp2.png "UteCpp2")  
  
     Należy zauważyć, że:  
  
    - Każdy test jest definiowana za pomocą `TEST_METHOD(YourTestName){...}`.  
  
         Nie trzeba napisać podpis konwencjonalnych funkcji. Podpis jest tworzony za pomocą makra TEST_METHOD. Makro generuje funkcją wystąpienia, która zwraca wartość void. Polecenie to generuje także funkcję statyczną, która zwraca informacje na temat metody testowej. Te informacje temu Eksplorator testów, można znaleźć metody.  
  
    - Metody testowe są pogrupowane według klasy przy użyciu `TEST_CLASS(YourClassName){...}`.  
  
         Gdy testy są uruchamiane, tworzone jest wystąpienie każdej klasy testu. Metody testowe są wywoływane w nieokreślonej kolejności. Można zdefiniować specjalne metody, które są wywoływane przed i po każdym modułu, klasy lub metody.  
  
3. Sprawdź, czy testy zostaną wykonane w Eksploratorze testów:  
  
    1. Wstaw kod testu:  
  
        ```cpp  
        TEST_METHOD(TestMethod1)  
        {  
        Assert::AreEqual(1,1);  
        }  
        ```  
  
         Należy zauważyć, że `Assert` klasa udostępnia kilka metod statycznych, których można sprawdzić wyniki za pomocą metod testowych.  
  
    2. Na **testu** menu, wybierz **Uruchom** , **wszystkie testy**.  
  
         Test skompilowane i uruchomione.  
  
         Pojawi się Eksploratora testów.  
  
         Test pojawi się w obszarze **testy zakończone powodzeniem**.  
  
         ![Eksplorator testów jednostki przy użyciu jednego testów zakończonych powodzeniem](../test/media/utecpp04.png "UteCpp04")  
  
### <a name="createDllProject"></a> Tworzenie projektu niezarządzaną biblioteką DLL  
  
1. Tworzenie **Visual C++** projektu przy użyciu **projekt systemu Win32** szablonu.  
  
     W tym przewodniku nosi nazwę projektu `RootFinder`.  
  
     ![Tworzenie C&#43; &#43; projekt systemu Win32](../test/media/utecpp05.png "UteCpp05")  
  
2. Wybierz **DLL** i **Eksportuj symbole** Kreatora aplikacji Win32.  
  
     **Eksportuj symbole** opcja powoduje wygenerowanie wygodne makro, które służy do deklarowania metod wyeksportowany.  
  
     ![C&#43; &#43; Kreator projektu zestawu biblioteki DLL i eksportowanie symboli](../test/media/utecpp06.png "UteCpp06")  
  
3. Zadeklaruj eksportowanych funkcji w pliku .h jednostki:  
  
     ![Nowy kod projektu i .h plik DLL za pomocą interfejsu API makra](../test/media/utecpp07.png "UteCpp07")  
  
     Deklarator `__declspec(dllexport)` powoduje, że publiczne i chronione składowe klasy mają być wyświetlane poza bibliotekę DLL. Aby uzyskać więcej informacji, zobacz [korzystanie z dllimport i dllexport w klasach C++](http://msdn.microsoft.com/library/8d7d1303-b9e9-47ca-96cc-67bf444a08a9).  
  
4. W pliku .cpp główną należy dodać minimalny treści funkcji:  
  
    ```cpp  
    // Find the square root of a number.  
    double CRootFinder::SquareRoot(double v)  
    {  
      return 0.0;  
    }  
    ```  
  
### <a name="coupleProjects"></a> Kilka projekt testowy do projektu biblioteki DLL  
  
1. Dodaj projekt biblioteki DLL do odwołań projektu dla projektu testowego:  
  
   1. Otwórz właściwości projektu testowego i wybierz polecenie **wspólne właściwości**, **szablon i odwołania**.  
  
        ![C&#43; &#43; właściwości projektu &#45; szablon i odwołania](../test/media/utecpp08.png "UteCpp08")  
  
   2. Wybierz **Dodaj nowe odwołanie**.  
  
        W **Dodaj odwołanie** okna dialogowego pole, zaznacz projekt DLL i wybierz **Dodaj**.  
  
        ![C&#43; &#43; właściwości projektu &#45; Dodaj nowe odwołanie](../test/media/utecpp09.png "UteCpp09")  
  
2. W pliku .cpp testu jednostkowego jednostki Dołącz plik .h kodu biblioteki DLL:  
  
   ```cpp  
   #include "..\RootFinder\RootFinder.h"  
   ```  
  
3. Dodaj podstawowy test, który używa eksportowanych funkcji:  
  
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
  
    Nowy test zostanie wyświetlony w Eksploratorze testów.  
  
5. W Eksploratorze testów wybierz **Uruchom wszystkie**.  
  
    ![Eksplorator testów jednostkowych &#45; podstawowy Test zakończony sukcesem](../test/media/utecpp10.png "UteCpp10")  
  
   Mają ustawienie testu i projekty kodu, a następnie zweryfikować, że można uruchomić testy, które uruchamiania funkcji w projekcie kodu. Teraz możesz rozpocząć pisanie rzeczywistych testów i kodu.  
  
### <a name="iterate"></a> Iteracyjne Udoskonal testy i nadawać im przekazać  
  
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
    >  Użytkownicy zmiany ich wymagań, wyłącz testy, które nie są już prawidłowe. Zapisz nowe testy i ich działania pojedynczo, w taki sam sposób przyrostowego.  
  
2. Skompiluj rozwiązanie, a następnie w Eksploratorze testów wybierz **Uruchom wszystkie**.  
  
     Nowy test kończy się niepowodzeniem.  
  
     ![Kończy się niepowodzeniem RangeTest](../test/media/ute-cpp-testexplorer-rangetest-fail.png "UTE_Cpp_TestExplorer_RangeTest_Fail")  
  
    > [!TIP]
    > Upewnij się, że każdy test zakończy się niepowodzeniem, natychmiast, po napisaniu go. Dzięki temu można uniknąć łatwe Błąd zapisywania testu, który nigdy nie zakończy się niepowodzeniem.  
  
3. Tak, aby nowy test zakończy się pomyślnie, należy zwiększyć testowanego kodu:  
  
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
  
4. Skompiluj rozwiązanie, a następnie w Eksploratorze testów wybierz **Uruchom wszystkie**.  
  
     Kod przechodzi oba testy.  
  
     ![Eksplorator testów jednostkowych &#45; zakresu pomyślny](../test/media/utecpp12.png "UteCpp12")  
  
    > [!TIP]
    > Tworzenie kodu, dodając jeden testów w danym momencie. Upewnij się, że po każdej iteracji kod przechodzi wszystkie testy.  
  
### <a name="debug"></a> Debuguj test niepowodzeniem  
  
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
  
2. Skompiluj rozwiązanie, a następnie wybierz **Uruchom wszystkie**.  
  
3. Otwórz lub kliknij dwukrotnie test zakończony niepowodzeniem.  
  
     Potwierdzenie nie powiodło się, jest wyróżniona. Komunikat o błędzie jest widoczne w okienku szczegółów w Eksploratorze testów.  
  
     ![Nie powiodło się NegativeRangeTests](../test/media/ute-cpp-testexplorer-negativerangetest-fail.png "UTE_Cpp_TestExplorer_NegativeRangeTest_Fail")  
  
4. Aby zobaczyć, dlaczego test zakończy się niepowodzeniem, krok przy użyciu funkcji:  
  
    1. Ustaw punkt przerwania na początku funkcji SquareRoot.  
  
    2. W menu skrótów testów zakończonych niepowodzeniem, wybierz **Debuguj wybrane testy**.  
  
         Po zatrzymaniu w punkcie przerwania Uruchom przejść przez kod.  
  
5. Wstaw kod w funkcji, który tworzysz:  
  
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
  
     ![Kod przechodzi wszystkie testy](../test/media/ute-ult-alltestspass.png "UTE_ULT_AllTestsPass")  
  
> [!TIP]
> Poszczególne testy nie ma żadnych zależności, które uniemożliwiają są uruchamiane w dowolnej kolejności, należy włączyć równoległe wykonywanie testów za pomocą ![WYKONAJ&#95;parallelicon&#45;małych](../test/media/ute-parallelicon-small.png "małych UTE_parallelicon") Przełącz przycisk na pasku narzędzi. Może to znacznie zmniejszyć czas poświęcony na uruchamianie wszystkich testów.  
  
### <a name="refactor"></a> Refaktoryzacja kodu bez zmieniania testów  
  
1. Uprość centralnej obliczeń w funkcji SquareRoot:  
  
    ```  
    // old code:  
    //   result = result - (result*result - v)/(2*result);  
    // new code:  
         result = (result + v/result)/2.0;  
  
    ```  
  
2. Skompiluj rozwiązanie, a następnie wybierz **Uruchom wszystkie**, aby upewnić się, że błąd nie zostały wprowadzone.  
  
    > [!TIP]
    > Dobry zestaw testów jednostkowych daje pewność, że użytkownik nie wprowadzają błędów po zmianie kodu.  
    >   
    >  Zachowaj refaktoryzacji oddzielnie od innych zmian.  
  
## <a name="next-steps"></a>Następne kroki  
  
- **Izolacja.** Większość bibliotek DLL są zależne od innych podsystemów, takich jak bazy danych i inne biblioteki dll. Te inne składniki często są opracowywane równolegle. Aby umożliwić jednostek testów do wykonania, podczas gdy inne składniki nie są jeszcze dostępne, trzeba zastąpić mock lub  
  
- **Testy weryfikacji kompilacji.** Może mieć testów wykonywanych na serwerze kompilacji zespołu w ustalonych odstępach czasu. Dzięki temu usterki nie są wprowadzane podczas pracy kilku członków zespołu jest zintegrowany.  
  
- **Testów zaewidencjonowania.** Aby uzasadniają, że niektóre testy są wykonywane przed każdy członek zespołu sprawdza kod do kontroli źródła. Jest to zazwyczaj podzbiór cały zestaw testów weryfikacyjnych kompilacji.  
  
     Można również wprowadzić minimalnego poziomu pokrycia kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie testów jednostkowych do istniejących aplikacji C++](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)   
 [Using Microsoft.VisualStudio.TestTools.CppUnitTestFramework](../test/using-microsoft-visualstudio-testtools-cppunittestframework.md)   
 [Przegląd interoperacyjności kodu zarządzanego/niezarządzanego](http://msdn.microsoft.com/library/ms973872.aspx)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)   
 [Przewodnik: Tworzenie i używanie biblioteki dołączanej dynamicznie (C++)](http://msdn.microsoft.com/library/3ae94848-44e7-4955-bbad-7d40f493e941)   
 [Importowanie i eksportowanie](http://msdn.microsoft.com/library/7c44c2aa-2117-4cec-9615-a65bfd3f8f7b)
