---
title: 'Szybki start: Programowanie sterowane testami za pomocą Eksploratora testów | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 5161b533-2127-4172-b473-d4ffc76ff05b
caps.latest.revision: 17
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eae08427e9ec61c34a98f3581355909317b69559
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672260"
---
# <a name="quick-start-test-driven-development-with-test-explorer"></a>Szybki start: programowanie sterowane testami za pomocą narzędzia Eksplorator testów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zalecamy utworzenie testów jednostkowych w celu zapewnienia poprawnego działania kodu przez wiele etapów tworzenia. Istnieje kilka struktur, za pomocą których można pisać testy jednostkowe, w tym niektóre opracowane przez strony trzecie. Niektóre środowiska testowe są wyspecjalizowane do testowania w różnych językach lub platformach. Eksplorator testów udostępnia jeden interfejs dla testów jednostkowych w dowolnej z tych platform. Karty są dostępne dla najczęściej używanych platform i można pisać własne karty dla innych platform.

 Eksplorator testów zastępuje okna testów jednostkowych znalezione we wcześniejszych wersjach programu Visual Studio. Korzyści obejmują:

- Uruchamiaj platformę .NET, niezarządzane, bazę danych i inne rodzaje testów przy użyciu jednego interfejsu.

- Użyj wybranej platformy testów jednostkowych, takiej jak NUnit lub MSTest Frameworks.

- Zobacz w jednym oknie wszystkie potrzebne informacje.

## <a name="using-test-explorer"></a>Korzystanie z Eksploratora testów
 ![Eksplorator testów jednostkowych z przyciskiem Uruchom wszystko](../test/media/unittestexplorer-beta.png "UnitTestExplorer (wersja beta)")

#### <a name="to-run-unit-tests-by-using-test-explorer"></a>Aby uruchomić testy jednostkowe za pomocą Eksploratora testów

1. Utwórz testy jednostkowe, które wykorzystują wybrane platformy testowe.

    Na przykład, aby utworzyć test, który używa struktury MSTest:

   1. Utwórz projekt testowy.

        W oknie dialogowym **Nowy projekt** rozwiń węzeł **Visual Basic**, **Visual C#** lub **Visual C++**, a następnie wybierz pozycję **Testuj**.

        Wybierz **projekt testu jednostkowego**.

   2. Napisz każdy test jednostkowy jako metodę. Opatrz każdą metodę testową prefiksem `[TestMethod]` atrybutu.

