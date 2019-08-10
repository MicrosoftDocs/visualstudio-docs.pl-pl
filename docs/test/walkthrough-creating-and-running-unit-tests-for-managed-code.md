---
title: C#Samouczek testów jednostkowych
ms.date: 05/14/2019
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
ms.openlocfilehash: 2c7a81eefc48626a57d15f99579e151390b52fb9
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926786"
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>Przewodnik: Tworzenie i uruchamianie testów jednostkowych dla kodu zarządzanego

Ten artykuł przeprowadzi Cię przez proces tworzenia, uruchamiania i dostosowywania serii testów jednostkowych przy użyciu struktury testów jednostkowych firmy Microsoft dla kodu zarządzanego i programu Visual Studio **Test Explorer**. Zacznij od C# projektu, który jest w fazie tworzenia, Twórz testy, które wykonują swój kod, uruchamiają testy i sprawdzają wyniki. Następnie należy zmienić kod projektu i ponownie uruchomić testy.

## <a name="create-a-project-to-test"></a>Utwórz projekt do przetestowania

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

2. W menu **plik** wybierz pozycję **Nowy** > **projekt**.

   **Nowy projekt** pojawi się okno dialogowe.

3. W kategorii **Visual C#**  > **.NET Core** wybierz szablon projektu **aplikacja konsoli (.NET Core)** .

4. Nadaj nazwę **bankowi**projektu, a następnie kliknij przycisk **OK**.

   Projekt banku zostanie utworzony i wyświetlony w **Eksplorator rozwiązań** z plikiem *program.cs* otwartym w edytorze kodu.

   > [!NOTE]
   > Jeśli *program.cs* nie jest otwarty w edytorze, kliknij dwukrotnie plik *program.cs* w **Eksplorator rozwiązań** , aby go otworzyć.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

2. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

3. Wyszukaj i wybierz C# szablon projektu **aplikacja konsoli (.NET Core)** , a następnie kliknij przycisk **dalej**.

4. Nadaj nazwę **bankowi**projektu, a następnie kliknij przycisk **Utwórz**.

   Projekt banku zostanie utworzony i wyświetlony w **Eksplorator rozwiązań** z plikiem *program.cs* otwartym w edytorze kodu.

   > [!NOTE]
   > Jeśli *program.cs* nie jest otwarty w edytorze, kliknij dwukrotnie plik *program.cs* w **Eksplorator rozwiązań** , aby go otworzyć.

::: moniker-end

5. Zastąp zawartość *program.cs* następującym C# kodem, który definiuje klasę, *BankAccount*:

   ```csharp
   using System;

   namespace BankAccountNS
   {
       /// <summary>
       /// Bank account demo class.
       /// </summary>
       public class BankAccount
       {
           private readonly string m_customerName;
           private double m_balance;

           private BankAccount() { }

           public BankAccount(string customerName, double balance)
           {
               m_customerName = customerName;
               m_balance = balance;
           }

           public string CustomerName
           {
               get { return m_customerName; }
           }

           public double Balance
           {
               get { return m_balance; }
           }

           public void Debit(double amount)
           {
               if (amount > m_balance)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               if (amount < 0)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               m_balance += amount; // intentionally incorrect code
           }

           public void Credit(double amount)
           {
               if (amount < 0)
               {
                   throw new ArgumentOutOfRangeException("amount");
               }

               m_balance += amount;
           }

           public static void Main()
           {
               BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);

               ba.Credit(5.77);
               ba.Debit(11.22);
               Console.WriteLine("Current balance is ${0}", ba.Balance);
           }
       }
   }
   ```

6. Zmień nazwę pliku na *BankAccount.cs* , klikając prawym przyciskiem myszy i wybierając polecenie **zmień nazwę** w **Eksplorator rozwiązań**.

7. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

Masz teraz projekt z metodami, które możesz przetestować. W tym artykule testy koncentrują się na `Debit` metodzie. `Debit` Metoda jest wywoływana w przypadku wycofania pieniędzy z konta.

## <a name="create-a-unit-test-project"></a>Tworzenie projektu testu jednostkowego

1. W menu **plik** wybierz pozycję **Dodaj** > **Nowy projekt**.

   > [!TIP]
   > Możesz również kliknąć prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** i wybrać polecenie **Dodaj** > **Nowy projekt**.

::: moniker range="vs-2017"

2. W oknie dialogowym **Nowy projekt** rozwiń węzeł **zainstalowane**, rozwiń pozycję **C#Wizualizacja**, a następnie wybierz pozycję **Testuj**.

3. Z listy szablonów wybierz pozycję **MSTest test Project (.NET Core)** .

4. W polu **Nazwa** wprowadź `BankTests`wartość, a następnie wybierz przycisk **OK**.

   Projekt **BankTests** jest dodawany do rozwiązania **bankowego** .

