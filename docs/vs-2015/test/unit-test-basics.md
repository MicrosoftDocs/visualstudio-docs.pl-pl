---
title: Podstawowe informacje o teście jednostkowym | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateUnitTest
ms.assetid: a80ba9cd-4575-483c-b957-af7ed8dc7e20
caps.latest.revision: 29
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0657fdd846c201b4f9bff4910bdd9fc271c399c9
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543783"
---
# <a name="unit-test-basics"></a>Podstawowe informacje o teście jednostkowym
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sprawdź, czy kod działa zgodnie z oczekiwaniami, tworząc i uruchamiając testy jednostkowe. Jest to tzw. Testowanie jednostkowe, ponieważ należy podzielić funkcjonalność programu na dyskretne zachowania weryfikowalne, które można testować jako pojedyncze *jednostki*. Program Visual Studio Test Explorer oferuje elastyczny i wydajny sposób uruchamiania testów jednostkowych i wyświetlania ich wyników w programie Visual Studio. Program Visual Studio instaluje struktury testów jednostkowych firmy Microsoft dla kodu zarządzanego i natywnego. Użyj *struktury testów jednostkowych* , aby utworzyć testy jednostkowe, uruchomić je i zgłosić wyniki tych testów. Ponownie uruchom testy jednostkowe, gdy wprowadzisz zmiany w celu przetestowania, że kod nadal działa poprawnie. Korzystając z Visual Studio Enterprise, można uruchomić testy automatycznie po każdej kompilacji.

 Testy jednostkowe mają największy wpływ na jakość kodu, gdy jest to integralna część przepływu pracy tworzenia oprogramowania. Gdy tylko napiszesz funkcję lub inny blok kodu aplikacji, należy utworzyć testy jednostkowe, które weryfikują zachowanie kodu w odpowiedzi na standardowe, graniczne i niepoprawne przypadki danych wejściowych oraz sprawdzają wszelkie jawne lub niejawne założenia wykonane przez kod. W przypadku *projektowania sterowanego testem*należy utworzyć testy jednostkowe przed zapisaniem kodu, więc należy użyć testów jednostkowych jako dokumentacji projektu i specyfikacji funkcjonalnych.

 Możesz szybko generować projekty testowe i metody testowe z kodu lub ręcznie tworzyć testy w miarę potrzeb. W przypadku korzystania z IntelliTest do eksplorowania kodu platformy .NET można generować dane testowe i zestaw testów jednostkowych. Dla każdej instrukcji w kodzie są generowane dane wejściowe testu, które spowodują wykonanie tej instrukcji. Dowiedz się, jak [generować testy jednostkowe dla kodu](https://msdn.microsoft.com/library/dn823749.aspx).

 Eksplorator testów może również uruchamiać platformy testów jednostkowych innych firm i open source, które mają zaimplementowane interfejsy dodatków w Eksploratorze testów. Wiele z tych platform można dodać za pomocą Menedżera rozszerzeń programu Visual Studio i galerii programu Visual Studio. Zobacz [Instalowanie platform testów jednostkowych](../test/install-third-party-unit-test-frameworks.md) innych firm

- [Przewodniki Szybki start](#BKMK_Quick_starts)

- [Przykład rozwiązania z banku](#BKMK_The_MyBank_Solution_example)

- [Tworzenie projektów testów jednostkowych i metod testowych](#BKMK_Creating_the_unit_test_projects)

- [Napisz testy](#BKMK_Writing_your_tests)

- [Uruchom testy w Eksploratorze testów](#BKMK_Running_tests_in_Test_Explorer)

- [Uruchom i Wyświetl testy](#BKMK_Running_and_viewing_tests_from_the_Test_Explorer_toolbar)

## <a name="unit-testing-overview"></a><a name="BKMK_Unit_testing_overview"></a>Przegląd testów jednostkowych

### <a name="quick-starts"></a><a name="BKMK_Quick_starts"></a>Szybki Start
 Aby zapoznać się z wprowadzeniem do testów jednostkowych, które są bezpośrednio wprowadzane do kodu, zobacz jeden z następujących tematów:

- [Przewodnik: tworzenie i uruchamianie testów jednostkowych zarządzanego kodu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)

- [Szybki start: programowanie sterowane testami za pomocą narzędzia Eksplorator testów](../test/quick-start-test-driven-development-with-test-explorer.md)

- [Testowanie jednostkowe kodu natywnego za pomocą Eksploratora testów](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c)

## <a name="the-mybank-solution-example"></a><a name="BKMK_The_MyBank_Solution_example"></a>Przykład rozwiązania z banku
 W tym temacie wykorzystujemy programowanie fikcyjnej aplikacji o nazwie `MyBank` jako przykład. Kod nie jest potrzebny do wykonania wyjaśnień w tym temacie. Metody testowe są zapisywane w języku C# i prezentowane przy użyciu struktury testów jednostkowych firmy Microsoft dla kodu zarządzanego, jednak te koncepcje można łatwo przenieść do innych języków i struktur.

 ![Rozwiązanie z banku](../test/media/ute-mybanksolution.png "UTE_MyBankSolution")

 Pierwsza próba zaprojektowania `MyBank` aplikacji obejmuje składnik konta, który reprezentuje pojedyncze konto i jego transakcje z bankiem, a składnik bazy danych, który reprezentuje funkcje do agregowania poszczególnych kont i zarządzania nimi.

 Tworzymy `MyBank` rozwiązanie, które zawiera dwa projekty:

- `Accounts`

- `BankDb`

  Nasza pierwsza próba projektowania `Accounts` projektu zawiera klasę, aby przechowywać podstawowe informacje o koncie, interfejs, który określa typowe funkcje dowolnego typu konta, takie jak kaucja i wycofanie zasobów z konta, oraz Klasa pochodna interfejsu, który reprezentuje konto sprawdzania. Rozpoczynamy projekty kont, tworząc następujące pliki źródłowe:

- `AccountInfo.cs`Definiuje podstawowe informacje o koncie.

- `IAccount.cs`Definiuje standardowy `IAccount` interfejs dla konta, w tym metody do depozytu i wycofywania zasobów z konta oraz do pobierania salda konta.

- `CheckingAccount.cs`zawiera `CheckingAccount` klasę, która implementuje `IAccounts` interfejs do sprawdzania konta.

  Wiemy, że jednym z nich jest wycofanie z konta kontroli, aby upewnić się, że wycofana kwota jest mniejsza niż saldo konta. Dlatego zastąpimy `IAccount.Withdaw` metodę `CheckingAccount` z użyciem metody, która sprawdza, czy jest to warunek. Metoda może wyglądać następująco:

```csharp

public void Withdraw(double amount)
{
    if(m_balance >= amount)
    {
        m_balance -= amount;
    }
    else
    {
        throw new ArgumentException(amount, "Withdrawal exceeds balance!")
    }
}

```

 Teraz, gdy mamy jakiś kod, czas na przetestowanie.

## <a name="create-unit-test-projects-and-test-methods"></a><a name="BKMK_Creating_the_unit_test_projects"></a>Tworzenie projektów testów jednostkowych i metod testowych
 Często jest szybsze generowanie projektu testów jednostkowych i testów jednostkowych w kodzie. Możesz też utworzyć projekt testu jednostkowego i testy ręcznie, w zależności od wymagań.

 **Generuj projekty testów jednostkowych i testy jednostkowe**

1. W oknie Edytor kodu kliknij prawym przyciskiem myszy i wybierz polecenie **Utwórz testy jednostkowe** z menu kontekstowego.

    ![W oknie Edytor Wyświetl menu kontekstowe.](../test/media/createunittestsrightclick.png "CreateUnitTestsRightClick")

2. Kliknij przycisk OK, aby zaakceptować wartości domyślne, aby utworzyć testy jednostkowe, lub Zmień wartości używane do utworzenia i nazwy projektu testów jednostkowych i testów jednostkowych. Można wybrać kod, który jest domyślnie dodawany do metod testów jednostkowych.

    ![Prawy&#45;kliknij w edytorze i wybierz pozycję Utwórz testy jednostkowe](../test/media/createunittestsdialog.png "CreateUnitTestsDialog")

3. Procedury pośredniczące testów jednostkowych są tworzone w nowym projekcie testów jednostkowych dla wszystkich metod w klasie.

    ![Testy jednostkowe są tworzone](../test/media/createunittestsstubs.png "CreateUnitTestsStubs")

4. Teraz przechodźmy, aby dowiedzieć się, jak [dodać kod do metod testów jednostkowych](#BKMK_Writing_your_tests) , aby sprawdzić, czy test jednostkowy jest znaczący, i wszelkie dodatkowe testy jednostkowe, które można dodać w celu dokładnego przetestowania kodu.

   **Utwórz ręcznie projekt testu jednostkowego i testy jednostkowe**

   Projekt testu jednostkowego zazwyczaj odzwierciedla strukturę pojedynczego projektu kodu. W przykładzie z banku dodaje się dwa projekty testów jednostkowych o nazwie `AccountsTests` i `BankDbTests` do `MyBanks` rozwiązania. Nazwy projektów testowych są dowolne, ale zaleca się zastosowanie standardowej konwencji nazewnictwa.

   **Aby dodać projekt testu jednostkowego do rozwiązania:**

5. W menu **plik** wybierz polecenie **Nowy** , a następnie wybierz **projekt** (klawiatura Ctrl + Shift + N).

6. W oknie dialogowym Nowy projekt rozwiń węzeł **zainstalowany** , wybierz język, który ma być używany dla projektu testowego, a następnie wybierz polecenie **Testuj**.

7. Aby użyć jednej z platform testów jednostkowych firmy Microsoft, wybierz opcję **projekt testu jednostkowego** z listy szablonów projektu. W przeciwnym razie wybierz szablon projektu dla struktury testów jednostkowych, który ma być używany. Aby przetestować `Accounts` projekt naszego przykładu, należy nazwać projekt `AccountsTests` .

   > [!WARNING]
   > Nie wszystkie struktury testów jednostkowych innych firm i typu open source zawierają szablon projektu programu Visual Studio. Zapoznaj się z dokumentem struktury, aby uzyskać informacje na temat tworzenia projektu.

8. W projekcie testów jednostkowych Dodaj odwołanie do badanego projektu kodu, w naszym przykładzie do projektu accounts.

    Aby utworzyć odwołanie do projektu kodu:

   1. Wybierz projekt w Eksplorator rozwiązań.

   2. W menu **projekt** wybierz polecenie **Dodaj odwołanie**.

   3. W oknie dialogowym Menedżer odwołań Otwórz węzeł **rozwiązania** i wybierz pozycję **projekty**. Wybierz nazwę projektu kodu i Zamknij okno dialogowe.

   Każdy projekt testu jednostkowego zawiera klasy, które są duplikatami nazw klas w projekcie kodu. W naszym przykładzie `AccountsTests` projekt będzie zawierał następujące klasy:

- `AccountInfoTests`Klasa zawiera metody testów jednostkowych dla `AccountInfo` klasy w `BankAccount` projekcie

- `CheckingAccountTests`Klasa zawiera metody testów jednostkowych `CheckingAccount` klasy.

## <a name="write-your-tests"></a><a name="BKMK_Writing_your_tests"></a>Napisz testy
 Używana struktura testów jednostkowych i Visual Studio IntelliSense przeprowadzi Cię przez proces pisania kodu dla testów jednostkowych w projekcie kodu. Aby uruchomić program w Eksploratorze testów, większość platform wymaga dodania określonych atrybutów do identyfikacji metod testów jednostkowych. Struktury zapewniają również sposób — zwykle za pomocą instrukcji Assert lub atrybutów metod — w celu wskazania, czy metoda testowa została pomyślnie zakończyła się powodzeniem, czy nie. Inne atrybuty identyfikują opcjonalne metody instalacji, które są inicjowane podczas inicjalizacji klasy, oraz przed każdą metodą testową i metodami usuwania, które są uruchamiane po każdej metodzie testowej i przed zniszczeniem klasy.

 Wzorzec AAA (porządkowanie, działanie, potwierdzenie) jest wspólnym sposobem pisania testów jednostkowych dla testowanej metody.

- Sekcja **Rozmieoć** metody testów jednostkowych inicjuje obiekty i ustawia wartość danych, które są przesyłane do testowanej metody.

- Sekcja **Act** wywołuje badaną metodę przy użyciu uporządkowanych parametrów.

- Sekcja **Assert** sprawdza, czy akcja testowanej metody zachowuje się zgodnie z oczekiwaniami.

  Aby przetestować `CheckingAccount.Withdraw` metodę w naszym przykładzie, możemy napisać dwa testy: jeden, który weryfikuje standardowe zachowanie metody, a drugi, który sprawdza, czy wycofanie więcej niż saldo zakończy się niepowodzeniem. W `CheckingAccountTests` klasie dodawane są następujące metody:

```csharp
[TestMethod]
public void Withdraw_ValidAmount_ChangesBalance()
{
    // arrange
    double currentBalance = 10.0;
    double withdrawal = 1.0;
    double expected = 9.0;
    var account = new CheckingAccount("JohnDoe", currentBalance);
    // act
    account.Withdraw(withdrawal);
    double actual = account.Balance;
    // assert
    Assert.AreEqual(expected, actual);
}

[TestMethod]
[ExpectedException(typeof(ArgumentException))]
public void Withdraw_AmountMoreThanBalance_Throws()
{
    // arrange
    var account = new CheckingAccount("John Doe", 10.0);
    // act
    account.Withdraw(20.0);
    // assert is handled by the ExpectedException
}

```

 Należy zauważyć, że program `Withdraw_ValidAmount_ChangesBalance` używa jawnej `Assert` instrukcji, aby określić, czy metoda testowa została przekazana lub niepowodzeniem, podczas gdy `Withdraw_AmountMoreThanBalance_Throws` używa `ExpectedException` atrybutu do ustalenia sukcesu metody testowej. W obszarze okładek struktura testów jednostkowych zawija metody testowe w instrukcjach try/catch. W większości przypadków w przypadku przechwyconego wyjątku metoda testowa kończy się niepowodzeniem, a wyjątek jest ignorowany. Ten `ExpectedException` atrybut powoduje, że metoda testowa zostanie przekazana w przypadku zgłoszenia określonego wyjątku.

 Aby uzyskać więcej informacji na temat platform testów jednostkowych firmy Microsoft, zobacz jeden z następujących tematów:

- [Pisanie testów jednostkowych dla .NET Framework za pomocą struktury testów jednostkowych Microsoft dla kodu zarządzanego](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)

- [Pisanie testów jednostkowych dla języka C/C++ za pomocą platformy testów jednostkowych firmy Microsoft dla języka C++](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)

## <a name="set-timeouts-for-unit-tests"></a>Ustawianie limitów czasu dla testów jednostkowych
 Aby ustawić limit czasu dla indywidualnej metody testowej:

```csharp
[TestMethod]
[Timeout(2000)]  // Milliseconds
public void My_Test()
{ ...
}
```

```vb

```

 Aby ustawić limit czasu dla maksymalnego dozwolonego limitu:

```csharp
[TestMethod]
[Timeout(TestTimeout.Infinite)]  // Milliseconds
public void My_Test ()
{ ...
}
```

## <a name="run-tests-in-test-explorer"></a><a name="BKMK_Running_tests_in_Test_Explorer"></a>Uruchom testy w Eksploratorze testów
 Podczas kompilowania projektu testowego, testy są wyświetlane w Eksploratorze testów. Jeśli Eksplorator testów nie jest widoczny, wybierz **Testuj** w menu programu Visual Studio, wybierz pozycję **Windows**, a następnie wybierz **Eksplorator testów**.

 ![Eksplorator testów jednostkowych](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")

 Podczas uruchamiania, zapisywania i ponownego uruchamiania testów, domyślny widok Eksploratora testów wyświetla wyniki w grupach **testów zakończonych niepowodzeniem**, testy **zakończone pomyślnie**, testy **pominięte** i **testy nie są uruchamiane**. Możesz wybrać nagłówek grupy, aby otworzyć widok, który wyświetla wszystkie testy w tej grupie.

 Możesz również filtrować testy w dowolnym widoku, dopasowując tekst w polu wyszukiwania na poziomie globalnym lub wybierając jeden z wstępnie zdefiniowanych filtrów. Dowolny wybór testów można uruchomić w dowolnym momencie. Wyniki przebiegu testu są natychmiast widoczne na pasku przekazywania/niepowodzenia w górnej części okna Eksploratora. Szczegóły wyniku metody testowej są wyświetlane po wybraniu testu.

### <a name="run-and-view-tests"></a><a name="BKMK_Running_and_viewing_tests_from_the_Test_Explorer_toolbar"></a>Uruchom i Wyświetl testy
 Pasek narzędzi Eksploratora testów pomaga odkrywać, organizować i uruchamiać testy, które Cię interesują.

 ![Uruchom testy z paska narzędzi Eksploratora testów](../test/media/ute-toolbar.png "UTE_ToolBar")

 Możesz wybrać opcję **Uruchom wszystkie** , aby uruchomić wszystkie testy, lub wybrać polecenie **Uruchom** , aby wybrać podzbiór testów do uruchomienia. Po uruchomieniu zestawu testów, podsumowanie przebiegu testowego pojawia się u dołu okna Eksplorator testów. Wybierz test, aby wyświetlić szczegóły tego testu w dolnym okienku. Wybierz pozycję **Otwórz test** z menu kontekstowego (klawiatura: F12), aby wyświetlić kod źródłowy wybranego testu.

 Jeśli pojedyncze testy nie mają żadnych zależności, które uniemożliwiają ich uruchomienie w dowolnej kolejności, Włącz równoległe wykonywanie testów przy użyciu przycisku ![wykonaj&#95;parallelicon&#45;mały](../test/media/ute-parallelicon-small.png "UTE_parallelicon — mały") przełącznik na pasku narzędzi. Może to znacznie skrócić czas potrzebny do uruchomienia wszystkich testów.

### <a name="run-tests-after-every-build"></a><a name="BKMK_Running_tests_after_every_build"></a>Uruchom testy po każdej kompilacji

> [!WARNING]
> Uruchamianie testów jednostkowych po każdej kompilacji jest obsługiwane tylko w Visual Studio Enterprise.

|Image (Obraz)|Opis|
|-|-|
|![Uruchom po kompilacji](../test/media/ute-runafterbuild-btn.png "UTE_RunAfterBuild_btn")|Aby uruchomić testy jednostkowe po każdej kompilacji lokalnej, wybierz **test** w menu Standard, wybierz opcję **Uruchom testy po kompilacji** na pasku narzędzi Eksploratora testów.|

### <a name="filter-and-group-the-test-list"></a><a name="BKMK_Filtering_and_grouping_the_test_list"></a>Filtrowanie i grupowanie listy testów
 Jeśli masz dużą liczbę testów, możesz wpisać w polu wyszukiwania programu Test Explorer, aby odfiltrować listę według określonego ciągu. Możesz ograniczyć zakres zdarzenia filtru, wybierając z listy filtr.

 ![Kategorie filtrów wyszukiwania](../test/media/ute-searchfilter.png "UTE_SearchFilter")

|Image (Obraz)|Opis|
|-|-|
|![Przycisk grupy Eksploratora testów](../test/media/ute-groupby-btn.png "UTE_GroupBy_btn")|Aby zgrupować testy według kategorii, wybierz przycisk **Grupuj według** .|

 Aby uzyskać więcej informacji, zobacz [Uruchamianie testów jednostkowych za pomocą Eksploratora testów](../test/run-unit-tests-with-test-explorer.md)

## <a name="qa"></a>Pytania i odpowiedzi
 **P: Jak mogę Debuguj testy jednostkowe?**

 Odp **.:** Użyj Eksploratora testów, aby rozpocząć sesję debugowania dla testów. Przechodzenie przez kod za pomocą debugera programu Visual Studio bezproblemowo przeprowadzi Cię z powrotem między testami jednostkowymi i badanym projektem. Aby rozpocząć debugowanie:

1. W edytorze programu Visual Studio Ustaw punkt przerwania w co najmniej jednej metodzie testowej, która ma być debugowana.

   > [!NOTE]
   > Ponieważ metody testowe mogą być uruchamiane w dowolnej kolejności, należy ustawić punkty przerwania we wszystkich metodach testowych, które mają być debugowane.

2. W Eksploratorze testów wybierz metody testowe, a następnie wybierz **Debuguj wybrane testy** z menu skrótów.

   Dowiedz się więcej na temat [debugowania testów jednostkowych](../debugger/debugging-in-visual-studio.md).

   **P: Jeśli używam TDD, jak wygenerować kod na podstawie testów?**

   Odp **.:** Użyj funkcji IntelliSense, aby generować klasy i metody w kodzie projektu. Napisz instrukcję w metodzie testowej, która wywołuje klasę lub metodę, którą chcesz wygenerować, a następnie otwórz menu IntelliSense w wywołaniu. Jeśli wywołanie jest konstruktorem nowej klasy, wybierz opcję **Generuj nowy typ** z menu i postępuj zgodnie z instrukcjami kreatora, aby wstawić klasę w projekcie kodu. Jeśli wywołanie jest metodą, wybierz polecenie **Generuj nową metodę** z menu IntelliSense.

   ![Generowanie menu IntelliSense metody](../test/media/ute-generatemethodstubintellisense.png "UTE_GenerateMethodStubIntellisense")

   **P: Czy można utworzyć testy jednostkowe, które pobierają wiele zestawów danych jako dane wejściowe do uruchomienia testu?**

   **Odpowiedź:** tak. *Metody testowe oparte na danych* umożliwiają przetestowanie zakresu wartości za pomocą pojedynczej metody testu jednostkowego. Użyj `DataSource` atrybutu dla metody testowej, która określa źródło danych i tabelę zawierającą wartości zmiennych, które chcesz przetestować.  W treści metody przypisujesz wartości wierszy do zmiennych przy użyciu `TestContext.DataRow[` indeksatora *ColumnName* `]` .

> [!NOTE]
> Te procedury dotyczą tylko metod testowych, które można napisać przy użyciu struktury testów jednostkowych firmy Microsoft dla kodu zarządzanego. Jeśli używasz innej platformy, zapoznaj się z dokumentacją struktury w celu zapewnienia odpowiedniej funkcjonalności.

 Załóżmy na przykład, że dodajemy niezbędną metodę do `CheckingAccount` klasy o nazwie `AddIntegerHelper` . `AddIntegerHelper`dodaje dwie liczby całkowite.

 Aby utworzyć Test oparty na danych dla `AddIntegerHelper` metody, najpierw tworzymy bazę danych Access o nazwie `AccountsTest.accdb` i tabelę o nazwie `AddIntegerHelperData` . `AddIntegerHelperData`Tabela definiuje kolumny, aby określić pierwszy i drugi operandy dodawania i kolumny, aby określić oczekiwany wynik. Wypełnijmy kilka wierszy z odpowiednimi wartościami.

```csharp

[DataSource(
    @"Provider=Microsoft.ACE.OLEDB.12.0;Data Source=C:\Projects\MyBank\TestData\AccountsTest.accdb",
    "AddIntegerHelperData"
)]
[TestMethod()]
public void AddIntegerHelper_DataDrivenValues_AllShouldPass()
{
    var target = new CheckingAccount();
    int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
    int y = Convert.ToInt32(TestContext.DataRow["SecondNumber"]);
    int expected = Convert.ToInt32(TestContext.DataRow["Sum"]);
    int actual = target.AddIntegerHelper(x, y);
    Assert.AreEqual(expected, actual);
}

```

 Metoda z atrybutem jest uruchamiana jednokrotnie dla każdego wiersza w tabeli. Eksplorator testów zgłasza niepowodzenie testu dla metody, jeśli którykolwiek z iteracji zakończy się niepowodzeniem. W okienku szczegółów wyniki testu dla metody jest wyświetlana Metoda stanu przekazywania/niepowodzenia dla każdego wiersza danych.

 Dowiedz się więcej o [testach jednostkowych opartych na danych](../test/how-to-create-a-data-driven-unit-test.md).

 **P: Czy mogę sprawdzić, jaka część mojego kodu jest testowana przez testy jednostkowe?**

 **Odpowiedź:** tak. Można określić ilość kodu, który jest faktycznie testowany przez testy jednostkowe za pomocą narzędzia pokrycia kodu w programie Visual Studio. Obsługiwane są języki natywne i zarządzane oraz wszystkie struktury testów jednostkowych, które mogą być uruchamiane przez strukturę testów jednostkowych.

 Można uruchomić pokrycie kodu dla wybranych testów lub wszystkich testów w rozwiązaniu. Okno wyniki pokrycia kodu przedstawia wartość procentową bloków kodu produktu, które były wykonywane przez wiersz, funkcję, klasę, przestrzeń nazw i moduł.

 Aby uruchomić pokrycie kodu dla metod testowych w rozwiązaniu, wybierz pozycję **testy** w menu programu Visual Studio, a następnie wybierz polecenie **Analizuj pokrycie kodu**.

 Wyniki pokrycia są wyświetlane w oknie wyników pokrycia kodu.

 ![Wyniki pokrycia kodu](../test/media/ute-codecoverageresults.png "UTE_CodeCoverageResults")

 Dowiedz się więcej o [pokryciu kodu](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) .

 **P: jak można testować metody w moim kodzie z zależnościami zewnętrznymi?**

 **Odpowiedź:** tak. Jeśli masz Visual Studio Enterprise, można użyć elementów sztucznych firmy Microsoft z metodami testowymi, które można napisać przy użyciu platform testów jednostkowych dla kodu zarządzanego.

 Sztuczne firmy Microsoft używają dwóch metod tworzenia klas zastępczych dla zależności zewnętrznych.

1. *Refragmenty* generują klasy zastępcze pochodne od interfejsu nadrzędnego docelowej klasy zależności. Metody zastępcze mogą zostać zastąpione dla publicznych metod wirtualnych klasy docelowej.

2. *Podkładki* korzystają z Instrumentacji środowiska uruchomieniowego, aby przekierować wywołania do metody docelowej do zastępczej metody podkładek dla metod niewirtualnych.

   W obu podejściach można użyć wygenerowanych delegatów wywołań do metody zależności, aby określić zachowanie, które ma zostać użyte w metodzie testowej.

   Dowiedz się więcej [na temat izolowania metod testów jednostkowych za pomocą](../test/isolating-code-under-test-with-microsoft-fakes.md)elementów sztucznych firmy Microsoft.

   **P: Czy można używać innych platform testów jednostkowych do tworzenia testów jednostkowych?**

   Odp **.:** Tak, wykonaj następujące kroki, aby [znaleźć i zainstalować inne platformy](../test/install-third-party-unit-test-frameworks.md). Po ponownym uruchomieniu programu Visual Studio Otwórz ponownie rozwiązanie, aby utworzyć testy jednostkowe, a następnie wybierz zainstalowane platformy tutaj:

   ![Wybierz inną zainstalowaną strukturę testów jednostkowych](../test/media/createunittestsdialogextensions.png "CreateUnitTestsDialogExtensions")

   Testy jednostkowe zostaną utworzone przy użyciu wybranej struktury.
