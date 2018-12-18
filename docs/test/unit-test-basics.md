---
title: Podstawowe informacje o teście jednostkowym
ms.date: 2016-01-07
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.CreateUnitTest
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dff6910f74b9a08a8064e4fb88828a21940c8ab9
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53053172"
---
# <a name="unit-test-basics"></a>Podstawowe informacje o teście jednostkowym

Sprawdź, czy kod działa zgodnie z oczekiwaniami, tworzenie i Uruchamianie testów jednostkowych. Jest to jednostka testowania, ponieważ możesz podzielić funkcjonalności programu, tworząc osobne sprawdzalnego działa zgodnie zachowań, które można przetestować jako indywidualne *jednostek*. Visual Studio Test Explorer umożliwia elastyczną i wydajną uruchomić testy jednostkowe i obejrzeć ich wyniki w programie Visual Studio. Program Visual Studio instaluje struktur dla kodu zarządzanego i natywnego testowania jednostkowego Microsoft. Użyj *testowania jednostkowego* Utwórz testy jednostkowe, uruchamiaj je i raportuje o wynikach tych testów. Jednostka ponownie uruchom testy przy wprowadzaniu zmian do testowania, Twój kod nadal działa poprawnie. Program Visual Studio Enterprise można to zrobić automatycznie za pomocą [Live Unit Testing](live-unit-testing-intro.md), który wykrywa testów, których dotyczą przez kod zmienia się i wykonuje na nich w tle podczas wpisywania.

Testy jednostkowe ma największy wpływ na jakość kodu, gdy jest integralną częścią przepływu pracy tworzenia oprogramowania. Jak najszybciej pisania funkcji lub innych bloku kodu aplikacji, Utwórz testy jednostkowe, sprawdź zachowania kodu w odpowiedzi na standardowy, granic lub niepoprawny przypadki danych wejściowych, a, sprawdzanie jawnego lub niejawnego założenia przez kod. Za pomocą *programowanie sterowane testami*, tworzenie testów jednostkowych, przed przystąpieniem do napisania kodu, więc użyć testów jednostkowych jako specyfikacji funkcjonalnych i dokumentacji projektu.

Można szybko wygenerować projekty testowe i metod testowych w kodzie lub ręcznie utworzyć testy, gdy ich potrzebujesz. Zapoznaj się z kodu platformy .NET przy użyciu funkcji IntelliTest, można generować dane testowe oraz pakiet testów jednostkowych. Dla każdej instrukcji w kodzie są generowane dane wejściowe testu, którymi instrukcja zostanie wykonana. Dowiedz się, jak [generowania testów jednostkowych dla kodu](generate-unit-tests-for-your-code-with-intellitest.md).

Eksplorator testów można również uruchomić innych firm i open source, struktur testów jednostek, które zostały zaimplementowane interfejsy dodatek programu Test Explorer. Można dodać wiele z tych środowisk przy użyciu Menedżera rozszerzeń programu Visual Studio i galerii programu Visual Studio. Zobacz [instalowanie platform testów jednostkowych innych firm](../test/install-third-party-unit-test-frameworks.md)

## <a name="get-started"></a>Wprowadzenie

Aby zapoznać się z wprowadzeniem do testów jednostkowych, które umożliwia przejście bezpośrednio do kodowania zobacz jeden z tych tematów:

- [Przewodnik: Tworzenie i Uruchamianie testów jednostkowych dla kodu zarządzanego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)

- [Szybki Start: Testów opartych na tworzenie aplikacji przy użyciu Eksploratora testów](../test/quick-start-test-driven-development-with-test-explorer.md)

- [Pisanie testów jednostkowych dla języka C/C++ w programie Visual Studio](../test/writing-unit-tests-for-c-cpp.md)

## <a name="the-mybank-solution-example"></a>Przykład rozwiązania MyBank