::: moniker-end

::: moniker range=">=vs-2019"

2. Wyszukaj i wybierz C# szablon projektu **projektu testowego MSTest (.NET Core)** , a następnie kliknij przycisk **dalej**.

3. Nazwij projekt **BankTests**.

4. Kliknij przycisk **Utwórz**.

   Projekt **BankTests** jest dodawany do rozwiązania **bankowego** .

::: moniker-end

5. W projekcie **BankTests** Dodaj odwołanie do projektu bankowego.

   W **Eksplorator rozwiązań**wybierz pozycję **zależności** w projekcie **BankTests** , a następnie wybierz pozycję **Dodaj odwołanie** z menu dostępnego po kliknięciu prawym przyciskiem myszy.

6. W oknie dialogowym **Menedżer odwołań** rozwiń węzeł **projekty**, wybierz pozycję **rozwiązanie**, a następnie sprawdź element **Bank** .

7. Wybierz **OK**.

## <a name="create-the-test-class"></a>Tworzenie klasy testowej

Utwórz klasę testową, aby zweryfikować `BankAccount` klasę. Możesz użyć pliku *UnitTest1.cs* , który został wygenerowany przez szablon projektu, ale Nadaj plikowi i klasy więcej nazw opisowych.

### <a name="rename-a-file-and-class"></a>Zmiana nazwy pliku i klasy

1. Aby zmienić nazwę pliku, w **Eksplorator rozwiązań**wybierz plik *UnitTest1.cs* w projekcie BankTests. W menu rozwijanym prawym przyciskiem myszy wybierz **Zmień nazwę**, a następnie zmień nazwę pliku na *BankAccountTests.cs*.

::: moniker range="vs-2017"

2. Aby zmienić nazwę klasy, wybierz pozycję **tak** w oknie dialogowym, które się pojawi i pyta, czy chcesz również zmienić nazwy odwołań do elementu kodu.

::: moniker-end

::: moniker range=">=vs-2019"

2. Aby zmienić nazwę klasy, umieść kursor `UnitTest1` w edytorze kodu, kliknij prawym przyciskiem myszy, a następnie wybierz **Zmień nazwę**. Wpisz w **BankAccountTests** , a następnie naciśnij klawisz **Enter**.

::: moniker-end

Plik *BankAccountTests.cs* zawiera teraz następujący kod:

