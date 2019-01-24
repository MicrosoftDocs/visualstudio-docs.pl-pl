---
title: Testowanie jednostek kodu języka Visual C# w Store app | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 23cb0d82-0451-464e-98ea-fa66e7010ead
caps.latest.revision: 21
author: alexhomer1
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6128ca2638f98600c9bfb17e8388cf0a663040a8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54766266"
---
# <a name="unit-testing-visual-c-code-in-a-store-app"></a>Testowanie jednostek kodu języka Visual C# w Store app
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano jeden ze sposobów tworzenia testów jednostkowych dla klasy języka Visual C# w aplikacji Windows Store. Klasa Rooter pokazuje niejasne chwile teorii limit z calculus poprzez implementację funkcji, który oblicza oszacowanie pierwiastek kwadratowy z podanej liczbie. Aplikacja matematycznych następnie może używać tej funkcji do pokazania użytkownika fun rzeczy, które można wykonać za pomocą matematyczne.  
  
 W tym temacie przedstawiono sposób użycia testowania jako pierwszy krok w rozwoju jednostek. W tym podejściu najpierw napisać metodę testową, która sprawdza określone zachowanie w systemie, które testujesz, a następnie napisać kod, który przejdzie test. Wycofanie tej strategii, wprowadzając zmiany kolejności poniższych procedur, w pierwszej operacji zapisu kod, który chcesz przetestować, a następnie napisz testy jednostkowe.  
  
 W tym temacie tworzy również jedno rozwiązanie Visual Studio i oddzielnych projektów dla testów jednostkowych i biblioteki DLL, która ma zostać przetestowana. Możesz również uwzględnić testy jednostkowe bezpośrednio w projekcie biblioteki DLL lub można utworzyć oddzielne rozwiązania dla testów jednostkowych i biblioteki DLL.  
  
