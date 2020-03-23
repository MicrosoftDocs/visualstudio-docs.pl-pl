---
title: Badanie jednostkowe kodu języka Visual C#
ms.date: 09/27/2019
ms.topic: conceptual
ms.author: mikejo
author: mikejo5000
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 31fbbfaa5d16dd51776f592b89a7846936b3013f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590868"
---
# <a name="unit-test-c-code"></a>Test jednostkowy kodu w języku C#

W tym artykule opisano jeden sposób tworzenia testów jednostkowych dla klasy Języka C# w aplikacji platformy uniwersalnej systemu i platformy uniwersalnej systemu.

**Rooter** Klasa, która jest klasą w fazie testów, implementuje funkcję, która oblicza oszacowanie pierwiastek kwadratowy danej liczby.

W tym artykule przedstawiono *rozwój oparty na testach*. W tym podejściu najpierw napisać test, który weryfikuje określone zachowanie w systemie, który testujesz, a następnie napisać kod, który przechodzi test.

## <a name="create-the-solution-and-the-unit-test-project"></a>Tworzenie rozwiązania i projektu testu jednostkowego

1. W menu **Plik** wybierz polecenie **Nowy** > **projekt**.

2. Wyszukaj i wybierz szablon projektu **Pusta aplikacja (uniwersalny system Windows).**

3. Nazwij projekt **Maths**.

4. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie i wybierz pozycję **Dodaj** > **nowy projekt**.

5. Wyszukaj i wybierz szablon projektu **aplikacji testu jednostkowego (Universal Windows).**

6. Nazwij projekt testowy **RooterTests**.

## <a name="verify-that-the-tests-run-in-test-explorer"></a>Sprawdź, czy testy są uruchamiane w Eksploratorze testów

1. Wstaw kod testowy do **pliku TestMethod1** w pliku *UnitTest.cs:*

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   Klasa <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> zawiera kilka metod statycznych, których można użyć do weryfikacji wyników w metodach testowych.

::: moniker range="vs-2017"

2. W menu **Test** wybierz polecenie **Uruchom** > **wszystkie testy**.

::: moniker-end

::: moniker range=">=vs-2019"

2. W menu **Test** wybierz polecenie **Uruchom wszystkie testy**.

::: moniker-end

   Projekt testowy tworzy i uruchamia. Bądź cierpliwy, ponieważ może to trochę potrwać. Zostanie wyświetlone okno **Eksploratora testów,** a test zostanie wyświetlony w obszarze **Testy przeszły**. Okienko **Podsumowanie** w dolnej części okna zawiera dodatkowe szczegóły dotyczące wybranego testu.

## <a name="add-the-rooter-class-to-the-maths-project"></a>Dodawanie klasy Rooter do projektu Matematyka

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **Matematyka,** a następnie wybierz polecenie **Dodaj** > **klasę**.

2. Nazwij plik klasy *Rooter.cs*.

3. Dodaj następujący kod do pliku *Rooter.cs* klasy **Rooter:**

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

   **Rooter** Klasa deklaruje konstruktora i **SquareRoot** estymatora metody. **SquareRoot** Metoda jest tylko minimalna implementacja, wystarczy, aby przetestować podstawową strukturę konfiguracji testowania.

4. Dodaj `public` słowo kluczowe do deklaracji klasy **Rooter,** dzięki czemu kod testowy może uzyskać do niego dostęp.

   ```csharp
   public class Rooter
   ```

## <a name="add-a-project-reference"></a>Dodawanie odwołania do projektu

1. Dodaj odwołanie z projektu RooterTests do aplikacji Maths.

    1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **RooterTests,** a następnie wybierz polecenie **Dodaj** > **odwołanie**.

    2. W oknie dialogowym **Dodawanie odwołania — Testy rooterów** rozwiń węzeł **Rozwiązanie** i wybierz pozycję **Projekty**. Wybierz projekt **Matematyka.**

        ![Dodawanie odwołania do projektu Matematyka](../test/media/ute_cs_windows_addreference.png)

2. Dodaj `using` instrukcję do pliku *UnitTest.cs:*

    1. Otwórz *UnitTest.cs*.

    2. Dodaj ten kod `using Microsoft.VisualStudio.TestTools.UnitTesting;` poniżej wiersza:

       ```csharp
       using Maths;
       ```

3. Dodaj test, który używa funkcji **Rooter.** Dodaj następujący kod do *UnitTest.cs:*

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

   Nowy test pojawia się w **Eksploratorze testów** w węźle **Nie uruchamiaj testów.**

