---
title: Tworzenie i Uruchamianie testów jednostkowych dla kodu zarządzanego
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
author: gewarren
ms.openlocfilehash: 130cb83e078a0f7c2924349dcd13692d3fe9125a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924603"
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>Przewodnik: Tworzenie i Uruchamianie testów jednostkowych dla kodu zarządzanego

Ten artykuł przeprowadzi Cię przez tworzenie, uruchamianie, i dostosowywać serie jednostek testów za pomocą środowiska testów jednostkowych Microsoft dla kodu zarządzanego i programu Visual Studio **Eksploratora testów**. Rozpocznij z projektu języka C#, który jest w fazie projektowania, tworzy testy, które wykonują kod, uruchom testy i bada wyniki. Następnie można zmienić kodu projektu i ponownie uruchom testy.

> [!NOTE]
> W tym instruktażu wykorzystano środowisko testów jednostkowych Microsoft dla kodu zarządzanego. **Eksplorator testów** można również uruchomić testy z innej struktury testów, która posiada adaptery dla **Eksploratora testów**. Aby uzyskać więcej informacji, zobacz [instalowanie platform testów jednostkowych innych firm](../test/install-third-party-unit-test-frameworks.md)

Aby uzyskać informacje o sposobach uruchamiania testów z wiersza polecenia, zobacz [opcje wiersza poleceń VSTest.Console.exe](vstest-console-options.md).

## <a name="prerequisites"></a>Wymagania wstępne

- Projekt o nazwie Bank. Zobacz [przykładowy projekt dotyczący tworzenia testów jednostkowych](../test/sample-project-for-creating-unit-tests.md).

## <a name="create-a-project-to-test"></a>Utwórz projekt do przetestowania

1. Otwórz program Visual Studio.

2. Na **pliku** menu, wybierz opcję **New** > **projektu**.

   **Nowy projekt** pojawi się okno dialogowe.

3. W obszarze **zainstalowane szablony**, kliknij przycisk **Visual C#**.

4. Na liście typów aplikacji, kliknij **biblioteki klas**.

5. W **nazwa** wpisz **Bank** a następnie kliknij przycisk **OK**.

   Nowy projekt o nazwie Bank jest tworzone i wyświetlane w **Eksploratora rozwiązań** z *Class1.cs* plik jest otwarty w edytorze kodu.

   > [!NOTE]
   > Jeśli *Class1.cs* nie jest otwarty w edytorze kodu, kliknij dwukrotnie plik *Class1.cs* w **Eksploratora rozwiązań** aby go otworzyć.

6. Skopiuj kod źródłowy z [przykładowy projekt dotyczący tworzenia testów jednostkowych](../test/sample-project-for-creating-unit-tests.md)i Zamień oryginalną zawartość *Class1.cs* skopiowany kod.

7. Zapisz plik jako *BankAccount.cs*.

8. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

Masz teraz projekt o nazwie Bank. Zawiera on kod źródłowy do testowania i narzędzia do testowania go. Przestrzeń nazw dla banku, BankAccountNS, zawiera klasę publiczną BankAccount, której metody należy testować w poniższych procedurach.

W tym artykule testy skoncentrować się na metodzie debetowej. Metoda jest wywoływana gdy pieniądze są wybierane z konta usługi. Poniżej przedstawiono definicję metody:

```csharp
// Method to be tested.
public void Debit(double amount)
{
    if(amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount");
    }
    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount");
    }
    m_balance += amount;
}
```

## <a name="create-a-unit-test-project"></a>Tworzenie projektu testu jednostkowego

1. Na **pliku** menu, wybierz opcję **Dodaj** > **nowy projekt**.

2. W **nowy projekt** okna dialogowego rozwiń **zainstalowane**, rozwiń węzeł **Visual C#**, a następnie wybierz **testu**.

3. Z listy szablonów wybierz **projektu testu jednostkowego**.

4. W **nazwa** wprowadź `BankTests`, a następnie wybierz pozycję **OK**.

   **BankTests** projekt jest dodawany do **Bank** rozwiązania.

5. W **BankTests** projektu, Dodaj odwołanie do **Bank** projektu.

   W **Eksploratora rozwiązań**, wybierz opcję **odwołania** w **BankTests** projektu, a następnie wybierz **Dodaj odwołanie** z menu podręcznego.

