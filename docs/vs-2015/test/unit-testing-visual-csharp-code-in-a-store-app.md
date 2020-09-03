---
title: Testowanie jednostkowe kodu Visual C# w aplikacji ze sklepu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 23cb0d82-0451-464e-98ea-fa66e7010ead
caps.latest.revision: 21
author: alexhomer1
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 81876493d48407549237ed626fc6ec5d2175fcd7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659604"
---
# <a name="unit-testing-visual-c-code-in-a-store-app"></a>Testowanie jednostkowe kodu Visual C# w aplikacji ze sklepu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano jeden ze sposobów tworzenia testów jednostkowych dla klasy Visual C# w aplikacji ze sklepu Windows. Klasa root pokazuje niejasne odnoszące się do granicy calculus przez implementację funkcji, która oblicza oszacowanie wartości pierwiastek kwadratowy danej liczby. Aplikacja Maths może następnie używać tej funkcji do wyświetlania użytkownikowi ciekawych rzeczy, które można wykonać za pomocą obliczeń matematycznych.

 W tym temacie przedstawiono sposób korzystania z testów jednostkowych jako pierwszego kroku projektowania. W tym podejściu najpierw napiszesz metodę testową, która weryfikuje określone zachowanie w testowanym systemie, a następnie pisze kod, który przekazuje test. Wprowadzając zmiany w kolejności następującej procedury, można odwrócić tę strategię, aby najpierw napisać kod, który ma zostać przetestowany, a następnie napisać testy jednostkowe.

 W tym temacie jest również tworzone pojedyncze rozwiązanie programu Visual Studio i oddzielne projekty dla testów jednostkowych i biblioteki DLL, która ma zostać przetestowana. Możesz również uwzględnić testy jednostkowe bezpośrednio w projekcie DLL lub utworzyć oddzielne rozwiązania dla testów jednostkowych i biblioteki DLL.

