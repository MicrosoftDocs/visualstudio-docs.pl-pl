---
title: Programowanie sterowane za pomocą narzędzia Eksplorator testów testami
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 4b0692a790955c537c00e35be97d52583862e5a3
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59649579"
---
# <a name="quickstart-test-driven-development-with-test-explorer"></a>Szybki start: Programowanie sterowane testami za pomocą narzędzia Eksplorator testów

Zaleca się utworzenie testów jednostkowych w celu zapewnienia poprawnego działania kodu przez wiele kroków przyrostowych cyklu rozwoju. Istnieje kilka środowisk, których można użyć do pisania testów jednostkowych, łącznie z niektórymi opracowanymi przez osoby trzecie. Niektóre środowiska testowe są wyspecjalizowane w testowaniu różnych języków lub platform. Eksplorator testów udostępnia jeden interfejs do testów jednostkowych w dowolnym z tych środowisk. Dostępne są adaptery dla większości powszechnie stosowanych środowisk, a następnie można napisać własne adaptery dla innych platform.

Eksplorator testów zastępuje okna testów jednostkowych ze starszych wersji programu Visual Studio. Jego zalety obejmują:

- Uruchamianie platformy .NET, niezarządzanych, bazy danych i innych rodzajów testów przy użyciu pojedynczego interfejsu.

- Użyj jednostki testu wybranego, takich jak NUnit środowiska lub środowisk MSTest.

- Zobacz w jednym oknie użytkownikowi potrzebnych informacji.

## <a name="use-test-explorer"></a>Korzystanie z Eksploratora testów

![Test Explorer z wyświetlonym przycisk Uruchom wszystko](../test/media/unittestexplorer-beta-.png)

### <a name="to-run-unit-tests-by-using-test-explorer"></a>Aby uruchomić testy jednostkowe za pomocą Eksploratora testów

1. Tworzenie testów jednostkowych, które używają wybranych środowisk testowych. Na przykład aby utworzyć test który używa środowiska Mstest:

   1. Tworzenie **projektu testu jednostkowego** projektu dla C#, Visual Basic lub C++.

   2. Napisz każdy test jednostkowy jako metodę. Prefiks każdej metody testowej z `[TestMethod]` atrybutu.

