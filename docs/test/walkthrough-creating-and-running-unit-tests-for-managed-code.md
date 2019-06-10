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
ms.openlocfilehash: b04a8eabd5b7bdbc5053a30a95609b86b6e61674
ms.sourcegitcommit: 51dad3e11d7580567673e0d426ab3b0a17584319
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66820922"
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>Przewodnik: Tworzenie i uruchamianie testów jednostkowych dla kodu zarządzanego

Ten artykuł przeprowadzi Cię przez tworzenie, uruchamianie, i dostosowywać serie jednostek testów za pomocą środowiska testów jednostkowych Microsoft dla kodu zarządzanego i programu Visual Studio **Eksploratora testów**. Rozpocznij z projektu języka C#, który jest w fazie projektowania, tworzy testy, które wykonują kod, uruchom testy i bada wyniki. Następnie możesz zmienić kodu projektu i ponownie uruchom testy.

## <a name="create-a-project-to-test"></a>Utwórz projekt do przetestowania

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

2. Na **pliku** menu, wybierz opcję **New** > **projektu**.

   **Nowy projekt** pojawi się okno dialogowe.

3. W obszarze **Visual C#**  > **platformy .NET Core** kategorii, wybierz **Aplikacja konsoli (.NET Core)** szablonu projektu.

4. Nadaj projektowi nazwę **Bank**, a następnie kliknij przycisk **OK**.

   Projekt o nazwie Bank, jest tworzony i wyświetlany w **Eksploratora rozwiązań** z *Program.cs* plik jest otwarty w edytorze kodu.

   > [!NOTE]
   > Jeśli *Program.cs* nie jest otwarty w edytorze, kliknij dwukrotnie plik *Program.cs* w **Eksploratora rozwiązań** aby go otworzyć.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

2. W oknie rozpoczęcia wybierz **Utwórz nowy projekt**.

3. Wyszukaj i wybierz pozycję C# **Aplikacja konsoli (.NET Core)** projektu szablonu, a następnie kliknij przycisk **dalej**.

4. Nadaj projektowi nazwę **Bank**, a następnie kliknij przycisk **Utwórz**.

   Projekt o nazwie Bank, jest tworzony i wyświetlany w **Eksploratora rozwiązań** z *Program.cs* plik jest otwarty w edytorze kodu.

   > [!NOTE]
   > Jeśli *Program.cs* nie jest otwarty w edytorze, kliknij dwukrotnie plik *Program.cs* w **Eksploratora rozwiązań** aby go otworzyć.

::: moniker-end

5. Zastąp zawartość *Program.cs* następującym C# kod, który definiuje klasę *BankAccount*:

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

6. Zmień nazwę pliku do *BankAccount.cs* , klikając prawym przyciskiem myszy i wybierając pozycję **Zmień nazwę** w **Eksploratora rozwiązań**.

7. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

Masz teraz projekt za pomocą metod, które można przetestować. W tym artykule testy skoncentrowane na `Debit` metody. `Debit` Metoda jest wywoływana gdy pieniądze są wybierane z konta usługi.

## <a name="create-a-unit-test-project"></a>Tworzenie projektu testu jednostkowego

1. Na **pliku** menu, wybierz opcję **Dodaj** > **nowy projekt**.

   > [!TIP]
   > Użytkownik może również kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj** > **nowy projekt**.

::: moniker range="vs-2017"

2. W **nowy projekt** okna dialogowego rozwiń **zainstalowane**, rozwiń węzeł **Visual C#** , a następnie wybierz **testu**.

3. Z listy szablonów wybierz **projekt testów MSTest (.NET Core)** .

4. W **nazwa** wprowadź `BankTests`, a następnie wybierz pozycję **OK**.

   **BankTests** projekt jest dodawany do **Bank** rozwiązania.

::: moniker-end

::: moniker range=">=vs-2019"

2. Wyszukaj i wybierz pozycję C# **projekt testów MSTest (.NET Core)** projektu szablonu, a następnie kliknij przycisk **dalej**.

3. Nadaj projektowi nazwę **BankTests**.

4. Kliknij przycisk **Utwórz**.

   **BankTests** projekt jest dodawany do **Bank** rozwiązania.