4. Aby uniknąć błędu "Ładunek zawiera dwa lub więcej plików z tą samą ścieżką docelową", w **Eksploratorze rozwiązań**rozwiń węzeł **Właściwości** w ramach projektu **Matematyka,** a następnie usuń plik *Default.rd.xml.*

::: moniker range="vs-2017"

6. W **Eksploratorze testów**wybierz pozycję **Uruchom wszystko**.

   Kompilacje rozwiązania i testy są uruchamiane i przebiegać.

   ![Testy podstawowe zdane w Eksploratorze testów](../test/media/ute_cpp_testexplorer_basictest.png)

::: moniker-end

::: moniker range=">=vs-2019"

6. W **Eksploratorze testów**wybierz pozycję **Uruchom wszystkie testy**.

   Kompilacje rozwiązania i testy są uruchamiane i przebiegać.

   ![Test podstawowy przekazany w Eksploratorze testów](../test/media/vs-2019/test-explorer-uwp-app.png)

::: moniker-end

Skonfigurowano projekty testów i aplikacji i zweryfikowano, że można uruchomić testy, które wywołują funkcje w projekcie aplikacji. Teraz możesz zacząć pisać prawdziwe testy i kod.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a>Iteratively zwiększyć testy i uczynić je przejść

1. Dodaj nowy test o nazwie **RangeTest**:

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
   > Zaleca się, aby nie zmieniać testów, które przeszły. Zamiast tego dodaj nowy test.

2. Uruchom **test RangeTest** i sprawdź, czy nie powiedzie się.

   ![Test rangetest kończy się niepowodzeniem](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > Natychmiast po napisaniu testu uruchom go, aby sprawdzić, czy nie powiedzie się. Pomaga to uniknąć łatwego błędu pisania testu, który nigdy nie kończy się niepowodzeniem.

3. Popraw kod w ramach testu, tak aby nowy test przebiegał pomyślnie. Zmień funkcję **SquareRoot** w *Rooter.cs* na ten sposób:

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

::: moniker range="vs-2017"

4. W **Eksploratorze testów**wybierz pozycję **Uruchom wszystko**.

::: moniker-end

::: moniker range=">=vs-2019"

4. W **Eksploratorze testów**wybierz pozycję **Uruchom wszystkie testy**.

::: moniker-end

   Wszystkie trzy testy teraz przechodzą.

> [!TIP]
> Opracowanie kodu przez dodanie testów po jednym na raz. Upewnij się, że wszystkie testy przechodzą po każdej iteracji.

## <a name="refactor-the-code"></a>Refaktoryzator kodu

W tej sekcji refaktoryzujesz kod aplikacji i testu, a następnie uruchom ponownie testy, aby upewnić się, że nadal przechodzą.

### <a name="simplify-the-square-root-estimation"></a>Uprość oszacowanie pierwiastek kwadratowy

1. Uprość centralne obliczenia w funkcji **SquareRoot,** zmieniając jeden wiersz kodu w następujący sposób:

    ```csharp
    // Old code
    //estimate = estimate - (estimate * estimate - x) / (2 * estimate);

    // New code
    estimate = (estimate + x/estimate) / 2.0;
    ```

2. Uruchom wszystkie testy, aby upewnić się, że nie wprowadzono regresji. Wszyscy powinni przejść.

> [!TIP]
> Stabilny zestaw dobrych testów jednostkowych daje pewność, że nie wprowadzono błędów po zmianie kodu.

### <a name="eliminate-duplicated-code"></a>Wyeliminuj zduplikowany kod

**RangeTest** Metody twarde kody mianownik zmiennej *tolerancji,* który jest przekazywany do <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> metody. Jeśli planujesz dodać dodatkowe testy, które używają tego samego obliczenia tolerancji, użycie wartości zakodowane w wielu lokalizacjach sprawia, że kod trudniejsze do utrzymania.

1. Dodaj prywatną metodę pomocnika do klasy **UnitTest1,** aby obliczyć wartość tolerancji, a następnie wywołaj tę metodę z **RangeTest**.

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
        // Old code
        // double tolerance = expected/1000;

        // New code
        double tolerance = ToleranceHelper(expected);
    }
    ...
    ```

2. Uruchom **RangeTest,** aby upewnić się, że nadal przechodzi.

> [!TIP]
> Jeśli dodasz metodę pomocniczą do klasy testowej i nie chcesz, aby była wyświetlana <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> w **Eksploratorze testów,** nie dodawaj atrybutu do metody.

## <a name="see-also"></a>Zobacz też

- [Instruktaż: Program rozwoju opartego na testach przy użyciu Eksploratora testów](quick-start-test-driven-development-with-test-explorer.md)
