---
title: 'Przewodnik: Tworzenie i uruchamianie testów jednostkowych dla kodu zarządzanego | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.assetid: 2b018b18-b412-4e0e-b0ee-b580a2f3ba9c
caps.latest.revision: 85
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 631a180789f5fff373799b78222c25a50ab32912
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657101"
---
# <a name="walkthrough-creating-and-running-unit-tests-for-managed-code"></a>Wskazówki: tworzenie i uruchamianie testów jednostkowych zarządzanego kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten przewodnik przeprowadzi Cię przez proces tworzenia, uruchamiania i dostosowywania serii testów jednostkowych przy użyciu struktury testów jednostkowych firmy Microsoft dla kodu zarządzanego i programu Visual Studio Test Explorer. Zacznij od C# projektu, który jest w fazie tworzenia, Twórz testy, które wykonują swój kod, uruchamiają testy i sprawdzają wyniki. Następnie można zmienić kod projektu i ponownie uruchomić testy.

 Ten temat zawiera następujące sekcje:

 [Przygotowanie przewodnika](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough)

 [Tworzenie projektu testu jednostkowego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_a_unit_test_project)

 [Tworzenie klasy testowej](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_test_class)

- [Wymagania dotyczące klasy testowej](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_class_requirements)

  [Utwórz pierwszą metodę testową](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_first_test_method)

- [Wymagania metody testowej](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_method_requirements)

  [Kompiluj i uruchamiaj test](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Build_and_run_the_test)

  [Popraw kod i ponownie uruchom testy](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Fix_your_code_and_rerun_your_tests)

  [Korzystanie z testów jednostkowych w celu ulepszania kodu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Use_unit_tests_to_improve_your_code)

> [!NOTE]
> W tym przewodniku zastosowano środowisko testów jednostkowych firmy Microsoft dla kodu zarządzanego. Eksplorator testów może również uruchamiać testy z innych platform testów jednostkowych innych firm, które mają karty w Eksploratorze testów. Aby uzyskać więcej informacji, zobacz [Instalowanie platform testów jednostkowych](../test/install-third-party-unit-test-frameworks.md) innych firm