2. Poszczególne testy nie ma żadnych zależności, które uniemożliwiają są uruchamiane w dowolnej kolejności, należy włączyć równoległe wykonywanie testów za pomocą ![WYKONAJ&#95;parallelicon&#45;małe](../test/media/ute_parallelicon-small.png) Przełącz przycisk na pasku narzędzi. Może to znacznie zmniejszyć czas poświęcony na uruchamianie wszystkich testów.

3. Na pasku menu wybierz **testu** > **uruchomić testy jednostkowe** > **wszystkie testy**.

    Rozwiązanie zostanie skompilowane i uruchomić testy.

    Eksplorator testów otwiera i wyświetla podsumowanie wyników.

   **Aby wyświetlić pełną listę testów:** Wybierz **Pokaż wszystko** w dowolnej kategorii.

   **Aby wyświetlić szczegóły wyniku testu:** Wybierz test w Eksploratorze testów, aby wyświetlić szczegóły, takie jak komunikaty wyjątków w okienku szczegółów.

   **Aby przejść do kodu testu:** Kliknij dwukrotnie test w Eksploratorze testów lub wybierz **Otwórz Test** w menu skrótów.

   **Aby debugować test:** Otwórz menu skrótów dla jednego lub więcej testów, a następnie wybierz **Debuguj wybrane testy**.

> [!IMPORTANT]
> Wyświetlane wyniki dotyczą ostatniego działają. Kolorowe paski wyników pokazują jedynie wyniki wykonanych testów. Na przykład jeśli uruchomisz kilka testów i niektóre z nich zakończyć się niepowodzeniem, a następnie uruchom testy zakończone powodzeniem, następnie paski wyników zostaną wyświetlone wszystkie zielony.

> [!NOTE]
> Jeśli pojawi się żaden test, upewnij się, że zainstalowano adapter do połączenia Eksploratora testów ze środowiskiem testowym, którego używasz. Aby uzyskać więcej informacji, zobacz [instalowanie platform testów jednostkowych innych firm](install-third-party-unit-test-frameworks.md).

## <a name="walkthrough-using-unit-tests-to-develop-a-method"></a>Przewodnik: Testów przy użyciu jednostki do opracowania metody

W tym instruktażu przedstawiono sposób opracować przetestowaną metodę w języku C# za pomocą środowiska testów jednostkowych firmy Microsoft. Możesz ją łatwo przystosować do innych języków i używać innych środowisk testowych, takich jak NUnit. Aby uzyskać więcej informacji, zobacz [instalowanie platform testów jednostkowych innych firm](install-third-party-unit-test-frameworks.md).

### <a name="create-the-test-and-method"></a>Tworzenie testu i metody

1. Tworzenie C# **biblioteki klas** projektu. Projekt ten będzie zawierał kod, który chcemy dostarczyć. W tym przykładzie jest on nazwany `MyMath`.

2. Utwórz nową **projektu testu jednostkowego** projektu.

   ![Nowe projekty kodu i testowanie](../test/media/unittestexplorerwalk1.png)

3. Napisz podstawową metodę testową. Sprawdź wynik uzyskany dla określonych danych wejściowych:

   ```csharp

   [TestMethod]
   public void BasicRooterTest()
   {
     // Create an instance to test:
     Rooter rooter = new Rooter();
     // Define a test input and output value:
     double expectedResult = 2.0;
     double input = expectedResult * expectedResult;
     // Run the method under test:
     double actualResult = rooter.SquareRoot(input);
     // Verify the result:
     Assert.AreEqual(expectedResult, actualResult,
         delta: expectedResult / 100);
   }
   ```

4. Wygeneruj metodę z testu.

   1.  Umieść kursor w `Rooter`, a następnie w menu skrótów wybierz polecenie **Generuj** > **nowy typ**.

   2.  W **Generuj nowy typ** okno dialogowe, zestaw **projektu** do projektu biblioteki klas. W tym przykładzie jest `MyMath`.

   3.  Umieść kursor w `SquareRoot`, a następnie w menu skrótów wybierz polecenie **Generuj** > **szkieletu metody**.

5. Uruchom test jednostkowy.

   1.  Na **testu** menu, wybierz **uruchomić testy jednostkowe** > **wszystkie testy**.

        Rozwiązanie zostanie skompilowane i działa.

        Eksplorator testów otwiera i wyświetla wyniki.

        Test pojawi się w obszarze **testy zakończone niepomyślnie**.

6. Wybierz nazwę testu.

    Szczegóły testu zostaną wyświetlone w dolnej części Eksploratora testów.

7. Wybierz elementy w obszarze **ślad stosu** aby zobaczyć, gdzie test nie powiódł się.

   ![Testów jednostkowych Test Explorer z wyświetlonym nie powiodło się.](../test/media/unittestexplorerwalkthrough2.png)

   Na tym etapie utworzono test i procedurę zastępczą, którą zmodyfikujesz, aby test zakończy się pomyślnie.

#### <a name="after-every-change-make-all-the-tests-pass"></a>Po każdej zmianie należy wprowadzić wszystkie testy.

1.  W *MyMath\Rooter.cs*, Popraw kod metody `SquareRoot`:

    ```csharp
    public double SquareRoot(double input)
     {
       return input / 2;
     }
    ```

2.  W Eksploratorze testów wybierz **Uruchom wszystkie**.

     Kod zostanie skompilowany, a test uruchomiony.

     Test zakończy się pomyślnie.

     ![Jednostka Test Explorer z wyświetlonym testu wynikiem pozytywnym.](../test/media/unittestexplorerwalkthrough3.png)

#### <a name="add-tests-to-extend-the-range-of-inputs"></a>Dodaj testy, aby rozszerzyć zakres danych wejściowych

1.  Aby zwiększyć pewność, że kod działa we wszystkich przypadkach, Dodaj testy, które sprawdzają szerszy zakres wartości wejściowych.

    > [!TIP]
    > Unikaj zmieniania istniejących testów, które przekazują. Zamiast tego Dodaj nowe testy. Zmieniaj istniejące testy tylko wtedy, gdy zmienią się wymagania użytkownika. Te zasady ułatwiają upewnij się, że nie tracisz istniejących funkcji podczas pracy nad rozszerzeniem kodu.

     W klasie testów Dodaj następujący test, który sprawdzi zakres wartości wejściowych:

    ```csharp
    [TestMethod]
    public void RooterValueRange()
    {
      // Create an instance to test:
      Rooter rooter = new Rooter();
      // Try a range of values:
      for (double expectedResult = 1e-8;
          expectedResult < 1e+8;
          expectedResult = expectedResult * 3.2)
      {
        RooterOneValue(rooter, expectedResult);
      }
    }

    private void RooterOneValue(Rooter rooter, double expectedResult)
    {
      double input = expectedResult * expectedResult;
      double actualResult = rooter.SquareRoot(input);
      Assert.AreEqual(expectedResult, actualResult,
          delta: expectedResult / 1000);
    }
    ```

2.  W Eksploratorze testów wybierz **Uruchom wszystkie**.

     Nowy test kończy się niepowodzeniem, chociaż nadal przechodzi pierwszy test.

     Aby znaleźć punkt awarii, zaznacz test niepowodzeniem, a następnie w dolnej części Eksploratora testów wybierz górny element w sekcji **ślad stosu**.

3.  Sprawdź testowaną metodę test, aby zobaczyć, co może być źle. W `MyMath.Rooter` klasy, przepisz:

    ```csharp
    public double SquareRoot(double input)
    {
      double result = input;
      double previousResult = -input;
      while (Math.Abs(previousResult - result) > result / 1000)
      {
        previousResult = result;
        result = result - (result * result - input) / (2 * result);
      }
      return result;
    }
    ```

4.  W Eksploratorze testów wybierz **Uruchom wszystkie**.

     Teraz kod przechodzi oba testy.

#### <a name="add-tests-for-exceptional-cases"></a>Dodawanie testów wyjątkowych przypadków

1.  Dodaj test ujemnych danych wejściowych:

    ```csharp
    [TestMethod]
     public void RooterTestNegativeInputx()
     {
         Rooter rooter = new Rooter();
         try
         {
             rooter.SquareRoot(-10);
         }
         catch (ArgumentOutOfRangeException e)
         {
             return;
         }
         Assert.Fail();
     }
    ```

2.  W Eksploratorze testów wybierz **Uruchom wszystkie**.

     Testowana metoda zapętla i musi zostać anulowana ręcznie.

3.  Wybierz **anulować**.

     Test zatrzyma się po 10 sekundach.

4.  Napraw kod metody:

    ```csharp

    public double SquareRoot(double input)
    {
      if (input <= 0.0)
      {
        throw new ArgumentOutOfRangeException();
      }
    ...
    ```

5.  W Eksploratorze testów wybierz **Uruchom wszystkie**.

     Kod przechodzi wszystkie testy.

#### <a name="refactor-without-changing-tests"></a>Refaktoryzacja bez zmieniania testów

1.  Uprość kod, ale nie zmieniaj testów.

    > [!TIP]
    > A *refaktoryzacji* jest zmianę, która jest przeznaczona do wprowadzania działania kodu lub uczynienie go łatwiejszym do zrozumienia. Nie jest przeznaczone do zmiany zachowania kodu, a w związku z tym testy nie są zmieniane.
    >
    > Firma Microsoft zaleca, aby wykonać kroki refaktoryzacji oddzielnie od kroków, które rozszerzają funkcjonalność. Utrzymywanie testów w niezmienionej postaci daje pewność, że możesz mieć nie zostaną przypadkowo wprowadzone usterki podczas refaktoryzacji.

    ```csharp
    public class Rooter
    {
      public double SquareRoot(double input)
      {
        if (input <= 0.0)
        {
          throw new ArgumentOutOfRangeException();
        }
        double result = input;
        double previousResult = -input;
        while (Math.Abs(previousResult - result) > result / 1000)
        {
          previousResult = result;
          result = (result + input / result) / 2;
          //was: result = result - (result * result - input) / (2*result);
        }
        return result;
      }
    }
    ```

2.  Wybierz **uruchomić wszystkie**.

     Kod nadal przechodzi wszystkie testy.

     ![Eksplorator testów jednostkowych pokazujący 3 testy zakończone pomyślnie.](../test/media/unittestexplorerwalkthrough4.png)
