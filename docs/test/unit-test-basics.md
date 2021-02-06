---
title: Podstawy testów jednostkowych
description: Dowiedz się, jak program Visual Studio Test Explorer zapewnia elastyczny i wydajny sposób uruchamiania testów jednostkowych i wyświetlania ich wyników.
ms.custom: SEO-VS-2020
ms.date: 08/07/2019
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateUnitTest
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5efed99b9934ed91b2194b5a38c99134d6d4b5e5
ms.sourcegitcommit: 686aa3516594ab951d48b192fc60b102eedaf9b7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2021
ms.locfileid: "99628035"
---
# <a name="unit-test-basics"></a>Podstawowe informacje o teście jednostkowym

Sprawdź, czy kod działa zgodnie z oczekiwaniami, tworząc i uruchamiając testy jednostkowe. Jest to tzw. Testowanie jednostkowe, ponieważ należy podzielić funkcjonalność programu na dyskretne zachowania weryfikowalne, które można testować jako pojedyncze *jednostki*. Program Visual Studio Test Explorer oferuje elastyczny i wydajny sposób uruchamiania testów jednostkowych i wyświetlania ich wyników w programie Visual Studio. Program Visual Studio instaluje struktury testów jednostkowych firmy Microsoft dla kodu zarządzanego i natywnego. Użyj *struktury testów jednostkowych* , aby utworzyć testy jednostkowe, uruchomić je i zgłosić wyniki tych testów. Ponownie uruchom testy jednostkowe, gdy wprowadzisz zmiany w celu przetestowania, że kod nadal działa poprawnie. Visual Studio Enterprise można to zrobić automatycznie przy użyciu [Live Unit Testing](live-unit-testing-intro.md), który wykrywa testy, na które wpłynie zmiana kodu i uruchamia je w tle podczas wpisywania.

Testy jednostkowe mają największy wpływ na jakość kodu, gdy jest to integralna część przepływu pracy tworzenia oprogramowania. Gdy tylko napiszesz funkcję lub inny blok kodu aplikacji, należy utworzyć testy jednostkowe, które weryfikują zachowanie kodu w odpowiedzi na standardowe, graniczne i niepoprawne przypadki danych wejściowych oraz sprawdzają wszelkie jawne lub niejawne założenia wykonane przez kod. W przypadku *projektowania sterowanego testem* należy utworzyć testy jednostkowe przed zapisaniem kodu, więc należy użyć testów jednostkowych jako dokumentacji projektu i specyfikacji funkcjonalnych.

Eksplorator testów może również uruchamiać platformy testów jednostkowych innych firm i open source, które mają zaimplementowane interfejsy dodatków w Eksploratorze testów. Wiele z tych platform można dodać za pomocą Menedżera rozszerzeń programu Visual Studio i galerii programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Instalowanie platform testów jednostkowych](../test/install-third-party-unit-test-frameworks.md)innych firm.

Możesz szybko generować projekty testowe i metody testowe z kodu lub ręcznie tworzyć testy w miarę potrzeb. W przypadku korzystania z IntelliTest do eksplorowania kodu platformy .NET można generować dane testowe i zestaw testów jednostkowych. Dla każdej instrukcji w kodzie są generowane dane wejściowe testu, które spowodują wykonanie tej instrukcji. Dowiedz się, jak [generować testy jednostkowe dla kodu platformy .NET](generate-unit-tests-for-your-code-with-intellitest.md).

## <a name="get-started"></a>Rozpoczęcie pracy

Aby zapoznać się z wprowadzeniem do testów jednostkowych, które są bezpośrednio wprowadzane do kodu, zobacz jeden z następujących tematów:

- [Przewodnik: Tworzenie i uruchamianie testów jednostkowych dla kodu platformy .NET](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)

- [Przewodnik: Programowanie sterowane testami za pomocą Eksploratora testów](../test/quick-start-test-driven-development-with-test-explorer.md)

