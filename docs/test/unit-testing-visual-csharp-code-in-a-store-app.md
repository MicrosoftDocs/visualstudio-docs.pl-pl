---
title: Testowanie jednostkowe kodu Visual C#
ms.date: 09/27/2019
ms.topic: conceptual
ms.author: mikejo
author: mikejo5000
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 31fbbfaa5d16dd51776f592b89a7846936b3013f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75590868"
---
# <a name="unit-test-c-code"></a>Test jednostkowy kodu w języku C#

W tym artykule opisano jeden ze sposobów tworzenia testów jednostkowych dla klasy C# w aplikacji platformy UWP.

Klasa **Rooter** , która jest klasą testowa, implementuje funkcję, która oblicza oszacowanie wartości pierwiastek kwadratowy danej liczby.

W tym artykule przedstawiono *Programowanie oparte na testach*. W tym podejściu najpierw napiszesz test, który weryfikuje określone zachowanie w systemie, który jest testowany, a następnie napisze kod, który przeszedł test.

## <a name="create-the-solution-and-the-unit-test-project"></a>Utwórz rozwiązanie i projekt testu jednostkowego

1. W menu **plik** wybierz pozycję **Nowy**  >  **projekt**.

2. Wyszukaj i wybierz szablon projektu **pusta aplikacja (uniwersalna systemu Windows)** .

3. Nazwij projekt **matematyczny**.

4. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie i wybierz polecenie **Dodaj**  >  **Nowy projekt**.

5. Wyszukaj i wybierz szablon projektu **aplikacja testów jednostkowych (uniwersalna systemu Windows)** .

6. Nazwij projekt testowy **RooterTests**.

## <a name="verify-that-the-tests-run-in-test-explorer"></a>Sprawdź, czy testy są uruchamiane w Eksploratorze testów

1. Wstaw kod testu do **TestMethod1** w pliku *UnitTest.cs* :

   ```csharp
   [TestMethod]
   public void TestMethod1()
   {
       Assert.AreEqual(0, 0);
   }
   ```

   <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>Klasa zawiera kilka metod statycznych, których można użyć do sprawdzenia wyników w metodach testowych.

::: moniker range="vs-2017"

2. W menu **test** wybierz polecenie **Uruchom** > **wszystkie testy**.

::: moniker-end

::: moniker range=">=vs-2019"

2. W menu **test** wybierz polecenie **Uruchom wszystkie testy**.

::: moniker-end

   Projekt testowy zostanie skompilowany i uruchomiony. Poczekaj, ponieważ może to trochę potrwać. Zostanie wyświetlone okno **Eksplorator testów** , a test zostanie wyświetlony na liście **zakończonych testów**. Okienko **Podsumowanie** u dołu okna zawiera dodatkowe szczegółowe informacje o wybranym teście.

## <a name="add-the-rooter-class-to-the-maths-project"></a>Dodawanie klasy Rooter do projektu Maths

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **matematyczny** , a następnie wybierz polecenie **Dodaj**  >  **klasę**.

2. Nazwij plik klasy *Rooter.cs*.

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

4. Dodaj `public` słowo kluczowe do deklaracji klasy **Rooter** , aby kod testu mógł uzyskać do niego dostęp.

   ```csharp
   public class Rooter
   ```

## <a name="add-a-project-reference"></a>Dodaj odwołanie do projektu

1. Dodaj odwołanie z projektu RooterTests do aplikacji Maths.

    1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **RooterTests** , a następnie wybierz polecenie **Dodaj**  >  **odwołanie**.

    2. W oknie dialogowym **Dodawanie odwołania — RooterTests** rozwiń węzeł **rozwiązanie** i wybierz pozycję **projekty**. Wybierz projekt **Maths** .

        ![Dodaj odwołanie do projektu Maths](../test/media/ute_cs_windows_addreference.png)

2. Dodaj `using` instrukcję do pliku *UnitTest.cs* :

    1. Otwórz *UnitTest.cs*.

    2. Dodaj następujący kod pod `using Microsoft.VisualStudio.TestTools.UnitTesting;` wierszem:

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

   Nowy test zostanie wyświetlony w **Eksploratorze testów** w węźle **nie uruchomiono testy** .

4. Aby uniknąć "ładunek zawiera co najmniej dwa pliki z tą samą ścieżką docelową", w **Eksplorator rozwiązań**rozwiń węzeł **Właściwości** w projekcie **Maths** , a następnie usuń plik *Default.rd.xml* .

::: moniker range="vs-2017"

6. W **Eksploratorze testów**wybierz opcję **Uruchom wszystkie**.

   Rozwiązanie zostanie skompilowane i testy są uruchamiane i przekazywane.

   ![BasicTest przeszedł do Eksploratora testów](../test/media/ute_cpp_testexplorer_basictest.png)

::: moniker-end

::: moniker range=">=vs-2019"

6. W **Eksploratorze testów**wybierz opcję **Uruchom wszystkie testy**.

   Rozwiązanie zostanie skompilowane i testy są uruchamiane i przekazywane.

   ![Test podstawowy zakończony w Eksploratorze testów](../test/media/vs-2019/test-explorer-uwp-app.png)

::: moniker-end

Zostały skonfigurowane projekty testów i aplikacji oraz sprawdzono, że można uruchomić testy, które wywołują funkcje w projekcie aplikacji. Teraz możesz zacząć pisać prawdziwe testy i kod.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a>Iteracyjnie rozszerza testy i przekazują je

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
   > Zalecamy, aby nie zmieniać testów, które zostały zakończone. Zamiast tego Dodaj nowy test.

2. Uruchom test **RangeTest** i sprawdź, czy ten błąd nie powiódł się.

   ![RangeTest kończy się niepowodzeniem](../test/media/ute_cpp_testexplorer_rangetest_fail.png)

   > [!TIP]
   > Natychmiast po napisaniu testu należy go uruchomić, aby sprawdzić, czy ten błąd nie powiódł się. Dzięki temu można uniknąć łatwego błędu podczas pisania testu, który nigdy nie powiedzie się.

3. Podnieś poziom testowanego kodu, tak aby nowe testy zostały przekazane. Zmień funkcję **SquareRoot** w *Rooter.cs* na:

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

4. W **Eksploratorze testów**wybierz opcję **Uruchom wszystkie**.

::: moniker-end

::: moniker range=">=vs-2019"

4. W **Eksploratorze testów**wybierz opcję **Uruchom wszystkie testy**.

::: moniker-end

   Wszystkie trzy testy są teraz przekazywane.

> [!TIP]
> Opracowuj kod przez dodanie testów pojedynczo. Upewnij się, że wszystkie testy są zakończone po każdej iteracji.

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
> Stabilny zestaw dobrych testów jednostkowych daje pewność, że podczas zmiany kodu nie wprowadzono usterek.

### <a name="eliminate-duplicated-code"></a>Eliminowanie duplikatu kodu

Metoda **RangeTest** określa mianownik zmiennej *tolerancji* , która jest przenoszona do <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> metody. Jeśli planujesz dodać dodatkowe testy, które używają tego samego obliczenia tolerancji, użycie zakodowanej wartości w wielu lokalizacjach sprawia, że kod jest trudniejszy do utrzymania.

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
> W przypadku dodania metody pomocnika do klasy testowej, która nie ma być wyświetlana w **Eksploratorze testów**, nie należy dodawać <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> atrybutu do metody.

## <a name="see-also"></a>Zobacz też

- [Przewodnik: Programowanie sterowane testami za pomocą Eksploratora testów](quick-start-test-driven-development-with-test-explorer.md)