> [!NOTE]
> Visual Studio Community, Enterprise. i Professional oferują dodatkowe funkcje do testowania jednostkowego.
>
> - Użyj platformy testów jednostkowych innych firm i open source, która utworzyła adapter dodatku dla programu Microsoft Test Explorer. Możesz również analizować i wyświetlać informacje o pokryciu kodu dla testów.
>   - Uruchom testy po każdej kompilacji.
>   - VS Enterprise również zawiera sztuczne firmy Microsoft, strukturę izolacji dla kodu zarządzanego, który ułatwia skoncentrowanie testów na własnym kodzie poprzez podstawianie kodu testowego dla systemu i funkcji innych firm.
>
>   Aby uzyskać więcej informacji, zobacz [Weryfikowanie kodu przy użyciu testów jednostkowych](https://msdn.microsoft.com/library/dd264975.aspx) w bibliotece MSDN.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> W tym temacie
 [Utwórz rozwiązanie i projekt testu jednostkowego](#BKMK_Create_the_solution_and_the_unit_test_project)

 [Sprawdź, czy testy są uruchamiane w Eksploratorze testów](#BKMK_Verify_that_the_tests_run_in_Test_Explorer)

 [Dodawanie klasy Rooter do projektu Maths](#BKMK_Add_the_Rooter_class_to_the_Maths_project)

 [Połącz projekt testowy z projektem aplikacji](#BKMK_Couple_the_test_project_to_the_app_project)

 [Iteracyjnie rozszerza testy i przekazują je](#BKMK_Iteratively_augment_the_tests_and_make_them_pass)

 [Debuguj test zakończony niepowodzeniem](#BKMK_Debug_a_failing_test)

 [Refaktoryzacja kodu](#BKMK_Refactor_the_code_)

## <a name="create-the-solution-and-the-unit-test-project"></a><a name="BKMK_Create_the_solution_and_the_unit_test_project"></a> Utwórz rozwiązanie i projekt testu jednostkowego

1. W menu **plik** wybierz pozycję **Nowy**, a następnie wybierz pozycję **Nowy projekt**.

2. W oknie dialogowym **Nowy projekt** rozwiń węzeł **zainstalowane**, rozwiń pozycję **Visual C#** , a następnie wybierz pozycję **Sklep Windows**. Następnie wybierz **pustą aplikację** z listy szablonów projektu.

3. Nazwij projekt `Maths` i upewnij się, że wybrano **Utwórz katalog dla rozwiązania** .

4. W Eksplorator rozwiązań wybierz nazwę rozwiązania, wybierz pozycję **Dodaj** z menu skrótów, a następnie wybierz pozycję **Nowy projekt**.

5. W oknie dialogowym **Nowy projekt** rozwiń węzeł **zainstalowane**, rozwiń pozycję **Visual C#** , a następnie wybierz pozycję **Sklep Windows** . Następnie wybierz pozycję **Biblioteka testów jednostkowych (aplikacje ze sklepu Windows)** z listy szablonów projektu.

     ![Tworzenie projektu testu jednostkowego](../test/media/ute-cs-windows-createunittestproject.png "UTE_Cs_windows_CreateUnitTestProject")

6. Otwórz UnitTest1.cs w edytorze programu Visual Studio.

    ```csharp

    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using Microsoft.VisualStudio.TestPlatform.UnitTestFramework;
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

     Należy pamiętać, że:

    1. Każdy test jest definiowany przy użyciu `[TestMethod]` . Metoda testowa musi zwracać typ void i nie może mieć żadnych parametrów.

    2. Metody testowe muszą znajdować się w klasie z `[TestClass]` atrybutem.

         Gdy testy są uruchamiane, tworzone jest wystąpienie każdej klasy testowej. Metody testowe są wywoływane w nieokreślonej kolejności.

    3. Można zdefiniować metody specjalne, które są wywoływane przed i po każdym module, klasie lub metodzie. Aby uzyskać więcej informacji, zobacz [Używanie elementów członkowskich Microsoft. VisualStudio. TestTools. UnitTesting w testach jednostkowych](../test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md) w bibliotece MSDN.

## <a name="verify-that-the-tests-run-in-test-explorer"></a><a name="BKMK_Verify_that_the_tests_run_in_Test_Explorer"></a> Sprawdź, czy testy są uruchamiane w Eksploratorze testów

1. Wstaw kod testu w `TestMethod1` pliku **UnitTest1.cs** :

    ```csharp

    [TestMethod]
    public void TestMethod1()
    {
        Assert.AreEqual(0, 0);
    }

    ```

     Należy zauważyć, że `Assert` Klasa zawiera kilka metod statycznych, których można użyć do sprawdzenia wyników w metodach testowych.

2. W menu **test** wybierz polecenie **Uruchom** , a następnie wybierz polecenie **Uruchom wszystkie**.

     Projekt testowy zostanie skompilowany i uruchomiony. Zostanie wyświetlone okno Eksplorator testów, a test zostanie wyświetlony na liście **zakończonych testów**. Okienko Podsumowanie u dołu okna zawiera dodatkowe szczegółowe informacje o wybranym teście.

     ![Eksplorator testów](../test/media/ute-cpp-testexplorer-testmethod1.png "UTE_Cpp_TestExplorer_TestMethod1")

## <a name="add-the-rooter-class-to-the-maths-project"></a><a name="BKMK_Add_the_Rooter_class_to_the_Maths_project"></a> Dodawanie klasy Rooter do projektu Maths

1. W Eksplorator rozwiązań wybierz nazwę projektu **Maths** . Z menu skrótów wybierz polecenie **Dodaj**, a następnie **klasy**.

2. Nazwij plik klasy `Rooter.cs`

3. Dodaj następujący kod do pliku **Rooter.Cser** klasy root:

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

     `Rooter`Klasa deklaruje konstruktora i `SqareRoot` metodę szacowania.

4. `SqareRoot`Metoda jest tylko minimalną implementacją, wystarczy do przetestowania podstawowej struktury instalacji testowej.

## <a name="couple-the-test-project-to-the-app-project"></a><a name="BKMK_Couple_the_test_project_to_the_app_project"></a> Połącz projekt testowy z projektem aplikacji

1. Dodaj odwołanie do aplikacji Maths do projektu RooterTests.

   1. W Eksplorator rozwiązań wybierz projekt **RooterTests** , a następnie wybierz pozycję **Dodaj odwołanie...** w menu skrótów.

   2. W oknie dialogowym **Dodawanie odwołania — RooterTests** rozwiń węzeł **rozwiązanie** i wybierz pozycję **projekty**. Następnie wybierz element **Maths** .

        ![Dodaj odwołanie do projektu Maths](../test/media/ute-cs-windows-addreference.png "UTE_Cs_windows_AddReference")

2. Dodaj instrukcję using do pliku UnitTest1.cs:

   1. Otwórz **UnitTest1.cs**.

   2. Dodaj następujący kod pod `using Microsoft.VisualStudio.TestPlatform.UnitTestFramework;` wierszem:

       ```csharp
       using Maths;
       ```

3. Dodaj test, który używa funkcji Rooter. Dodaj następujący kod do **UnitTest1. cpp**:

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

    Nowy test zostanie wyświetlony w Eksploratorze testów w węźle **nie uruchomiono testy** .

5. W Eksploratorze testów wybierz opcję **Uruchom wszystkie**.

    ![Test podstawowy zakończony zakończono](../test/media/ute-cpp-testexplorer-basictest.png "UTE_Cpp_TestExplorer_BasicTest")

   Został skonfigurowany test i projekty kodu i zweryfikowane, że można uruchomić testy, które uruchamiają funkcje w projekcie kodu. Teraz możesz zacząć pisać prawdziwe testy i kod.

## <a name="iteratively-augment-the-tests-and-make-them-pass"></a><a name="BKMK_Iteratively_augment_the_tests_and_make_them_pass"></a> Iteracyjnie rozszerza testy i przekazują je

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
            double tolerance = ToleranceHelper(expected);
            Assert.AreEqual(expected, actual, tolerance);
        }
    }

    ```

    > [!TIP]
    > Zalecamy, aby nie zmieniać testów, które zostały zakończone. Zamiast tego Dodaj nowy test, zaktualizuj kod tak, aby test zakończył się powodzeniem, a następnie Dodaj inny test i tak dalej.
    >
    >  Gdy użytkownicy zmienią swoje wymagania, należy wyłączyć testy, które nie są już poprawne. Napisz nowe testy i Przekształć je w jeden raz w ten sam przyrostowy sposób.

2. W Eksploratorze testów wybierz opcję **Uruchom wszystkie**.

3. Test zakończy się niepowodzeniem.

     ![RangeTest kończy się niepowodzeniem](../test/media/ute-cpp-testexplorer-rangetest-fail.png "UTE_Cpp_TestExplorer_RangeTest_Fail")

    > [!TIP]
    > Natychmiast po jego zapisaniu Sprawdź, czy każdy test nie powiedzie się. Dzięki temu można uniknąć łatwego błędu podczas pisania testu, który nigdy nie powiedzie się.

4. Podnieś poziom testowanego kodu, tak aby nowe testy zostały przekazane. Zmień `SqareRoot` funkcję w **Rooter.cs** na:

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

5. Skompiluj rozwiązanie, a następnie w Eksploratorze testów wybierz opcję **Uruchom wszystkie**.

     Wszystkie trzy testy są teraz przekazywane.

> [!TIP]
> Opracowuj kod przez dodanie testów pojedynczo. Upewnij się, że wszystkie testy są zakończone po każdej iteracji.

## <a name="debug-a-failing-test"></a><a name="BKMK_Debug_a_failing_test"></a> Debuguj test zakończony niepowodzeniem

1. Dodaj inny test do **UnitTest1.cs**:

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

2. W Eksploratorze testów wybierz opcję **Uruchom wszystkie**.

    Test zakończy się niepowodzeniem. Wybierz nazwę testu w Eksploratorze testów. Niepowodzenie zostało wyróżnione. Komunikat o błędzie jest widoczny w okienku szczegółów w Eksploratorze testów.

    ![NegativeRangeTests nie powiodło się](../test/media/ute-cpp-testexplorer-negativerangetest-fail.png "UTE_Cpp_TestExplorer_NegativeRangeTest_Fail")

3. Aby zobaczyć dlaczego test nie powiedzie się, przechodzenie przez funkcję:

   1. Ustaw punkt przerwania na początku `SquareRoot` funkcji.

   2. W menu skrótów testu zakończonego niepowodzeniem wybierz **Debuguj wybrane testy**.

        Gdy przebieg zostanie zatrzymany w punkcie przerwania, przejdź do kodu.

   3. Dodaj kod do metody Rooter, aby przechwycić wyjątek:

       ```csharp
       public double SquareRoot(double x)
       {
           if (x < 0.0)
           {
               throw new ArgumentOutOfRangeException();
       }

       ```

   1. W Eksploratorze testów wybierz opcję **Uruchom wszystkie** , aby przetestować poprawioną metodę i upewnić się, że regresja nie została wprowadzona.

   Wszystkie testy są teraz zakończone pomyślnie.

   ![Wszystkie testy zakończone powodzeniem](../test/media/ute-ult-alltestspass.png "UTE_ULT_AllTestsPass")

## <a name="refactor-the-code"></a><a name="BKMK_Refactor_the_code_"></a> Refaktoryzacja kodu
 **Uprość Obliczanie centralne w funkcji SquareRoot.**

1. Zmiana implementacji wyniku

    ```csharp
    // old code
    //result = result - (result*result - v)/(2*result);
    // new code
    result = (result + v/result) / 2.0;

    ```

2. Wybierz opcję **Uruchom wszystkie** , aby przetestować metodę refaktoryzacji i upewnić się, że regresja nie została wprowadzona.

> [!TIP]
> Stabilny zestaw dobrych testów jednostkowych daje pewność, że podczas zmiany kodu nie wprowadzono usterek.

 **Refaktoryzacja kodu testowego w celu wyeliminowania zduplikowanego kodu.**

 Należy zauważyć, że `RangeTest` Metoda określa mianownik zmiennej tolerancji używanej w `Assert` metodzie. Jeśli planujesz dodać dodatkowe testy, które używają tego samego obliczenia tolerancji, użycie zakodowanej wartości w wielu lokalizacjach może prowadzić do błędów.

1. Dodaj prywatną metodę do klasy Unit1Test, aby obliczyć wartość tolerancji, a następnie Wywołaj tę metodę zamiast tego.

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

2. Wybierz opcję **Uruchom wszystkie** , aby przetestować metodę refaktoryzacji i upewnić się, że błąd nie został wprowadzony.

> [!NOTE]
> Aby dodać metodę pomocnika do klasy testowej, nie należy dodawać `[TestMethod]` atrybutu do metody. Eksplorator testów nie rejestruje metody do uruchomienia.