```csharp
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

### <a name="add-a-using-statement"></a>Dodaj instrukcję using

Dodaj instrukcję do klasy testowej, aby umożliwić wywoływanie w badanym projekcie bez używania w pełni kwalifikowanych nazw. [ `using` ](/dotnet/csharp/language-reference/keywords/using-statement) W górnej części pliku klasy Dodaj:

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a>Wymagania dotyczące klasy testowej

Minimalne wymagania dotyczące klasy testowej to:

- Ten `[TestClass]` atrybut jest wymagany dla każdej klasy, która zawiera metody testów jednostkowych, które mają być uruchamiane w Eksploratorze testów.

- Każda metoda testowa, którą ma rozpoznać Eksplorator testów, musi mieć `[TestMethod]` atrybut.

Można mieć inne klasy w projekcie testów jednostkowych, które nie mają `[TestClass]` atrybutu, i można mieć inne metody w klasach testowych, które nie `[TestMethod]` mają atrybutu. Można wywołać te inne klasy i metody z metod testowych.

## <a name="create-the-first-test-method"></a>Utwórz pierwszą metodę testową

W tej procedurze należy napisać metody testów jednostkowych, aby zweryfikować zachowanie `Debit` metody `BankAccount` klasy.

Istnieją co najmniej trzy zachowania, które należy sprawdzić:

- Metoda zgłasza <xref:System.ArgumentOutOfRangeException> , czy kwota debetu jest większa niż saldo.

- Metoda zgłasza <xref:System.ArgumentOutOfRangeException> , czy kwota debetu jest mniejsza od zera.

- Jeśli kwota Debet jest prawidłowa, Metoda odejmuje kwotę debetu od salda konta.

> [!TIP]
> Możesz usunąć metodę domyślną `TestMethod1` , ponieważ nie będziesz jej używać w tym instruktażu.

### <a name="to-create-a-test-method"></a>Aby utworzyć metodę testową

Pierwszy test weryfikuje, czy prawidłowa kwota (czyli taka, która jest mniejsza niż saldo konta i większa od zera) odnosi poprawną kwotę z konta. Dodaj następującą metodę do tej `BankAccountTests` klasy:

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

Metoda jest prosta: konfiguruje nowy `BankAccount` obiekt z saldem początkowym, a następnie wycofuje prawidłową kwotę. Używa <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType> metody do sprawdzenia, czy saldo końcowe jest zgodnie z oczekiwaniami.

### <a name="test-method-requirements"></a>Wymagania metody testowej

Metoda testowa musi spełniać następujące wymagania:

- Jest on uzupełniony `[TestMethod]` atrybutem.

- Zwraca wartość `void`.

- Nie może mieć parametrów.

## <a name="build-and-run-the-test"></a>Kompiluj i uruchamiaj test

1. W menu **kompilacja** wybierz polecenie **Kompiluj rozwiązanie**.

2. Jeśli **Eksplorator testów** nie jest otwarty, otwórz go, wybierając pozycję **Testuj** > **Eksplorator testów** **systemu Windows** > z górnego paska menu.

3. Wybierz **Uruchom wszystkie** , aby uruchomić test.

   Podczas gdy test jest uruchomiony, pasek stanu w górnej części okna **Eksploratora testów** jest animowany. Na końcu przebiegu testu pasek zmieni kolor na zielony, jeśli wszystkie metody testowe są przekazywane lub czerwone, jeśli którykolwiek z testów zakończy się niepowodzeniem.

   W takim przypadku test kończy się niepowodzeniem.

4. Wybierz metodę w **Eksploratorze testów** , aby wyświetlić szczegóły w dolnej części okna.

## <a name="fix-your-code-and-rerun-your-tests"></a>Popraw kod i ponownie uruchom testy

Wynik testu zawiera komunikat, który opisuje błąd. W przypadku `AreEqual` metody komunikat wyświetla oczekiwane i co zostało faktycznie odebrane. Spodziewasz się, że saldo zostało zmniejszone, ale zwiększy się o kwotę wycofania.

Test jednostkowy nie wykrył usterki: ilość wycofania jest dodawana do salda konta, gdy należy ją *odjąć*.

### <a name="correct-the-bug"></a>Popraw usterkę

Aby poprawić błąd, w pliku *BankAccount.cs* Zastąp wiersz:

```csharp
m_balance += amount;
```

się

```csharp
m_balance -= amount;
```

### <a name="rerun-the-test"></a>Uruchom ponownie test

W **Eksploratorze testów**wybierz opcję **Uruchom wszystkie** , aby ponownie uruchomić test. Czerwony/zielony pasek zmieni kolor na zielony, aby wskazać, że test zakończono.

![Eksplorator testów w programie Visual Studio 2019 pokazujący zakończony test](media/test-explorer-banktests-passed.png)

## <a name="use-unit-tests-to-improve-your-code"></a>Korzystanie z testów jednostkowych w celu ulepszania kodu

W tej sekcji opisano, w jaki sposób iteracyjny proces analizy, opracowywanie testów jednostkowych i Refaktoryzacja może pomóc zwiększyć niezawodność i skuteczność kodu produkcyjnego.

### <a name="analyze-the-issues"></a>Analizowanie problemów

Utworzono metodę testową w celu potwierdzenia, że prawidłowa kwota jest prawidłowo odejmowana w `Debit` metodzie. Teraz sprawdź, czy metoda zgłasza <xref:System.ArgumentOutOfRangeException> , czy kwota debetu to:

- większe niż saldo lub
- mniejsze od zera.

### <a name="create-and-run-new-test-methods"></a>Utwórz i uruchom nowe metody testowe

Utwórz metodę testową, aby sprawdzić poprawność działania, gdy kwota debetu jest mniejsza od zera:

```csharp
[TestMethod]
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = -100.00;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act and assert
    Assert.ThrowsException<System.ArgumentOutOfRangeException>(() => account.Debit(debitAmount));
}
```

<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> Użyj metody w celu potwierdzenia, że został zgłoszony poprawny wyjątek. Ta metoda powoduje niepowodzenie testu, chyba że <xref:System.ArgumentOutOfRangeException> zostanie zgłoszony. W przypadku tymczasowej modyfikacji testowanej metody w celu wygenerowania bardziej <xref:System.ApplicationException> ogólnego, gdy kwota debetu jest mniejsza od zera, test działa prawidłowo&mdash;, czyli kończy się niepowodzeniem.

Aby przetestować przypadek, gdy wycofana ilość jest większa niż saldo, wykonaj następujące czynności:

1. Utwórz nową metodę testową o `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`nazwie.

2. Skopiuj treść metody z `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` do nowej metody.

3. Ustaw wartość `debitAmount` na wartość większą niż saldo.

Uruchamianie dwóch testów i sprawdzanie, czy są one przekazywane.

### <a name="continue-the-analysis"></a>Kontynuuj analizę

Testowana Metoda może zostać ulepszona. W bieżącej implementacji nie ma sposobu, aby wiedzieć, który warunek (`amount > m_balance` lub `amount < 0`) przeprowadził wyjątek podczas testu. Wiemy, że `ArgumentOutOfRangeException` został zgłoszony w metodzie. Lepszym rozwiązaniem jest określenie, który warunek w `BankAccount.Debit` wyniku zgłoszenia wyjątku (`amount > m_balance` lub `amount < 0`), dzięki czemu mamy pewność, że nasza metoda jest Sanity — sprawdzanie argumentów prawidłowo.

Sprawdź, czy metoda jest ponownie testowana`BankAccount.Debit`() i Zauważ, że obie instrukcje warunkowe `ArgumentOutOfRangeException` używają konstruktora, który po prostu przyjmuje nazwę argumentu jako parametr:

```csharp
throw new ArgumentOutOfRangeException("amount");
```

Istnieje Konstruktor, którego można użyć do zgłaszania szczegółowych informacji: <xref:System.ArgumentOutOfRangeException.%23ctor(System.String,System.Object,System.String)> zawiera nazwę argumentu, wartość argumentu i komunikat zdefiniowany przez użytkownika. Możesz użyć refaktoryzacji testowanej metody w celu użycia tego konstruktora. Jeszcze lepsze, możesz użyć dostępnych publicznie elementów typu, aby określić błędy.

### <a name="refactor-the-code-under-test"></a>Refaktoryzacja testowanego kodu

Najpierw Zdefiniuj dwie stałe dla komunikatów o błędach w zakresie klasy. Umieść je w testowanej klasie, `BankAccount`:

```csharp
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount is less than zero";
```

Następnie zmodyfikuj dwie instrukcje warunkowe w `Debit` metodzie:

```csharp
if (amount > m_balance)
{
    throw new System.ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);
}