> [!NOTE]
> Aby uzyskać informacje o sposobach uruchamiania testów z wiersza polecenia, zobacz [Przewodnik: korzystanie z narzędzia testowego wiersza polecenia](https://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867).

## <a name="prerequisites"></a>Wymagania wstępne

- Projekt banku. Zobacz [przykładowy projekt, aby utworzyć testy jednostkowe](../test/sample-project-for-creating-unit-tests.md).

## <a name="BKMK_Prepare_the_walkthrough"></a>Przygotowanie przewodnika

1. Otwórz program Visual Studio.

2. W menu **plik** wskaż polecenie **Nowy** , a następnie kliknij pozycję **projekt**.

    Pojawi się okno dialogowe **Nowy projekt** .

3. W obszarze **zainstalowane szablony**kliknij **pozycję C#Wizualizacja** .

4. Na liście typów aplikacji kliknij pozycję **Biblioteka klas**.

5. W polu **Nazwa** wpisz `Bank` a następnie kliknij przycisk **OK**.

   > [!NOTE]
   > Jeśli nazwa "Bank" jest już używana, wybierz inną nazwę dla projektu.

    Nowy projekt banku zostanie utworzony i wyświetlony w Eksplorator rozwiązań z plikiem Class1.cs otwartym w edytorze kodu.

   > [!NOTE]
   > Jeśli plik Class1.cs nie jest otwarty w edytorze kodu, kliknij dwukrotnie plik Class1.cs w Eksplorator rozwiązań, aby go otworzyć.

6. Skopiuj kod źródłowy z [przykładowego projektu, aby utworzyć testy jednostkowe](../test/sample-project-for-creating-unit-tests.md).

7. Zastąp pierwotną zawartość Class1.cs kodem z [przykładowego projektu, aby utworzyć testy jednostkowe](../test/sample-project-for-creating-unit-tests.md).

8. Zapisz plik jako BankAccount.cs

9. W menu **kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

   Masz teraz projekt o nazwie Bank. Zawiera kod źródłowy do testowania i narzędzi do przetestowania za pomocą. Przestrzeń nazw dla Bank **BankAccountNS**zawiera klasy Public **BankAccount**, której metody należy przetestować w poniższych procedurach.

   W tym przewodniku szybki start skupmy się na `Debit` metodzie. Metoda Debet jest wywoływana, gdy pieniądze zostanie wycofane z konta i zawiera następujący kod:

```csharp
// method under test
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

## <a name="BKMK_Create_a_unit_test_project"></a>Tworzenie projektu testu jednostkowego
 **Wymaganie wstępne**: wykonaj kroki opisane w tej procedurze, a następnie [Przygotuj Przewodnik](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough).

#### <a name="to-create-a-unit-test-project"></a>Aby utworzyć projekt testu jednostkowego

1. W menu **plik** , wybierz **Dodaj**, a następnie wybierz **Nowy projekt..** ..

2. W oknie dialogowym Nowy projekt rozwiń węzeł **zainstalowane**, rozwiń pozycję **Wizualizacja C#** , a następnie wybierz pozycję **Testuj**.

3. Z listy szablonów wybierz pozycję **projekt testu jednostkowego**.

4. W polu **Nazwa** wprowadź BankTest, a następnie wybierz przycisk **OK**.

     Projekt **BankTests** jest dodawany do rozwiązania **bankowego** .

5. W projekcie **BankTests** Dodaj odwołanie do rozwiązania **bankowego** .

     W Eksplorator rozwiązań wybierz pozycję **odwołania** w projekcie **BankTests** , a następnie wybierz pozycję **Dodaj odwołanie...** z menu kontekstowego.

6. W oknie dialogowym Menedżer odwołań rozwiń węzeł **rozwiązanie** , a następnie sprawdź element **Bank** .

## <a name="BKMK_Create_the_test_class"></a>Tworzenie klasy testowej
 Potrzebujemy klasy testowej do weryfikacji klasy `BankAccount`. Możemy użyć UnitTest1.cs, który został wygenerowany przez szablon projektu, ale powinienmy nadać plikowi i klasie więcej nazw opisowych. Możemy to zrobić w jednym kroku, zmieniając nazwę pliku w Eksplorator rozwiązań.

 **Zmiana nazwy pliku klasy**

 W Eksplorator rozwiązań wybierz plik UnitTest1.cs w projekcie BankTests. Z menu kontekstowego wybierz polecenie **Zmień nazwę**, a następnie zmień nazwę pliku na BankAccountTests.cs. Wybierz pozycję **tak** w oknie dialogowym z pytaniem, czy chcesz zmienić nazwy wszystkich odwołań w projekcie na element kodu "UnitTest1". Ten krok zmienia nazwę klasy na `BankAccountTest`.

 Plik BankAccountTests.cs zawiera teraz następujący kod:

```csharp
// unit test code
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

 **Dodaj instrukcję using do badanego projektu**

 Możemy również dodać instrukcję using do klasy, aby umożliwić nam wywoływanie w badanym projekcie bez używania w pełni kwalifikowanych nazw. W górnej części pliku klasy Dodaj:

```csharp
using BankAccountNS;
```

### <a name="BKMK_Test_class_requirements"></a>Wymagania dotyczące klasy testowej
 Minimalne wymagania dotyczące klasy testowej są następujące:

- Atrybut `[TestClass]` jest wymagany w środowisku testów jednostkowych firmy Microsoft dla kodu zarządzanego dla każdej klasy zawierającej metody testów jednostkowych, które mają być uruchamiane w Eksploratorze testów.

- Każda metoda testowa, którą ma uruchamiać Eksplorator testów, musi mieć `[TestMethod]`attribute.

  Można mieć inne klasy w projekcie testów jednostkowych, które nie mają atrybutu `[TestClass]` i można mieć inne metody w klasach testowych, które nie mają atrybutu `[TestMethod]`. Możesz użyć tych innych klas i metod w metodach testowych.

## <a name="BKMK_Create_the_first_test_method"></a>Utwórz pierwszą metodę testową
 W tej procedurze będziemy pisać metody testów jednostkowych, aby zweryfikować zachowanie metody `Debit` klasy `BankAccount`. Ta metoda jest wymieniona powyżej.

 Analizując badaną metodę, stwierdzamy, że istnieją co najmniej trzy zachowania, które należy sprawdzić:

1. Metoda zgłasza [wyjątku ArgumentOutOfRangeException] (<!-- TODO: review code entity reference <xref:assetId:///ArgumentOutOfRangeException?qualifyHint=False&amp;autoUpgrade=True>  -->), jeśli kwota debetu jest większa niż saldo.

2. Zwraca również `ArgumentOutOfRangeException`, jeśli kwota debetu jest mniejsza od zera.

3. Jeśli kontrole w 1.) i 2). są spełnione, metoda odejmowanie kwoty od salda konta.

   W pierwszym teście sprawdzimy, czy prawidłowa kwota (taka, która jest mniejsza niż saldo konta i większa od zera) odnosi poprawną kwotę z konta.