6. W **Menadżer odwołań** okna dialogowego rozwiń **rozwiązania** , a następnie sprawdź **Bank** elementu.

## <a name="create-the-test-class"></a>Utwórz klasę testową

Tworzenie klasy testowej, aby sprawdzić `BankAccount` klasy. Możesz użyć *UnitTest1.cs* pliku, który został wygenerowany przez szablon projektu, ale nadaj plikowi i klasie bardziej opisowe nazwy. Możesz to zrobić w jednym kroku, zmiana nazwy pliku w **Eksploratora rozwiązań**.

### <a name="rename-a-class-file"></a>Zmień nazwę pliku klasy

W **Eksploratora rozwiązań**, wybierz opcję *UnitTest1.cs* plik z projektu BankTests. Z menu kliknij prawym przyciskiem myszy, wybierz **Zmień nazwę**, a następnie zmień nazwę pliku do *BankAccountTests.cs*. Wybierz **tak** w oknie dialogowym z pytaniem, jeśli chcesz zmienić wszystkie odwołania do elementu kodu `UnitTest1` w projekcie.

Ten krok zmienia nazwę klasy, która ma `BankAccountTests`. *BankAccountTests.cs* plik zawiera teraz następujący kod:

```csharp
using System;
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace BankTests
{
    [TestClass]
    public class BankAccountTests
    {
        [TestMethod]
        public void TestMethod1()
        {
        }
    }
}
```

### <a name="add-a-using-statement-to-the-project-under-test"></a>Dodaj instrukcję using instrukcji do testowanego projektu

Można również dodać `using` instrukcji do klasy, aby mieć możliwość wywołania testowanego projektu bez użycia w pełni kwalifikowanych nazw. W górnej części pliku klasy należy dodać:

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a>Wymagania klasy testowej

Minimalne wymagania dla klasy testowej są następujące:

- `[TestClass]` Atrybut jest wymagany w jednostce Microsoft struktury testowania dla zarządzanego kodu, dla każdej klasy, która zawiera metody testów jednostkowych, które chcesz uruchomić w Eksploratorze testów.

- Każdej metody testowej, który Eksploratora testów do uruchomienia musi mieć `[TestMethod]` atrybutu.

Może mieć inne klasy projekt testów jednostkowych, które nie mają `[TestClass]` atrybut, na które może mieć innych metod w klasach testowych, które nie mają `[TestMethod]` atrybutu. Te klasy i metody można użyć w swoich metod testowych.

## <a name="create-the-first-test-method"></a>Tworzenie pierwszej metody testowej

W tej procedurze przedstawiono tworzenie metody, aby sprawdzić zachowanie testów jednostkowych `Debit` metody `BankAccount` klasy. `Debit` Metoda jest przedstawionych wcześniej w tym artykule.

Istnieją przynajmniej trzy zachowania, które muszą być sprawdzone:

- Metoda zgłasza <xref:System.ArgumentOutOfRangeException> Jeśli kwota debet jest większa niż saldo.

- Metoda zgłasza <xref:System.ArgumentOutOfRangeException> Jeśli kwota debet jest mniejsza niż zero.

- Jeśli kwota debet jest prawidłowy, metoda odejmuje kwotę debetowej od salda konta.

> [!TIP]
> Można usunąć domyślnego `TestMethod1` metody, ponieważ nie będzie go używać w tym przewodniku.

### <a name="to-create-a-test-method"></a>Aby utworzyć metodę testową

Pierwszy test sprawdza, czy prawidłową kwotę (oznacza to, że jeden, która jest mniejsza niż saldo konta i większa od zera) powoduje wybranie poprawnej ilości z konta. Dodaj następującą metodę do tego `BankAccountTests` klasy:

```csharp
[TestMethod]
public void Debit_WithValidAmount_UpdatesBalance()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 4.55;
    double expected = 7.44;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert
    double actual = account.Balance;
    Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");
}
```

Ta metoda jest prosta: Konfiguruje nowy `BankAccount` obiektu z saldem, a następnie wycofa prawidłową kwotę. Używa ona <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> metodę, aby sprawdzić, czy saldo końcowe jest zgodne z oczekiwaniami.

### <a name="test-method-requirements"></a>Wymagania metod testowych

Metoda testowa musi spełniać następujące wymagania:

