---
title: Testowanie jednostek kodu języka Visual C#
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
author: gewarren
ms.openlocfilehash: dfb0ed5775e011471ba32d4962b0bf25cfcda2b1
ms.sourcegitcommit: 16175e0cea6af528e9ec76f0b94690faaf1bed30
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71481887"
---
# <a name="unit-test-c-code"></a>Test jednostkowy kodu w języku C#

W tym artykule opisano jeden ze sposobów tworzenia testów jednostkowych C# dla klasy w aplikacji platformy UWP. Klasa Rooter pokazuje niejasne chwile teorii limit z calculus poprzez implementację funkcji, który oblicza oszacowanie pierwiastek kwadratowy z podanej liczbie. Aplikacja matematycznych następnie może używać tej funkcji do pokazania użytkownika fun rzeczy, które można wykonać za pomocą matematyczne.

W tym artykule przedstawiono sposób korzystania z jednostki testowania jako pierwszy krok w rozwoju. W tym podejściu najpierw napisać metodę testową, która sprawdza określone zachowanie w systemie, które testujesz, a następnie napisać kod, który przejdzie test. Wycofanie tej strategii, wprowadzając zmiany kolejności poniższych procedur, w pierwszej operacji zapisu kod, który chcesz przetestować, a następnie napisz testy jednostkowe.

W tym artykule tworzy również jedno rozwiązanie Visual Studio i oddzielnych projektów dla testów jednostkowych i biblioteki DLL, która ma zostać przetestowana. Możesz również uwzględnić testy jednostkowe bezpośrednio w projekcie biblioteki DLL lub można utworzyć oddzielne rozwiązania dla testów jednostkowych i biblioteki DLL.

## <a name="create-the-solution-and-the-unit-test-project"></a>Tworzenie rozwiązania i projektu testu jednostkowego

1. Na **pliku** menu, wybierz **New** > **projektu**.

2. Wyszukaj i wybierz szablon projektu **pusta aplikacja (uniwersalna systemu Windows)** .

3. Nadaj nazwę projektowi `Maths`.

4. W **Eksploratora rozwiązań**, wybierz nazwę rozwiązania, wybierz **Dodaj** z menu skrótów, a następnie wybierz **nowy projekt**.

5. Wyszukaj i wybierz szablon projektu **aplikacja testów jednostkowych (uniwersalna systemu Windows)** .