::: moniker-end

5. W **BankTests** projektu, Dodaj odwołanie do **Bank** projektu.

   W **Eksploratora rozwiązań**, wybierz opcję **zależności** w obszarze **BankTests** projektu, a następnie wybierz **Dodaj odwołanie** z prawym przyciskiem myszy menu.

6. W **Menadżer odwołań** okna dialogowego rozwiń **projektów**, wybierz opcję **rozwiązania**, a następnie sprawdź **Bank** elementu.

7. Wybierz **OK**.

## <a name="create-the-test-class"></a>Utwórz klasę testową

Tworzenie klasy testowej, aby sprawdzić `BankAccount` klasy. Możesz użyć *UnitTest1.cs* pliku, który został wygenerowany przez szablon projektu, ale nadaj plikowi i klasie bardziej opisowe nazwy.

### <a name="rename-a-file-and-class"></a>Zmień nazwę pliku i klasy

1. Aby zmienić nazwę pliku, w **Eksploratora rozwiązań**, wybierz opcję *UnitTest1.cs* plik z projektu BankTests. Z menu kliknij prawym przyciskiem myszy, wybierz **Zmień nazwę**, a następnie zmień nazwę pliku do *BankAccountTests.cs*.

::: moniker range="vs-2017"

2. Aby zmienić nazwę klasy, wybierz opcję **tak** w oknie dialogowym, które pojawia się i pyta, czy też zmienić nazwę odwołania do elementu kodu.

::: moniker-end

::: moniker range=">=vs-2019"

2. Aby zmienić nazwę klasy, umieść kursor na `UnitTest1` w edytorze kodu, kliknij prawym przyciskiem myszy, a następnie wybierz **Zmień nazwę**. Wpisz **BankAccountTests** , a następnie naciśnij klawisz **Enter**.

::: moniker-end

*BankAccountTests.cs* plik zawiera teraz następujący kod:

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

### <a name="add-a-using-statement"></a>Dodaj instrukcję using — instrukcja

Dodaj [ `using` instrukcji](/dotnet/csharp/language-reference/keywords/using-statement) do klasy testowej, aby móc wywoływać testowanego projektu bez użycia w pełni kwalifikowanych nazw. W górnej części pliku klasy należy dodać:

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a>Wymagania klasy testowej

Minimalne wymagania dla klasy testowej są następujące:

- `[TestClass]` Atrybut jest wymagany w każdej klasy, która zawiera metody testów jednostkowych, które chcesz uruchomić w Eksploratorze testów.

- Musi mieć każdej metody testowej, który Test Explorer, rozpoznawał `[TestMethod]` atrybutu.

Może mieć inne klasy projekt testów jednostkowych, które nie mają `[TestClass]` atrybut, na które może mieć innych metod w klasach testowych, które nie mają `[TestMethod]` atrybutu. Te klasy i metody można wywołać z swoje metody testowe.

## <a name="create-the-first-test-method"></a>Tworzenie pierwszej metody testowej

W tej procedurze przedstawiono tworzenie metody, aby sprawdzić zachowanie testów jednostkowych `Debit` metody `BankAccount` klasy.

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

Ta metoda jest prosta: Konfiguruje nowy `BankAccount` obiektu z saldem, a następnie wycofa prawidłową kwotę. Używa ona <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType> metodę, aby sprawdzić, czy saldo końcowe jest zgodne z oczekiwaniami.

### <a name="test-method-requirements"></a>Wymagania metod testowych

Metoda testowa musi spełniać następujące wymagania:

- Ma ona `[TestMethod]` atrybutu.

- Zwraca `void`.

- Go nie może mieć parametrów.

## <a name="build-and-run-the-test"></a>Kompilowanie i uruchamianie testu

1. Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.

2. Jeśli **Eksplorator testów** nie jest otwarty, otwórz go, wybierając **testu** > **Windows** > **Eksplorator testów** z pasek menu u góry.

