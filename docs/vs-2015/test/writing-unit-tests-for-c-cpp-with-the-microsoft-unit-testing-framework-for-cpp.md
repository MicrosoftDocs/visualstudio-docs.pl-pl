---
title: Pisanie testów jednostkowych dla językaC++ C — za pomocą platformy testowania jednostkowego firmy Microsoft dla C++ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 4f4b5f10-7314-4725-8c6e-e72f52eff918
caps.latest.revision: 16
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5b6f358f43dcace230e1d58773e58be011d9033e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657079"
---
# <a name="writing-unit-tests-for-cc-with-the-microsoft-unit-testing-framework-for-c"></a>Framework testów jednostkowych firmy Microsoft dla języka C++ pozwala pisać testy jednostkowe dla projektów języka C++.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio można utworzyć testy jednostkowe dla niezarządzanego kodu C++, który jest pisany. Kod niezarządzany jest czasami określany jako kod natywny.

 Poniższa procedura zawiera podstawowe informacje, które pomogą Ci rozpocząć pracę. W kolejnych sekcjach znajduje się przewodnik, w którym opisano kroki bardziej szczegółowo.

### <a name="to-write-unit-tests-for-an-unmanaged-code-dll"></a>Aby napisać testy jednostkowe dla biblioteki DLL kodu niezarządzanego

1. Użyj szablonu **natywnego projektu testowego** , aby utworzyć oddzielny projekt programu Visual Studio dla testów.

     Projekt zawiera przykładowy kod testu.

