---
title: Wskazówki dotyczące programowania opartego na testach
description: Dowiedz się, jak opracować przetestowaną metodę w języku C# przy użyciu platformy Microsoft Test Framework, którą można łatwo dostosować do innych języków lub platform testowych, takich jak NUnit.
ms.custom: SEO-VS-2020
ms.date: 07/24/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 82cccbc47d26dd9ef74ee02931d6efb4bbfa0054
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329162"
---
# <a name="walkthrough-test-driven-development-using-test-explorer"></a>Przewodnik: Programowanie sterowane testami za pomocą Eksploratora testów

Utwórz testy jednostkowe, aby zapewnić prawidłowe działanie kodu przez przyrostowe zmiany kodu. Istnieje kilka struktur, za pomocą których można pisać testy jednostkowe, w tym niektóre opracowane przez strony trzecie. Niektóre środowiska testowe są wyspecjalizowane do testowania w różnych językach lub platformach. Eksplorator testów udostępnia jeden interfejs dla testów jednostkowych w dowolnej z tych platform. Aby uzyskać więcej informacji na temat programu **Test Explorer**, zobacz [Uruchamianie testów jednostkowych za pomocą Eksploratora testów](run-unit-tests-with-test-explorer.md) i [Eksploratora testów — często zadawane pytania](test-explorer-faq.md).

W tym instruktażu przedstawiono sposób tworzenia przetestowanej metody w języku C# przy użyciu platformy Microsoft Test Framework (MSTest). Można łatwo dostosować ją do innych języków lub innych platform testowych, takich jak NUnit. Aby uzyskać więcej informacji, zobacz [Instalowanie platform testów jednostkowych](install-third-party-unit-test-frameworks.md)innych firm.

## <a name="create-a-test-and-generate-code"></a>Tworzenie testu i generowanie kodu

1. Utwórz projekt **biblioteki klas C# (.NET standard)** . Ten projekt będzie zawierać kod, który chcemy przetestować. Nazwij projekt **Math**.

2. W tym samym rozwiązaniu Dodaj nowy projekt **projektu testowego MSTest (.NET Core)** . Nazwij projekt testowy **MathTests**.

   ![Nowy kod i projekty testowe](../test/media/test-driven-development-ide.png)

3. Napisz prostą metodę testową, która weryfikuje wynik uzyskany dla konkretnego danych wejściowych. Dodaj następujący kod do `UnitTest1` klasy:

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

   1. Umieść kursor na stronie `Rooter` , a następnie w menu żarówki wybierz polecenie **Generuj typ "Rooter"**  >  **Generuj nowy typ**.

      ![Generuj nowy typ szybka akcja](media/test-driven-development-generate-new-type.png)

   2. W oknie dialogowym **generowanie typu** ustaw wartość **Project** na **wyrażenie Math**, projekt biblioteki klas, a następnie wybierz **przycisk OK**.

      ![Okno dialogowe generowanie typu w programie Visual Studio 2019](media/test-driven-development-generate-type-dialog.png)

5. Generuj metodę z kodu testu. Umieść kursor na `SquareRoot` , a następnie w menu żarówki wybierz polecenie **Generuj metodę "Rooter. SquareRoot"**.

6. Uruchom test jednostkowy.

   1. Aby otworzyć **Eksploratora testów**, w menu **test** wybierz polecenie **Windows**  >  **Eksplorator testów** systemu Windows.

   2. W **Eksploratorze testów** wybierz przycisk **Uruchom wszystko** , aby uruchomić test.

   Rozwiązanie zostanie skompilowane, a testy zakończą się niepowodzeniem.

7. Wybierz nazwę testu.

   Szczegóły testu są wyświetlane w okienku **podsumowania szczegółów testu** .

   ![Podsumowanie szczegółów testu w Eksploratorze testów](media/test-driven-development-test-detail-summary.png)