W tym temacie, użyjemy rozwoju fikcyjnej aplikacji o nazwie `MyBank` jako przykład. Nie musisz rzeczywisty kod, aby uprościć wyjaśnienia, w tym temacie. Metody testowe są napisane w języku C# i przedstawiane za pomocą Frameworka testów jednostkowych firmy Microsoft dla kodu zarządzanego. Jednakże pojęcia można łatwo przenosić do innych języków i struktur.

![Rozwiązanie MyBank](../test/media/ute_mybanksolution.png)

Nasze pierwsza próba zaprojektować `MyBank` aplikacja zawiera składnik kont, który reprezentuje pojedyncze konto i jego transakcji z Bankiem i składnik bazy danych, który reprezentuje funkcję agregacji i zarządzanie nimi indywidualne konta.

Utworzymy `MyBank` rozwiązanie, które zawiera dwa projekty:

- `Accounts`

- `BankDb`

Nasze pierwsza próba projektowania `Accounts` projekt zawiera klasę do przechowywania podstawowe informacje o koncie, interfejs, który określa typowych funkcji dowolnego typu konta, takie jak zdeponowanie i wycofania zasobów z konta i klasy pochodzi z interfejsu, który reprezentuje konto sprawdzanie. Zaczniemy projektów kont, tworząc następujące pliki źródłowe:

- *AccountInfo.cs* definiuje podstawowych informacji o koncie.

- *IAccount.cs* zdefiniowano standard `IAccount` interfejs dla konta, takie jak metody złożenia i wycofać zasoby z konta usługi i pobrać salda konta.

- *CheckingAccount.cs* zawiera `CheckingAccount` klasę, która implementuje `IAccount` interfejsu dla konta rozliczeniowego.

Zdajemy sobie sprawę doświadczenia, że tego jednego rzeczą, jaką należy wykonać wycofania z konta rozliczeniowego, upewnij się, że wybierana kwota jest mniejsza niż saldo konta. Dlatego firma Microsoft Zastąp `IAccount.Withdraw` method in Class metoda `CheckingAccount` z metodą, która sprawdza, czy dla tego warunku. Metoda może wyglądać następująco:

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

Teraz, gdy jakiś kod, nadszedł czas na testowanie.

## <a name="create-unit-test-projects-and-test-methods"></a>Tworzenie projektów testów jednostkowych i metod testowych

Często jest szybsze generowanie projektu testu jednostkowego i wycinków testów jednostkowych w kodzie. Lub możesz utworzyć projekt testów jednostkowych i testów ręcznie w zależności od wymagań.

### <a name="generate-unit-test-project-and-unit-test-stubs"></a>Generowanie projektu testów jednostkowych i testów jednostkowych wycinków

1. W oknie edytora kodu, kliknij prawym przyciskiem myszy i wybierz polecenie **Utwórz testy jednostkowe** z menu kontekstowego.

    ![W oknie edytora wyświetlić menu kontekstowe](../test/media/createunittestsrightclick.png)