#### <a name="to-create-a-test-method"></a>Aby utworzyć metodę testową

1. Dodaj instrukcję using `BankAccountNS;` do pliku BankAccountTests.cs.

2. Dodaj następującą metodę do tej klasy `BankAccountTests`:

   ```csharp
   // unit test code
   [TestMethod]
   public void Debit_WithValidAmount_UpdatesBalance()
   {
       // arrange
       double beginningBalance = 11.99;
       double debitAmount = 4.55;
       double expected = 7.44;
       BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

       // act
       account.Debit(debitAmount);

       // assert
       double actual = account.Balance;
       Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");
   }
   ```

   Metoda jest raczej prosta. Skonfigurujemy nowy obiekt `BankAccount` z saldem początkowym, a następnie wycofasz prawidłową kwotę. Użyjemy struktury testów jednostkowych firmy Microsoft dla kodu zarządzanego <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> metody, aby sprawdzić, czy saldo końcowe jest oczekiwane.

### <a name="BKMK_Test_method_requirements"></a>Wymagania metody testowej
 Metoda testowa musi spełniać następujące wymagania:

- Metoda musi mieć atrybut `[TestMethod]`.

- Metoda musi zwracać `void`.

- Metoda nie może mieć parametrów.

## <a name="BKMK_Build_and_run_the_test"></a>Kompiluj i uruchamiaj test

#### <a name="to-build-and-run-the-test"></a>Aby skompilować i uruchomić test

1. W menu **kompilacja** wybierz polecenie **Kompiluj rozwiązanie**.

     Jeśli nie ma żadnych błędów, zostanie wyświetlone okno UnitTestExplorer z **Debit_WithValidAmount_UpdatesBalance** na liście **nieuruchomionych testów** . Jeśli Eksplorator testów nie jest wyświetlany po pomyślnej kompilacji, wybierz **test** z menu, a następnie wybierz **Windows**, a następnie wybierz **Eksplorator testów**.

2. Wybierz **Uruchom wszystkie** , aby uruchomić test. Gdy test jest uruchomiony, pasek stanu w górnej części okna jest animowany. Na końcu przebiegu testu pasek zmieni kolor na zielony, jeśli wszystkie metody testowe są przekazywane lub czerwone, jeśli którykolwiek z testów zakończy się niepowodzeniem.

3. W takim przypadku test kończy się niepowodzeniem. Metoda testowa jest przenoszona do **testów zakończonych niepowodzeniem**. Group. Wybierz metodę w Eksploratorze testów, aby wyświetlić szczegóły w dolnej części okna.

## <a name="BKMK_Fix_your_code_and_rerun_your_tests"></a>Popraw kod i ponownie uruchom testy
 **Analizowanie wyników testów**

 Wynik testu zawiera komunikat, który opisuje błąd. W przypadku metody `AreEquals` komunikat wyświetla oczekiwany (oczekiwany<strong>\<*XXX* ></strong>parametr) i to, co zostało faktycznie odebrane ( **rzeczywisty \<*yyy* >** parametr). Oczekujemy, że saldo odrzucisz od salda początkowego, ale zamiast tego wzrosło o kwotę wycofania.

 Badanie kodu debetu pokazuje, że test jednostkowy pomyślnie wyszukał usterkę. Kwota wycofania jest dodawana do salda konta, gdy powinna zostać odjęta.

 **Popraw usterkę**

 Aby poprawić błąd, po prostu Zastąp wiersz

```csharp
m_balance += amount;
```

 with

```csharp
m_balance -= amount;
```

 **Uruchom ponownie test**

 W Eksploratorze testów wybierz opcję **Uruchom wszystkie** , aby ponownie uruchomić test. Czerwony/zielony pasek zmienia kolor na zielony, a test jest przenoszony do grupy **zakończone testy** .