8. Wybierz górny link w obszarze **ślad stosu** , aby przejść do lokalizacji, w której test zakończył się niepowodzeniem.

W tym momencie utworzono test i element zastępczy, który można zmodyfikować tak, aby test zakończył się powodzeniem.

## <a name="verify-a-code-change"></a>Weryfikowanie zmiany kodu

1. W pliku *Class1.cs* Popraw kod `SquareRoot` :

    ```csharp
    public double SquareRoot(double input)
    {
        return input / 2;
    }
    ```

2. W **Eksploratorze testów** wybierz opcję **Uruchom wszystkie**.

   Rozwiązanie zostanie skompilowane, a testy są wykonywane i przekazywane.

   ![Eksplorator testów z przekazaniem testu](../test/media/test-driven-development-passed-test.png)

## <a name="extend-the-range-of-inputs"></a>Zwiększ zakres danych wejściowych

Aby poprawić wiarygodność kodu we wszystkich przypadkach, należy dodać testy, które próbują uzyskać szerszy zakres wartości wejściowych.

> [!TIP]
> Należy unikać zmiany istniejących testów, które przechodzą pomyślnie. Zamiast tego Dodaj nowe testy. Zmień istniejące testy tylko wtedy, gdy wymagania dotyczące użytkownika zostały zmienione. Te zasady pomagają upewnić się, że nie utracisz istniejących funkcji podczas pracy w celu poszerzenia kodu.

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

2. W **Eksploratorze testów** wybierz opcję **Uruchom wszystkie**.

   Nowy test zakończy się niepowodzeniem (mimo że pierwszy test nadal przebiega). Aby znaleźć punkt awarii, wybierz test zakończony niepowodzeniem, a następnie sprawdź szczegóły w okienku **podsumowania szczegółów testu** .

3. Zbadaj badaną metodę, aby zobaczyć, co może być błędne. Zmień `SquareRoot` kod w następujący sposób:

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

4. W **Eksploratorze testów** wybierz opcję **Uruchom wszystkie**.

   Oba testy są teraz przekazywane.

## <a name="add-tests-for-exceptional-cases"></a>Dodawanie testów do wyjątkowych przypadków

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

2. W **Eksploratorze testów** wybierz opcję **Uruchom wszystkie**.

   Metoda testowa pętle i musi być anulowana ręcznie.

3. Wybierz pozycję **Anuluj** na pasku narzędzi **Eksploratora testów**.

   Test przerywa wykonywanie.

4. Popraw `SquareRoot` kod przez dodanie następującej `if` instrukcji na początku metody:

    ```csharp
    public double SquareRoot(double input)
    {
        if (input <= 0.0)
        {
            throw new ArgumentOutOfRangeException();
        }
        ...
    ```

5. W **Eksploratorze testów** wybierz opcję **Uruchom wszystkie**.

   Wszystkie testy zostały zakończone pomyślnie.

## <a name="refactor-the-code-under-test"></a>Refaktoryzacja testowanego kodu

Refaktoryzacja kodu, ale nie zmieniaj testów.

> [!TIP]
> *Refaktoryzacja* to zmiana, która jest przeznaczona do lepszego lub łatwiejszego zrozumienia kodu. Nie jest przeznaczone do zmiany zachowania kodu, dlatego testy nie są zmieniane.
>
> Zalecamy wykonanie czynności refaktoryzacji niezależnie od kroków rozszerzających funkcjonalność. Pozostawienie niezmienionych testów daje pewność, że podczas refaktoryzacji nie wprowadzono przypadkowo błędów.

1. Zmień wiersz obliczany `result` w `SquareRoot` metodzie w następujący sposób:

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

2. Wybierz pozycję **Uruchom wszystkie** i sprawdź, czy wszystkie testy są nadal zakończone pomyślnie.

   ![Eksplorator testów przedstawiający 3 testy zakończone](../test/media/test-driven-development-three-passed-tests.png)
