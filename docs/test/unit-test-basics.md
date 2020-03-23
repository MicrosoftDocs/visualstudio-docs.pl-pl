---
title: Podstawy testowania jednostek
ms.date: 08/07/2019
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateUnitTest
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77ac5ffd14f97fd6fdd753327fe193ceb80ea57e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75846929"
---
# <a name="unit-test-basics"></a>Podstawowe informacje o teście jednostkowym

Sprawdź, czy kod działa zgodnie z oczekiwaniami, tworząc i uruchamiając testy jednostkowe. To się nazywa testowanie jednostkowe, ponieważ można podzielić funkcjonalność programu na dyskretne sprawdzone zachowania, które można przetestować jako poszczególne *jednostki.* Visual Studio Test Explorer zapewnia elastyczny i wydajny sposób uruchamiania testów jednostkowych i wyświetlania ich wyników w programie Visual Studio. Visual Studio instaluje struktury testowania jednostkowego firmy Microsoft dla kodu zarządzanego i natywnego. Użyj *struktury testowania jednostkowego* do tworzenia testów jednostkowych, uruchamiania ich i raportowania wyników tych testów. Uruchom ponownie testy jednostkowe po wprowadzeniu zmian w celu sprawdzenia, czy kod nadal działa poprawnie. Visual Studio Enterprise można to zrobić automatycznie za pomocą [live unit testing](live-unit-testing-intro.md), który wykrywa testy, których dotyczą zmiany kodu i uruchamia je w tle podczas pisania.

Testowanie jednostkowe ma największy wpływ na jakość kodu, gdy jest integralną częścią przepływu pracy tworzenia oprogramowania. Jak najszybciej napisać funkcję lub inny blok kodu aplikacji, należy utworzyć testy jednostkowe, które weryfikują zachowanie kodu w odpowiedzi na standardowe, granice i niepoprawne przypadki danych wejściowych i które sprawdzają wszelkie jawne lub niejawne założenia wprowadzone przez kod. W *przypadku rozwoju opartego*na testach należy utworzyć testy jednostkowe przed napisaniem kodu, dlatego testy jednostkowe są używane zarówno jako dokumentacja projektowa, jak i specyfikacje funkcjonalne.

Można szybko wygenerować projekty testowe i metody testowe z kodu lub ręcznie utworzyć testy, jak ich potrzebujesz. Korzystając z intellitestu do eksplorowania kodu .NET, można wygenerować dane testowe i zestaw testów jednostkowych. Dla każdej instrukcji w kodzie jest generowany test danych wejściowych, który wykona tę instrukcję. Dowiedz się, jak [wygenerować testy jednostkowe dla kodu](generate-unit-tests-for-your-code-with-intellitest.md).

Eksplorator testów może również uruchamiać struktury testów jednostek innych firm i open source, które zaimplementowały interfejsy dodatków Eksploratora testów. Można dodać wiele z tych struktur za pośrednictwem Visual Studio Extension Manager i galerii Visual Studio. Aby uzyskać więcej informacji, zobacz [Instalowanie struktur testów jednostkowych innych firm](../test/install-third-party-unit-test-frameworks.md).

## <a name="get-started"></a>Wprowadzenie

Aby zapoznać się z wprowadzeniem do testowania jednostkowego, które prowadzi bezpośrednio do kodowania, zobacz jeden z następujących tematów:

- [Przewodnik: tworzenie i uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)

- [Szybki start: program rozwoju oparty na testach za pomocą Eksploratora testów](../test/quick-start-test-driven-development-with-test-explorer.md)

- [Zapisywanie testów jednostkowych dla języka C/C++ w programie Visual Studio](../test/writing-unit-tests-for-c-cpp.md)

## <a name="the-mybank-solution-example"></a>Przykład rozwiązania MyBank

W tym artykule używamy rozwoju fikcyjnej `MyBank` aplikacji o nazwie jako przykład. Nie potrzebujesz rzeczywistego kodu, aby postępować zgodnie z objaśnieniami w tym temacie. Metody testowe są zapisywane w języku C# i prezentowane przy użyciu struktury microsoft unit testing framework dla kodu zarządzanego. Jednak pojęcia są łatwo przenoszone do innych języków i struktur.

::: moniker range="vs-2017"
![Rozwiązanie MyBank](../test/media/ute_mybanksolution.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Rozwiązanie MyBank 2019](../test/media/vs-2019/basics-mybank-solution.png)
::: moniker-end

