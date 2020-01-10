---
title: Podstawy testów jednostkowych
ms.date: 08/07/2019
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateUnitTest
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e78b021e41caf584a74172cbdf00135e525df265
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590504"
---
# <a name="unit-test-basics"></a>Podstawowe informacje o teście jednostkowym

Sprawdź, czy kod działa zgodnie z oczekiwaniami, tworzenie i Uruchamianie testów jednostkowych. Jest to tzw. Testowanie jednostkowe, ponieważ należy podzielić funkcjonalność programu na dyskretne zachowania weryfikowalne, które można testować jako pojedyncze *jednostki*. Visual Studio Test Explorer umożliwia elastyczną i wydajną uruchomić testy jednostkowe i obejrzeć ich wyniki w programie Visual Studio. Program Visual Studio instaluje struktur dla kodu zarządzanego i natywnego testowania jednostkowego Microsoft. Użyj *struktury testów jednostkowych* , aby utworzyć testy jednostkowe, uruchomić je i zgłosić wyniki tych testów. Jednostka ponownie uruchom testy przy wprowadzaniu zmian do testowania, Twój kod nadal działa poprawnie. Visual Studio Enterprise można to zrobić automatycznie przy użyciu [Live Unit Testing](live-unit-testing-intro.md), który wykrywa testy, na które wpłynie zmiana kodu i uruchamia je w tle podczas wpisywania.

Testy jednostkowe ma największy wpływ na jakość kodu, gdy jest integralną częścią przepływu pracy tworzenia oprogramowania. Jak najszybciej pisania funkcji lub innych bloku kodu aplikacji, Utwórz testy jednostkowe, sprawdź zachowania kodu w odpowiedzi na standardowy, granic lub niepoprawny przypadki danych wejściowych, a, sprawdzanie jawnego lub niejawnego założenia przez kod. W przypadku *projektowania sterowanego testem*należy utworzyć testy jednostkowe przed zapisaniem kodu, więc należy użyć testów jednostkowych jako dokumentacji projektu i specyfikacji funkcjonalnych.

Można szybko wygenerować projekty testowe i metod testowych w kodzie lub ręcznie utworzyć testy, gdy ich potrzebujesz. Zapoznaj się z kodu platformy .NET przy użyciu funkcji IntelliTest, można generować dane testowe oraz pakiet testów jednostkowych. Dla każdej instrukcji w kodzie są generowane dane wejściowe testu, którymi instrukcja zostanie wykonana. Dowiedz się, jak [generować testy jednostkowe dla kodu](generate-unit-tests-for-your-code-with-intellitest.md).

Eksplorator testów można również uruchomić innych firm i open source, struktur testów jednostek, które zostały zaimplementowane interfejsy dodatek programu Test Explorer. Można dodać wiele z tych środowisk przy użyciu Menedżera rozszerzeń programu Visual Studio i galerii programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Instalowanie platform testów jednostkowych](../test/install-third-party-unit-test-frameworks.md)innych firm.

## <a name="get-started"></a>Wprowadzenie

Aby zapoznać się z wprowadzeniem do testów jednostkowych, które umożliwia przejście bezpośrednio do kodowania zobacz jeden z tych tematów:

- [Przewodnik: Tworzenie i uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)

- [Szybki Start: Programowanie sterowane testami za pomocą Eksploratora testów](../test/quick-start-test-driven-development-with-test-explorer.md)

- [Zapisz testy jednostkowe dla CC++ /w Visual Studio](../test/writing-unit-tests-for-c-cpp.md)

## <a name="the-mybank-solution-example"></a>Przykład rozwiązania MyBank

W tym artykule używamy tworzenia fikcyjnej aplikacji o nazwie `MyBank` jako przykładu. Nie musisz rzeczywisty kod, aby uprościć wyjaśnienia, w tym temacie. Metody testowe są napisane w języku C# i przedstawiane za pomocą Frameworka testów jednostkowych firmy Microsoft dla kodu zarządzanego. Jednakże pojęcia można łatwo przenosić do innych języków i struktur.