- [Zapisz testy jednostkowe dla C/C++ w programie Visual Studio](../test/writing-unit-tests-for-c-cpp.md)

## <a name="the-mybank-solution-example"></a>Przykład rozwiązania z banku

W tym artykule używamy programowania fikcyjnej aplikacji o nazwie `MyBank` jako przykładu. Kod nie jest potrzebny do wykonania wyjaśnień w tym temacie. Metody testowe są zapisywane w języku C# i prezentowane przy użyciu struktury testów jednostkowych firmy Microsoft dla kodu zarządzanego. Pojęcia te można jednak łatwo przenieść do innych języków i struktur.

::: moniker range="vs-2017"
![Rozwiązanie z banku](../test/media/ute_mybanksolution.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Rozwiązanie z banku 2019](../test/media/vs-2019/basics-mybank-solution.png)
::: moniker-end

Pierwsza próba zaprojektowania `MyBank` aplikacji obejmuje składnik konta, który reprezentuje pojedyncze konto i jego transakcje z bankiem, a składnik bazy danych, który reprezentuje funkcje do agregowania poszczególnych kont i zarządzania nimi.

Tworzymy `MyBank` rozwiązanie, które zawiera dwa projekty:

- `Accounts`

- `BankDb`

Nasza pierwsza próba projektowania `Accounts` projektu zawiera klasę, która przechowuje podstawowe informacje o koncie, interfejs, który określa typowe funkcje dowolnego typu konta, takie jak kaucja i wycofanie zasobów z konta, oraz Klasa pochodna interfejsu, który reprezentuje konto sprawdzania. Rozpoczynamy projekty kont, tworząc następujące pliki źródłowe:

- *AccountInfo.cs* definiuje podstawowe informacje o koncie.

- *IAccount.cs* definiuje standardowy `IAccount` interfejs dla konta, w tym metody do depozytu i wycofywania zasobów z konta oraz do pobierania salda konta.

- *CheckingAccount.cs* zawiera `CheckingAccount` klasę, która implementuje `IAccount` interfejs do sprawdzania konta.

Wiemy, że jednym z nich jest wycofanie z konta kontroli, aby upewnić się, że wycofana kwota jest mniejsza niż saldo konta. Dlatego zastąpimy `IAccount.Withdraw` metodę `CheckingAccount` z użyciem metody, która sprawdza, czy jest to warunek. Metoda może wyglądać następująco:

```csharp
public void Withdraw(double amount)
{
    if(m_balance >= amount)
    {
        m_balance -= amount;
    }
    else
    {
        throw new ArgumentException(nameof(amount), "Withdrawal exceeds balance!");
    }
}
```

Teraz, gdy mamy jakiś kod, czas na przetestowanie.

## <a name="create-unit-test-projects-and-test-methods"></a>Tworzenie projektów testów jednostkowych i metod testowych

W języku C# często jest szybsze generowanie projektu testów jednostkowych i testów jednostkowych w kodzie. Możesz też utworzyć projekt testu jednostkowego i testy ręcznie, w zależności od wymagań. Jeśli chcesz utworzyć testy jednostkowe z kodu za pomocą struktury innej firmy, konieczne będzie zainstalowanie jednego z tych rozszerzeń: [nunit](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension-18371) lub [xUnit](https://marketplace.visualstudio.com/items?itemName=YowkoTsai.xUnitnetTestGenerator). Jeśli nie używasz języka C#, Pomiń tę sekcję i przejdź do sekcji [Tworzenie projektu testów jednostkowych i testów jednostkowych ręcznie](#create-the-unit-test-project-and-unit-tests-manually).

### <a name="generate-unit-test-project-and-unit-test-stubs"></a>Generuj projekty testów jednostkowych i testy jednostkowe