2. Jeśli pojedyncze testy nie mają żadnych zależności, które uniemożliwiają ich uruchomienie w dowolnej kolejności, Włącz równoległe wykonywanie testów przy użyciu przycisku ![wykonaj&#95;parallelicon&#45;mały](../test/media/ute-parallelicon-small.png "UTE_parallelicon — mały") przełącznik na pasku narzędzi. Może to znacznie skrócić czas potrzebny do uruchomienia wszystkich testów.

3. Na pasku menu wybierz **test**, **Uruchom testy jednostkowe**, **wszystkie testy**.

    Rozwiązanie kompiluje i uruchamia testy.

    Zostanie otwarty Eksplorator testów i zostanie wyświetlone podsumowanie wyników.

   **Aby wyświetlić pełną listę testów:** Wybierz pozycję **Pokaż wszystko** w dowolnej kategorii.

   **Aby wyświetlić szczegóły wyniku testu:** Wybierz test w Eksploratorze testów, aby wyświetlić szczegóły, takie jak komunikaty o wyjątkach, w okienku szczegółów.

   **Aby przejść do kodu testu:** Kliknij dwukrotnie test w Eksploratorze testów lub wybierz **Otwórz test** w menu skrótów.

   **Aby debugować test:** Otwórz menu skrótów dla jednego lub więcej testów, a następnie wybierz **Debuguj wybrane testy**.

> [!IMPORTANT]
> Wyświetlane wyniki dotyczą ostatniego uruchomienia. Kolorowy pasek wyników zawiera tylko wyniki testów, które zostały uruchomione. Jeśli na przykład uruchomisz kilka testów i niektóre z nich zakończą się niepowodzeniem, a następnie uruchomisz tylko testy zakończone powodzeniem, na pasku wyników będzie wyświetlana wartość wszystkie zielony.

> [!NOTE]
> Jeśli żaden test nie zostanie wyświetlony, upewnij się, że zainstalowano adapter do łączenia Eksploratora testów z używanym środowiskiem testowym. Aby uzyskać więcej informacji, zobacz [Korzystanie z innego środowiska testowego](/visualstudio/test/getting-started-with-unit-testing#use-a-third-party-test-framework).

## <a name="walkthrough-using-unit-tests-to-develop-a-method"></a><a name="walkthrough"></a> Przewodnik: korzystanie z testów jednostkowych do opracowania metody
 W tym instruktażu przedstawiono sposób tworzenia przetestowanej metody w języku C# przy użyciu struktury testów jednostkowych firmy Microsoft. Można łatwo dostosować ją do innych języków i korzystać z innych platform testowych, takich jak NUnit. Aby uzyskać więcej informacji, zobacz [Korzystanie z innego środowiska testowego](/visualstudio/test/getting-started-with-unit-testing#use-a-third-party-test-framework).

#### <a name="creating-the-test-and-method"></a>Tworzenie testu i metody

1. Utwórz projekt biblioteki klas języka Visual C#. Ten projekt będzie zawierać kod, który chcemy dostarczyć. W tym przykładzie ma nazwę `MyMath` .

2. Utwórz projekt testowy.

   - W oknie dialogowym **Nowy projekt** wybierz pozycję **Visual C#**, **test** , a następnie wybierz pozycję **projekt testu jednostkowego**.

        ![Nowy kod i projekty testowe](../test/media/unittestexplorerwalk1.png "UnitTestExplorerWalk1")

3. Napisz podstawową metodę testową. Sprawdź wynik uzyskany dla konkretnego danych wejściowych:

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

4. Generuj metodę z testu.

   1. Umieść kursor na `Rooter` , a następnie w menu skrótów wybierz polecenie **Generuj**, **nowy typ**.

   2. W oknie dialogowym **generowanie nowego typu** Ustaw **projekt** na projekt biblioteki klas. W tym przykładzie jest to `MyMath`.

   3. Umieść kursor na `SquareRoot` , a następnie w menu skrótów wybierz polecenie **Generuj**, **Metoda zastępcza**.

5. Uruchom test jednostkowy.

   1. W menu **test** wybierz kolejno opcje **Uruchom testy jednostkowe**i **wszystkie testy**.

        Rozwiązanie zostanie skompilowane i uruchomione.

        Zostanie otwarty Eksplorator testów i zostaną wyświetlone wyniki.

        Test pojawi się w obszarze **testy zakończone niepowodzeniem**.

6. Wybierz nazwę testu.

    Szczegóły testu są wyświetlane w dolnej części Eksploratora testów.

7. Wybierz elementy w obszarze **ślad stosu** , aby zobaczyć, gdzie test nie powiódł się.

   ![Eksplorator testów jednostkowych przedstawiający test zakończony niepowodzeniem.](../test/media/unittestexplorerwalkthrough2.png "UnitTestExplorerWalkthrough2")

   W tym momencie utworzono test i element zastępczy, który należy zmodyfikować tak, aby test zakończył się powodzeniem.

#### <a name="after-every-change-make-all-the-tests-pass"></a>Po każdej zmianie wykonaj wszystkie testy zakończone powodzeniem

1. W programie `MyMath\Rooter.cs` Popraw kod `SquareRoot` :

    ```csharp
    public double SquareRoot(double input)
     {
       return input / 2;
     }
    ```

2. W Eksploratorze testów wybierz opcję **Uruchom wszystkie**.

     Kod kompiluje i przebiegi testowe.

     Test kończy się powodzeniem.

     ![Eksplorator testów jednostkowych przedstawiający test zakończony powodzeniem.](../test/media/unittestexplorerwalkthrough3.png "UnitTestExplorerWalkthrough3")

#### <a name="add-tests-to-extend-the-range-of-inputs"></a>Dodawanie testów w celu poszerzenia zakresu wejść

1. Aby zwiększyć poziom pewności, że kod działa we wszystkich przypadkach, należy dodać testy, które próbują uzyskać szerszy zakres wartości wejściowych.

    > [!TIP]
    > Należy unikać zmiany istniejących testów, które przechodzą pomyślnie. Zamiast tego Dodaj nowe testy. Zmień istniejące testy tylko wtedy, gdy wymagania dotyczące użytkownika zostały zmienione. Te zasady ułatwiają zapewnienie, że nie utracisz istniejących funkcji podczas pracy w celu rozbudowania kodu.

     W klasie testowej Dodaj następujący test, który próbuje wykonać zakres wartości wejściowych:

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

2. W Eksploratorze testów wybierz opcję **Uruchom wszystkie**.

     Nowy test kończy się niepowodzeniem, mimo że pierwszy test jest nadal zakończony.

     Aby znaleźć punkt awarii, wybierz test zakończony niepowodzeniem, a następnie w dolnej części Eksploratora testów wybierz górny element **śladu stosu**.

3. Zbadaj badaną metodę, aby zobaczyć, co może być błędne. W `MyMath.Rooter` klasie ponownie Napisz kod:

    ```
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

4. W Eksploratorze testów wybierz opcję **Uruchom wszystkie**.

     Oba testy są teraz przekazywane.

#### <a name="add-tests-for-exceptional-cases"></a>Dodawanie testów do wyjątkowych przypadków

1. Dodaj test dla negatywnych danych wejściowych:

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

2. W Eksploratorze testów wybierz opcję **Uruchom wszystkie**.

     Metoda testowa pętle i musi być anulowana ręcznie.

3. Wybierz pozycję **Anuluj**.

     Test zatrzyma się po 10 sekundach.

4. Popraw kod metody:

    ```csharp

    public double SquareRoot(double input)
    {
      if (input <= 0.0)
      {
        throw new ArgumentOutOfRangeException();
      }
    ...
    ```

5. W Eksploratorze testów wybierz opcję **Uruchom wszystkie**.

     Wszystkie testy zostały zakończone pomyślnie.

#### <a name="refactor-without-changing-tests"></a>Refaktoryzacja bez zmiany testów

1. Uprość kod, ale nie zmieniaj testów.

    > [!TIP]
    > *Refaktoryzacja* to zmiana, która jest przeznaczona do lepszego wykonywania kodu lub ułatwienia zrozumienia kodu. Nie jest przeznaczone do zmiany zachowania kodu, dlatego testy nie są zmieniane.
    >
    >  Zalecamy wykonanie czynności refaktoryzacji niezależnie od kroków rozszerzających funkcjonalność. Pozostawienie niezmienionych testów daje pewność, że podczas refaktoryzacji nie wprowadzono przypadkowo błędów.

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

2. Wybierz pozycję **Uruchom wszystkie**.

     Wszystkie testy są nadal przekazywane.

     ![Eksplorator testów jednostkowych przedstawiający 3 testy zakończone.](../test/media/unittestexplorerwalkthrough4.png "UnitTestExplorerWalkthrough4")
