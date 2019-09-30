---
title: Testowanie jednostek kodu języka Visual C#
ms.date: 09/27/2019
ms.topic: conceptual
ms.author: gewarren
author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 0a724ab273401994faeb88ae197966ef538e842a
ms.sourcegitcommit: 13decf878b33fc0c5d665a88067170c2861b261b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71681596"
---
# <a name="unit-test-c-code"></a>Test jednostkowy kodu w języku C#

W tym artykule opisano jeden ze sposobów tworzenia testów jednostkowych C# dla klasy w aplikacji platformy UWP.

Klasa **Rooter** , która jest klasą testowa, implementuje funkcję, która oblicza oszacowanie wartości pierwiastek kwadratowy danej liczby.

W tym artykule przedstawiono *Programowanie oparte na testach*. W tym podejściu najpierw napiszesz test, który weryfikuje określone zachowanie w systemie, który jest testowany, a następnie napisze kod, który przeszedł test.

## <a name="create-the-solution-and-the-unit-test-project"></a>Tworzenie rozwiązania i projektu testu jednostkowego

1. Na **pliku** menu, wybierz **New** > **projektu**.

2. Wyszukaj i wybierz szablon projektu **pusta aplikacja (uniwersalna systemu Windows)** .

3. Nazwij projekt **matematyczny**.

4. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie i wybierz polecenie **dodaj** **Nowy projekt** > .

5. Wyszukaj i wybierz szablon projektu **aplikacja testów jednostkowych (uniwersalna systemu Windows)** .

6. Nazwij projekt testowy **RooterTests**.

## <a name="verify-that-the-tests-run-in-test-explorer"></a>Sprawdź, czy testy zostaną wykonane w Eksploratorze testów

1. Wstaw kod testu do **TestMethod1** w pliku *UnitTest.cs* :

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   Klasa <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> zawiera kilka metod statycznych, których można użyć do sprawdzenia wyników w metodach testowych.

::: moniker range="vs-2017"

2. W menu **test** wybierz polecenie **Uruchom** > **wszystkie testy**.

::: moniker-end

::: moniker range=">=vs-2019"

2. W menu **test** wybierz polecenie **Uruchom wszystkie testy**.

::: moniker-end

   Projekt testowy skompilowane i uruchomione. Poczekaj, ponieważ może to trochę potrwać. **Eksploratora testów** zostanie wyświetlone okno i test znajduje się w obszarze **testy zakończone powodzeniem**. **Podsumowanie** okienku u dołu okna udostępnia dodatkowe szczegóły dotyczące wybranego testu.

## <a name="add-the-rooter-class-to-the-maths-project"></a>Dodaj klasę Rooter do projektu matematycznych

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **matematyczny** , a następnie wybierz polecenie **Dodaj** **klasę** > .

2. Nazwa pliku klasy *Rooter.cs*.

3. Dodaj następujący kod do pliku *Rooter.Cser* klasy **root** :

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

   Klasa **root** deklaruje Konstruktor i metodę szacowania **SquareRoot** . Metoda **SquareRoot** jest tylko minimalną implementacją, wystarczy do przetestowania podstawowej struktury instalacji testowej.

4. Dodaj słowo kluczowe `public` do deklaracji klasy **Rooter** , aby kod testu mógł uzyskać do niego dostęp.

   ```csharp
   public class Rooter
   ```

## <a name="add-a-project-reference"></a>Dodaj odwołanie do projektu

1. Dodaj odwołanie z projektu RooterTests do aplikacji Maths.

    1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **RooterTests** , a następnie wybierz polecenie **Dodaj** **odwołanie** > .

    2. W **Dodaj odwołanie - RooterTests** okna dialogowego rozwiń **rozwiązania** i wybierz polecenie **projektów**. Wybierz projekt **Maths** .

        ![Dodaj odwołanie do projektu matematycznych](../test/media/ute_cs_windows_addreference.png)

2. Dodaj instrukcję `using` do pliku *UnitTest.cs* :

    1. Otwórz *UnitTest.cs*.

    2. Dodaj następujący kod poniżej `using Microsoft.VisualStudio.TestTools.UnitTesting;` wiersza:

       ```csharp
       using Maths;
       ```

3. Dodaj test, który używa funkcji **Rooter** . Dodaj następujący kod do *UnitTest.cs*:

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

   Nowy test jest wyświetlany w **Eksploratora testów** w **testy nieuruchamiane** węzła.

