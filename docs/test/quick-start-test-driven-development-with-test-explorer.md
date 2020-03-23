---
title: Przewodnik po rozwoju oparty na testach
ms.date: 07/24/2019
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: a264975014fea88126bbca0589fe037e629dae10
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566283"
---
# <a name="walkthrough-test-driven-development-using-test-explorer"></a>Instruktaż: Program rozwoju opartego na testach przy użyciu Eksploratora testów

Tworzenie testów jednostkowych, aby pomóc zachować kod działa poprawnie poprzez zmiany kodu przyrostowego. Istnieje kilka struktur, których można używać do pisania testów jednostkowych, w tym niektóre opracowane przez strony trzecie. Niektóre struktury testów są wyspecjalizowane do testowania w różnych językach lub platformach. Eksplorator testów udostępnia jeden interfejs dla testów jednostkowych w dowolnej z tych struktur. Aby uzyskać więcej informacji na temat **Eksploratora testów,** zobacz [Uruchamianie testów jednostkowych z często zadawanymi pytaniami Eksploratora testów](run-unit-tests-with-test-explorer.md) i [Eksploratora testów](test-explorer-faq.md).

W tym przewodniku pokazano, jak opracować przetestowaną metodę w języku C# przy użyciu programu Microsoft Test Framework (MSTest). Można łatwo dostosować go do innych języków lub innych struktur testowych, takich jak NUnit. Aby uzyskać więcej informacji, zobacz [Instalowanie struktur testów jednostkowych innych firm](install-third-party-unit-test-frameworks.md).

## <a name="create-a-test-and-generate-code"></a>Tworzenie testu i generowanie kodu

1. Utwórz projekt biblioteki klas języka C# **(.NET Standard).** Ten projekt będzie zawierać kod, który chcemy przetestować. Nazwij projekt **MyMath**.

2. W tym samym rozwiązaniu dodaj nowy projekt **testu MSTest (.NET Core).** Nazwij projekt testowy **MathTests**.

   ![Nowy kod i projekty testowe](../test/media/test-driven-development-ide.png)

3. Napisz prostą metodę testową, która weryfikuje wynik uzyskany dla określonego wejścia. Dodaj następujący kod `UnitTest1` do klasy:

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

4. Generowanie typu z kodu testu.

   1. Umieść kursor na `Rooter`, a następnie z menu żarówki wybierz polecenie **Generuj typ "Rooter"** > **Generuj nowy typ**.

      ![Generowanie szybkiego działania nowego typu](media/test-driven-development-generate-new-type.png)

   2. W oknie dialogowym **Generowanie typu** ustaw pozycję **Project** na **MyMath**, projekt biblioteki klas, a następnie wybierz przycisk **OK**.

      ![Okno dialogowe Generowanie typu w programie Visual Studio 2019](media/test-driven-development-generate-type-dialog.png)

5. Wygeneruj metodę z kodu testowego. Umieść kursor na `SquareRoot`, a następnie z menu żarówki wybierz opcję **Generuj metodę 'Rooter.SquareRoot'**.

6. Uruchom test jednostkowy.

   1. Aby otworzyć **Eksploratora testów**w menu **Test,** wybierz polecenie**Eksplorator testów** **systemu Windows** > .

   2. W **Eksploratorze testów**wybierz przycisk **Uruchom wszystko,** aby uruchomić test.

   Rozwiązanie tworzy, a test jest uruchamiany i kończy się niepowodzeniem.

7. Wybierz nazwę testu.

   Szczegóły testu są wyświetlane w okienku **Podsumowanie szczegółów testu.**

   ![Podsumowanie szczegółów testu w Eksploratorze testów](media/test-driven-development-test-detail-summary.png)

8. Wybierz górne łącze w obszarze **Śledzenie stosu,** aby przejść do lokalizacji, w której test nie powiódł się.

W tym momencie utworzono test i skrótowy, który można zmodyfikować, tak aby test przebiegł pomyślnie.

## <a name="verify-a-code-change"></a>Weryfikowanie zmiany kodu

1. W pliku *Class1.cs* poprawić `SquareRoot`kod:

    ```csharp
    public double SquareRoot(double input)
    {
        return input / 2;
    }
    ```

2. W **Eksploratorze testów**wybierz pozycję **Uruchom wszystko**.

   Rozwiązanie tworzy, a test jest uruchamiany i przekazy.

   ![Eksplorator testów przedstawiający test zdawacyjny](../test/media/test-driven-development-passed-test.png)

## <a name="extend-the-range-of-inputs"></a>Rozszerzenie zakresu wejść

Aby zwiększyć naszą pewność, że kod działa we wszystkich przypadkach, dodaj testy, które próbują szerszy zakres wartości wejściowych.

> [!TIP]
> Należy unikać zmiany istniejących testów, które przechodzą. Zamiast tego dodaj nowe testy. Zmień istniejące testy tylko wtedy, gdy zmieniają się wymagania użytkownika. Ta zasada pomaga upewnić się, że nie utracisz istniejących funkcji podczas pracy nad rozszerzeniem kodu.

1. W klasie testowej dodaj następujący test, który próbuje zakresu wartości wejściowych:

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

2. W **Eksploratorze testów**wybierz pozycję **Uruchom wszystko**.

   Nowy test kończy się niepowodzeniem (chociaż pierwszy test nadal kończy się pomyślnie). Aby znaleźć punkt błędu, wybierz test nieudolny, a następnie spójrz na szczegóły w okienku **Podsumowanie szczegółów testu.**

3. Sprawdź metodę w ramach testu, aby zobaczyć, co może być nie tak. Zmień `SquareRoot` kod w następujący sposób:

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

4. W **Eksploratorze testów**wybierz pozycję **Uruchom wszystko**.

   Oba testy teraz przechodzą.

## <a name="add-tests-for-exceptional-cases"></a>Dodaj testy w wyjątkowych przypadkach

1. Dodaj nowy test dla danych wejściowych ujemnych:

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

2. W **Eksploratorze testów**wybierz pozycję **Uruchom wszystko**.

   Metoda w pętli testowej i musi być anulowana ręcznie.

3. Wybierz **pozycję Anuluj** na pasku narzędzi **Eksploratora testów**.

   Test przestaje być wykonywany.

4. Napraw `SquareRoot` kod, dodając `if` następującą instrukcję na początku metody:

    ```csharp
    public double SquareRoot(double input)
    {
        if (input <= 0.0)
        {
            throw new ArgumentOutOfRangeException();
        }
        ...
    ```

5. W **Eksploratorze testów**wybierz pozycję **Uruchom wszystko**.

   Wszystkie testy przechodzą.

## <a name="refactor-the-code-under-test"></a>Refaktoryzuje testowany kod

Refaktoryzować kod, ale nie należy zmieniać testów.

> [!TIP]
> *Refaktoryzacji* jest zmiana, która ma na celu kod wykonać lepiej lub łatwiejsze do zrozumienia. Nie jest przeznaczony do zmiany zachowania kodu i dlatego testy nie są zmieniane.
>
> Zaleca się wykonywanie kroków refaktoryzacji oddzielnie od kroków rozszerzających funkcjonalność. Utrzymanie testów bez zmian daje pewność, że nie przypadkowo wprowadzono błędy podczas refaktoryzacji.

1. Zmień wiersz, który `result` oblicza w metodzie w `SquareRoot` następujący sposób:

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

2. Wybierz **pozycję Uruchom wszystko**i sprawdź, czy wszystkie testy nadal przechodzą.

   ![Eksplorator testów pokazujący 3 zdań testów](../test/media/test-driven-development-three-passed-tests.png)