- Ma ona `[TestMethod]` atrybutu.

- Zwraca `void`.

- Go nie może mieć parametrów.

## <a name="build-and-run-the-test"></a>Kompilowanie i uruchamianie testu

1. Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.

   Jeśli nie ma żadnych błędów **Eksplorator testów** pojawia się z **Debit_WithValidAmount_UpdatesBalance** na liście **testy nieuruchamiane** grupy.

   > [!TIP]
   > Jeśli **Eksplorator testów** nie jest wyświetlana po pomyślnej kompilacji, wybierz **testu** menu, kliknij **Windows**, a następnie wybierz **Eksplorator testów**.

2. Wybierz **Uruchom wszystkie** do uruchomienia testu. Gdy test jest uruchomiony, pasek stanu u góry okna jest animowany. Na końcu przebiegu testowego pasek zmieni kolor zielony, jeśli wszystkie metody testowe zakończy się pomyślnie lub czerwony Jeśli którykolwiek z testów nie powiedzie się.

3. W takim przypadku test kończy się niepowodzeniem. Metoda testowa jest przenoszona do **testy zakończone niepomyślnie** grupy. Wybierz metodę w **Eksplorator testów** Aby wyświetlić szczegóły u dołu okna.

## <a name="fix-your-code-and-rerun-your-tests"></a>Napraw kod i ponownego przeprowadzania testów

### <a name="analyze-the-test-results"></a>Analizuj wyniki testu

Wynik testu zawiera komunikat, który opisuje błąd. Dla `AreEqual` metody komunikat wyświetla co oczekiwano ( **oczekiwana\<*wartość* >**  parametr) i co zostało rzeczywiście przesłane ( **Rzeczywiste\<*wartość* >** parametru). Oczekiwano saldo, aby zmniejszyć, ale zamiast tego wzrosła o kwotę wycofania.

Test jednostkowy ma niewykrytych usterek: ilość wycofanie *dodano* do salda konta, a powinien znajdować *odejmować*.

### <a name="correct-the-bug"></a>Należy poprawić usterkę

Aby poprawić ten błąd, Zastąp wiersz:

```csharp
m_balance += amount;
```

Za pomocą:

```csharp
m_balance -= amount;
```

### <a name="rerun-the-test"></a>Uruchom ponownie test

W **Eksploratora testów**, wybierz **Uruchom wszystkie** do ponownego uruchomienia testu. Czerwony/zielony pasek zmieni kolor na zielony, aby wskazać, że test zakończył się powodzeniem, a test przenoszony jest do **testy zakończone powodzeniem** grupy.

## <a name="use-unit-tests-to-improve-your-code"></a>Użyj testów jednostkowych, aby poprawić kod

W tej sekcji opisano, jak proces iteracyjny analizy, tworzenie testów jednostkowych i Refaktoryzacja może pomóc zwiększyć kodu produkcyjnego, bardziej niezawodnego i skutecznego.

### <a name="analyze-the-issues"></a>Analizuj problemy

Utworzono metody testowej, aby upewnić się, że prawidłową kwotę jest prawidłowo odejmowana w `Debit` metody. Teraz, sprawdź, czy metoda zgłasza <xref:System.ArgumentOutOfRangeException> Jeśli kwota debet:

- większa niż saldo, lub
- mniejsza niż zero.

### <a name="create-the-test-methods"></a>Utwórz metody testowe

Utwórz metodę testową, aby zweryfikować poprawne zachowanie w sytuacji, gdy kwota debetowa jest mniejsza od zera:

```csharp
[TestMethod]
[ExpectedException(typeof(ArgumentOutOfRangeException))]
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = -100.00;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert is handled by the ExpectedException attribute on the test method.
}
```

Użyj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> atrybutu do potwierdzenia, że zgłoszono poprawny wyjątek. Atrybut powoduje, że test zakończył się niepowodzeniem, chyba że <xref:System.ArgumentOutOfRangeException> zgłaszany. Jeśli zmodyfikujesz tymczasowo testowaną metodę Aby zgłosić generyczny więcej wyjątek <xref:System.ApplicationException> gdy kwota debet jest mniejsza niż zero, test działa poprawnie&mdash;oznacza to, nie powiedzie się.

Aby przetestować przypadek, gdy wybierana kwota jest większa niż saldo, wykonaj następujące czynności:

1. Tworzenie nowej metody testowej, o nazwie `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`.

2. Skopiuj ciało metody z `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` do nowej metody.

3. Ustaw `debitAmount` na liczbę większą niż saldo.

### <a name="run-the-tests"></a>Uruchom testy

Uruchomione dwóch metod testowych pokazuje, czy testy działają poprawnie.

### <a name="continue-the-analysis"></a>Kontynuuj analizę

Ostatnie dwie metody testowe są jednak także trudne. Nie można mieć pewne uruchamiania tych testów, który warunek w testowanej metody zgłasza wyjątek. Jakiś sposób na rozróżnienie tych dwóch warunków będącego kwotą Debet ujemna ani większa niż saldo kwoty, zwiększyłaby zaufanie w testach.

Spójrz na testowaną metodę ponownie i zwróć uwagę, że obie instrukcje warunkowe używają `ArgumentOutOfRangeException` Konstruktor, który właśnie przyjmuje nazwę argumentu jako parametr:

```csharp
throw new ArgumentOutOfRangeException("amount");
```

Brak konstruktora można użyć, który zgłasza znacznie bogatsze informacje: <xref:System.ArgumentOutOfRangeException.%23ctor(System.String,System.Object,System.String)> zawiera nazwę argumentu, wartość argumentu i wiadomość zdefiniowanych przez użytkownika. Możesz refaktoryzować testowaną metodę Aby użyć tego konstruktora. Jeszcze lepiej służy publicznie dostępnych typów elementów członkowskich do określenia błędów.

### <a name="refactor-the-code-under-test"></a>Refaktoryzuj testowany kod

Najpierw należy zdefiniować dwie stałe dla komunikatów o błędach w zakresie klasy. Umieść je w klasie testowanej BankAccount:

```csharp
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount is less than zero";
```

Następnie należy zmodyfikować dwie instrukcje warunkowe w `Debit` metody:

```csharp
    if (amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);
    }

    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);
    }
```

### <a name="refactor-the-test-methods"></a>Refaktoryzuj metody testowe

Usuń `ExpectedException` atrybutu metody testowania i zamiast tego, przechwytujemy zgłoszony wyjątek i sprawdź skojarzone komunikat. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> Metoda zapewnia możliwość porównania dwóch ciągów.

Teraz `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` może wyglądać następująco:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
    }
}
```

### <a name="retest-rewrite-and-reanalyze"></a>Ponów test, przepisz i Analizuj ponownie

Przyjęto założenie, znajduje się błąd w metodzie, w ramach testu i `Debit` metoda nawet nie wyrzuca <xref:System.ArgumentOutOfRangeException>, nieważne danych wyjściowych prawidłowy komunikat z wyjątkiem. Obecnie metoda testowa nie obsługuje tej sprawy. Jeśli `debitAmount` wartość jest prawidłowa (czyli mniej niż saldo, ale większa od zera), żaden wyjątek nie jest przechwytywany, więc asercja nigdy nie jest uruchamiany. Jeszcze Metoda test kończy się powodzeniem. To nie jest dobry, ponieważ chcesz, aby testowanej metody, aby zakończyć się niepowodzeniem, jeśli jest zgłaszany żaden wyjątek.

Jest to błąd w metodzie testowej. Aby rozwiązać ten problem, należy dodać <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> asercja na koniec testowanej metody, aby obsłużyć przypadek, gdzie jest zgłaszany żaden wyjątek.

Ale ponownie uruchamiając test wskazuje, że test teraz *nie powiedzie się* Jeśli przechwytywany jest poprawny wyjątek. `catch` Bloku przechwytuje wyjątek, ale kontynuuje wykonywanie metody nie powiedzie się nową <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> potwierdzenia. Aby rozwiązać ten problem, należy dodać `return` instrukcji znajdującej się po `StringAssert` w `catch` bloku. Ponownie uruchamiając test potwierdza, że zostały rozwiązano ten problem. Ostateczna wersja `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` wygląda podobnie do następującego:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
        return;
    }

    Assert.Fail("The expected exception was not thrown.");
}
```

Ulepszenia do kodu testu, doprowadziła do bardziej niezawodnych i wartościowych metod testowych. Ale co ważniejsze, one również ulepszona, testowany kod.