## <a name="BKMK_Use_unit_tests_to_improve_your_code"></a>Korzystanie z testów jednostkowych w celu ulepszania kodu
 W tej sekcji opisano, w jaki sposób iteracyjny proces analizy, opracowywanie testów jednostkowych i Refaktoryzacja może pomóc zwiększyć niezawodność i skuteczność kodu produkcyjnego.

 **Analizowanie problemów**

 Po utworzeniu metody testowej w celu potwierdzenia, że prawidłowa kwota jest prawidłowo odejmowana w metodzie `Debit`, możemy włączyć pozostałe przypadki w naszej pierwotnej analizie:

1. Metoda zgłasza `ArgumentOutOfRangeException`, jeśli kwota debetu jest większa niż saldo.

2. Zwraca również `ArgumentOutOfRangeException`, jeśli kwota debetu jest mniejsza od zera.

   **Tworzenie metod testowych**

   Pierwsza próba utworzenia metody testowej w celu rozwiązania tych problemów wydaje się być obietnicą:

```csharp
//unit test method
[TestMethod]
[ExpectedException(typeof(ArgumentOutOfRangeException))]
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()
{
    // arrange
    double beginningBalance = 11.99;
    double debitAmount = -100.00;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // act
    account.Debit(debitAmount);

    // assert is handled by ExpectedException
}

```

 Używamy atrybutu <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> w celu potwierdzenia, że został wygenerowany właściwy wyjątek. Ten atrybut powoduje niepowodzenie testu, chyba że zostanie zgłoszony `ArgumentOutOfRangeException`. Uruchamianie testu z wartościami dodatnimi i ujemnymi `debitAmount`, a następnie tymczasowe modyfikowanie testowanej metody w celu zgłaszania ogólnych <xref:System.ApplicationException>, gdy kwota jest mniejsza niż zero, pokazuje, że test działa poprawnie. Aby przetestować przypadek, gdy wycofana kwota jest większa niż saldo, należy wykonać następujące czynności:

1. Utwórz nową metodę testową o nazwie `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`.

2. Skopiuj treść metody z `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` do nowej metody.

3. Ustaw `debitAmount` na liczbę większą niż saldo.

   **Uruchom testy**

   Uruchomienie dwóch metod z różnymi wartościami dla `debitAmount` pokazuje, że testy odpowiednio obsługują nasze pozostałe przypadki. Uruchomienie wszystkich trzech testów potwierdza, że wszystkie przypadki w naszej pierwotnej analizie są pokryte prawidłowo.

   **Kontynuuj analizę**

   Jednakże ostatnie dwie metody testowe są również nieco niepokojące. Nie można się upewnić, że warunek w testowanym kodzie jest zgłaszany w przypadku uruchomienia testu. W ten sposób można ułatwić rozróżnienie tych dwóch warunków. Gdy myślisz o tym problemie, stanie się jasne, że wiedząc, który warunek został naruszony, zwiększy nasz stopień zaufania w testach. Te informacje również byłyby przydatne w mechanizmie produkcyjnym, który obsługuje wyjątek, gdy jest generowany przez metodę poddawaną testom. Generowanie większej ilości informacji w przypadku, gdy metoda zgłasza wszystkie zainteresowane dane, ale atrybut `ExpectedException` nie może podawać tych informacji.

   Patrząc na ponownie metodę testową, zobaczymy obie instrukcje warunkowe przy użyciu konstruktora `ArgumentOutOfRangeException`, który przyjmuje nazwę argumentu jako parametr:

```csharp
throw new ArgumentOutOfRangeException("amount");
```

 Z poziomu wyszukiwania biblioteki MSDN wiemy, że istnieje Konstruktor, który raportuje informacje o znacznie bogatszych informacjach. <xref:System.ArgumentOutOfRangeException.%23ctor%2A> `(String, Object, String)` obejmuje nazwę argumentu, wartość argumentu oraz komunikat zdefiniowany przez użytkownika. Możemy użyć refaktoryzacji testowanej metody w celu użycia tego konstruktora. Jeszcze lepszym rozwiązaniem jest użycie publicznie dostępnego typu elementów członkowskich, aby określić błędy.

 **Refaktoryzacja testowanego kodu**

 Najpierw definiujemy dwie stałe dla komunikatów o błędach w zakresie klasy:

```csharp
// class under test
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount less than zero";
```

 Następnie zmodyfikujemy dwie instrukcje warunkowe w `Debit` metodzie:

```csharp
// method under test
// ...
    if (amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);
    }

    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);
    }
// ...
```

 **Refaktoryzacja metod testowych**

 W naszej metodzie testowej najpierw usuniemy atrybut `ExpectedException`. W tym miejscu przechwytujmy zgłoszony wyjątek i sprawdź, czy został on zgłoszony w prawidłowej instrukcji Condition. Jednak musimy teraz podjąć decyzję między dwiema opcjami, aby zweryfikować pozostałe warunki. Na przykład w metodzie `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` można wykonać jedną z następujących czynności:

- Potwierdź, że właściwość `ActualValue` wyjątku (drugi parametr konstruktora `ArgumentOutOfRangeException`) jest większa niż saldo początkowe. Ta opcja wymaga przetestowania właściwości `ActualValue` wyjątku względem zmiennej `beginningBalance` metody testowej, a także wymaga sprawdzenia, czy `ActualValue` jest większa od zera.

- Potwierdź, że komunikat (trzeci parametr konstruktora) zawiera `DebitAmountExceedsBalanceMessage` zdefiniowanej w klasie `BankAccount`.

  Metoda <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> w środowisku testów jednostkowych firmy Microsoft umożliwia nam zweryfikowanie drugiej opcji bez obliczeń wymaganych od pierwszej opcji.

  Druga próba zmiany `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` może wyglądać następująco:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // assert
        StringAssert.Contains(e.Message, BankAccount. DebitAmountExceedsBalanceMessage);
    }
}
```

 **Ponowne testowanie, ponowne zapisywanie i ponowne analizowanie**

 Po przetestowaniu metod testowych z różnymi wartościami wystąpią następujące fakty:

1. Jeśli przechwytuje poprawny błąd przy użyciu potwierdzenia, gdzie `debitAmount`, który jest większy od salda, potwierdzenie `Contains` kończy się powodzeniem, wyjątek jest ignorowany i dlatego metoda testowa zostanie przekazana. Jest to zachowanie, które chcemy.

2. Jeśli użyjemy `debitAmount`, która jest mniejsza niż 0, potwierdzenie nie powiedzie się, ponieważ zwracany jest niewłaściwy komunikat o błędzie. Potwierdzenie kończy się niepowodzeniem, Jeśli wprowadzimy tymczasowy wyjątek `ArgumentOutOfRange` w innym punkcie metody w obszarze Testuj ścieżkę kodu. Jest to zbyt dobre.

3. Jeśli wartość `debitAmount` jest prawidłowa (tj. mniejsza od salda, ale większa od zera, żaden wyjątek nie jest przechwytywany, więc potwierdzenie nigdy nie jest przechwytywane. Metoda testowa kończy się powodzeniem. Nie jest to dobre, ponieważ chcemy, aby metoda testowa została zakończona niepowodzeniem, jeśli nie zostanie zgłoszony żaden wyjątek.

   Trzeci fakt jest usterką w naszej metodzie testowej. Aby spróbować rozwiązać ten problem, dodamy potwierdzenie <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> na końcu metody testowej, aby obsłużyć przypadek, w którym nie jest zgłaszany żaden wyjątek.

   Jednak przetestowanie pokazuje, że test zakończy się niepowodzeniem, jeśli przechwycono poprawny wyjątek. Instrukcja catch resetuje wyjątek, a metoda nadal wykonuje operację, która kończy się niepowodzeniem z nowym potwierdzeniem. Aby rozwiązać nowy problem, dodamy instrukcję `return` po `StringAssert`. Ponowne testowanie potwierdza, że rozwiązano nasze problemy. Wersja ostateczna `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` wygląda następująco:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // assert
        StringAssert.Contains(e.Message, BankAccount. DebitAmountExceedsBalanceMessage);
        return;
    }
    Assert.Fail("No exception was thrown.");
}

```

 W tej ostatniej sekcji zadziałała, że Ulepszono nasz kod testu do bardziej niezawodnych i informacyjnych metod testowych. Ale co ważniejsze, Dodatkowa analiza również doprowadziła do lepszego kodu w naszym projekcie testowym.