3. Wybierz **Uruchom wszystkie** do uruchomienia testu.

   Gdy test jest uruchomiony, pasek stanu u góry **Eksploratora testów** okna jest animowany. Na końcu przebiegu testowego pasek zmieni kolor zielony, jeśli wszystkie metody testowe zakończy się pomyślnie lub czerwony Jeśli którykolwiek z testów nie powiedzie się.

   W takim przypadku test kończy się niepowodzeniem.

4. Wybierz metodę w **Eksplorator testów** Aby wyświetlić szczegóły u dołu okna.

## <a name="fix-your-code-and-rerun-your-tests"></a>Napraw kod i ponownego przeprowadzania testów

Wynik testu zawiera komunikat, który opisuje błąd. Aby uzyskać `AreEqual` metody komunikat wyświetlany oczekiwanym i co zostało rzeczywiście przesłane. Oczekiwano saldo, aby zmniejszyć, ale zamiast tego wzrosła o kwotę wycofania.

Test jednostkowy ma niewykrytych usterek: ilość wycofanie *dodano* do salda konta, a powinien znajdować *odejmować*.

### <a name="correct-the-bug"></a>Należy poprawić usterkę

Aby naprawić błąd, w *BankAccount.cs* pliku, Zastąp wiersz:

```csharp
m_balance += amount;
```

Za pomocą:

```csharp
m_balance -= amount;
```

### <a name="rerun-the-test"></a>Uruchom ponownie test

W **Eksploratora testów**, wybierz **Uruchom wszystkie** do ponownego uruchomienia testu. Czerwony/zielony pasek zmienia kolor na zielony, wskazują, że test jest zaliczony.

![Eksplorator testów w Visual Studio 2019 przedstawiający przekazywane testu](media/test-explorer-banktests-passed.png)

## <a name="use-unit-tests-to-improve-your-code"></a>Użyj testów jednostkowych, aby poprawić kod

W tej sekcji opisano, jak proces iteracyjny analizy, tworzenie testów jednostkowych i Refaktoryzacja może pomóc zwiększyć kodu produkcyjnego, bardziej niezawodnego i skutecznego.

### <a name="analyze-the-issues"></a>Analizuj problemy

Utworzono metody testowej, aby upewnić się, że prawidłową kwotę jest prawidłowo odejmowana w `Debit` metody. Teraz, sprawdź, czy metoda zgłasza <xref:System.ArgumentOutOfRangeException> Jeśli kwota debet:

- większa niż saldo, lub
- mniejsza niż zero.

### <a name="create-and-run-new-test-methods"></a>Tworzenie i uruchamianie nowych metod testowych

Utwórz metodę testową, aby zweryfikować poprawne zachowanie w sytuacji, gdy kwota debetowa jest mniejsza od zera:

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

Użyj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> metody do potwierdzenia, że zgłoszono poprawny wyjątek. Ta metoda powoduje, że test zakończył się niepowodzeniem, chyba że <xref:System.ArgumentOutOfRangeException> zgłaszany. Jeśli zmodyfikujesz tymczasowo testowaną metodę Aby zgłosić generyczny więcej wyjątek <xref:System.ApplicationException> gdy kwota debet jest mniejsza niż zero, test działa poprawnie&mdash;oznacza to, nie powiedzie się.

Aby przetestować przypadek, gdy wybierana kwota jest większa niż saldo, wykonaj następujące czynności:

1. Tworzenie nowej metody testowej, o nazwie `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`.

2. Skopiuj ciało metody z `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` do nowej metody.

3. Ustaw `debitAmount` na liczbę większą niż saldo.

Uruchamianie dwóch testów i sprawdź, czy zostaną pomyślnie.

### <a name="continue-the-analysis"></a>Kontynuuj analizę

Dodatkowo można zwiększyć metoda poddawana testom. Za pomocą bieżącej implementacji, firma Microsoft nie ma możliwości wiedzieć, który warunek (`amount > m_balance` lub `amount < 0`) spowodowało wyjątek podczas testu. Po prostu wiemy, że `ArgumentOutOfRangeException` zgłoszono gdzieś w metodzie. Byłoby lepiej można stwierdzić, który warunek w `BankAccount.Debit` spowodowała zgłoszenie wyjątku (`amount > m_balance` lub `amount < 0`) dzięki czemu mamy pewność, czy naszych metody jest poprawnością sprawdzania argumentów poprawnie.