1. W oknie Edytor kodu kliknij prawym przyciskiem myszy i wybierz polecenie [**Utwórz testy jednostkowe**](create-unit-tests-menu.md) z menu dostępnego po kliknięciu prawym przyciskiem myszy.

   ::: moniker range="vs-2017"
   ![W oknie Edytor Wyświetl menu kontekstowe.](../test/media/createunittestsrightclick.png)

   > [!NOTE]
   > Polecenie **Utwórz testy jednostkowe** jest dostępne tylko dla kodu zarządzanego, który jest przeznaczony dla .NET Framework (ale nie do programu .NET Core).
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![W oknie Edytor Wyświetl menu kontekstowe.](../test/media/vs-2019/basics-create-unit-tests.png)

   > [!NOTE]
   > Polecenie **Utwórz testy jednostkowe** jest dostępne tylko dla kodu w języku C#.
   ::: moniker-end

2. Kliknij przycisk **OK** , aby zaakceptować wartości domyślne, aby utworzyć testy jednostkowe, lub Zmień wartości używane do utworzenia i nazwy projektu testów jednostkowych i testów jednostkowych. Można wybrać kod, który jest domyślnie dodawany do metod testów jednostkowych.

   ![Okno dialogowe Tworzenie testów jednostkowych w programie Visual Studio](../test/media/create-unit-tests.png)

3. Procedury pośredniczące testów jednostkowych są tworzone w nowym projekcie testów jednostkowych dla wszystkich metod w klasie.

   ::: moniker range="vs-2017"
   ![Testy jednostkowe są tworzone](../test/media/createunittestsstubs.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Testy jednostkowe są tworzone](../test/media/vs-2019/basics-test-stub.png)
   ::: moniker-end

4. Teraz przechodźmy, aby dowiedzieć się, jak [dodać kod do metod testów jednostkowych](#write-your-tests) , aby sprawdzić, czy test jednostkowy jest znaczący, i wszelkie dodatkowe testy jednostkowe, które można dodać w celu dokładnego przetestowania kodu.

### <a name="create-the-unit-test-project-and-unit-tests-manually"></a>Utwórz ręcznie projekt testu jednostkowego i testy jednostkowe

Projekt testu jednostkowego zazwyczaj odzwierciedla strukturę pojedynczego projektu kodu. W przykładzie z banku dodaje się dwa projekty testów jednostkowych o nazwie `AccountsTests` i `BankDbTests` do `MyBanks` rozwiązania. Nazwy projektów testowych są dowolne, ale zaleca się zastosowanie standardowej konwencji nazewnictwa.

**Aby dodać projekt testu jednostkowego do rozwiązania:**

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy rozwiązanie i wybierz polecenie **Dodaj**  >  **Nowy** **projekt**.

::: moniker range="vs-2017"

2. W oknie dialogowym **Nowy projekt** rozwiń węzeł **zainstalowany** , wybierz język, który ma być używany dla projektu testowego, a następnie wybierz polecenie **Testuj**.

3. Aby użyć jednej z platform testów jednostkowych firmy Microsoft, wybierz opcję **projekt testu jednostkowego** z listy szablonów projektu. W przeciwnym razie wybierz szablon projektu dla struktury testów jednostkowych, który ma być używany. Aby przetestować `Accounts` projekt naszego przykładu, należy nazwać projekt `AccountsTests` .

   > [!NOTE]
   > Nie wszystkie struktury testów jednostkowych innych firm i typu open source zawierają szablon projektu programu Visual Studio. Zapoznaj się z dokumentem struktury, aby uzyskać informacje na temat tworzenia projektu.

::: moniker-end

::: moniker range=">=vs-2019"

2. Użyj pola wyszukiwania szablonu projektu, aby znaleźć szablon projektu testów jednostkowych dla środowiska testowego, którego chcesz użyć.

3. Na następnej stronie Nadaj projektowi nazwę. Aby przetestować `Accounts` projekt naszego przykładu, można nazwać projekt `AccountsTests` .

::: moniker-end

4. W projekcie testów jednostkowych Dodaj odwołanie do badanego projektu kodu, w naszym przykładzie do projektu accounts.

   Aby utworzyć odwołanie do projektu kodu:

   1. Wybierz projekt w **Eksplorator rozwiązań**.

   2. W menu **projekt** wybierz polecenie **Dodaj odwołanie**.

   3. W oknie dialogowym **Menedżer odwołań** Otwórz węzeł **rozwiązania** i wybierz pozycję **projekty**. Wybierz nazwę projektu kodu i Zamknij okno dialogowe.

Każdy projekt testu jednostkowego zawiera klasy, które są duplikatami nazw klas w projekcie kodu. W naszym przykładzie `AccountsTests` projekt będzie zawierał następujące klasy:

- `AccountInfoTests` Klasa zawiera metody testów jednostkowych dla `AccountInfo` klasy w `Accounts` projekcie

- `CheckingAccountTests` Klasa zawiera metody testów jednostkowych `CheckingAccount` klasy.

## <a name="write-your-tests"></a>Napisz testy

Używana struktura testów jednostkowych i Visual Studio IntelliSense przeprowadzi Cię przez proces pisania kodu dla testów jednostkowych w projekcie kodu. Aby uruchomić program w **Eksploratorze testów**, większość platform wymaga dodania określonych atrybutów do identyfikacji metod testów jednostkowych. Struktury zapewniają również sposób — zwykle za pomocą instrukcji Assert lub atrybutów metod — w celu wskazania, czy metoda testowa została pomyślnie zakończyła się powodzeniem, czy nie. Inne atrybuty identyfikują opcjonalne metody instalacji, które są inicjowane podczas inicjalizacji klasy, oraz przed każdą metodą testową i metodami usuwania, które są uruchamiane po każdej metodzie testowej i przed zniszczeniem klasy.

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

    // assert
    Assert.AreEqual(expected, account.Balance);
}