::: moniker range="vs-2017"
![Rozwiązanie MyBank](../test/media/ute_mybanksolution.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Rozwiązanie z banku 2019](../test/media/vs-2019/basics-mybank-solution.png)
::: moniker-end

Pierwsza próba zaprojektowania aplikacji `MyBank` obejmuje składnik konta, który reprezentuje pojedyncze konto i jego transakcje z bankiem, a składnik bazy danych, który reprezentuje funkcje do agregowania poszczególnych kont i zarządzania nimi.

Tworzymy `MyBank` rozwiązanie, które zawiera dwa projekty:

- `Accounts`

- `BankDb`

Nasza pierwsza próba projektowania projektu `Accounts` zawiera klasę, aby przechowywać podstawowe informacje o koncie, interfejs, który określa typowe funkcje dowolnego typu konta, takie jak kaucja i wycofanie zasobów z konta, oraz Klasa pochodna interfejsu, który reprezentuje konto sprawdzania. Zaczniemy projektów kont, tworząc następujące pliki źródłowe:

- *AccountInfo.cs* definiuje podstawowe informacje o koncie.

- *IAccount.cs* definiuje standardowy interfejs `IAccount` dla konta, w tym metody wnoszenia i wycofywania zasobów z konta oraz do pobierania salda konta.

- *CheckingAccount.cs* zawiera klasę `CheckingAccount`, która implementuje interfejs `IAccount` do sprawdzania konta.

Zdajemy sobie sprawę doświadczenia, że tego jednego rzeczą, jaką należy wykonać wycofania z konta rozliczeniowego, upewnij się, że wybierana kwota jest mniejsza niż saldo konta. Dlatego zastąpimy metodę `IAccount.Withdraw` w `CheckingAccount` za pomocą metody, która sprawdza ten warunek. Metoda może wyglądać następująco:

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

Teraz, gdy jakiś kod, nadszedł czas na testowanie.

## <a name="create-unit-test-projects-and-test-methods"></a>Tworzenie projektów testów jednostkowych i metod testowych