2. Udostępnienie biblioteki DLL dla projektu testowego:

    - `#include` plik `.h`, który zawiera deklaracje funkcji dostępnych zewnętrznie bibliotek DLL.

         Plik `.h` powinien zawierać deklaracje funkcji oznaczone `_declspec(dllimport)`. Alternatywnie można eksportować metody przy użyciu pliku DEF. Aby uzyskać więcej informacji, zobacz [Importowanie i eksportowanie](https://msdn.microsoft.com/library/7c44c2aa-2117-4cec-9615-a65bfd3f8f7b).

         Testy jednostkowe mogą uzyskiwać dostęp tylko do funkcji, które zostały wyeksportowane z biblioteki DLL objętej testem.

    - Dodaj projekt biblioteki DLL do odwołań projektu testowego:

         We **właściwościach** projektu testowego rozwiń węzeł **wspólne właściwości**, **Struktura i odwołania**, a następnie wybierz pozycję **Dodaj odwołanie**.

3. W projekcie testowym Utwórz klasy testowe i metody testowe przy użyciu makr testowych i klasy Assert w następujący sposób:

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

    - `Assert` zawiera kilka funkcji statycznych, których można użyć do sprawdzenia wyniku testu.

    - Parametr `LINE_INFO()` jest opcjonalny. W przypadkach, gdy nie istnieje plik PDB, umożliwia modułowi uruchamiającego testy zidentyfikowanie lokalizacji błędu.

    - Możesz również napisać konfigurację testu i metody czyszczenia. Aby uzyskać więcej informacji, Otwórz definicję makra `TEST_METHOD` i przeczytaj komentarze w CppUnitTest. h

    - Nie można zagnieżdżać klas testowych.

4. Użyj Eksploratora testów do uruchomienia testów:

    1. W menu **Widok** wybierz **inne okna**, **Eksplorator testów**.

    2. Utwórz rozwiązanie Visual Studio.

    3. W Eksploratorze testów wybierz opcję **Uruchom wszystkie**.

    4. Aby szczegółowo zbadać każdy test w Eksploratorze testów:

        1. Wybierz nazwę testu, aby zobaczyć więcej szczegółów, takich jak komunikat o niepowodzeniu i ślad stosu.

        2. Otwórz nazwę testu (na przykład przez dwukrotne kliknięcie), aby przejść do lokalizacji niepowodzenia lub do kodu testu.

        3. W menu skrótów dla testu wybierz **Debuguj wybrany test** , aby uruchomić test w debugerze.

## <a name="walkthrough"></a>Przewodnik: Tworzenie niezarządzanej biblioteki DLL za pomocą Eksploratora testów
 Ten Instruktaż można dostosować w celu opracowania własnej biblioteki DLL. Główne kroki są następujące:

1. [Utwórz natywny projekt testowy](#unitTestProject). Testy są tworzone w oddzielnym projekcie od opracowywanej biblioteki DLL.

2. [Utwórz projekt DLL](#createDllProject). W tym instruktażu zostanie utworzona nowa biblioteka DLL, ale procedura testowania istniejącej biblioteki DLL jest podobna.

3. [Uczyń funkcje biblioteki DLL widocznymi dla testów](#coupleProjects).

4. [Iteracyjnie rozszerza testy](#iterate). Zalecamy cykliczny cykl "czerwony-zielony-Refaktoryzacja", w którym rozwój kodu jest kierowany przez testy.

5. [Debugowanie testów zakończonych niepowodzeniem](#debug). Testy można uruchamiać w trybie debugowania.

6. [Refaktoryzacja przy zachowaniu niezmienionych testów](#refactor). Refaktoryzacja oznacza poprawę struktury kodu bez zmiany jego zachowania zewnętrznego. Można to zrobić, aby zwiększyć wydajność, rozszerzalność lub czytelność kodu. Ponieważ zamiarem nie jest zmiana zachowania, nie należy zmieniać testów podczas zmiany refaktoryzacji kodu. Testy pomagają upewnić się, że nie są wprowadzane usterki podczas refaktoryzacji. W związku z tym można wprowadzić takie zmiany o znacznie większym stopniu pewności niż w przypadku braku testów.

7. [Sprawdź pokrycie](https://msdn.microsoft.com/library/fc8hec9e.aspx). Testy jednostkowe są bardziej przydatne, gdy wykonują więcej kodu. Można wykryć, które części kodu zostały wykorzystane przez testy.

8. [Izoluj jednostki od zasobów zewnętrznych](https://msdn.microsoft.com/library/hh549174.aspx). Zazwyczaj Biblioteka DLL jest zależna od innych składników systemu, które tworzysz, takich jak inne biblioteki DLL, bazy danych lub zdalne podsystemy. Warto przetestować każdą jednostkę w izolacji od jej zależności. Składniki zewnętrzne mogą sprawiać, że testy działają wolno. W trakcie programowania inne składniki mogą nie być kompletne.

### <a name="unitTestProject"></a>Utwórz natywny projekt testów jednostkowych

1. W menu **plik** wybierz polecenie **Nowy**, **projekt**.

     W oknie dialogowym Rozwiń węzeł **zainstalowane**, **Szablony**, **wizualizacje C++** i **testy**.

     Wybierz szablon **projektu testu natywnego** .

     W tym instruktażu projekt testowy ma nazwę `NativeRooterTest`.

     ![Tworzenie projektu testu&#43; &#43; jednostkowego C](../test/media/utecpp01.png "UteCpp01")

2. W nowym projekcie Sprawdź **UnitTest1. cpp**

     ![Test projektu z klasą&#95;testową&#95;i metodą testową](../test/media/utecpp2.png "UteCpp2")

     Zwróć uwagę, że:

    - Każdy test jest definiowany przy użyciu `TEST_METHOD(YourTestName){...}`.

         Nie trzeba pisać sygnatury funkcji konwencjonalnej. Podpis jest tworzony przez makro TEST_METHOD. Makro generuje funkcję wystąpienia zwracającą typ void. Generuje również funkcję statyczną, która zwraca informacje o metodzie testowej. Te informacje umożliwiają Eksploratorowi testów znalezienie metody.

    - Metody testowe są pogrupowane w klasy przy użyciu `TEST_CLASS(YourClassName){...}`.

         Gdy testy są uruchamiane, tworzone jest wystąpienie każdej klasy testowej. Metody testowe są wywoływane w nieokreślonej kolejności. Można zdefiniować metody specjalne, które są wywoływane przed i po każdym module, klasie lub metodzie.

3. Sprawdź, czy testy są uruchamiane w Eksploratorze testów:

    1. Wstaw kod testu:

        ```cpp
        TEST_METHOD(TestMethod1)
        {
        Assert::AreEqual(1,1);
        }
        ```

         Należy zauważyć, że Klasa `Assert` dostarcza kilka metod statycznych, których można użyć do sprawdzenia wyników w metodach testowych.

    2. W menu **test** wybierz polecenie **Uruchom** , a następnie **wszystkie testy**.

         Test kompiluje i uruchamia.

         Zostanie wyświetlony Eksplorator testów.

         Test jest wyświetlany w obszarze **testy zakończone**.

         ![Eksplorator testów jednostkowych z jednym zakończonym testem](../test/media/utecpp04.png "UteCpp04")

### <a name="createDllProject"></a>Tworzenie niezarządzanego projektu biblioteki DLL

1. Utwórz projekt **wizualny C++**  przy użyciu szablonu **projektu Win32** .

     W tym instruktażu projekt ma nazwę `RootFinder`.

     ![Tworzenie projektu systemu&#43; &#43; Win32 w języku C](../test/media/utecpp05.png "UteCpp05")

2. Wybierz opcję **dll** i **Eksportuj symbole** w Kreatorze aplikacji Win32.

     Opcja **Eksportuj symbole** generuje wygodne makro, którego można użyć do zadeklarowania eksportowanych metod.

     ![Kreator&#43; &#43; projektu C ustawiony dla biblioteki DLL i symboli eksportu](../test/media/utecpp06.png "UteCpp06")

3. Zadeklaruj wyeksportowaną funkcję w pliku Principal. h:

     ![Nowy projekt kodu DLL i plik h z makrami interfejsu API](../test/media/utecpp07.png "UteCpp07")

     Deklarator `__declspec(dllexport)` powoduje, że publiczne i chronione elementy członkowskie klasy są widoczne poza biblioteką DLL. Aby uzyskać więcej informacji, zobacz [using dllimport i dllexport C++ w klasach](https://msdn.microsoft.com/library/8d7d1303-b9e9-47ca-96cc-67bf444a08a9).

4. W pliku Principal. cpp Dodaj minimalną treść dla funkcji:

    ```cpp
    // Find the square root of a number.
    double CRootFinder::SquareRoot(double v)
    {
      return 0.0;
    }
    ```

### <a name="coupleProjects"></a>Połącz projekt testowy z projektem DLL

1. Dodaj projekt DLL do odwołań projektu projektu testowego:

   1. Otwórz właściwości projektu testowego i wybierz pozycję **wspólne właściwości**, **Struktura i odwołania**.

        ![Struktura i informacje o projekcie języka C&#43; &#43; &#45;](../test/media/utecpp08.png "UteCpp08")

   2. Wybierz pozycję **Dodaj nowe odwołanie**.

        W oknie dialogowym **Dodaj odwołanie** wybierz projekt DLL i wybierz pozycję **Dodaj**.

        ![&#43; &#43; Właściwości &#45; projektu C Dodaj nowe odwołanie](../test/media/utecpp09.png "UteCpp09")

2. W pliku. cpp testu jednostkowego podmiotu zabezpieczeń należy uwzględnić plik. h kodu DLL:

   ```cpp
   #include "..\RootFinder\RootFinder.h"
   ```

3. Dodaj podstawowy test, który używa wyeksportowanej funkcji:

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

    Nowy test pojawi się w Eksploratorze testów.

5. W Eksploratorze testów wybierz opcję **Uruchom wszystkie**.

    ![Test podstawowego Eksploratora &#45; testów jednostkowych zakończonych niepowodzeniem](../test/media/utecpp10.png "UteCpp10")

   Został skonfigurowany test i projekty kodu i zweryfikowane, że można uruchomić testy, które uruchamiają funkcje w projekcie kodu. Teraz możesz zacząć pisać prawdziwe testy i kod.

### <a name="iterate"></a>Iteracyjnie rozszerza testy i przekazują je

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
    > Zalecamy, aby nie zmieniać testów, które zostały zakończone. Zamiast tego Dodaj nowy test, zaktualizuj kod tak, aby test zakończył się powodzeniem, a następnie Dodaj inny test i tak dalej.
    >
    >  Gdy użytkownicy zmienią swoje wymagania, należy wyłączyć testy, które nie są już poprawne. Napisz nowe testy i Przekształć je w jeden raz w ten sam przyrostowy sposób.

2. Skompiluj rozwiązanie, a następnie w Eksploratorze testów wybierz opcję **Uruchom wszystkie**.

     Nowy test zakończy się niepowodzeniem.

     ![RangeTest kończy się niepowodzeniem](../test/media/ute-cpp-testexplorer-rangetest-fail.png "UTE_Cpp_TestExplorer_RangeTest_Fail")

    > [!TIP]
    > Sprawdź, czy każdy test kończy się niepowodzeniem natychmiast po jego zapisaniu. Dzięki temu można uniknąć łatwego błędu podczas pisania testu, który nigdy nie powiedzie się.

3. Podnieś poziom testowanego kodu, tak aby nowe przebiegi testowe:

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

4. Skompiluj rozwiązanie, a następnie w Eksploratorze testów wybierz opcję **Uruchom wszystkie**.

     Oba testy zostały zakończone pomyślnie.

     ![Test zakresu Eksploratora &#45; testów jednostkowych zakończonych](../test/media/utecpp12.png "UteCpp12")

    > [!TIP]
    > Opracowuj kod przez dodanie testów pojedynczo. Upewnij się, że wszystkie testy są zakończone po każdej iteracji.

### <a name="debug"></a>Debuguj test zakończony niepowodzeniem

1. Dodaj inny test:

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

2. Skompiluj rozwiązanie i wybierz polecenie **Uruchom wszystkie**.

3. Otwórz (lub kliknij dwukrotnie) Test zakończony niepowodzeniem.

     Niepowodzenie zostało wyróżnione. Komunikat o błędzie jest widoczny w okienku szczegółów w Eksploratorze testów.

     ![NegativeRangeTests nie powiodło się](../test/media/ute-cpp-testexplorer-negativerangetest-fail.png "UTE_Cpp_TestExplorer_NegativeRangeTest_Fail")

4. Aby zobaczyć dlaczego test nie powiedzie się, przechodzenie przez funkcję:

    1. Ustaw punkt przerwania na początku funkcji SquareRoot.

    2. W menu skrótów testu zakończonego niepowodzeniem wybierz **Debuguj wybrane testy**.

         Gdy przebieg zostanie zatrzymany w punkcie przerwania, przejdź do kodu.

5. Wstaw kod w funkcji, którą tworzysz:

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

6. Wszystkie testy są teraz zakończone pomyślnie.

     ![Wszystkie testy zakończone powodzeniem](../test/media/ute-ult-alltestspass.png "UTE_ULT_AllTestsPass")

> [!TIP]
> Jeśli pojedyncze testy nie mają żadnych zależności, które uniemożliwiają ich uruchomienie w dowolnej kolejności, należy włączyć równoległe wykonywanie testów za pomocą przycisku przełączania ![&#95;wykonaj parallelicon&#45;mały](../test/media/ute-parallelicon-small.png "UTE_parallelicon — mały") przełącznik na pasku narzędzi. Może to znacznie skrócić czas potrzebny do uruchomienia wszystkich testów.

### <a name="refactor"></a>Refaktoryzacja kodu bez zmiany testów

1. Uprość Obliczanie centralne w funkcji SquareRoot:

    ```
    // old code:
    //   result = result - (result*result - v)/(2*result);
    // new code:
         result = (result + v/result)/2.0;

    ```

2. Skompiluj rozwiązanie i wybierz pozycję **Uruchom wszystkie**, aby upewnić się, że nie wprowadzono błędu.

    > [!TIP]
    > Dobry zestaw testów jednostkowych daje pewność, że podczas zmiany kodu nie wprowadzono usterek.
    >
    >  Kontynuuj refaktoryzację niezależnie od innych zmian.

## <a name="next-steps"></a>Następne kroki

- **Izolacji.** Większość bibliotek DLL jest zależna od innych podsystemów, takich jak bazy danych i inne biblioteki DLL. Te inne składniki są często opracowywane równolegle. Aby zezwolić na wykonywanie testów jednostkowych, gdy inne składniki nie są jeszcze dostępne, musisz zastąpić imitację lub

- **Testy weryfikacyjne kompilacji.** Testy można wykonywać na serwerze kompilacji zespołu w ustalonych odstępach czasu. Gwarantuje to, że usterki nie są wprowadzane podczas integracji pracy kilku członków zespołu.

- **Testy ewidencjonowania.** Można określić, że niektóre testy są wykonywane, zanim każdy członek zespołu sprawdzi kod w kontroli źródła. Zwykle jest to podzestaw kompletnego zestawu testów weryfikacyjnych kompilacji.

     Istnieje również możliwość przydzielenia minimalnego poziomu pokrycia kodu.

## <a name="see-also"></a>Zobacz też
 [Dodawanie testów jednostkowych do C++ istniejących aplikacji](../test/unit-testing-existing-cpp-applications-with-test-explorer.md) [przy użyciu programu Microsoft. VisualStudio. TestTools. CppUnitTestFramework](../test/using-microsoft-visualstudio-testtools-cppunittestframework.md) [— Przegląd informacji o współdziałaniu kodu zarządzanego/niezarządzanego](https://msdn.microsoft.com/library/ms973872.aspx) [Debugowanie kodu natywnego](../debugger/debugging-native-code.md) [— Przewodnik: Tworzenie i używanie biblioteki dołączanej dynamicznieC++()](https://msdn.microsoft.com/library/3ae94848-44e7-4955-bbad-7d40f493e941) [Importowanie i eksportowanie](https://msdn.microsoft.com/library/7c44c2aa-2117-4cec-9615-a65bfd3f8f7b)