Przyjrzyj się metoda poddawana testom (`BankAccount.Debit`) ponownie i zwróć uwagę, że obie instrukcje warunkowe użyj `ArgumentOutOfRangeException` Konstruktor, który właśnie przyjmuje nazwę argumentu jako parametr:

```csharp
throw new ArgumentOutOfRangeException("amount");
```

Brak konstruktora można użyć, który zgłasza znacznie bogatsze informacje: <xref:System.ArgumentOutOfRangeException.%23ctor(System.String,System.Object,System.String)> zawiera nazwę argumentu, wartość argumentu i wiadomość zdefiniowanych przez użytkownika. Możesz refaktoryzować testowaną metodę Aby użyć tego konstruktora. Jeszcze lepiej służy publicznie dostępnych typów elementów członkowskich do określenia błędów.

### <a name="refactor-the-code-under-test"></a>Refaktoryzuj testowany kod

Najpierw należy zdefiniować dwie stałe dla komunikatów o błędach w zakresie klasy. Umieść je w klasie w ramach badania, `BankAccount`:

```csharp
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount is less than zero";
```

Następnie należy zmodyfikować dwie instrukcje warunkowe w `Debit` metody:

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

### <a name="refactor-the-test-methods"></a>Refaktoryzuj metody testowe

Refaktoryzuj metody testowe, usuwając wywołanie <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>. Opakować wywołanie `Debit()` w `try/catch` blokowania, catch określony wyjątek, który oczekuje się i sprawdź komunikat skojarzony. <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> Metoda zapewnia możliwość porównania dwóch ciągów.

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
    catch (System.ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
    }
}
```

### <a name="retest-rewrite-and-reanalyze"></a>Ponów test, przepisz i Analizuj ponownie

Założono w testowanej metody znajduje się błąd i `Debit` metoda nawet nie wyrzuca <xref:System.ArgumentOutOfRangeException> nigdy nie należy pamiętać, dane wyjściowe prawidłowy komunikat z wyjątkiem. Obecnie metoda testowa nie obsługuje tej sprawy. Jeśli `debitAmount` wartość jest prawidłowa (czyli mniej niż saldo, ale większa od zera), żaden wyjątek nie jest przechwytywany, więc asercja nigdy nie jest uruchamiany. Jeszcze Metoda test kończy się powodzeniem. To nie jest dobry, ponieważ chcesz, aby testowanej metody, aby zakończyć się niepowodzeniem, jeśli jest zgłaszany żaden wyjątek.

Jest to błąd w metodzie testowej. Aby rozwiązać ten problem, należy dodać <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> asercja na koniec testowanej metody, aby obsłużyć przypadek, gdzie jest zgłaszany żaden wyjątek.

Ponownie uruchamiając test wskazuje, że test teraz *nie powiedzie się* Jeśli przechwytywany jest poprawny wyjątek. `catch` Bloku przechwytuje wyjątek, ale kontynuuje wykonywanie metody nie powiedzie się nową <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> potwierdzenia. Aby rozwiązać ten problem, należy dodać `return` instrukcji znajdującej się po `StringAssert` w `catch` bloku. Ponownie uruchamiając test potwierdza, że zostały rozwiązano ten problem. Ostateczna wersja `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` wygląda podobnie do następującego:

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

Ulepszenia do kodu testu, doprowadziła do bardziej niezawodnych i wartościowych metod testowych. Ale co ważniejsze, one również ulepszona, testowany kod.

> [!TIP]
> W tym instruktażu wykorzystano środowisko testów jednostkowych Microsoft dla kodu zarządzanego. **Eksplorator testów** , można uruchomić testów jednostkowych innej firmy środowisk testowych, która posiada adaptery dla **Eksploratora testów**. Aby uzyskać więcej informacji, zobacz [instalowanie platform testów jednostkowych innych firm](../test/install-third-party-unit-test-frameworks.md)

## <a name="see-also"></a>Zobacz także

Aby uzyskać informacje o sposobach uruchamiania testów z wiersza polecenia, zobacz [opcje wiersza poleceń VSTest.Console.exe](vstest-console-options.md).