[TestMethod]
public void Withdraw_AmountMoreThanBalance_Throws()
{
    // arrange
    var account = new CheckingAccount("John Doe", 10.0);

    // act and assert
    Assert.ThrowsException<System.ArgumentException>(() => account.Withdraw(20.0));
}
```

Aby uzyskać więcej informacji na temat platform testów jednostkowych firmy Microsoft, zobacz jeden z następujących tematów:

- [Testowanie jednostkowe kodu](unit-test-your-code.md)

- [Pisanie testów jednostkowych dla C/C++](writing-unit-tests-for-c-cpp.md)

- [Używanie struktury MSTest w testach jednostkowych](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

## <a name="set-timeouts-for-unit-tests"></a>Ustawianie limitów czasu dla testów jednostkowych

Jeśli używasz platformy MSTest Framework, możesz użyć, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TimeoutAttribute> Aby ustawić limit czasu dla indywidualnej metody testowej:

```csharp
[TestMethod]
[Timeout(2000)]  // Milliseconds
public void My_Test()
{ ...
}
```

Aby ustawić limit czasu dla maksymalnego dozwolonego limitu:

```csharp
[TestMethod]
[Timeout(TestTimeout.Infinite)]  // Milliseconds
public void My_Test ()
{ ...
}
```

## <a name="run-tests-in-test-explorer"></a>Uruchom testy w Eksploratorze testów

Podczas kompilowania projektu testowego, testy są wyświetlane w **Eksploratorze testów**. Jeśli **Eksplorator testów** nie jest widoczny, wybierz polecenie **Testuj** w menu programu Visual Studio, wybierz pozycję **Windows**, a następnie wybierz polecenie **Eksplorator testów** (lub naciśnij **klawisze CTRL**  +  **E**, **T**).

::: moniker range="vs-2017"
![Eksplorator testów jednostkowych](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Eksplorator testów jednostkowych](../test/media/vs-2019/basics-test-explorer.png)
::: moniker-end

Podczas uruchamiania, zapisywania i ponownego uruchamiania testów, **Eksplorator testów** może wyświetlać wyniki w grupach **testów zakończonych niepowodzeniem**, testów **zakończonych pomyślnie**, **pominiętych testów** i **nieuruchomionych testów**. Na pasku narzędzi można wybrać różne opcje grupowania.

Możesz również filtrować testy w dowolnym widoku, dopasowując tekst w polu wyszukiwania na poziomie globalnym lub wybierając jeden z wstępnie zdefiniowanych filtrów. Dowolny wybór testów można uruchomić w dowolnym momencie. Wyniki przebiegu testu są natychmiast widoczne na pasku przekazywania/niepowodzenia w górnej części okna Eksploratora. Szczegóły wyniku metody testowej są wyświetlane po wybraniu testu.

### <a name="run-and-view-tests"></a>Uruchom i Wyświetl testy

Pasek narzędzi **Eksploratora testów** pomaga odkrywać, organizować i uruchamiać testy, które Cię interesują.

::: moniker range="vs-2017"
![Uruchom testy z paska narzędzi Eksploratora testów](../test/media/ute_toolbar.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Uruchom testy z paska narzędzi Eksploratora testów](../test/media/vs-2019/test-explorer-toolbar-diagram-16-2.png)
::: moniker-end

Możesz wybrać opcję **Uruchom wszystkie** , aby uruchomić wszystkie testy (lub nacisnąć **klawisze CTRL**  +  **r**, **V**) lub wybrać polecenie **Uruchom** , aby wybrać podzbiór testów do uruchomienia (**Ctrl**  +  **r**, **T**). Wybierz test, aby wyświetlić szczegóły tego testu w okienku Szczegóły testu. Wybierz **Otwórz test z menu dostępnego** po kliknięciu prawym przyciskiem myszy (klawiatura: **F12**), aby wyświetlić kod źródłowy wybranego testu.

::: moniker range="vs-2017"

Jeśli pojedyncze testy nie mają żadnych zależności, które uniemożliwiają ich uruchomienie w dowolnej kolejności, należy włączyć równoległe wykonywanie testów przy użyciu ![Zrzut ekranu przedstawiający przycisk przełączania równoległego wykonywania testu na pasku narzędzi programu Visual Studio Test Explorer.](../test/media/ute_parallelicon-small.png) przycisk przełączania na pasku narzędzi. Może to znacznie skrócić czas potrzebny do uruchomienia wszystkich testów.

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli pojedyncze testy nie mają żadnych zależności, które uniemożliwiają ich uruchomienie w dowolnej kolejności, Włącz równoległe wykonywanie testów w menu Ustawienia na pasku narzędzi. Może to znacznie skrócić czas potrzebny do uruchomienia wszystkich testów.

::: moniker-end

### <a name="run-tests-after-every-build"></a>Uruchom testy po każdej kompilacji

::: moniker range="vs-2017"

|Przycisk|Opis|
|-|-|
|![Uruchom po kompilacji](../test/media/ute_runafterbuild_btn.png)|Aby uruchomić testy jednostkowe po każdej kompilacji lokalnej, wybierz **test** w menu Standard, a następnie wybierz polecenie **Uruchom testy po kompilacji** na pasku narzędzi **Eksploratora testów** .|

> [!NOTE]
> Uruchamianie testów jednostkowych po każdej kompilacji wymaga programu Visual Studio 2017 Enterprise Edition lub Visual Studio 2019. W programie Visual Studio 2019 ta funkcja jest dostępna w wersjach Community i Professional, a także w wersji Enterprise.

::: moniker-end

::: moniker range=">=vs-2019"

Aby uruchomić testy jednostkowe po każdej kompilacji lokalnej, Otwórz ikonę ustawienia na pasku narzędzi Eksploratora testów i wybierz opcję **Uruchom testy po kompilacji**.

::: moniker-end

### <a name="filter-and-group-the-test-list"></a>Filtrowanie i grupowanie listy testów

Jeśli masz dużą liczbę testów, możesz wpisać w polu wyszukiwania **Eksploratora testów** , aby odfiltrować listę według określonego ciągu. Możesz ograniczyć zakres zdarzenia filtru, wybierając z listy filtr.

::: moniker range="vs-2017"
![Kategorie filtrów wyszukiwania](../test/media/ute_searchfilter.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Kategorie filtrów wyszukiwania](../test/media/vs-2019/test-explorer-search-filter-16-2.png)
::: moniker-end

|Przycisk|Opis|
|-|-|
|![Przycisk grupy Eksploratora testów](../test/media/ute_groupby_btn.png)|Aby zgrupować testy według kategorii, wybierz przycisk **Grupuj według** .|

Aby uzyskać więcej informacji, zobacz [Uruchamianie testów jednostkowych za pomocą Eksploratora testów](../test/run-unit-tests-with-test-explorer.md).

## <a name="qa"></a>Pytania i odpowiedzi

**P: Jak mogę Debuguj testy jednostkowe?**

Odp **.:** Użyj **Eksploratora testów** , aby rozpocząć sesję debugowania dla testów. Przechodzenie przez kod za pomocą debugera programu Visual Studio bezproblemowo przeprowadzi Cię z powrotem między testami jednostkowymi i badanym projektem. Aby rozpocząć debugowanie:

1. W edytorze programu Visual Studio Ustaw punkt przerwania w co najmniej jednej metodzie testowej, która ma być debugowana.

    > [!NOTE]
    > Ponieważ metody testowe mogą być uruchamiane w dowolnej kolejności, należy ustawić punkty przerwania we wszystkich metodach testowych, które mają być debugowane.

2. W **Eksploratorze testów** wybierz metody testowe, a następnie wybierz **Debuguj wybrane testy** z menu skrótów.

Dowiedz się więcej na temat [debugowania testów jednostkowych](../debugger/debugger-feature-tour.md).

**P: Jeśli używam TDD, jak wygenerować kod na podstawie testów?**

Odp **.:** Użyj szybkich akcji do wygenerowania klas i metod w kodzie projektu. Napisz instrukcję w metodzie testowej, która wywołuje klasę lub metodę, którą chcesz wygenerować, a następnie otwórz żarówki, która pojawia się pod błędem. Jeśli wywołanie jest konstruktorem nowej klasy, wybierz polecenie **Generuj typ** z menu i postępuj zgodnie z instrukcjami kreatora, aby wstawić klasę w projekcie kodu. Jeśli wywołanie jest metodą, wybierz polecenie **Generuj metodę** z menu IntelliSense.

::: moniker range="vs-2017"
![Menu Generuj szybką akcję klasy zastępczej](../test/media/ute_generatemethodstubintellisense.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Menu Generuj szybką akcję klasy zastępczej](../test/media/vs-2019/basics-generate-method-tdd.png)
::: moniker-end

**P: Czy można utworzyć testy jednostkowe, które pobierają wiele zestawów danych jako dane wejściowe do uruchomienia testu?**

**Odpowiedź:** tak. *Metody testowe oparte na danych* umożliwiają przetestowanie zakresu wartości za pomocą pojedynczej metody testu jednostkowego. Użyj `DataSource` atrybutu dla metody testowej, która określa źródło danych i tabelę zawierającą wartości zmiennych, które chcesz przetestować.  W treści metody przypisujesz wartości wierszy do zmiennych przy użyciu `TestContext.DataRow[` indeksatora *ColumnName* `]` .

> [!NOTE]
> Te procedury dotyczą tylko metod testowych, które można napisać przy użyciu struktury testów jednostkowych firmy Microsoft dla kodu zarządzanego. Jeśli używasz innej platformy, zapoznaj się z dokumentacją struktury w celu zapewnienia odpowiedniej funkcjonalności.

Załóżmy na przykład, że dodajemy niezbędną metodę do `CheckingAccount` klasy o nazwie `AddIntegerHelper` . `AddIntegerHelper` dodaje dwie liczby całkowite.

Aby utworzyć Test oparty na danych dla `AddIntegerHelper` metody, najpierw tworzymy bazę danych Access o nazwie *AccountsTest. accdb* i tabelę o nazwie `AddIntegerHelperData` . `AddIntegerHelperData`Tabela definiuje kolumny, aby określić pierwszy i drugi operandy dodawania i kolumny, aby określić oczekiwany wynik. Wypełnijmy kilka wierszy z odpowiednimi wartościami.

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

Metoda z atrybutem jest uruchamiana jednokrotnie dla każdego wiersza w tabeli. **Eksplorator testów** zgłasza niepowodzenie testu dla metody, jeśli którykolwiek z iteracji zakończy się niepowodzeniem. W okienku szczegółów wyniki testu dla metody jest wyświetlana Metoda stanu przekazywania/niepowodzenia dla każdego wiersza danych.

Dowiedz się więcej o [testach jednostkowych opartych na danych](../test/how-to-create-a-data-driven-unit-test.md).

**P: Czy mogę sprawdzić, jaka część mojego kodu jest testowana przez testy jednostkowe?**

**Odpowiedź:** tak. Można określić ilość kodu, który jest faktycznie testowany przez testy jednostkowe za pomocą narzędzia pokrycia kodu w programie Visual Studio w Visual Studio Enterprise. Obsługiwane są języki natywne i zarządzane oraz wszystkie struktury testów jednostkowych, które mogą być uruchamiane przez strukturę testów jednostkowych.

Można uruchomić pokrycie kodu dla wybranych testów lub wszystkich testów w rozwiązaniu. Okno **wyniki pokrycia kodu** przedstawia wartość procentową bloków kodu produktu, które były wykonywane przez wiersz, funkcję, klasę, przestrzeń nazw i moduł.

Aby uruchomić pokrycie kodu dla metod testowych w rozwiązaniu, wybierz **Testuj**  >  **Przeanalizuj pokrycie kodu dla wszystkich testów**.

Wyniki pokrycia są wyświetlane w oknie **wyników pokrycia kodu** .

![Wyniki pokrycia kodu](../test/media/ute_codecoverageresults.png)

Dowiedz się więcej o [pokryciu kodu](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) .

**P: Czy można testować metody w moim kodzie, który ma zależności zewnętrzne?**

**Odpowiedź:** tak. Jeśli masz Visual Studio Enterprise, można użyć elementów sztucznych firmy Microsoft z metodami testowymi, które można napisać przy użyciu platform testów jednostkowych dla kodu zarządzanego.

Sztuczne firmy Microsoft używają dwóch metod tworzenia klas zastępczych dla zależności zewnętrznych:

1. *Refragmenty* generują klasy zastępcze pochodne od interfejsu nadrzędnego docelowej klasy zależności. Metody zastępcze mogą zostać zastąpione dla publicznych metod wirtualnych klasy docelowej.

2. *Podkładki* korzystają z Instrumentacji środowiska uruchomieniowego, aby przekierować wywołania do metody docelowej do zastępczej metody podkładek dla metod niewirtualnych.

W obu podejściach można użyć wygenerowanych delegatów wywołań do metody zależności, aby określić zachowanie, które ma zostać użyte w metodzie testowej.

Dowiedz się więcej [na temat izolowania metod testów jednostkowych za pomocą](../test/isolating-code-under-test-with-microsoft-fakes.md)elementów sztucznych firmy Microsoft.

**P: Czy można używać innych platform testów jednostkowych do tworzenia testów jednostkowych?**

Odp **.:** Tak, wykonaj następujące kroki, aby [znaleźć i zainstalować inne platformy](../test/install-third-party-unit-test-frameworks.md). Po ponownym uruchomieniu programu Visual Studio Otwórz ponownie rozwiązanie, aby utworzyć testy jednostkowe, a następnie wybierz zainstalowane platformy tutaj:

![Wybierz inną zainstalowaną strukturę testów jednostkowych](../test/media/createunittestsdialogextensions.png)

Testy jednostkowe zostaną utworzone przy użyciu wybranej struktury.
