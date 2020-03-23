---
title: Samouczek testu jednostkowego języka C#
ms.date: 05/14/2019
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
author: mikejo5000
ms.openlocfilehash: 4d5878e2c5950e45f65f8d56efdf53cd7b2e89ea
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094674"
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>Przewodnik: tworzenie i uruchamianie testów jednostkowych dla kodu zarządzanego

W tym artykule można wykonać kroki podczas tworzenia, uruchamiania i dostosowywania serii testów jednostkowych przy użyciu struktury testów jednostkowych firmy Microsoft dla kodu zarządzanego i **Eksploratora testów**programu Visual Studio. Należy rozpocząć od projektu Języka C#, który jest w trakcie opracowywania, tworzenie testów, które wykonują jego kod, uruchom testy i zbadać wyniki. Następnie należy zmienić kod projektu i ponownie uruchomić testy.



## <a name="create-a-project-to-test"></a>Tworzenie projektu do przetestowania

::: moniker range="vs-2017"

1. Otwórz program Visual Studio.

2. W menu **Plik** wybierz pozycję **Nowy** > **Projekt**.

   Zostanie wyświetlone okno dialogowe **Nowy projekt**.

3. W kategorii **Visual C#** > **.NET Core** wybierz szablon projektu aplikacji konsoli **(net core).**

4. Nazwij **bank**projektu, a następnie kliknij przycisk **OK**.

   Projekt Bank jest tworzony i wyświetlany w **Eksploratorze rozwiązań** z plikiem *Program.cs* otwartym w edytorze kodu.

   > [!NOTE]
   > Jeśli *Program.cs* nie jest otwarty w edytorze, kliknij dwukrotnie *plik, Program.cs* w **Eksploratorze rozwiązań,** aby go otworzyć.

::: moniker-end

::: moniker range=">=vs-2019"

1. Otwórz program Visual Studio.

2. W oknie początkowym wybierz pozycję **Utwórz nowy projekt**.

3. Wyszukaj i wybierz szablon projektu aplikacji konsoli C# **(.NET Core),** a następnie kliknij przycisk **Dalej**.

4. Nazwij **bank**projektu, a następnie kliknij przycisk **Utwórz**.

   Projekt Bank jest tworzony i wyświetlany w **Eksploratorze rozwiązań** z plikiem *Program.cs* otwartym w edytorze kodu.

   > [!NOTE]
   > Jeśli *Program.cs* nie jest otwarty w edytorze, kliknij dwukrotnie *plik, Program.cs* w **Eksploratorze rozwiązań,** aby go otworzyć.

::: moniker-end

5. Zastąp zawartość *Program.cs* następującym kodem Języka C#, który definiuje klasę *BankAccount:*

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

6. Zmień nazwę pliku, aby *BankAccount.cs,* klikając prawym przyciskiem myszy i wybierając polecenie **Zmień nazwę** w **Eksploratorze rozwiązań**.

7. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

Masz teraz projekt z metodami, które można przetestować. W tym artykule testy `Debit` koncentrują się na metodzie. Metoda `Debit` jest wywoływana, gdy pieniądze są wypłacane z konta.

## <a name="create-a-unit-test-project"></a>Tworzenie projektu testu jednostkowego

1. W menu **Plik** wybierz polecenie **Dodaj** > **nowy projekt**.

   > [!TIP]
   > Możesz również kliknąć prawym przyciskiem myszy rozwiązanie w **Eksploratorze rozwiązań** i wybrać pozycję **Dodaj** > **nowy projekt**.

::: moniker range="vs-2017"

2. W oknie dialogowym **Nowy projekt** rozwiń rozwiń pozycję **Zainstalowany**, rozwiń pozycję **Visual C#,** a następnie wybierz polecenie **Testuj**.

3. Z listy szablonów wybierz pozycję **MSTest Test Project (.NET Core).**

4. W polu **Nazwa** `BankTests`wprowadź , a następnie wybierz **przycisk OK**.

   Projekt **BankTests** jest dodawany do rozwiązania **Bank.**

::: moniker-end

::: moniker range=">=vs-2019"

2. Wyszukaj i wybierz szablon projektu testu MSTest języka C# **(core.NET),** a następnie kliknij przycisk **Dalej**.

3. Nazwij projekt **BankTests**.

4. Kliknij przycisk **Utwórz**.

   Projekt **BankTests** jest dodawany do rozwiązania **Bank.**

::: moniker-end