6. Otwórz *UnitTest1.cs* w edytorze programu Visual Studio.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;
   using Microsoft.VisualStudio.TestTools.UnitTesting;
   using Maths;

   namespace RooterTests
   {
       [TestClass]
       public class UnitTest1

           [TestMethod]
           public void TestMethod1()
           {

           }
   ```

   Należy pamiętać o następujących kwestiach:

   - Każdy test jest definiowana za pomocą <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atrybutu. Metoda testowa musi zwracać typ void i nie może mieć żadnych parametrów.

   - Metody testu muszą być w klasie z atrybutem <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> atrybutu.

        Gdy testy są uruchamiane, tworzone jest wystąpienie każdej klasy testu. Metody testowe są wywoływane w nieokreślonej kolejności.

   - Można zdefiniować specjalne metody, które są wywoływane przed i po każdym modułu, klasy lub metody. Aby uzyskać więcej informacji, zobacz [używania struktury MSTest w testach jednostkowych](../test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md).

## <a name="verify-that-the-tests-run-in-test-explorer"></a>Sprawdź, czy testy zostaną wykonane w Eksploratorze testów

1. Wstaw kod testu w TestMethod1 w *UnitTest1.cs* pliku:

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   Należy zauważyć, że <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> klasa udostępnia kilka metod statycznych, których można sprawdzić wyniki za pomocą metod testowych.

2. Na **testu** menu, wybierz **Uruchom** , a następnie wybierz **Uruchom wszystkie**.

   Projekt testowy skompilowane i uruchomione. **Eksploratora testów** zostanie wyświetlone okno i test znajduje się w obszarze **testy zakończone powodzeniem**. **Podsumowanie** okienku u dołu okna udostępnia dodatkowe szczegóły dotyczące wybranego testu.

   ![Eksplorator testów](../test/media/ute_cpp_testexplorer_testmethod1.png)

## <a name="add-the-rooter-class-to-the-maths-project"></a>Dodaj klasę Rooter do projektu matematycznych

1. W **Eksploratora rozwiązań**, wybierz **matematycznych** nazwy projektu. Z menu skrótów wybierz polecenie **Dodaj**, a następnie **klasy**.

2. Nazwa pliku klasy *Rooter.cs*.

3. Dodaj następujący kod do klasy Rooter *Rooter.cs* pliku:

   ```csharp
   public Rooter()
   {
   }

   // estimate the square root of a number
   public double SquareRoot(double x)
   {
       return 0.0;
   }
   ```

   `Rooter` Klasa deklaruje Konstruktor i `SquareRoot` metoda narzędzie do szacowania.

4. `SquareRoot` Metodą jest tylko minimalny implementacji wystarczający do testowania podstawowej struktury testowania instalacji.

## <a name="couple-the-test-project-to-the-app-project"></a>Kilka projekt testowy do projektu aplikacji

1. Dodaj odwołanie do niej matematycznych w projekcie RooterTests.

    1. W **Eksploratora rozwiązań**, wybierz **RooterTests** projektu, a następnie wybierz **Dodaj odwołanie** w menu skrótów.

    2. W **Dodaj odwołanie - RooterTests** okna dialogowego rozwiń **rozwiązania** i wybierz polecenie **projektów**. Następnie wybierz pozycję **matematycznych** elementu.

        ![Dodaj odwołanie do projektu matematycznych](../test/media/ute_cs_windows_addreference.png)

2. Dodaj instrukcję using instrukcję, aby *UnitTest1.cs* pliku:

    1. Otwórz *UnitTest1.cs*.

    2. Dodaj następujący kod poniżej `using Microsoft.VisualStudio.TestTools.UnitTesting;` wiersza:

       ```csharp
       using Maths;
       ```

3. Dodaj test, który używa funkcji Rooter. Dodaj następujący kod do *UnitTest1.cs*:

   ```csharp
   [TestMethod]
   public void BasicTest()
   {
       Maths.Rooter rooter = new Rooter();
       double expected = 0.0;
       double actual = rooter.SquareRoot(expected * expected);
       double tolerance = .001;
       Assert.AreEqual(expected, actual, tolerance);
   }
   ```

4. Skompiluj rozwiązanie.

   Nowy test jest wyświetlany w **Eksploratora testów** w **testy nieuruchamiane** węzła.

5. W **Eksplorator testów**, wybierz **Uruchom wszystkie**.

   ![Podstawowy Test zakończony pomyślnie](../test/media/ute_cpp_testexplorer_basictest.png)

Mają ustawienie testu i projekty kodu, a następnie zweryfikować, że można uruchomić testy, które uruchamiania funkcji w projekcie kodu. Teraz możesz rozpocząć pisanie rzeczywistych testów i kodu.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a>Iteracyjne Udoskonal testy i nadawać im przekazać

1. Dodaj nowy test:

   ```csharp
   [TestMethod]
   public void RangeTest()
   {
       Rooter rooter = new Rooter();
       for (double v = 1e-6; v < 1e6; v = v * 3.2)
       {
           double expected = v;
           double actual = rooter.SquareRoot(v*v);
           double tolerance = expected/1000;
           Assert.AreEqual(expected, actual, tolerance);
       }
   }
   ```

   > [!TIP]
   > Firma Microsoft zaleca, nie należy zmieniać testy, które zostały przekazane. Zamiast tego Dodaj nowy test, zaktualizować kod, tak aby test zakończy się pomyślnie, a następnie dodaj innego testu, i tak dalej.
   >
   > Użytkownicy zmiany ich wymagań, wyłącz testy, które nie są już prawidłowe. Zapisz nowe testy i ich działania pojedynczo, w taki sam sposób przyrostowego.

2. W **Eksplorator testów**, wybierz **Uruchom wszystkie**.

3. Test nie powiedzie się.

   ![RangeTest kończy się niepowodzeniem](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > Po napisaniu go Sprawdź, czy każdy test zakończy się niepowodzeniem. Dzięki temu można uniknąć łatwe Błąd zapisywania testu, który nigdy nie zakończy się niepowodzeniem.

4. Tak, aby nowy test zakończy się pomyślnie, należy zwiększyć testowany kod. Zmiana `SquareRoot` działa w programach *Rooter.cs* do tego:

   ```csharp
   public double SquareRoot(double x)
   {
       double estimate = x;
       double diff = x;
       while (diff > estimate / 1000)
       {
           double previousEstimate = estimate;
           estimate = estimate - (estimate * estimate - x) / (2 * estimate);
           diff = Math.Abs(previousEstimate - estimate);
       }
       return estimate;
   }
   ```

5. Kompiluj rozwiązanie, a następnie w polu **Eksplorator testów**, wybierz **Uruchom wszystkie**.

   Teraz kod przechodzi wszystkie trzy testy.

> [!TIP]
> Tworzenie kodu, dodając jeden testów w danym momencie. Upewnij się, że po każdej iteracji kod przechodzi wszystkie testy.

## <a name="debug-a-failing-test"></a>Debuguj test niepowodzeniem

1. Dodaj kolejny test do *UnitTest1.cs*:

    ```csharp
    // Verify that negative inputs throw an exception.
    [TestMethod]
    public void NegativeRangeTest()
    {
        string message;
        Rooter rooter = new Rooter();
        for (double v = -0.1; v > -3.0; v = v - 0.5)
        {
            try
            {
                // Should raise an exception:
                double actual = rooter.SquareRoot(v);

                message = String.Format("No exception for input {0}", v);
                Assert.Fail(message);
            }
            catch (ArgumentOutOfRangeException ex)
            {
                continue; // Correct exception.
            }
            catch (Exception e)
            {
                message = String.Format("Incorrect exception for {0}", v);
                Assert.Fail(message);
            }
        }
    }
    ```

2. W **Eksplorator testów**, wybierz **Uruchom wszystkie**.

   Test nie powiedzie się. Wybierz nazwę testu w **Eksploratora testów**. Potwierdzenie nie powiodło się, jest wyróżniona. Komunikat o błędzie jest widoczny w okienku szczegółów **Eksplorator testów**.

   ![NegativeRangeTests nie powiodło się.](../test/media/ute_cpp_testexplorer_negativerangetest_fail.png)

3. Aby zobaczyć, dlaczego test zakończy się niepowodzeniem, krok przy użyciu funkcji:

    1. Ustaw punkt przerwania na początku `SquareRoot` funkcji.

    2. W menu skrótów testów zakończonych niepowodzeniem, wybierz **Debuguj wybrane testy**.

        Po zatrzymaniu w punkcie przerwania Uruchom przejść przez kod.

    3. Dodaj kod do metody Rooter w celu wyłapania wyjątku:

        ```csharp
        public double SquareRoot(double x)
        {
            if (x < 0.0)
            {
                throw new ArgumentOutOfRangeException();
        }
        ```

4. W **Eksploratora testów**, wybierz **Uruchom wszystkie** poprawiony metoda testowa, i upewnij się, że nie zostały wprowadzone regresji.

Teraz kod przechodzi wszystkie testy.

![Kod przechodzi wszystkie testy](../test/media/ute_ult_alltestspass.png)

## <a name="refactor-the-code"></a>Refaktoryzacja kodu

**Uprość centralnej obliczeń w funkcji SquareRoot.**

1. Zmień implementację wynik

    ```csharp
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;
    ```

2. Wybierz **Uruchom wszystkie** wycofanej metoda testowa, i upewnij się, że nie zostały wprowadzone regresji.

> [!TIP]
> Stabilne zestawy testów jednostkowych dobre daje pewność, że użytkownik nie wprowadzają błędów po zmianie kodu.

**Refaktoryzuj kod testu, aby wyeliminować zduplikowany kodem.**

Należy pamiętać, że `RangeTest` metoda twardych kody mianownik `tolerance` zmiennej, która jest przekazywana do <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> metody. Jeśli planujesz dodać dodatkowe testy, które używają tych samych obliczeń na uszkodzenia użytkowania ustaloną wartość w wielu miejscach może prowadzić do błędów.

1. Dodaj prywatną metodę do klasy Unit1Test, aby obliczyć wartość tolerancji, a następnie zamiast tego wywołać tej metody.

    ```csharp
    private double ToleranceHelper(double expected)
    {
        return expected / 1000;
    }

    ...

    [TestMethod]
    public void RangeTest()
    {
        ...
        // old code
        // double tolerance = expected/1000;
        // new code
        double tolerance = ToleranceHelper(expected);
        Assert.AreEqual(expected, actual, tolerance);
    }
    ...
    ```

2. Wybierz **Uruchom wszystkie** wycofanej metoda testowa, i upewnij się, że nie zostały wprowadzone błąd.

> [!NOTE]
> Jeśli dodasz metody pomocnika do klasy testowej, które nie mają być wyświetlane w **Eksploratora testów**, nie należy dodawać <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atrybutu do metody.