Nasza pierwsza próba projektu `MyBank` aplikacji obejmuje składnik kont, który reprezentuje indywidualne konto i jego transakcje z bankiem, oraz składnik bazy danych, który reprezentuje funkcjonalność agregowania poszczególnych kont i zarządzania nimi.

Tworzymy `MyBank` rozwiązanie, które zawiera dwa projekty:

- `Accounts`

- `BankDb`

Nasza pierwsza próba projektowania `Accounts` projektu zawiera klasę do przechowywania podstawowych informacji o koncie, interfejs, który określa wspólne funkcje dowolnego typu konta, takie jak deponowanie i wycofywanie zasobów z konta, a klasa pochodząca z interfejsu, który reprezentuje konto czekowe. Rozpoczynamy projekty Kont, tworząc następujące pliki źródłowe:

- *AccountInfo.cs* definiuje podstawowe informacje dla konta.

- *IAccount.cs* definiuje standardowy `IAccount` interfejs dla konta, w tym metody wpłaty i wypłaty aktywów z konta i odzyskania salda konta.

- *CheckingAccount.cs* zawiera `CheckingAccount` klasę, która implementuje `IAccount` interfejs dla konta czekowego.

Z doświadczenia wiemy, że jedną z rzeczy, które musi zrobić wypłata z konta czekowego, jest upewnienie się, że wypłacona kwota jest mniejsza niż saldo konta. Dlatego zastępujemy `IAccount.Withdraw` metodę za `CheckingAccount` pomocą metody, która sprawdza ten warunek. Metoda może wyglądać następująco:

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

Teraz, gdy mamy jakiś kod, nadszedł czas na testowanie.

## <a name="create-unit-test-projects-and-test-methods"></a>Tworzenie projektów testów jednostkowych i metod testowych

