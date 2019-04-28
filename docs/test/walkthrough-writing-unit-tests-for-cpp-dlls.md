---
title: 'Instrukcje: Pisanie testów jednostkowych dla bibliotek DLL języka C++'
ms.date: 11/04/2017
ms.topic: conceptual
ms.author: mblome
manager: jillfra
ms.workload:
- cplusplus
author: mikeblome
ms.openlocfilehash: 960eb242a8b03b863f1b4e38e0cb8cae53eed469
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62819798"
---
# <a name="how-to-write-unit-tests-for-c-dlls"></a>Instrukcje: Pisanie testów jednostkowych dla bibliotek DLL języka C++

W tym przewodniku opisano sposób tworzenia natywnej biblioteki DLL C++ przy użyciu metodologii wczesnego testowania. Podstawowe kroki są następujące:

1. [Utwórz projekt testu natywnych](#create_test_project). Projekt testowy znajduje się w tym samym rozwiązaniu co projekt biblioteki DLL.

2. [Utwórz projekt biblioteki DLL](#create_dll_project). Ten poradnik tworzy DLL, nowe, ale procedura testowania istniejącej biblioteki DLL jest podobny.

3. [Uwidacznianie funkcji DLL testów](#make_functions_visible).

4. [Iteracyjne Udoskonal testy](#iterate). Firma Microsoft zaleca cyklu "ruch zrefaktoryzuj red zielony", w którym tworzenia kodu zostanie przeprowadzony przez testy.

5. [Debugowanie w przypadku braku testy](#debug). Można uruchomić testy w trybie debugowania.

6. [Refaktoryzuj podczas utrzymanie testów bez zmian](#refactor). Refaktoryzacja oznacza, że poprawy struktury kodu bez zmiany zachowania zewnętrznych. Możesz to zrobić w celu poprawy wydajności, rozszerzalność i czytelności kodu. Ponieważ zamiar nie należy zmieniać zachowanie, nie zmieniaj testów podczas wprowadzania zmian refaktoryzacji w kodzie. Testy pomoc, upewnij się, że nie wprowadzają błędów podczas są refaktoryzacji.

7. [Sprawdź pokrycia](using-code-coverage-to-determine-how-much-code-is-being-tested.md). Testy jednostkowe są bardziej użyteczne, gdy korzystają oni z kodu. Może odnajdywać, które części kodu były używane przez testy.

8. [Izolowanie jednostki z zasobami zewnętrznymi](using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md). Zazwyczaj Biblioteka DLL jest zależny od innych składników systemu, które tworzysz, takich jak inne biblioteki dll, bazy danych lub zdalnego podsystemów. Warto przetestować każda jednostka w izolacji od jego zależności. Składniki zewnętrzne, można wprowadzić testy spowolnienie działania. Podczas tworzenia aplikacji inne składniki mogą być niekompletne.

## <a name="create_test_project"></a> Utwórz natywny projekt testów jednostkowych

1. Na **pliku** menu, wybierz **New** > **projektu**.

     W oknie dialogowym Rozwiń **zainstalowane** > **szablony** > **Visual C++** > **testu**.

     Wybierz **natywny projekt testów jednostkowych** szablon lub niezależnie od zainstalowanego framework użytkownik sobie tego życzy. Jeśli wybierzesz inny szablon, takich jak Google Test i Boost.Test, podstawowe zasady są takie same, mimo że niektóre szczegóły będą się różnić.

     W tym przewodniku nosi nazwę projektu testowego `NativeRooterTest`.

     ![Tworzenie projektu testu jednostkowego w języku C++](../test/media/utecpp01.png)

2. W nowym projekcie, należy sprawdzić **unittest1.cpp**

     ![Projekt testowy z TESTEM&#95;klasy i testowania&#95;— metoda](../test/media/utecpp2.png)

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

    2. Na **testu** menu, wybierz **Uruchom** > **wszystkie testy**.

         Test skompilowane i uruchomione.

         **Eksplorator testów** pojawia się.

         Test pojawi się w obszarze **testy zakończone powodzeniem**.

         ![Eksplorator testów jednostki przy użyciu jednego testów zakończonych powodzeniem](../test/media/utecpp04.png)

## <a name="create_dll_project"></a> Utwórz projekt biblioteki DLL

1. Tworzenie **Visual C++** projektu przy użyciu **projekt systemu Win32** szablonu.

     W tym przewodniku nosi nazwę projektu `RootFinder`.

     ![Tworzenie projektu C++ Win32](../test/media/utecpp05.png)

2. Wybierz **DLL** i **Eksportuj symbole** Kreatora aplikacji Win32.

     **Eksportuj symbole** opcja powoduje wygenerowanie wygodne makro, które służy do deklarowania metod wyeksportowany.

     ![Kreator projektu C++ ustaw dla biblioteki DLL i eksportowanie symboli](../test/media/utecpp06.png)

3. Zadeklaruj eksportowanych funkcji podmiot zabezpieczeń *.h* pliku:

     ![Nowy kod projektu i .h plik DLL za pomocą interfejsu API makra](../test/media/utecpp07.png)

     Deklarator `__declspec(dllexport)` powoduje, że publiczne i chronione składowe klasy mają być wyświetlane poza bibliotekę DLL. Aby uzyskać więcej informacji, zobacz [korzystanie z dllimport i dllexport w klasach C++](/cpp/cpp/using-dllimport-and-dllexport-in-cpp-classes).

4. W polu podmiot zabezpieczeń *.cpp* plik i dodać minimalny treści funkcji:

    ```cpp
        // Find the square root of a number.
        double CRootFinder::SquareRoot(double v)
        {
            return 0.0;
        }
    ```

## <a name="make_functions_visible"></a> Kilka projekt testowy do projektu biblioteki DLL

1. Dodaj projekt biblioteki DLL do odwołań projektu dla projektu testowego:

   1. Otwórz właściwości projektu testowego i wybierz polecenie **wspólne właściwości** > **szablon i odwołania**.

        ![Właściwości projektu C++ | Szablon i odwołania](../test/media/utecpp08.png)

   2. Wybierz **Dodaj nowe odwołanie**.

        W **Dodaj odwołanie** okna dialogowego pole, zaznacz projekt DLL i wybierz **Dodaj**.

        ![Właściwości projektu C++ | Dodaj nowe odwołanie](../test/media/utecpp09.png)

2. W teście jednostkę główną *.cpp* plików, obejmują *.h* plik z kodem biblioteki DLL:

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

    Nowy test jest wyświetlany w **Eksploratora testów**.

5. W **Eksplorator testów**, wybierz **Uruchom wszystkie**.

    ![Eksplorator testów jednostkowych &#45; podstawowy Test zakończony sukcesem](../test/media/utecpp10.png)

   Mają ustawienie testu i projekty kodu, a następnie zweryfikować, że można uruchomić testy, które uruchamiania funkcji w projekcie kodu. Teraz możesz rozpocząć pisanie rzeczywistych testów i kodu.

## <a name="iterate"></a> Iteracyjne Udoskonal testy i nadawać im przekazać

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
    > Użytkownicy zmiany ich wymagań, wyłącz testy, które nie są już prawidłowe. Zapisz nowe testy i ich działania pojedynczo, w taki sam sposób przyrostowego.

2. Skompiluj rozwiązanie, a następnie w polu **Eksplorator testów**, wybierz **Uruchom wszystkie**.

     Nowy test kończy się niepowodzeniem.

     ![RangeTest kończy się niepowodzeniem](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

    > [!TIP]
    > Upewnij się, że każdy test zakończy się niepowodzeniem, natychmiast, po napisaniu go. Dzięki temu można uniknąć łatwe Błąd zapisywania testu, który nigdy nie zakończy się niepowodzeniem.

3. Zwiększ swój kod biblioteki DLL tak, aby nowy test zakończy się pomyślnie:

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

4. Kompiluj rozwiązanie, a następnie w polu **Eksplorator testów**, wybierz **Uruchom wszystkie**.

     Kod przechodzi oba testy.

     ![Eksplorator testów jednostkowych &#45; zakresu Test zakończony sukcesem](../test/media/utecpp12.png)

    > [!TIP]
    > Tworzenie kodu, dodając jeden testów w danym momencie. Upewnij się, że po każdej iteracji kod przechodzi wszystkie testy.

## <a name="debug"></a> Debuguj test niepowodzeniem

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

     Potwierdzenie nie powiodło się, jest wyróżniona. Komunikat o błędzie jest widoczny w okienku szczegółów **Eksplorator testów**.

     ![NegativeRangeTests nie powiodło się.](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

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

     ![Kod przechodzi wszystkie testy](../test/media/ute_ult_alltestspass.png)

> [!TIP]
> Poszczególne testy nie ma żadnych zależności, które uniemożliwiają są uruchamiane w dowolnej kolejności, należy włączyć równoległe wykonywanie testów za pomocą ![WYKONAJ&#95;parallelicon&#45;małych](../test/media/ute_parallelicon-small.png) Przełącz przycisk na pasku narzędzi. Może to znacznie zmniejszyć czas poświęcony na uruchamianie wszystkich testów.

## <a name="refactor"></a> Refaktoryzacja kodu bez zmieniania testów

1. Uprość centralnej obliczeń w funkcji SquareRoot:

    ```cpp
    // old code:
    //   result = result - (result*result - v)/(2*result);
    // new code:
         result = (result + v/result)/2.0;

    ```

2. Skompiluj rozwiązanie, a następnie wybierz **Uruchom wszystkie**, aby upewnić się, że błąd nie zostały wprowadzone.

    > [!TIP]
    > Dobry zestaw testów jednostkowych daje pewność, że użytkownik nie wprowadzają błędów po zmianie kodu.
    >
    > Zachowaj refaktoryzacji oddzielnie od innych zmian.

## <a name="next-steps"></a>Następne kroki

- **Izolacja.** Większość bibliotek DLL są zależne od innych podsystemów, takich jak bazy danych i inne biblioteki dll. Te inne składniki często są opracowywane równolegle. Aby umożliwić jednostek testów do wykonania, podczas gdy inne składniki nie są jeszcze dostępne, trzeba zastąpić mock lub

- **Testy weryfikacji kompilacji.** Może mieć testów wykonywanych na serwerze kompilacji zespołu w ustalonych odstępach czasu. Dzięki temu usterki nie są wprowadzane podczas pracy kilku członków zespołu jest zintegrowany.

- **Testów zaewidencjonowania.** Aby uzasadniają, że niektóre testy są wykonywane przed każdy członek zespołu sprawdza kod do kontroli źródła. Jest to zazwyczaj podzbiór cały zestaw testów weryfikacyjnych kompilacji.

     Można również wprowadzić minimalnego poziomu pokrycia kodu.

## <a name="see-also"></a>Zobacz także

- [Dodawanie testów jednostkowych do istniejących aplikacji C++](../test/how-to-use-microsoft-test-framework-for-cpp.md)
- [Korzystanie z elementu Microsoft.VisualStudio.TestTools.CppUnitTestFramework](how-to-use-microsoft-test-framework-for-cpp.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
- [Przewodnik: Tworzenie i używanie biblioteki dołączanej dynamicznie (C++)](/cpp/build/walkthrough-creating-and-using-a-dynamic-link-library-cpp)
- [Importowanie i eksportowanie](/cpp/build/importing-and-exporting)