Często jest szybsze generowanie projektu testu jednostkowego i wycinków testów jednostkowych w kodzie. Lub możesz utworzyć projekt testów jednostkowych i testów ręcznie w zależności od wymagań. Jeśli chcesz utworzyć testy jednostkowe za pomocą struktury innej firmy, konieczne będzie zainstalowanie jednego z tych rozszerzeń: [nunit](https://marketplace.visualstudio.com/items?itemName=NUnitDevelopers.TestGeneratorNUnitextension-18371) lub [xUnit](https://marketplace.visualstudio.com/items?itemName=YowkoTsai.xUnitnetTestGenerator).

### <a name="generate-unit-test-project-and-unit-test-stubs"></a>Generowanie projektu testów jednostkowych i testów jednostkowych wycinków

1. W oknie Edytor kodu kliknij prawym przyciskiem myszy i wybierz polecenie [**Utwórz testy jednostkowe**](create-unit-tests-menu.md) z menu dostępnego po kliknięciu prawym przyciskiem myszy.

   ::: moniker range="vs-2017"
   ![W oknie edytora wyświetlić menu kontekstowe](../test/media/createunittestsrightclick.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![W oknie edytora wyświetlić menu kontekstowe](../test/media/vs-2019/basics-create-unit-tests.png)
   ::: moniker-end

   > [!NOTE]
   > Polecenie **Utwórz testy jednostkowe** jest dostępne tylko dla kodu zarządzanego, który jest przeznaczony dla .NET Framework (ale nie do programu .NET Core).

2. Kliknij przycisk **OK** , aby zaakceptować wartości domyślne, aby utworzyć testy jednostkowe, lub Zmień wartości używane do utworzenia i nazwy projektu testów jednostkowych i testów jednostkowych. Możesz wybrać kod, który jest domyślnie dodawany do metody testów jednostkowych.

   ![Okno dialogowe Tworzenie testów jednostkowych w programie Visual Studio](../test/media/create-unit-tests.png)

3. Wycinki kodu testu jednostki są tworzone w nowy projekt testu jednostki dla wszystkich metod w klasie.

   ::: moniker range="vs-2017"
   ![Testy jednostkowe są tworzone.](../test/media/createunittestsstubs.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Testy jednostkowe są tworzone.](../test/media/vs-2019/basics-test-stub.png)
   ::: moniker-end

4. Teraz przechodźmy, aby dowiedzieć się, jak [dodać kod do metod testów jednostkowych](#write-your-tests) , aby sprawdzić, czy test jednostkowy jest znaczący, i wszelkie dodatkowe testy jednostkowe, które można dodać w celu dokładnego przetestowania kodu.

### <a name="create-the-unit-test-project-and-unit-tests-manually"></a>Test jednostkowy projekt i testy jednostkowe ręczne tworzenie

Projekt testu jednostkowego zwykle odzwierciedla strukturę projektu pojedynczego kodu. W przykładzie z banku dodaje się dwa projekty testów jednostkowych o nazwie `AccountsTests` i `BankDbTests` do rozwiązania `MyBanks`. W nazwach projektów testów są dowolne, ale przyjęcie standardowej konwencji nazewnictwa jest dobrym pomysłem.

**Aby dodać projekt testu jednostkowego do rozwiązania:**

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie i wybierz polecenie **Dodaj** > **Nowy** **projekt**.

::: moniker range="vs-2017"

2. W oknie dialogowym **Nowy projekt** rozwiń węzeł **zainstalowany** , wybierz język, który ma być używany dla projektu testowego, a następnie wybierz polecenie **Testuj**.

3. Aby użyć jednej z platform testów jednostkowych firmy Microsoft, wybierz opcję **projekt testu jednostkowego** z listy szablonów projektu. W przeciwnym razie wybierz szablon projektu jednostki środowiskiem testowym, którego chcesz użyć. Aby przetestować `Accounts` projektu w naszym przykładzie, należy nazwać projekt `AccountsTests`.

   > [!NOTE]
   > Nie wszystkie platform testów jednostkowych innych firm i open source udostępniają szablon projektu Visual Studio. Zapoznaj się z dokumentem framework, aby uzyskać informacje o tworzeniu projektu.

::: moniker-end

::: moniker range=">=vs-2019"

2. Użyj pola wyszukiwania szablonu projektu, aby znaleźć szablon projektu testów jednostkowych dla środowiska testowego, którego chcesz użyć.

3. Na następnej stronie Nadaj projektowi nazwę. Aby przetestować `Accounts` projektu w naszym przykładzie, można nazwać projekt `AccountsTests`.

::: moniker-end

4. W projekcie testu jednostki Dodaj odwołanie do projektu kodu, w ramach badania, w tym przykładzie do projektu kont.

   Aby utworzyć odwołanie do projektu kodu:

   1. Wybierz projekt w **Eksplorator rozwiązań**.

   2. W menu **projekt** wybierz polecenie **Dodaj odwołanie**.

   3. W oknie dialogowym **Menedżer odwołań** Otwórz węzeł **rozwiązania** i wybierz pozycję **projekty**. Wybierz nazwę projektu kodu, a następnie zamknij okno dialogowe.

Każdy projekt testu jednostkowego zawiera klasy, które odzwierciedlają nazwy klasy w projekcie kodu. W naszym przykładzie projekt `AccountsTests` będzie zawierał następujące klasy:

- Klasa `AccountInfoTests` zawiera metody testów jednostkowych klasy `AccountInfo` w projekcie `Accounts`

- Klasa `CheckingAccountTests` zawiera metody testów jednostkowych klasy `CheckingAccount`.

## <a name="write-your-tests"></a>Pisania testów

Platformy, których używasz testów jednostkowych i funkcji IntelliSense Visual Studio poprowadzi Cię pisanie kodu dla testów jednostkowych dla projektu kodu. Aby uruchomić program w **Eksploratorze testów**, większość platform wymaga dodania określonych atrybutów do identyfikacji metod testów jednostkowych. Struktury umożliwiają także — zwykle za pomocą potwierdzenia instrukcji lub atrybuty metody, aby wskazać, czy metoda testowa został przekazany albo nie powiodło się. Inne atrybuty zidentyfikować metody Instalacja opcjonalna, znajdujących się podczas inicjowania klasy i przed każdej metody testowej, a metody usuwania, które są uruchamiane po każdej metody testowej, a przed klasa jest niszczona.

Wzorzec AAA (rozmieszczanie, Act, Asercja) jest typowy sposób pisania testów jednostkowych dla metody, w ramach testu.

- Sekcja **Rozmieoć** metody testów jednostkowych inicjuje obiekty i ustawia wartość danych, które są przesyłane do testowanej metody.

- Sekcja **Act** wywołuje badaną metodę przy użyciu uporządkowanych parametrów.

- Sekcja **Assert** sprawdza, czy akcja testowanej metody zachowuje się zgodnie z oczekiwaniami.

Aby przetestować metodę `CheckingAccount.Withdraw` w naszym przykładzie, możemy napisać dwa testy: jeden, który weryfikuje standardowe zachowanie metody, a drugi, który sprawdza, czy wycofanie więcej niż saldo zakończy się niepowodzeniem. W klasie `CheckingAccountTests` dodajemy następujące metody:

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

Aby uzyskać więcej informacji na temat struktur testów jednostek pochodzących od firmy Microsoft Zobacz jeden z następujących tematów:

- [Testowanie jednostkowe kodu](unit-test-your-code.md)

- [Pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md)

- [Używanie struktury MSTest w testach jednostkowych](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

## <a name="set-timeouts-for-unit-tests"></a>Ustawianie limitów czasu dla testów jednostkowych

Jeśli używasz platformy MSTest Framework, możesz użyć <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TimeoutAttribute>, aby ustawić limit czasu dla indywidualnej metody testowej:

```csharp
[TestMethod]
[Timeout(2000)]  // Milliseconds
public void My_Test()
{ ...
}
```

Aby ustawić maksymalny dozwolony limit czasu:

```csharp
[TestMethod]
[Timeout(TestTimeout.Infinite)]  // Milliseconds
public void My_Test ()
{ ...
}
```

## <a name="run-tests-in-test-explorer"></a>Uruchom testy w Eksploratorze testów

Podczas kompilowania projektu testowego, testy są wyświetlane w **Eksploratorze testów**. Jeśli **Eksplorator testów** nie jest widoczny, wybierz **Testuj** w menu programu Visual Studio, wybierz pozycję **Windows**, a następnie wybierz **Eksplorator testów**.

::: moniker range="vs-2017"
![Eksplorator testów jednostkowych](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Eksplorator testów jednostkowych](../test/media/vs-2019/basics-test-explorer.png)
::: moniker-end

Podczas uruchamiania, zapisywania i ponownego uruchamiania testów, **Eksplorator testów** może wyświetlać wyniki w grupach **testów zakończonych niepowodzeniem**, testów **zakończonych pomyślnie**, **pominiętych testów** i **nieuruchomionych testów**. Na pasku narzędzi można wybrać różne opcje grupowania.

Można również filtrować testy w dowolnym widoku, pasujący tekst w polu wyszukiwania na poziomie globalnym lub wybierając jeden z wstępnie zdefiniowanych filtrów. W dowolnym momencie można uruchomić żadnych ustawień testów. Wyniki przebiegu testu są natychmiast widoczny pasek Powodzenie/niepowodzenie u góry okna Eksploratora. Szczegóły wyniku metody testu są wyświetlane po wybraniu testu.

### <a name="run-and-view-tests"></a>Uruchom, aby wyświetlić testy

Pasek narzędzi **Eksploratora testów** pomaga odkrywać, organizować i uruchamiać testy, które Cię interesują.

::: moniker range="vs-2017"
![Uruchom testy z paska narzędzi Eksploratora testów](../test/media/ute_toolbar.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Uruchom testy z paska narzędzi Eksploratora testów](../test/media/vs-2019/test-explorer-toolbar-diagram-16-2.png)
::: moniker-end

Możesz wybrać opcję **Uruchom wszystkie** , aby uruchomić wszystkie testy, lub wybrać polecenie **Uruchom** , aby wybrać podzbiór testów do uruchomienia. Wybierz test, aby wyświetlić szczegóły tego testu w okienku Szczegóły testu. Wybierz **Otwórz test z menu dostępnego** po kliknięciu prawym przyciskiem myszy (klawiatura: **F12**), aby wyświetlić kod źródłowy wybranego testu.

::: moniker range="vs-2017"

Poszczególne testy nie ma żadnych zależności, które uniemożliwiają są uruchamiane w dowolnej kolejności, należy włączyć równoległe wykonywanie testów za pomocą ![WYKONAJ&#95;parallelicon&#45;małe](../test/media/ute_parallelicon-small.png) Przełącz przycisk na pasku narzędzi. Może to znacznie zmniejszyć czas poświęcony na uruchamianie wszystkich testów.

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli pojedyncze testy nie mają żadnych zależności, które uniemożliwiają ich uruchomienie w dowolnej kolejności, Włącz równoległe wykonywanie testów w menu Ustawienia na pasku narzędzi. Może to znacznie zmniejszyć czas poświęcony na uruchamianie wszystkich testów.

::: moniker-end

### <a name="run-tests-after-every-build"></a>Uruchamianie testów po każdej kompilacji

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

Jeśli masz dużą liczbę testów, możesz wpisać w polu wyszukiwania **Eksploratora testów** , aby odfiltrować listę według określonego ciągu. Można ograniczyć zdarzenia filtru więcej, wybierając z listy filtrów.

::: moniker range="vs-2017"
![Przeszukaj kategorie filtru](../test/media/ute_searchfilter.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Przeszukaj kategorie filtru](../test/media/vs-2019/test-explorer-search-filter-16-2.png)
::: moniker-end

|Przycisk|Opis|
|-|-|
|![Przycisk grupy Eksploratora testów](../test/media/ute_groupby_btn.png)|Aby zgrupować testy według kategorii, wybierz przycisk **Grupuj według** .|

Aby uzyskać więcej informacji, zobacz [Uruchamianie testów jednostkowych za pomocą Eksploratora testów](../test/run-unit-tests-with-test-explorer.md).

## <a name="qa"></a>PYTANIA I ODPOWIEDZI

**P: Jak mogę Debuguj testy jednostkowe?**

Odp **.:** Użyj **Eksploratora testów** , aby rozpocząć sesję debugowania dla testów. Krokowe wykonywanie kodu za pomocą debugera programu Visual Studio bezproblemowe przejście i z powrotem między testami jednostek a testowanego projektu. Aby rozpocząć debugowanie:

1. W edytorze programu Visual Studio Ustaw punkt przerwania w metodach testów, które chcesz debugować.

    > [!NOTE]
    > Ponieważ metody testowe można uruchomić w dowolnej kolejności, ustaw punkty przerwania w wszystkich metodach testowych, które chcesz debugować.

2. W **Eksploratorze testów**wybierz metody testowe, a następnie wybierz **Debuguj wybrane testy** z menu skrótów.

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

Odp **.:** Opcję. *Metody testowe oparte na danych* umożliwiają przetestowanie zakresu wartości za pomocą pojedynczej metody testu jednostkowego. Użyj `DataSource` atrybutu dla metody testowej, która określa źródło danych i tabelę zawierającą wartości zmiennych, które chcesz przetestować.  W treści metody przypisujesz wartości wierszy do zmiennych przy użyciu indeksatora `TestContext.DataRow[`*columnname*`]`.

> [!NOTE]
> Te procedury dotyczą tylko metody testowe, które piszesz za pomocą środowiska testów jednostkowych Microsoft dla kodu zarządzanego. Jeśli używasz innej struktury, zajrzyj do dokumentacji framework równoważne funkcje.

Załóżmy na przykład, że dodajemy niezbędną metodę do klasy `CheckingAccount` o nazwie `AddIntegerHelper`. `AddIntegerHelper` dodaje dwie liczby całkowite.

Aby utworzyć Test oparty na danych dla metody `AddIntegerHelper`, należy najpierw utworzyć bazę danych Access o nazwie *AccountsTest. accdb* oraz tabelę o nazwie `AddIntegerHelperData`. Tabela `AddIntegerHelperData` definiuje kolumny, aby określić pierwszy i drugi operandy dodawania i kolumny, aby określić oczekiwany wynik. Firma Microsoft Podaj liczbę wierszy odpowiednimi wartościami.

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

Metoda opartego na atrybutach jest uruchamiane jeden raz dla każdego wiersza w tabeli. **Eksplorator testów** zgłasza niepowodzenie testu dla metody, jeśli którykolwiek z iteracji zakończy się niepowodzeniem. W okienku szczegółów wyników testów dla metody zawiera metodę stanu Powodzenie/Niepowodzenie dla każdego wiersza danych.

Dowiedz się więcej o [testach jednostkowych opartych na danych](../test/how-to-create-a-data-driven-unit-test.md).

**P: Czy mogę sprawdzić, jaka część mojego kodu jest testowana przez testy jednostkowe?**

Odp **.:** Opcję. Można określić ilość kodu, który jest faktycznie testowany przez testy jednostkowe za pomocą narzędzia pokrycia kodu w programie Visual Studio w Visual Studio Enterprise. Języki macierzystymi i zarządzanymi i wszystkich platform testów jednostkowych, które mogą być uruchamiane przez strukturę testu jednostki są obsługiwane.

Można uruchomić pokrycie kodów w wybranych testach albo we wszystkich testach w rozwiązaniu. Okno **wyniki pokrycia kodu** przedstawia wartość procentową bloków kodu produktu, które były wykonywane przez wiersz, funkcję, klasę, przestrzeń nazw i moduł.

Aby uruchomić pokrycie kodu dla metod testowych w rozwiązaniu, wybierz **test** > **analizować pokrycie kodu dla wszystkich testów**.

Wyniki pokrycia są wyświetlane w oknie **wyników pokrycia kodu** .

![Wyniki pokrycia kodu](../test/media/ute_codecoverageresults.png)

Dowiedz się więcej o [pokryciu kodu](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) .

**P: Czy można testować metody w moim kodzie, który ma zależności zewnętrzne?**

Odp **.:** Opcję. Jeśli masz program Visual Studio Enterprise, Microsoft Fakes może służyć za pomocą metody testowe, które należy zapisać przy użyciu struktur testów jednostek dla kodu zarządzanego.

Microsoft Fakes używa dwa podejścia do tworzenia klas zastępczych dla zależności zewnętrznych:

1. *Refragmenty* generują klasy zastępcze pochodne od interfejsu nadrzędnego docelowej klasy zależności. Można zastąpić metody klasy zastępczej dla publicznej metody wirtualne klasy docelowej.

2. *Podkładki* korzystają z Instrumentacji środowiska uruchomieniowego, aby przekierować wywołania do metody docelowej do zastępczej metody podkładek dla metod niewirtualnych.

W obu metod użyjesz wygenerowanego delegatów wywołania metody zależności do określania zachowania, który ma w metodzie testowej.

Dowiedz się więcej [na temat izolowania metod testów jednostkowych za pomocą](../test/isolating-code-under-test-with-microsoft-fakes.md)elementów sztucznych firmy Microsoft.

**P: Czy można używać innych platform testów jednostkowych do tworzenia testów jednostkowych?**

Odp **.:** Tak, wykonaj następujące kroki, aby [znaleźć i zainstalować inne platformy](../test/install-third-party-unit-test-frameworks.md). Po ponownym uruchomieniu programu Visual Studio ponownie otwórz rozwiązanie do utworzenia testów jednostkowych, a następnie wybierz zainstalowany struktur w tym miejscu:

![Wybierz inne zainstalowane testów jednostkowych](../test/media/createunittestsdialogextensions.png)

Twoje wycinków testu jednostki zostanie utworzony za pomocą wybranej platformy.