Często szybciej jest wygenerować projekt testu jednostkowego i wycinki testów jednostkowych z kodu. Lub można utworzyć projekt testu jednostkowego i testy ręcznie w zależności od wymagań. Jeśli chcesz utworzyć testy jednostkowe z platformą innej firmy, potrzebujesz jednego z tych rozszerzeń zainstalowanych: [NUnit](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension-18371) lub [xUnit](https://marketplace.visualstudio.com/items?itemName=YowkoTsai.xUnitnetTestGenerator).

### <a name="generate-unit-test-project-and-unit-test-stubs"></a>Generowanie wycinków projektu testu jednostkowego i testu jednostkowego

1. W oknie edytora kodu kliknij prawym przyciskiem myszy i wybierz polecenie [**Utwórz testy jednostkowe**](create-unit-tests-menu.md) z menu po kliknięciu prawym przyciskiem myszy.

   ::: moniker range="vs-2017"
   ![W oknie edytora wyświetl menu kontekstowe](../test/media/createunittestsrightclick.png)

   > [!NOTE]
   > Polecenie Menu **Utwórz testy jednostkowe** jest dostępne tylko dla kodu zarządzanego przeznaczonego dla programu .NET Framework (ale nie dla programu .NET Core).
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![W oknie edytora wyświetl menu kontekstowe](../test/media/vs-2019/basics-create-unit-tests.png)

   > [!NOTE]
   > Polecenie Menu **Utwórz testy jednostkowe** jest dostępne tylko dla kodu zarządzanego.
   ::: moniker-end

2. Kliknij **przycisk OK,** aby zaakceptować wartości domyślne w celu utworzenia testów jednostkowych lub zmienić wartości używane do tworzenia i nazywania projektu testu jednostkowego i testów jednostkowych. Można wybrać kod, który jest domyślnie dodawany do metod testowania jednostkowego.

   ![Okno dialogowe Tworzenie testów jednostkowych w programie Visual Studio](../test/media/create-unit-tests.png)

3. Odcinki testu jednostkowego są tworzone w nowym projekcie testu jednostkowego dla wszystkich metod w klasie.

   ::: moniker range="vs-2017"
   ![Testy jednostkowe są tworzone](../test/media/createunittestsstubs.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Testy jednostkowe są tworzone](../test/media/vs-2019/basics-test-stub.png)
   ::: moniker-end

4. Teraz przejdź do przodu, aby dowiedzieć się, jak [dodać kod do metod testów jednostkowych,](#write-your-tests) aby twój test jednostkowy miał znaczenie, a wszelkie dodatkowe testy jednostkowe, które można dodać, aby dokładnie przetestować kod.

### <a name="create-the-unit-test-project-and-unit-tests-manually"></a>Ręczne tworzenie projektu testu jednostkowego i testów jednostkowych

Projekt testu jednostkowego zwykle dubluje strukturę projektu pojedynczego kodu. W przykładzie MyBank dodajesz dwa `AccountsTests` projekty `BankDbTests` testów `MyBanks` jednostkowych o nazwie i do rozwiązania. Nazwy projektów testowych są dowolne, ale przyjęcie standardowej konwencji nazewnictwa jest dobrym pomysłem.

**Aby dodać projekt testu jednostkowego do rozwiązania:**

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie i wybierz pozycję **Dodaj** > **nowy** **projekt**.

::: moniker range="vs-2017"

2. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Zainstalowany,** wybierz język, którego chcesz użyć w projekcie testowym, a następnie wybierz pozycję **Testuj**.

3. Aby użyć jednej z jednostek testów firmy Microsoft, wybierz pozycję **Unit Test Project** z listy szablonów projektów. W przeciwnym razie wybierz szablon projektu struktury testów jednostkowych, które chcesz użyć. Aby przetestować projekt naszego `Accounts` przykładu, `AccountsTests`należy nazwać projekt .

   > [!NOTE]
   > Nie wszystkie struktury testów jednostek innych firm i open source zapewniają szablon projektu programu Visual Studio. Informacje na temat tworzenia projektu można znaleźć w dokumencie ramowym.

::: moniker-end

::: moniker range=">=vs-2019"

2. Użyj pola wyszukiwania szablonu projektu, aby znaleźć szablon projektu testu jednostkowego dla struktury testów, której chcesz użyć.

3. Na następnej stronie nazwij projekt. Aby przetestować projekt naszego `Accounts` przykładu, `AccountsTests`można nazwać projekt .

::: moniker-end

4. W projekcie testu jednostkowego dodaj odwołanie do projektu kodu w ramach testu, w naszym przykładzie do projektu Konta.

   Aby utworzyć odwołanie do projektu kodu:

   1. Wybierz projekt w **Eksploratorze rozwiązań**.

   2. W menu **Projekt** wybierz polecenie **Dodaj odwołanie**.

   3. W oknie dialogowym **Menedżer odwołań** otwórz węzeł **Rozwiązanie** i wybierz pozycję **Projekty**. Wybierz nazwę projektu kodu i zamknij okno dialogowe.

Każdy projekt testu jednostkowego zawiera klasy, które dublują nazwy klas w projekcie kodu. W naszym przykładzie `AccountsTests` projekt będzie zawierał następujące klasy:

- `AccountInfoTests`zawiera metody badania jednostkowego `AccountInfo` dla `Accounts` klasy w projekcie

- `CheckingAccountTests`zawiera metody badania jednostkowego dla `CheckingAccount` klasy.

## <a name="write-your-tests"></a>Napisz swoje testy

Struktura testów jednostkowych, którego używasz i Visual Studio IntelliSense poprowadzi Cię przez pisanie kodu dla testów jednostkowych dla projektu kodu. Aby uruchomić w **Eksploratorze testów,** większość struktur wymaga dodania określonych atrybutów w celu zidentyfikowania metod testowania jednostkowego. Struktury zapewniają również sposób — zwykle za pośrednictwem assert instrukcji lub atrybutów metody — aby wskazać, czy metoda testowa została przekazana, czy nie powiodła się. Inne atrybuty identyfikują opcjonalne metody konfiguracji, które są inicjowania klasy i przed każdej metody testowej i metody teardown, które są uruchamiane po każdej metody testowej i przed klasa jest niszczony.

Wzorzec AAA (Arrange, Act, Assert) jest typowym sposobem pisania testów jednostkowych dla badanej metody.

- Sekcja **Rozmieść** metody badania jednostkowego inicjuje obiekty i ustawia wartość danych, która jest przekazywana do metody w ramach testu.

- Sekcja **Act** wywołuje metodę testowaną z ustalonymi parametrami.

- Assert **Assert** sekcji sprawdza, czy akcja metody w ramach testu zachowuje się zgodnie z oczekiwaniami.

Aby przetestować metodę naszego `CheckingAccount.Withdraw` przykładu, możemy napisać dwa testy: jeden, który weryfikuje standardowe zachowanie metody i taki, który sprawdza, czy wycofanie więcej niż saldo zakończy się niepowodzeniem. W `CheckingAccountTests` klasie dodajemy następujące metody:

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

Aby uzyskać więcej informacji na temat struktury testowania jednostek firmy Microsoft, zobacz jeden z następujących tematów:

- [Jednostka przetestować swój kod](unit-test-your-code.md)

- [Pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md)

- [Użyj struktury MSTest w testach jednostkowych](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

## <a name="set-timeouts-for-unit-tests"></a>Ustawianie limitów czasu dla testów jednostkowych

Jeśli używasz struktury MSTest, można <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TimeoutAttribute> użyć, aby ustawić limit czasu dla poszczególnych metod testowych:

```csharp
[TestMethod]
[Timeout(2000)]  // Milliseconds
public void My_Test()
{ ...
}
```

Aby ustawić limit czasu na maksymalny dozwolony:

```csharp
[TestMethod]
[Timeout(TestTimeout.Infinite)]  // Milliseconds
public void My_Test ()
{ ...
}
```

## <a name="run-tests-in-test-explorer"></a>Uruchamianie testów w Eksploratorze testów

Podczas tworzenia projektu testowego testy są wyświetlane w **Eksploratorze testów.** Jeśli **Eksplorator testów** nie jest widoczny, wybierz polecenie **Testuj** w menu programu Visual Studio, wybierz pozycję **Windows**, a następnie wybierz pozycję **Eksplorator testów**.

::: moniker range="vs-2017"
![Eksplorator testów jednostkowych](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Eksplorator testów jednostkowych](../test/media/vs-2019/basics-test-explorer.png)
::: moniker-end

Podczas uruchamiania, zapisywania i ponownego uruchamiania testów **Eksplorator testów** może wyświetlać wyniki w grupach **testów nieudanych,** **testów przeszłych,** **pominiętych testów** i nie **uruchamianych testów.** Na pasku narzędzi można wybrać inną grupę według opcji.

Testy można również filtrować w dowolnym widoku, dopasowując tekst w polu wyszukiwania na poziomie globalnym lub wybierając jeden ze wstępnie zdefiniowanych filtrów. W dowolnym momencie można uruchomić dowolny wybór testów. Wyniki przebiegu testu są natychmiast widoczne na pasku przebiegu/niepowodzenia w górnej części okna eksploratora. Szczegóły wyniku metody badania są wyświetlane po wybraniu testu.

### <a name="run-and-view-tests"></a>Uruchamianie i wyświetlanie testów

Pasek narzędzi **Eksploratora testów** ułatwia odnajdywanie, organizowanie i uruchamianie zainteresowanych testów.

::: moniker range="vs-2017"
![Uruchamianie testów z paska narzędzi Eksploratora testów](../test/media/ute_toolbar.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Uruchamianie testów z paska narzędzi Eksploratora testów](../test/media/vs-2019/test-explorer-toolbar-diagram-16-2.png)
::: moniker-end

Można wybrać **uruchom wszystkie** testy, lub **wybierz** uruchom, aby wybrać podzbiór testów do uruchomienia. Wybierz test, aby wyświetlić szczegóły tego testu w okienku szczegółów testu. Wybierz **polecenie Otwórz test** z menu po kliknięciu prawym przyciskiem myszy (Klawiatura: **F12),** aby wyświetlić kod źródłowy wybranego testu.

::: moniker range="vs-2017"

Jeśli poszczególne testy nie mają zależności, które uniemożliwiają ich uruchamianie w dowolnej kolejności, włącz równoległe wykonanie testu za pomocą ![Ute&#95;równoległości&#45;małe](../test/media/ute_parallelicon-small.png) na pasku narzędzi. Może to znacznie skrócić czas pracy wszystkich testów.

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli poszczególne testy nie mają żadnych zależności, które uniemożliwiają ich uruchamianie w dowolnej kolejności, włącz równoległe wykonanie testu w menu ustawień paska narzędzi. Może to znacznie skrócić czas pracy wszystkich testów.

::: moniker-end

### <a name="run-tests-after-every-build"></a>Uruchamianie testów po każdej kompilacji

::: moniker range="vs-2017"

|Button|Opis|
|-|-|
|![Uruchom po kompilacji](../test/media/ute_runafterbuild_btn.png)|Aby uruchomić testy jednostkowe po każdej kompilacji lokalnej, wybierz polecenie **Testuj** w standardowym menu, a następnie wybierz polecenie **Uruchom testy po kompilacji** na pasku narzędzi **Eksploratora testów.**|

> [!NOTE]
> Uruchamianie testów jednostkowych po każdej kompilacji wymaga programu Visual Studio 2017 Enterprise edition lub Visual Studio 2019. W programie Visual Studio 2019 funkcja jest dostępna w wersji Community i Professional, oprócz wersji Enterprise.

::: moniker-end

::: moniker range=">=vs-2019"

Aby uruchomić testy jednostkowe po każdej kompilacji lokalnej, otwórz ikonę ustawień na pasku narzędzi Eksploratora testów i wybierz pozycję **Uruchom testy po kompilacji**.

::: moniker-end

### <a name="filter-and-group-the-test-list"></a>Filtrowanie i grupowanie listy testów

Jeśli masz dużą liczbę testów, możesz wpisać w polu wyszukiwania **Eksploratora testów,** aby filtrować listę według określonego ciągu. Możesz ograniczyć zdarzenie filtru, wybierając z listy filtrów.

::: moniker range="vs-2017"
![Kategorie filtrów wyszukiwania](../test/media/ute_searchfilter.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Kategorie filtrów wyszukiwania](../test/media/vs-2019/test-explorer-search-filter-16-2.png)
::: moniker-end

|Button|Opis|
|-|-|
|![Przycisk Grupy Eksploratora testów](../test/media/ute_groupby_btn.png)|Aby pogrupować testy według kategorii, wybierz przycisk **Grupuj według.**|

Aby uzyskać więcej informacji, zobacz [Uruchamianie testów jednostkowych za pomocą Eksploratora testów](../test/run-unit-tests-with-test-explorer.md).

## <a name="qa"></a>Pytania i odpowiedzi

**Pyt.: Jak debugować testy jednostkowe?**

**Odp.:** Użyj **Eksploratora testów,** aby rozpocząć sesję debugowania dla testów. Krok po kroku kodu z debugerem visual studio bezproblemowo zabierze Cię tam iz powrotem między testów jednostkowych i projektu w ramach testu. Aby rozpocząć debugowanie:

1. W edytorze Visual Studio ustaw punkt przerwania w co najmniej jednej metod testowania, które chcesz debugować.

    > [!NOTE]
    > Ponieważ metody testowe można uruchomić w dowolnej kolejności, ustawić punkty przerwania we wszystkich metodach testowych, które chcesz debugować.

2. W **Eksploratorze testów**wybierz metody testowe, a następnie wybierz polecenie **Debugowanie wybranych testów** z menu skrótów.

Dowiedz się więcej szczegółów na temat [debugowania testów jednostkowych](../debugger/debugger-feature-tour.md).

**Pyt.: Jeśli używam TDD, jak wygenerować kod z moich testów?**

**Odp.:** Użyj szybkich akcji do generowania klas i metod w kodzie projektu. Napisz instrukcję w metodzie testowej, która wywołuje klasę lub metodę, którą chcesz wygenerować, a następnie otwórz żarówkę, która pojawia się pod błędem. Jeśli wywołanie jest konstruktorem nowej klasy, wybierz **pozycję Generuj typ** z menu i postępuj zgodnie z kreatorem, aby wstawić klasę do projektu kodu. Jeśli wywołanie jest do metody, wybierz **opcję Generuj metodę** z menu IntelliSense.

::: moniker range="vs-2017"
![Generowanie menu szybkiego działania skrótu metody](../test/media/ute_generatemethodstubintellisense.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Generowanie menu szybkiego działania skrótu metody](../test/media/vs-2019/basics-generate-method-tdd.png)
::: moniker-end

**Pyt.: Czy można utworzyć testy jednostkowe, które przyjmują wiele zestawów danych jako dane wejściowe, aby uruchomić test?**

**Odpowiedź:** tak. *Oparte na danych metody testowe* umożliwiają testowanie zakresu wartości za pomocą metody badania pojedynczej jednostkowej. Użyj `DataSource` atrybutu dla metody testowej, która określa źródło danych i tabelę zawierającą wartości zmiennych, które chcesz przetestować.  W treści metody można przypisać wartości wierszy `TestContext.DataRow[`do zmiennych za pomocą indeksatora *ColumnName.* `]`

> [!NOTE]
> Te procedury mają zastosowanie tylko do metod testowych, które można zapisać przy użyciu struktury testów jednostkowych firmy Microsoft dla kodu zarządzanego. Jeśli używasz innej struktury, zapoznaj się z dokumentacją struktury dla równoważnych funkcji.

Załóżmy na przykład, że `CheckingAccount` dodajemy niepotrzebną metodę do klasy o nazwie `AddIntegerHelper`. `AddIntegerHelper`dodaje dwie liczby całkowite.

Aby utworzyć test oparty na `AddIntegerHelper` danych dla tej metody, najpierw tworzymy bazę `AddIntegerHelperData`danych programu Access o nazwie *AccountsTest.accdb* i tabelę o nazwie . Tabela `AddIntegerHelperData` definiuje kolumny, aby określić pierwszy i drugi operands dodawania i kolumny, aby określić oczekiwany wynik. Wypełniamy kilka wierszy odpowiednimi wartościami.

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

Przypisana metoda jest uruchamiana raz dla każdego wiersza w tabeli. **Eksplorator testów** zgłasza błąd testu dla metody, jeśli którakolwiek z iteracji nie powiedzie się. W okienku szczegółów wyników testu dla metody jest wyświetlana metoda stanu przebiegu/niepowodzenia dla każdego wiersza danych.

Dowiedz się więcej o [testach jednostkowych opartych na danych](../test/how-to-create-a-data-driven-unit-test.md).

**Pyt.: Czy mogę wyświetlić, jaka część mojego kodu jest testowana przez moje testy jednostkowe?**

**Odpowiedź:** tak. Można określić ilość kodu, który jest faktycznie testowany przez testy jednostkowe przy użyciu narzędzia pokrycia kodu programu Visual Studio w programie Visual Studio Enterprise. Języki macierzyste i zarządzane oraz wszystkie struktury testów jednostkowych, które mogą być uruchamiane przez jednostkową platformę testową, są obsługiwane.

Pokrycie kodu można uruchomić w wybranych testach lub na wszystkich testach w rozwiązaniu. Okno **Wyniki pokrycia kodu** wyświetla procent bloków kodu produktu, które zostały wykonywane przez wiersz, funkcję, klasę, obszar nazw i moduł.

Aby uruchomić pokrycie kodu dla metod testowych w rozwiązaniu, wybierz opcję **Testowanie** > **pokrycia kodu analizy dla wszystkich testów.**

Wyniki pokrycia są wyświetlane w oknie **Wyniki pokrycia kodu.**

![Wyniki pokrycia kodu](../test/media/ute_codecoverageresults.png)

Dowiedz się więcej o [pokryciu kodu](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) .

**Pyt.: Czy mogę przetestować metody w moim kodzie, które mają zależności zewnętrzne?**

**Odpowiedź:** tak. Jeśli masz visual studio enterprise, Microsoft Fakes mogą być używane z metodami testowymi, które można zapisać przy użyciu struktury testów jednostkowych dla kodu zarządzanego.

Microsoft Fakes używa dwóch podejść do tworzenia klas zastępczych dla zależności zewnętrznych:

1. *Wycinki* generują klasy zastępcze pochodzące z interfejsu nadrzędnego klasy zależności docelowej. Metody skrótowe można zastąpić publicznymi metodami wirtualnymi klasy docelowej.

2. *Podkładki* używają instrumentacji środowiska uruchomieniowego do przekazywania wywołań do metody docelowej do metody podkładki zastępczej dla metod niewirtualnych.

W obu podejściach można użyć wygenerowanych delegatów wywołań metody zależności, aby określić zachowanie, które chcesz w metodzie testowej.

Dowiedz się więcej o [izolowaniu metod testowania jednostek za pomocą programu Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).

**Pyt.: Czy można użyć innych jednostek testów struktury do tworzenia testów jednostkowych?**

**Odp.:** Tak, wykonaj następujące kroki, aby [znaleźć i zainstalować inne struktury](../test/install-third-party-unit-test-frameworks.md). Po ponownym uruchomieniu programu Visual Studio ponownie otwórz rozwiązanie, aby utworzyć testy jednostkowe, a następnie wybierz zainstalowane struktury w tym miejscu:

![Wybierz inną zainstalowaną strukturę testową jednostki](../test/media/createunittestsdialogextensions.png)

Odcinki testu jednostkowego zostaną utworzone przy użyciu wybranej struktury.