if (amount < 0)
{
    throw new System.ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);
}
```

### <a name="refactor-the-test-methods"></a>Refaktoryzacja metod testowych

Refaktoryzacja metod testowych przez usunięcie wywołania do <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>. Zawiń wywołanie `Debit()` `try/catch` w bloku, Przechwyć określony wyjątek, który jest oczekiwany, i sprawdź jego skojarzony komunikat. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> Metoda zapewnia możliwość porównania dwóch ciągów.

`Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` Teraz może wyglądać następująco:

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
    catch (System.ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
    }
}
```

### <a name="retest-rewrite-and-reanalyze"></a>Ponowne testowanie, ponowne zapisywanie i ponowne analizowanie

Przyjęto założenie, że w testowanej metodzie występuje `Debit` błąd, a metoda nie <xref:System.ArgumentOutOfRangeException> generuje nawet danych wyjściowych z wyjątkiem. Obecnie metoda testowa nie obsługuje tego przypadku. `debitAmount` Jeśli wartość jest prawidłowa (to jest mniejsza niż saldo, ale większa od zera), żaden wyjątek nie jest przechwytywany, więc potwierdzenie nigdy nie zostanie wyzwolone. Jeszcze metoda testowa kończy się powodzeniem. Nie jest to dobre, ponieważ metoda testowa ma kończyć się niepowodzeniem, jeśli nie zostanie zgłoszony żaden wyjątek.

Jest to usterka w metodzie testowej. Aby rozwiązać ten problem, Dodaj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> potwierdzenie na końcu metody testowej, aby obsłużyć przypadek, w którym nie jest zgłaszany żaden wyjątek.

Ponownie uruchomienie testu pokazuje, że test zakończy *się niepowodzeniem* w przypadku przechwyconego poprawnego wyjątku. Blok przechwytuje wyjątek, ale metoda nadal jest wykonywana i kończy się niepowodzeniem z nowym <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> potwierdzeniem. `catch` Aby rozwiązać ten problem, należy dodać `return` instrukcję `StringAssert` po `catch` bloku. Ponowne uruchomienie testu potwierdza, że ten problem został rozwiązany. Końcowa wersja `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` wygląda następująco:

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
    catch (System.ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
        return;
    }

    Assert.Fail("The expected exception was not thrown.");
}
```

### <a name="conclusion"></a>Wniosek

Ulepszenia kodu testowego doprowadziły do bardziej niezawodnych i informacyjnych metod testowych. Ale co ważniejsze, poprawiły się także kod testowy.

> [!TIP]
> W tym przewodniku zastosowano środowisko testów jednostkowych firmy Microsoft dla kodu zarządzanego. **Eksplorator testów** może również uruchamiać testy z platform testów jednostkowych innych firm, które mają karty w **Eksploratorze testów**. Aby uzyskać więcej informacji, zobacz [instalowanie platform testów jednostkowych innych firm](../test/install-third-party-unit-test-frameworks.md).

## <a name="see-also"></a>Zobacz także

Aby uzyskać informacje o sposobach uruchamiania testów z wiersza polecenia, zobacz [Opcje wiersza polecenia VSTest. Console. exe](vstest-console-options.md).
