---
title: Wskazówki dotyczące programowania opartego na testach
ms.date: 07/24/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: a264975014fea88126bbca0589fe037e629dae10
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566283"
---
# <a name="walkthrough-test-driven-development-using-test-explorer"></a>Przewodnik: Programowanie sterowane testami za pomocą Eksploratora testów

Utwórz testy jednostkowe, aby zapewnić prawidłowe działanie kodu przez przyrostowe zmiany kodu. Istnieje kilka środowisk, których można użyć do pisania testów jednostkowych, łącznie z niektórymi opracowanymi przez osoby trzecie. Niektóre środowiska testowe są wyspecjalizowane do testowania w różnych językach lub platformach. Eksplorator testów udostępnia jeden interfejs do testów jednostkowych w dowolnym z tych środowisk. Aby uzyskać więcej informacji na temat programu **Test Explorer**, zobacz [Uruchamianie testów jednostkowych za pomocą Eksploratora testów](run-unit-tests-with-test-explorer.md) i [Eksploratora testów — często zadawane pytania](test-explorer-faq.md).

W tym instruktażu przedstawiono sposób tworzenia przetestowanej C# metody w programie przy użyciu programu Microsoft Test Framework (MSTest). Można łatwo dostosować ją do innych języków lub innych platform testowych, takich jak NUnit. Aby uzyskać więcej informacji, zobacz [instalowanie platform testów jednostkowych innych firm](install-third-party-unit-test-frameworks.md).

## <a name="create-a-test-and-generate-code"></a>Tworzenie testu i generowanie kodu

1. C# Utwórz projekt **biblioteki klas (.NET standard)** . Ten projekt będzie zawierać kod, który chcemy przetestować. Nazwij projekt **Math**.

2. W tym samym rozwiązaniu Dodaj nowy projekt **projektu testowego MSTest (.NET Core)** . Nazwij projekt testowy **MathTests**.

   ![Nowe projekty kodu i testowanie](../test/media/test-driven-development-ide.png)