2. Kliknij przycisk **OK** zaakceptować ustawienia domyślne, aby utworzyć testy jednostkowe lub zmienić wartości używane do tworzenia i nazwij projekt testów jednostkowych i testów jednostkowych. Możesz wybrać kod, który jest domyślnie dodawany do metody testów jednostkowych.

    ![Po prawej stronie&#45;kliknij w edytorze i wybierz polecenie Utwórz testy jednostkowe](../test/media/createunittestsdialog.png)

3. Wycinki kodu testu jednostki są tworzone w nowy projekt testu jednostki dla wszystkich metod w klasie.

    ![Testy jednostkowe są tworzone.](../test/media/createunittestsstubs.png)

4. Teraz przejdź od razu, aby dowiedzieć się, jak [Dodaj kod do metody testów jednostkowych](#write-your-tests) istotnych testu jednostkowego i wszelkie testy jednostkowe dodatkowe, które możesz zechcieć dodać do dokładnego przetestowania kodu.

### <a name="create-the-unit-test-project-and-unit-tests-manually"></a>Test jednostkowy projekt i testy jednostkowe ręczne tworzenie

Projekt testu jednostkowego zwykle odzwierciedla strukturę projektu pojedynczego kodu. W tym przykładzie MyBank Dodaj dwa projekty testów jednostkowych, o nazwie `AccountsTests` i `BankDbTests` do `MyBanks` rozwiązania. W nazwach projektów testów są dowolne, ale przyjęcie standardowej konwencji nazewnictwa jest dobrym pomysłem.

**Aby dodać projekt testu jednostkowego do rozwiązania:**

1. Na **pliku** menu, wybierz **New** , a następnie wybierz **projektu** (klawiatura **Ctrl**+**Shift** + **N**).

2. Na **nowy projekt** okna dialogowego rozwiń **zainstalowane** węzła, wybierz język, którego chcesz użyć dla projektu testowego, a następnie wybierz **testu**.

3. Aby użyć jednego z platform testów jednostkowych firmy Microsoft, wybierz opcję **projektu testu jednostkowego** z listy szablonów projektu. W przeciwnym razie wybierz szablon projektu jednostki środowiskiem testowym, którego chcesz użyć. Aby przetestować `Accounts` projekt naszego przykładu, czy nazwa projektu `AccountsTests`.

   > [!WARNING]
   > Nie wszystkie platform testów jednostkowych innych firm i open source udostępniają szablon projektu Visual Studio. Zapoznaj się z dokumentem framework, aby uzyskać informacje o tworzeniu projektu.

4. W projekcie testu jednostki Dodaj odwołanie do projektu kodu, w ramach badania, w tym przykładzie do projektu kont.

   Aby utworzyć odwołanie do projektu kodu:

   1.  Wybierz projekt w **Eksploratora rozwiązań**.

   2.  Na **projektu** menu, wybierz **Dodaj odwołanie**.

   3.  Na **Menadżer odwołań** po otwarciu okna dialogowego **rozwiązania** węzeł i wybierz polecenie **projektów**. Wybierz nazwę projektu kodu, a następnie zamknij okno dialogowe.

Każdy projekt testu jednostkowego zawiera klasy, które odzwierciedlają nazwy klasy w projekcie kodu. W naszym przykładzie `AccountsTests` projekt będzie zawierać następujące klasy:

-   `AccountInfoTests` Klasa zawiera metody testów jednostkowych dla `AccountInfo` klasy w `Accounts` projektu

-   `CheckingAccountTests` Klasa zawiera metody testów jednostkowych dla `CheckingAccount` klasy.

## <a name="write-your-tests"></a>Pisania testów

Platformy, których używasz testów jednostkowych i funkcji IntelliSense Visual Studio poprowadzi Cię pisanie kodu dla testów jednostkowych dla projektu kodu. Do uruchomienia w **Eksploratora testów**, większość struktur wymagają, aby dodać określone atrybuty, które identyfikują jednostkę metod testowych. Struktury umożliwiają także — zwykle za pomocą potwierdzenia instrukcji lub atrybuty metody, aby wskazać, czy metoda testowa został przekazany albo nie powiodło się. Inne atrybuty zidentyfikować metody Instalacja opcjonalna, znajdujących się podczas inicjowania klasy i przed każdej metody testowej, a metody usuwania, które są uruchamiane po każdej metody testowej, a przed klasa jest niszczona.

Wzorzec AAA (rozmieszczanie, Act, Asercja) jest typowy sposób pisania testów jednostkowych dla metody, w ramach testu.

- **Rozmieść** sekcji metodę testu jednostkowego inicjuje obiektów i ustawia wartość danych, który jest przekazywany do metody w ramach testu.

- **Act** sekcji wywołuje metodę w ramach testu z parametrami ułożonymi.

- **Asercja** sekcji sprawdza, czy akcja testowaną metodę zachowuje się zgodnie z oczekiwaniami.

Aby przetestować `CheckingAccount.Withdraw` metody w naszym przykładzie, możemy napisać dwóch testów: taki, który sprawdza standardowe zachowanie metody oraz jedna, która sprawdza się, że cofnięcie większa niż saldo zakończy się niepowodzeniem. W `CheckingAccountTests` klasy, możemy dodać następujących metod:

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

Należy pamiętać, że `Withdraw_ValidAmount_ChangesBalance` używa jawnego `Assert` instrukcję, aby ustalić, czy metoda testowa przekazuje lub nie powiedzie się, gdy `Withdraw_AmountMoreThanBalance_Throws` używa `ExpectedException` atrybutu do ustalenia powodzenia metody testowej. Dzieje się w tle środowiska testów jednostkowych opakowuje metod testowych w instrukcjach bloku try/catch. W większości przypadków gdy wystąpił wyjątek testowana metoda kończy się niepowodzeniem, a wyjątek jest ignorowany. `ExpectedException` Atrybutu powoduje, że metoda testowa do przekazywania, jeśli określony wyjątek zostanie zgłoszony.

Aby uzyskać więcej informacji na temat struktur testów jednostek pochodzących od firmy Microsoft Zobacz jeden z następujących tematów:

-   [Kod testu jednostkowego](unit-test-your-code.md)

-   [Pisanie testów jednostkowych dla języka C/C++](writing-unit-tests-for-c-cpp.md)

-   [Użyj struktury MSTest w testach jednostkowych](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

## <a name="set-timeouts-for-unit-tests"></a>Ustawianie limitów czasu dla testów jednostkowych

Aby ustawić limit czasu dla metody testowej poszczególnych:

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

Podczas tworzenia projektu testowego, testy są wyświetlane w **Eksploratora testów**. Jeśli **Eksplorator testów** nie jest widoczny, wybierz **testu** menu programu Visual Studio, wybierz **Windows**, a następnie wybierz **Eksplorator testów**.

![Eksplorator testów jednostkowych](../test/media/ute_failedpassednotrunsummary.png)

Jak uruchomić, zapisać i ponownie uruchomić testy domyślny widok **Eksplorator testów** wyświetla wyniki w grupach **testy zakończone niepomyślnie**, **testy zakończone powodzeniem**, **pomijane Testy** i **Esty nieuruchamiane**. Możesz wybrać nagłówek grupy, aby otworzyć widok, który wyświetla wszystkie testy w tej grupie.

Można również filtrować testy w dowolnym widoku, pasujący tekst w polu wyszukiwania na poziomie globalnym lub wybierając jeden z wstępnie zdefiniowanych filtrów. W dowolnym momencie można uruchomić żadnych ustawień testów. Wyniki przebiegu testu są natychmiast widoczny pasek Powodzenie/niepowodzenie u góry okna Eksploratora. Szczegóły wyniku metody testu są wyświetlane po wybraniu testu.

### <a name="run-and-view-tests"></a>Uruchom, aby wyświetlić testy

**Eksplorator testów** narzędzi ułatwia odnajdywanie, organizowanie i uruchamiać testy, które Cię interesuje.

![Uruchom testy z paska narzędzi Eksploratora testów](../test/media/ute_toolbar.png)

Możesz wybrać **Uruchom wszystkie** Aby uruchomić wszystkie testy, lub wybierz **Uruchom** wybranie podzestawu testów do uruchomienia. Po uruchomieniu zestawu testów, podsumowanie przebiegu testu zostanie wyświetlony u dołu **Eksploratora testów** okna. Wybierz test, aby wyświetlić szczegóły tego testu w dolnym okienku. Wybierz **Otwórz Test** z menu kontekstowego (klawiatura: **F12**) aby wyświetlić kod źródłowy dla wybranych testów.

Poszczególne testy nie ma żadnych zależności, które uniemożliwiają są uruchamiane w dowolnej kolejności, należy włączyć równoległe wykonywanie testów za pomocą ![WYKONAJ&#95;parallelicon&#45;małe](../test/media/ute_parallelicon-small.png) Przełącz przycisk na pasku narzędzi. Może to znacznie zmniejszyć czas poświęcony na uruchamianie wszystkich testów.

### <a name="run-tests-after-every-build"></a>Uruchamianie testów po każdej kompilacji

> [!WARNING]
> Uruchamianie testów jednostek po każdej kompilacji jest obsługiwane tylko w programie Visual Studio Enterprise.

|Przycisk|Opis|
|-|-|
|![Uruchom po kompilacji](../test/media/ute_runafterbuild_btn.png)|Aby uruchomić testy jednostkowe po każdej kompilacji lokalnej, wybierz **testu** w menu standardowym, wybierz **Uruchom testy po kompilacji** na **Eksplorator testów** paska narzędzi.|

### <a name="filter-and-group-the-test-list"></a>Filtrowanie i grupowanie listy testów

Jeśli masz dużą liczbę testów, można wpisać **Eksplorator testów** polu wyszukiwania, aby filtrować listę według określonego ciągu. Można ograniczyć zdarzenia filtru więcej, wybierając z listy filtrów.

![Przeszukaj kategorie filtru](../test/media/ute_searchfilter.png)

|Przycisk|Opis|
|-|-|
|![Przycisk grupy Eksploratora testów](../test/media/ute_groupby_btn.png)|Do grupowania testów według kategorii, wybierz **Group By** przycisku.|

Aby uzyskać więcej informacji, zobacz [Uruchamianie testów jednostkowych w Eksploratorze testów](../test/run-unit-tests-with-test-explorer.md)

## <a name="qa"></a>PYTANIA I ODPOWIEDZI

**P: jak Debuguj testy jednostkowe?**

**Odp.:** użyj **Eksplorator testów** do uruchamiania sesji debugowania dla testów. Krokowe wykonywanie kodu za pomocą debugera programu Visual Studio bezproblemowe przejście i z powrotem między testami jednostek a testowanego projektu. Aby rozpocząć debugowanie:

1.  W edytorze programu Visual Studio Ustaw punkt przerwania w metodach testów, które chcesz debugować.

    > [!NOTE]
    > Ponieważ metody testowe można uruchomić w dowolnej kolejności, ustaw punkty przerwania w wszystkich metodach testowych, które chcesz debugować.

2.  W **Eksploratora testów**, wybierz metody badania, a następnie wybierz **Debuguj wybrane testy** z menu skrótów.

Dowiedz się więcej szczegółów o [debugowanie testów jednostkowych](../debugger/debugging-in-visual-studio.md).

**Pyt.: jeśli używam TDD, jak I generowanie kodu na podstawie moich testów?**

**Odp.:** wykorzystania IntelliSense do generowania klasy i metody w kodzie projektu. Napisze instrukcję w metodzie badania, która wywołuje klasy lub metody, która ma zostać wygenerowany, a następnie otwórz menu funkcji IntelliSense w wywołaniu. Jeśli wywołanie konstruktora dla nowej klasy, wybierz **Generuj nowy typ** menu i wykonaj polecenia kreatora, aby wstawić klasy w projekcie kodu. W przypadku wywołania do metody, wybierz **wygenerować nową metodę** menu funkcji IntelliSense.

![Generowanie Menu IntelliSense Stub — metoda](../test/media/ute_generatemethodstubintellisense.png)

**P: czy można utworzyć testów, które przyjmują wiele zestawów danych jako dane wejściowe, aby uruchomić test?**

**Odp.:** tak. *Metody testowe opartych na danych* pozwala testować zakres wartości z metodą testową pojedyncza jednostka. Użyj `DataSource` atrybut metody testowej, który określa źródło danych i tabelę, która zawiera wartości zmiennych, które mają zostać przetestowane.  W treści metody, przypisz wartości wierszy do zmiennych, przy użyciu `TestContext.DataRow[` *ColumnName* `]` indeksatora.

> [!NOTE]
> Te procedury dotyczą tylko metody testowe, które piszesz za pomocą środowiska testów jednostkowych Microsoft dla kodu zarządzanego. Jeśli używasz innej struktury, zajrzyj do dokumentacji framework równoważne funkcje.

Załóżmy na przykład, możemy dodać metodę niepotrzebne `CheckingAccount` klasę, która nosi nazwę `AddIntegerHelper`. `AddIntegerHelper` dodaje dwie liczby całkowite.

Aby utworzyć test opartych na danych `AddIntegerHelper` metody, należy najpierw utworzyć bazy danych programu Access, o nazwie *AccountsTest.accdb* i tabelę o nazwie `AddIntegerHelperData`. `AddIntegerHelperData` Tabela definiuje kolumny do określenia pierwszego i drugiego operandu dodanie i kolumn do określenia oczekiwanych wyników. Firma Microsoft Podaj liczbę wierszy odpowiednimi wartościami.

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

Metoda opartego na atrybutach jest uruchamiane jeden raz dla każdego wiersza w tabeli. **Eksplorator testów** zgłasza błąd testu dla metody, jeśli dowolny iteracje zakończy się niepowodzeniem. W okienku szczegółów wyników testów dla metody zawiera metodę stanu Powodzenie/Niepowodzenie dla każdego wiersza danych.

Dowiedz się więcej o [testów jednostkowych opartych na danych](../test/how-to-create-a-data-driven-unit-test.md).

**P: czy można wyświetlić jaka część mojego kodu jest testowana za Moje testy jednostkowe?**

**Odp.:** tak. Można określić ilość swój kod, który jest aktualnie testowany przez nasze testy jednostkowe za pomocą narzędzia pokrycia kodu programu Visual Studio. Języki macierzystymi i zarządzanymi i wszystkich platform testów jednostkowych, które mogą być uruchamiane przez strukturę testu jednostki są obsługiwane.

Można uruchomić pokrycie kodów w wybranych testach albo we wszystkich testach w rozwiązaniu. **Wyniki pokrycia kodu** okno wyświetla procent bloków kodu produktu, które były wykonywane przez wiersz, funkcji, klasy, przestrzeni nazw i moduł.

Aby uruchomić pokrycie kodu dla metod testowych w rozwiązaniu, wybierz **testy** menu programu Visual Studio, a następnie wybierz **analiza pokrycia kodu**.

Wyniki pokrycia są wyświetlane w **wyniki pokrycia kodu** okna.

![Wyniki pokrycia kodu](../test/media/ute_codecoverageresults.png)

Dowiedz się więcej o [pokrycia kodu](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) .

**P: czy mogę metod testowych w Mój kod, który ma zależności zewnętrznych?**

**Odp.:** tak. Jeśli masz program Visual Studio Enterprise, Microsoft Fakes może służyć za pomocą metody testowe, które należy zapisać przy użyciu struktur testów jednostek dla kodu zarządzanego.

Microsoft Fakes używa dwa podejścia do tworzenia klas zastępczych dla zależności zewnętrznych:

1.  *Wycinki* Generowanie klas zastępczych pochodzi od klasy docelowej zależności interfejs nadrzędny. Można zastąpić metody klasy zastępczej dla publicznej metody wirtualne klasy docelowej.

2.  *Podkładki* umożliwia kierowanie wywołań do metody docelowej, do metody podkładkę substytut dla metod niewirtualnych środowiska uruchomieniowego instrumentacji.

W obu metod użyjesz wygenerowanego delegatów wywołania metody zależności do określania zachowania, który ma w metodzie testowej.

Dowiedz się więcej o [izolowanie metody testów jednostkowych with Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).

**P: czy do tworzenia testów jednostkowych można używać innych struktur testów jednostek?**

**Odp.:** tak, wykonaj następujące kroki, aby [znajdować i instalować innych struktur](../test/install-third-party-unit-test-frameworks.md). Po ponownym uruchomieniu programu Visual Studio ponownie otwórz rozwiązanie do utworzenia testów jednostkowych, a następnie wybierz zainstalowany struktur w tym miejscu:

![Wybierz inne zainstalowane testów jednostkowych](../test/media/createunittestsdialogextensions.png)

Twoje wycinków testu jednostki zostanie utworzony za pomocą wybranej platformy.