4. Aby uniknąć "ładunek zawiera co najmniej dwa pliki z tą samą ścieżką docelową", w **Eksplorator rozwiązań**rozwiń węzeł **Właściwości** w projekcie **Maths** , a następnie usuń plik *default. Rd. XML* .

::: moniker range="vs-2017"

6. W **Eksplorator testów**, wybierz **Uruchom wszystkie**.

   Rozwiązanie zostanie skompilowane i testy są uruchamiane i przekazywane.

   ![BasicTest przeszedł do Eksploratora testów](../test/media/ute_cpp_testexplorer_basictest.png)

::: moniker-end

::: moniker range=">=vs-2019"

6. W **Eksploratorze testów**wybierz opcję **Uruchom wszystkie testy**.

   Rozwiązanie zostanie skompilowane i testy są uruchamiane i przekazywane.

   ![Test podstawowy zakończony w Eksploratorze testów](../test/media/vs-2019/test-explorer-uwp-app.png)

::: moniker-end

Zostały skonfigurowane projekty testów i aplikacji oraz sprawdzono, że można uruchomić testy, które wywołują funkcje w projekcie aplikacji. Teraz możesz rozpocząć pisanie rzeczywistych testów i kodu.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a>Iteracyjne Udoskonal testy i nadawać im przekazać

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
   > Firma Microsoft zaleca, nie należy zmieniać testy, które zostały przekazane. Zamiast tego Dodaj nowy test.

2. Uruchom test **RangeTest** i sprawdź, czy ten błąd nie powiódł się.

   ![RangeTest kończy się niepowodzeniem](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > Natychmiast po napisaniu testu należy go uruchomić, aby sprawdzić, czy ten błąd nie powiódł się. Dzięki temu można uniknąć łatwe Błąd zapisywania testu, który nigdy nie zakończy się niepowodzeniem.

3. Tak, aby nowy test zakończy się pomyślnie, należy zwiększyć testowany kod. Zmień funkcję **SquareRoot** w *Rooter.cs* na:

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

4. W **Eksplorator testów**, wybierz **Uruchom wszystkie**.

::: moniker-end

::: moniker range=">=vs-2019"

4. W **Eksploratorze testów**wybierz opcję **Uruchom wszystkie testy**.

::: moniker-end

   Teraz kod przechodzi wszystkie trzy testy.

> [!TIP]
> Tworzenie kodu, dodając jeden testów w danym momencie. Upewnij się, że po każdej iteracji kod przechodzi wszystkie testy.

## <a name="refactor-the-code"></a>Refaktoryzacja kodu

W tej sekcji Refaktoryzacja dotyczy zarówno aplikacji, jak i kodu testowego, a następnie ponownie uruchamia testy, aby upewnić się, że są one nadal przekazywane.

### <a name="simplify-the-square-root-estimation"></a>Uproszczenie oszacowania głównego elementu kwadratowego

1. Uprość Obliczanie centralne w funkcji **SquareRoot** , zmieniając jeden wiersz kodu w następujący sposób:

    ```csharp
    // Old code
    //estimate = estimate - (estimate * estimate - x) / (2 * estimate);

    // New code
    estimate = (estimate + x/estimate) / 2.0;
    ```

2. Uruchom wszystkie testy, aby upewnić się, że regresja nie została wprowadzona. Wszystkie te powinny być przekazywane.

> [!TIP]
> Stabilne zestawy testów jednostkowych dobre daje pewność, że użytkownik nie wprowadzają błędów po zmianie kodu.

### <a name="eliminate-duplicated-code"></a>Eliminowanie duplikatu kodu

Metoda **RangeTest** określa mianownik zmiennej *tolerancji* , która jest przenoszona do metody <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>. Jeśli planujesz dodać dodatkowe testy, które używają tego samego obliczenia tolerancji, użycie zakodowanej wartości w wielu lokalizacjach sprawia, że kod jest trudniejszy do utrzymania.

1. Dodaj prywatną metodę pomocnika do klasy **UnitTest1** , aby obliczyć wartość tolerancji, a następnie Wywołaj tę metodę z **RangeTest**.

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

2. Uruchom **RangeTest** , aby upewnić się, że nadal kończy się powodzeniem.

> [!TIP]
> W przypadku dodania metody pomocnika do klasy testowej, która nie ma być wyświetlana w **Eksploratorze testów**, nie należy dodawać atrybutu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> do metody.

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Programowanie oparte na testach przy użyciu narzędzia Test Explorer @ no__t-0