3. Napisz prostą metodę testową, która weryfikuje wynik uzyskany dla konkretnego danych wejściowych. Dodaj następujący kod do klasy `UnitTest1`:

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
     Assert.AreEqual(expectedResult, actualResult, delta: expectedResult / 100);
   }
   ```

4. Generuj typ na podstawie kodu testu.

   1. Umieść kursor na `Rooter`, a następnie w menu żarówki wybierz polecenie **Generuj typ "Rooter"**  > **Wygeneruj nowy typ**.

      ![Generuj nowy typ szybka akcja](media/test-driven-development-generate-new-type.png)

   2. W oknie dialogowym **generowanie typu** ustaw wartość **Project** na **wyrażenie Math**, projekt biblioteki klas, a następnie wybierz **przycisk OK**.

      ![Okno dialogowe generowanie typu w programie Visual Studio 2019](media/test-driven-development-generate-type-dialog.png)

5. Generuj metodę z kodu testu. Umieść kursor na `SquareRoot`, a następnie w menu żarówki wybierz polecenie **Generuj metodę "Rooter. SquareRoot"** .

6. Uruchom test jednostkowy.

   1. Aby otworzyć **Eksploratora testów**, w menu **test** wybierz pozycję **Windows** > **Test Explorer**.

   2. W **Eksploratorze testów**wybierz przycisk **Uruchom wszystko** , aby uruchomić test.

   Rozwiązanie zostanie skompilowane, a testy zakończą się niepowodzeniem.

7. Wybierz nazwę testu.

   Szczegóły testu są wyświetlane w okienku **podsumowania szczegółów testu** .

   ![Podsumowanie szczegółów testu w Eksploratorze testów](media/test-driven-development-test-detail-summary.png)

8. Wybierz górny link w obszarze **ślad stosu** , aby przejść do lokalizacji, w której test zakończył się niepowodzeniem.

W tym momencie utworzono test i element zastępczy, który można zmodyfikować tak, aby test zakończył się powodzeniem.

## <a name="verify-a-code-change"></a>Weryfikowanie zmiany kodu

1. W pliku *Class1.cs* popraw kod `SquareRoot`:

    ```csharp
    public double SquareRoot(double input)
    {
        return input / 2;
    }
    ```

2. W **Eksplorator testów**, wybierz **Uruchom wszystkie**.

   Rozwiązanie zostanie skompilowane, a testy są wykonywane i przekazywane.

   ![Eksplorator testów z przekazaniem testu](../test/media/test-driven-development-passed-test.png)

## <a name="extend-the-range-of-inputs"></a>Zwiększ zakres danych wejściowych

Aby poprawić wiarygodność kodu we wszystkich przypadkach, należy dodać testy, które próbują uzyskać szerszy zakres wartości wejściowych.

> [!TIP]
> Unikaj zmieniania istniejących testów, które przekazują. Zamiast tego Dodaj nowe testy. Zmieniaj istniejące testy tylko wtedy, gdy zmienią się wymagania użytkownika. Te zasady ułatwiają upewnij się, że nie tracisz istniejących funkcji podczas pracy nad rozszerzeniem kodu.

1. W klasie testowej Dodaj następujący test, który próbuje wykonać zakres wartości wejściowych:

    ```csharp
    [TestMethod]
    public void RooterValueRange()
    {
        // Create an instance to test.
        Rooter rooter = new Rooter();

        // Try a range of values.
        for (double expected = 1e-8; expected < 1e+8; expected *= 3.2)
        {
            RooterOneValue(rooter, expected);
        }
    }

    private void RooterOneValue(Rooter rooter, double expectedResult)
    {
        double input = expectedResult * expectedResult;
        double actualResult = rooter.SquareRoot(input);
        Assert.AreEqual(expectedResult, actualResult, delta: expectedResult / 1000);
    }
    ```

2. W **Eksplorator testów**, wybierz **Uruchom wszystkie**.

   Nowy test zakończy się niepowodzeniem (mimo że pierwszy test nadal przebiega). Aby znaleźć punkt awarii, wybierz test zakończony niepowodzeniem, a następnie sprawdź szczegóły w okienku **podsumowania szczegółów testu** .

3. Sprawdź testowaną metodę test, aby zobaczyć, co może być źle. Zmień kod `SquareRoot` w następujący sposób:

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

4. W **Eksplorator testów**, wybierz **Uruchom wszystkie**.

   Teraz kod przechodzi oba testy.

## <a name="add-tests-for-exceptional-cases"></a>Dodawanie testów wyjątkowych przypadków

1. Dodaj nowy test dla negatywnych danych wejściowych:

    ```csharp
    [TestMethod]
    public void RooterTestNegativeInputx()
    {
        Rooter rooter = new Rooter();
        try
        {
            rooter.SquareRoot(-10);
        }
        catch (System.ArgumentOutOfRangeException)
        {
            return;
        }
        Assert.Fail();
    }
    ```

2. W **Eksplorator testów**, wybierz **Uruchom wszystkie**.

   Metoda testowa pętle i musi być anulowana ręcznie.

3. Wybierz pozycję **Anuluj** na pasku narzędzi **Eksploratora testów**.

   Test przerywa wykonywanie.

4. Popraw kod `SquareRoot` poprzez dodanie następującej instrukcji `if` na początku metody:

    ```csharp
    public double SquareRoot(double input)
    {
        if (input <= 0.0)
        {
            throw new ArgumentOutOfRangeException();
        }
        ...
    ```

5. W **Eksplorator testów**, wybierz **Uruchom wszystkie**.

   Kod przechodzi wszystkie testy.

## <a name="refactor-the-code-under-test"></a>Refaktoryzacja testowanego kodu

Refaktoryzacja kodu, ale nie zmieniaj testów.

> [!TIP]
> *Refaktoryzacja* to zmiana, która jest przeznaczona do lepszego lub łatwiejszego zrozumienia kodu. Nie jest przeznaczone do zmiany zachowania kodu, a w związku z tym testy nie są zmieniane.
>
> Firma Microsoft zaleca, aby wykonać kroki refaktoryzacji oddzielnie od kroków, które rozszerzają funkcjonalność. Utrzymywanie testów w niezmienionej postaci daje pewność, że możesz mieć nie zostaną przypadkowo wprowadzone usterki podczas refaktoryzacji.

1. Zmień wiersz, który oblicza `result` w metodzie `SquareRoot` w następujący sposób:

    ```csharp
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
    ```

2. Wybierz pozycję **Uruchom wszystkie**i sprawdź, czy wszystkie testy są nadal zakończone pomyślnie.

   ![Eksplorator testów przedstawiający 3 testy zakończone](../test/media/test-driven-development-three-passed-tests.png)