> [!NOTE]
>  Visual Studio Community, Enterprise. i Professional zapewniają dodatkowe funkcje testów jednostkowych.  
> 
> - Użyj dowolnego środowiska testów jednostkowych innych firm i open source, który utworzył karty dodatku dla programu Microsoft Test Explorer. Można również analizować i wyświetlić informacje o pokryciu kodu dla testów.  
>   -   Uruchom testy po każdej kompilacji.  
>   -   Programu Visual Studio Enterprise zawiera także Microsoft Fakes framework izolacji dla kodu zarządzanego, który ułatwia skoncentrowanie się testy na własny kod, zastępując kod testu systemu i innych firm funkcjonalność.  
> 
>   Aby uzyskać więcej informacji, zobacz [weryfikowanie kodu przy użyciu testów jednostkowych](http://msdn.microsoft.com/library/dd264975.aspx) w bibliotece MSDN.  
  
##  <a name="BKMK_In_this_topic"></a> W tym temacie  
 [Tworzenie rozwiązania i projektu testu jednostkowego](#BKMK_Create_the_solution_and_the_unit_test_project)  
  
 [Sprawdź, czy testy zostaną wykonane w Eksploratorze testów](#BKMK_Verify_that_the_tests_run_in_Test_Explorer)  
  
 [Dodaj klasę Rooter do projektu matematycznych](#BKMK_Add_the_Rooter_class_to_the_Maths_project)  
  
 [Kilka projekt testowy do projektu aplikacji](#BKMK_Couple_the_test_project_to_the_app_project)  
  
 [Iteracyjne Udoskonal testy i nadawać im przekazać](#BKMK_Iteratively_augment_the_tests_and_make_them_pass)  
  
 [Debuguj test niepowodzeniem](#BKMK_Debug_a_failing_test)  
  
 [Refaktoryzacja kodu](#BKMK_Refactor_the_code_)  
  
##  <a name="BKMK_Create_the_solution_and_the_unit_test_project"></a> Tworzenie rozwiązania i projektu testu jednostkowego  
  
1.  Na **pliku** menu, wybierz **New**, a następnie wybierz **nowy projekt**.  
  
2.  W **nowy projekt** okna dialogowego rozwiń **zainstalowane**, następnie rozwiń **Visual C#** i wybierz polecenie **Windows Store**. Następnie wybierz **pusta aplikacja** z listy szablonów projektu.  
  
3.  Nadaj projektowi nazwę `Maths` i upewnij się, że **Utwórz katalog rozwiązania** jest zaznaczone.  
  
4.  W Eksploratorze rozwiązań, wybierz nazwę rozwiązania, wybierz pozycję **Dodaj** z menu skrótów, a następnie wybierz **nowy projekt**.  
  
5.  W **nowy projekt** okna dialogowego rozwiń **zainstalowane**, następnie rozwiń **Visual C#** i wybierz polecenie **Windows Store** . Następnie wybierz **Biblioteka testów jednostkowych (Windows Store apps)** z listy szablonów projektu.  
  
     ![Tworzenie projektu testu jednostkowego](../test/media/ute-cs-windows-createunittestproject.png "UTE_Cs_windows_CreateUnitTestProject")  
  
6.  Otwórz UnitTest1.cs w edytorze programu Visual Studio.  
  
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
  
     Należy pamiętać o następujących kwestiach:  
  
    1.  Każdy test jest definiowana za pomocą `[TestMethod]`. Metoda testowa musi zwracać typ void i nie może mieć żadnych parametrów.  
  
    2.  Metody testu muszą być w klasie z atrybutem `[TestClass]` atrybutu.  
  
         Gdy testy są uruchamiane, tworzone jest wystąpienie każdej klasy testu. Metody testowe są wywoływane w nieokreślonej kolejności.  
  
    3.  Można zdefiniować specjalne metody, które są wywoływane przed i po każdym modułu, klasy lub metody. Aby uzyskać więcej informacji, zobacz [korzystanie ze składowych Microsoft.VisualStudio.TestTools.UnitTesting w testach jednostkowych](../test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md) w bibliotece MSDN.  
  
##  <a name="BKMK_Verify_that_the_tests_run_in_Test_Explorer"></a> Sprawdź, czy testy zostaną wykonane w Eksploratorze testów  
  
1.  Wstaw kod testu w `TestMethod1` z **UnitTest1.cs** pliku:  
  
    ```csharp  
  
    [TestMethod]  
    public void TestMethod1()  
    {  
        Assert.AreEqual(0, 0);  
    }  
  
    ```  
  
     Należy zauważyć, że `Assert` klasa udostępnia kilka metod statycznych, których można sprawdzić wyniki za pomocą metod testowych.  
  
2.  Na **testu** menu, wybierz **Uruchom** , a następnie wybierz **Uruchom wszystkie**.  
  
     Projekt testowy skompilowane i uruchomione. Zostanie wyświetlone okno Eksploratora testów i test znajduje się w obszarze **testy zakończone powodzeniem**. Okienko podsumowania w dolnej części okna udostępnia dodatkowe szczegóły dotyczące wybranego testu.  
  
     ![Test Explorer](../test/media/ute-cpp-testexplorer-testmethod1.png "UTE_Cpp_TestExplorer_TestMethod1")  
  
##  <a name="BKMK_Add_the_Rooter_class_to_the_Maths_project"></a> Dodaj klasę Rooter do projektu matematycznych  
  
1.  W Eksploratorze rozwiązań wybierz **matematycznych** nazwy projektu. Z menu skrótów wybierz polecenie **Dodaj**, a następnie **klasy**.  
  
2.  Nazwa pliku klasy `Rooter.cs`  
  
3.  Dodaj następujący kod do klasy Rooter **Rooter.cs** pliku:  
  
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
  
     `Rooter` Klasa deklaruje Konstruktor i `SqareRoot` metoda narzędzie do szacowania.  
  
4.  `SqareRoot` Metodą jest tylko minimalny implementacji wystarczający do testowania podstawowej struktury testowania instalacji.  
  
##  <a name="BKMK_Couple_the_test_project_to_the_app_project"></a> Kilka projekt testowy do projektu aplikacji  
  
1. Dodaj odwołanie do niej matematycznych w projekcie RooterTests.  
  
   1.  W Eksploratorze rozwiązań wybierz **RooterTests** projektu, a następnie wybierz **Dodaj odwołanie...**  menu skrótów.  
  
   2.  Na **Dodaj odwołanie - RooterTests** okna dialogowego rozwiń **rozwiązania** i wybierz polecenie **projektów**. Następnie wybierz pozycję **matematycznych** elementu.  
  
        ![Dodaj odwołanie do projektu matematycznych](../test/media/ute-cs-windows-addreference.png "UTE_Cs_windows_AddReference")  
  
2. Dodaj instrukcję using instrukcję, aby plik UnitTest1.cs:  
  
   1.  Otwórz **UnitTest1.cs**.  
  
   2.  Dodaj następujący kod poniżej `using Microsoft.VisualStudio.TestPlatform.UnitTestFramework;` wiersza:  
  
       ```csharp  
       using Maths;  
       ```  
  
3. Dodaj test, który używa funkcji Rooter. Dodaj następujący kod do **UnitTest1.cpp**:  
  
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
  
    Nowy test jest wyświetlany w Eksploratorze testów w **testy nieuruchamiane** węzła.  
  
5. W Eksploratorze testów wybierz **Uruchom wszystkie**.  
  
    ![Podstawowy Test zakończony sukcesem](../test/media/ute-cpp-testexplorer-basictest.png "UTE_Cpp_TestExplorer_BasicTest")  
  
   Mają ustawienie testu i projekty kodu, a następnie zweryfikować, że można uruchomić testy, które uruchamiania funkcji w projekcie kodu. Teraz możesz rozpocząć pisanie rzeczywistych testów i kodu.  
  
##  <a name="BKMK_Iteratively_augment_the_tests_and_make_them_pass"></a> Iteracyjne Udoskonal testy i nadawać im przekazać  
  
1.  Dodaj nowy test:  
  
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
    >  Firma Microsoft zaleca, nie należy zmieniać testy, które zostały przekazane. Zamiast tego Dodaj nowy test, zaktualizować kod, tak aby test zakończy się pomyślnie, a następnie dodaj innego testu, i tak dalej.  
    >   
    >  Użytkownicy zmiany ich wymagań, wyłącz testy, które nie są już prawidłowe. Zapisz nowe testy i ich działania pojedynczo, w taki sam sposób przyrostowego.  
  
2.  W Eksploratorze testów wybierz **Uruchom wszystkie**.  
  
3.  Test nie powiedzie się.  
  
     ![Kończy się niepowodzeniem RangeTest](../test/media/ute-cpp-testexplorer-rangetest-fail.png "UTE_Cpp_TestExplorer_RangeTest_Fail")  
  
    > [!TIP]
    >  Po napisaniu go Sprawdź, czy każdy test zakończy się niepowodzeniem. Dzięki temu można uniknąć łatwe Błąd zapisywania testu, który nigdy nie zakończy się niepowodzeniem.  
  
4.  Tak, aby nowy test zakończy się pomyślnie, należy zwiększyć testowany kod. Zmiana `SqareRoot` działa w programach **Rooter.cs** do tego:  
  
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
  
5.  Skompiluj rozwiązanie, a następnie w Eksploratorze testów wybierz **Uruchom wszystkie**.  
  
     Teraz kod przechodzi wszystkie trzy testy.  
  
> [!TIP]
>  Tworzenie kodu, dodając jeden testów w danym momencie. Upewnij się, że po każdej iteracji kod przechodzi wszystkie testy.  
  
##  <a name="BKMK_Debug_a_failing_test"></a> Debuguj test niepowodzeniem  
  
1. Dodaj kolejny test do **UnitTest1.cs**:  
  
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
  
2. W Eksploratorze testów wybierz **Uruchom wszystkie**.  
  
    Test nie powiedzie się. Wybierz nazwę testu w Eksploratorze testów. Potwierdzenie nie powiodło się, jest wyróżniona. Komunikat o błędzie jest widoczne w okienku szczegółów w Eksploratorze testów.  
  
    ![Nie powiodło się NegativeRangeTests](../test/media/ute-cpp-testexplorer-negativerangetest-fail.png "UTE_Cpp_TestExplorer_NegativeRangeTest_Fail")  
  
3. Aby zobaczyć, dlaczego test zakończy się niepowodzeniem, krok przy użyciu funkcji:  
  
   1.  Ustaw punkt przerwania na początku `SquareRoot` funkcji.  
  
   2.  W menu skrótów testów zakończonych niepowodzeniem, wybierz **Debuguj wybrane testy**.  
  
        Po zatrzymaniu w punkcie przerwania Uruchom przejść przez kod.  
  
   3.  Dodaj kod do metody Rooter w celu wyłapania wyjątku:  
  
       ```csharp  
       public double SquareRoot(double x)  
       {  
           if (x < 0.0)  
           {  
               throw new ArgumentOutOfRangeException();  
       }  
  
       ```  
  
   1.  W Eksploratorze testów wybierz **Uruchom wszystkie** poprawiony metoda testowa, i upewnij się, że nie zostały wprowadzone regresji.  
  
   Teraz kod przechodzi wszystkie testy.  
  
   ![Kod przechodzi wszystkie testy](../test/media/ute-ult-alltestspass.png "UTE_ULT_AllTestsPass")  
  
##  <a name="BKMK_Refactor_the_code_"></a> Refaktoryzacja kodu  
 **Uprość centralnej obliczeń w funkcji SquareRoot.**  
  
1.  Zmień implementację wynik  
  
    ```csharp  
    // old code  
    //result = result - (result*result - v)/(2*result);  
    // new code  
    result = (result + v/result) / 2.0;  
  
    ```  
  
2.  Wybierz **Uruchom wszystkie** wycofanej metoda testowa, i upewnij się, że nie zostały wprowadzone regresji.  
  
> [!TIP]
>  Stabilne zestawy testów jednostkowych dobre daje pewność, że użytkownik nie wprowadzają błędów po zmianie kodu.  
  
 **Refaktoryzuj kod testu, aby wyeliminować zduplikowany kodem.**  
  
 Należy pamiętać, że `RangeTest` metoda twardych kody mianownik zmiennej na uszkodzenia, która jest używana w `Assert` metody. Jeśli planujesz dodać dodatkowe testy, które używają tych samych obliczeń na uszkodzenia użytkowania ustaloną wartość w wielu miejscach może prowadzić do błędów.  
  
1.  Dodaj prywatną metodę do klasy Unit1Test, aby obliczyć wartość tolerancji, a następnie zamiast tego wywołać tej metody.  
  
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
  
2.  Wybierz **Uruchom wszystkie** wycofanej metoda testowa, i upewnij się, że nie zostały wprowadzone błąd.  
  
> [!NOTE]
>  Aby dodać metodę pomocnika do klasy testowej, nie należy dodawać `[TestMethod]` atrybutu do metody. Eksplorator testów nie rejestruje metody do uruchomienia.