5. W projekcie **BankTests** dodaj odwołanie do projektu **Bank.**

   W **Eksploratorze rozwiązań**wybierz pozycję **Zależności** w ramach projektu **BankTests,** a następnie wybierz polecenie **Dodaj odwołanie** z menu po kliknięciu prawym przyciskiem myszy.

6. W oknie dialogowym **Menedżer odwołań** rozwiń pozycję **Projekty**, wybierz pozycję **Rozwiązanie**, a następnie zaznacz pozycję **Pozycja Bank.**

7. Wybierz pozycję **OK**.

## <a name="create-the-test-class"></a>Tworzenie klasy testowej

Utwórz klasę testową, aby zweryfikować `BankAccount` klasę. Można użyć pliku *UnitTest1.cs,* który został wygenerowany przez szablon projektu, ale nadać plikowi i klasie bardziej opisowe nazwy.

### <a name="rename-a-file-and-class"></a>Zmienianie nazwy pliku i klasy

1. Aby zmienić nazwę pliku, w **Eksploratorze rozwiązań**wybierz *UnitTest1.cs* plik w projekcie BankTests. Z menu prawym przyciskiem myszy wybierz polecenie **Zmień nazwę**, a następnie zmień nazwę pliku, aby *BankAccountTests.cs*.

::: moniker range="vs-2017"

2. Aby zmienić nazwę klasy, wybierz **tak** w oknie dialogowym, które pojawia się i pyta, czy chcesz również zmienić nazwę odwołań do elementu kodu.

::: moniker-end

::: moniker range=">=vs-2019"

2. Aby zmienić nazwę klasy, umieść `UnitTest1` kursor w edytorze kodu, kliknij prawym przyciskiem myszy, a następnie wybierz polecenie **Zmień nazwę**. Wpisz **w pliku BankAccountTests,** a następnie naciśnij **klawisz Enter**.

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

### <a name="add-a-using-statement"></a>Dodawanie instrukcji using

Dodaj [ `using` instrukcję](/dotnet/csharp/language-reference/keywords/using-statement) do klasy testowej, aby móc wywołać do projektu w ramach testu bez użycia w pełni kwalifikowanych nazw. U góry pliku klasy dodaj:

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a>Wymagania dotyczące klas testowych

Minimalne wymagania dla klasy testowej to:

- Atrybut `[TestClass]` jest wymagany dla każdej klasy, która zawiera metody testów jednostkowych, które chcesz uruchomić w Eksploratorze testów.

- Każda metoda testowa, którą chcesz rozpoznać Eksploratora testów, musi mieć `[TestMethod]` atrybut.

Można mieć inne klasy w projekcie testu jednostkowego, które nie mają atrybutu `[TestClass]` i może mieć `[TestMethod]` inne metody w klasach testów, które nie mają atrybutu. Można wywołać te inne klasy i metody z metod testowych.

## <a name="create-the-first-test-method"></a>Tworzenie pierwszej metody testowej

W tej procedurze napiszesz metody badania jednostkowego, aby sprawdzić zachowanie `Debit` metody `BankAccount` klasy.

Istnieją co najmniej trzy zachowania, które należy sprawdzić:

- Metoda <xref:System.ArgumentOutOfRangeException> zgłasza, jeśli kwota debetu jest większa niż saldo.

- Metoda <xref:System.ArgumentOutOfRangeException> zgłasza, jeśli kwota debetu jest mniejsza niż zero.

- Jeśli kwota debetu jest prawidłowa, metoda odejmuje kwotę debetu od salda konta.

> [!TIP]
> Metodę domyślną `TestMethod1` można usunąć, ponieważ nie będzie jej używać w tym instruktażu.

### <a name="to-create-a-test-method"></a>Aby utworzyć metodę testową

Pierwszy test sprawdza, czy prawidłowa kwota (czyli taka, która jest mniejsza niż saldo konta i większa od zera) wypłaca prawidłową kwotę z konta. Dodaj następującą metodę `BankAccountTests` do tej klasy:

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

Metoda jest prosta: konfiguruje `BankAccount` nowy obiekt z saldem początkowym, a następnie wypłaca prawidłową kwotę. Używa metody, <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A?displayProperty=nameWithType> aby sprawdzić, czy saldo końcowe jest zgodnie z oczekiwaniami.

### <a name="test-method-requirements"></a>Wymagania dotyczące metody badania

Metoda badawcza musi spełniać następujące wymagania:

- Jest ozdobiony atrybutem. `[TestMethod]`

- Zwraca `void`.

- Nie może mieć parametrów.

## <a name="build-and-run-the-test"></a>Tworzenie i uruchamianie testu

1. W menu **Kompilacja** wybierz polecenie **Build Solution**.

2. Jeśli **Eksplorator testów** nie jest otwarty, otwórz go, wybierając **pozycję Test** > **Windows** > **Test Explorer** z górnego paska menu.

3. Wybierz **pozycję Uruchom wszystko,** aby uruchomić test.

   Gdy test jest uruchomiony, pasek stanu w górnej części okna **Eksploratora testów** jest animowany. Po zakończeniu testu pasek zmienia kolor na zielony, jeśli wszystkie metody badania przebiegają zaliczają się, lub na czerwono, jeśli którykolwiek z testów nie powiedzie się.

   W takim przypadku test zakończy się niepowodzeniem.

4. Wybierz metodę w **Eksploratorze testów,** aby wyświetlić szczegóły w dolnej części okna.

## <a name="fix-your-code-and-rerun-your-tests"></a>Napraw kod i uruchom ponownie testy

Wynik testu zawiera komunikat opisujący błąd. Dla `AreEqual` metody komunikat wyświetla, co było oczekiwane i co zostało faktycznie odebrane. Oczekiwano, że saldo zmniejszy się, ale zamiast tego zwiększyło się o kwotę wypłaty.

Test jednostkowy odkrył błąd: kwota wypłaty jest *dodawana* do salda konta, gdy powinna zostać *odjęty.*

### <a name="correct-the-bug"></a>Popraw błąd

Aby poprawić błąd, w *pliku BankAccount.cs* zastąp wiersz:

```csharp
m_balance += amount;
```

tym:

```csharp
m_balance -= amount;
```

### <a name="rerun-the-test"></a>Ponowne uruchomienie testu

W **Eksploratorze testów**wybierz pozycję **Uruchom wszystko,** aby ponownie uruchomić test. Czerwony/zielony pasek zmienia kolor na zielony, aby wskazać, że test nie przeszedł.

![Eksplorator testów w programie Visual Studio 2019 z pozytywnym testem](media/test-explorer-banktests-passed.png)

## <a name="use-unit-tests-to-improve-your-code"></a>Użyj testów jednostkowych, aby poprawić swój kod

W tej sekcji opisano, jak iteracyjny proces analizy, rozwoju testów jednostkowych i refaktoryzacji może pomóc w bardziej niezawodnym i skutecznym kodzie produkcyjnym.

### <a name="analyze-the-issues"></a>Analizowanie problemów

Utworzono metodę testową, aby potwierdzić, że prawidłowa kwota jest poprawnie odliczana w metodzie. `Debit` Teraz sprawdź, czy metoda <xref:System.ArgumentOutOfRangeException> zgłasza, jeśli kwota debetu jest albo:

- większa niż waga, lub
- mniej niż zero.

### <a name="create-and-run-new-test-methods"></a>Tworzenie i uruchamianie nowych metod testowych

Utwórz metodę testową, aby zweryfikować poprawne zachowanie, gdy kwota debetu jest mniejsza niż zero:

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

Użyj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> metody, aby potwierdzić, że został zgłoszony poprawny wyjątek. Ta metoda powoduje, że <xref:System.ArgumentOutOfRangeException> test zakończy się niepowodzeniem, chyba że zostanie rzucony. Jeśli tymczasowo zmodyfikować metodę w ramach testu, aby zgłosić bardziej ogólne, <xref:System.ApplicationException> gdy&mdash;kwota debetowa jest mniejsza niż zero, test zachowuje się poprawnie, czyli kończy się niepowodzeniem.

Aby przetestować przypadek, gdy wypłacona kwota jest większa niż saldo, wykonaj następujące czynności:

1. Utwórz nową metodę `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`testową o nazwie .

2. Skopiuj `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` treść metody z do nowej metody.

3. Ustaw `debitAmount` liczbę większą niż waga.

Uruchamianie dwóch testów i sprawdź, czy przechodzą.

### <a name="continue-the-analysis"></a>Kontynuuj analizę

Testowana metoda może zostać ulepszona jeszcze bardziej. Przy bieżącej implementacji nie mamy możliwości`amount > m_balance` poznania, który warunek ( lub `amount < 0`) doprowadził do wyjątku zgłaszanych podczas testu. Wiemy tylko, `ArgumentOutOfRangeException` że został wrzucony gdzieś w metodzie. Byłoby lepiej, gdybyśmy mogli stwierdzić, w `BankAccount.Debit` jakim stanie`amount > m_balance` `amount < 0`spowodował wyjątek być odrzucone ( lub ), więc możemy być pewni, że nasza metoda jest poczytalność sprawdzanie jego argumenty poprawnie.

Spójrz na metodę testowane`BankAccount.Debit`( ) ponownie i zauważyć, `ArgumentOutOfRangeException` że obie instrukcje warunkowe użyć konstruktora, który po prostu bierze nazwę argumentu jako parametr:

```csharp
throw new ArgumentOutOfRangeException("amount");
```

Istnieje konstruktor, który można użyć, że <xref:System.ArgumentOutOfRangeException.%23ctor(System.String,System.Object,System.String)> raporty znacznie bogatsze informacje: zawiera nazwę argumentu, wartość argumentu i komunikat zdefiniowany przez użytkownika. Można refaktoryzować metodę w ramach testu, aby użyć tego konstruktora. Co więcej, można użyć publicznie dostępnych elementów członkowskich typu, aby określić błędy.

### <a name="refactor-the-code-under-test"></a>Refaktoryzuje testowany kod

Najpierw zdefiniuj dwie stałe dla komunikatów o błędach w zakresie klasy. Umieścić je w klasie `BankAccount`poddanej próbie,:

```csharp
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount is less than zero";
```

Następnie zmodyfikuj dwie `Debit` instrukcje warunkowe w metodzie:

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

### <a name="refactor-the-test-methods"></a>Refaktoryzator metod badawczych

Refaktoryzowanie metod testowych <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType>przez usunięcie wywołania . Zawiń wywołanie `Debit()` `try/catch` w bloku, przechwytuj oczekiwany wyjątek i weryfikuj skojarzony z nim komunikat. Metoda <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> zapewnia możliwość porównania dwóch ciągów.

Teraz `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` może wyglądać tak:

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

### <a name="retest-rewrite-and-reanalyze"></a>Przetestuj ponownie, przepisaj i ponownie analyze

Załóżmy, że istnieje błąd w `Debit` metodzie w ramach <xref:System.ArgumentOutOfRangeException> testu i metoda nawet nie zgłasza nie ważne dane wyjściowe poprawny komunikat z wyjątkiem. Obecnie metoda testowa nie obsługuje tego przypadku. Jeśli `debitAmount` wartość jest prawidłowa (czyli mniej niż saldo i większa niż zero), nie zostanie przechwycony żaden wyjątek, więc assert nigdy nie zostanie uruchamiany. Jednak metoda testowa przechodzi. To nie jest dobre, ponieważ chcesz, aby metoda testowa nie powiodła się, jeśli nie zostanie zgłoszony wyjątek.

Jest to błąd w metodzie testowej. Aby rozwiązać ten problem, dodaj <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> potwierdzenia na końcu metody testowej do obsługi przypadku, w którym nie jest zgłaszany wyjątek.

Ponowne uruchomienie testu pokazuje, że test *kończy się niepowodzeniem,* jeśli zostanie przechwycony poprawny wyjątek. Blok `catch` połowy wyjątek, ale metoda nadal wykonywać i kończy <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> się niepowodzeniem w nowym assert. Aby rozwiązać ten problem, należy `StringAssert` dodać `catch` instrukcję `return` po w bloku. Ponowne uruchomienie testu potwierdza, że rozwiązałeś ten problem. Ostateczna wersja `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` wygląda następująco:

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

### <a name="conclusion"></a>Podsumowanie

Ulepszenia kodu testowego doprowadziły do bardziej niezawodnych i pouczające metody testowania. Ale co ważniejsze, również poprawiła kod w ramach testu.

> [!TIP]
> W tym instruktażu użyto struktury testów jednostkowych firmy Microsoft dla kodu zarządzanego. **Eksplorator testów** może również uruchamiać testy z platform testów jednostkowych innych firm, które mają karty dla **Eksploratora testów.** Aby uzyskać więcej informacji, zobacz [Instalowanie struktur testów jednostkowych innych firm](../test/install-third-party-unit-test-frameworks.md).

## <a name="see-also"></a>Zobacz też

Aby uzyskać informacje dotyczące uruchamiania testów z wiersza polecenia, zobacz [opcje wiersza polecenia VSTest.Console.exe](vstest-console-options.md).
