---
title: 'Przewodnik: Tworzenie i Uruchamianie testów jednostkowych dla kodu zarządzanego | Dokumentacja firmy Microsoft'
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
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2e120499893a5b2a85d9a40a57e078f3d8f6586d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695049"
---
# <a name="walkthrough-creating-and-running-unit-tests-for-managed-code"></a>Przewodnik: Tworzenie i Uruchamianie testów jednostkowych dla kodu zarządzanego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym przewodniku krok po kroku tworzenia, uruchamiania i dostosowywać serie testów jednostkowych przy użyciu środowiska testów jednostkowych Microsoft dla kodu zarządzanego i Visual Studio Test Explorer. Rozpocznij z projektu języka C#, który jest w fazie projektowania, tworzy testy, które wykonują kod, uruchom testy i bada wyniki. Następnie można zmienić kodu projektu i ponownie uruchomić testy.  
  
 Ten temat zawiera następujące sekcje:  
  
 [Przygotuj przewodnik](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough)  
  
 [Tworzenie projektu testu jednostkowego](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_a_unit_test_project)  
  
 [Utwórz klasę testową](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_test_class)  
  
- [Wymagania klasy testowej](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_class_requirements)  
  
  [Tworzenie pierwszej metody testowej](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Create_the_first_test_method)  
  
- [Wymagania metod testowych](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Test_method_requirements)  
  
  [Kompilowanie i uruchamianie testu](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Build_and_run_the_test)  
  
  [Napraw kod i ponownego przeprowadzania testów](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Fix_your_code_and_rerun_your_tests)  
  
  [Użyj testów jednostkowych, aby poprawić kod](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Use_unit_tests_to_improve_your_code)  
  
> [!NOTE]
> W tym instruktażu wykorzystano środowisko testów jednostkowych Microsoft dla kodu zarządzanego. Eksplorator testów można również uruchomić testy z innej struktury testów, które posiada adaptery dla Eksploratora testów. Aby uzyskać więcej informacji, zobacz [instalowanie platform testów jednostkowych innych firm](../test/install-third-party-unit-test-frameworks.md)  
  
> [!NOTE]
> Aby uzyskać informacje o sposobach uruchamiania testów z wiersza polecenia, zobacz [wskazówki: Korzystanie z narzędzia testu wiersza polecenia](https://msdn.microsoft.com/library/52c11992-9e94-4067-a4b7-59f19d69d867).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
  
- Projekt o nazwie Bank. Zobacz [przykładowy projekt dotyczący tworzenia testów jednostkowych](../test/sample-project-for-creating-unit-tests.md).  
  
## <a name="BKMK_Prepare_the_walkthrough"></a> Przygotuj przewodnik  
  
1. Otwórz program Visual Studio.  
  
2. Na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu**.  
  
    **Nowy projekt** pojawi się okno dialogowe.  
  
3. W obszarze **zainstalowane szablony**, kliknij przycisk **Visual C#**.  
  
4. Na liście typów aplikacji, kliknij **biblioteki klas**.  
  
5. W **nazwa** wpisz `Bank` a następnie kliknij przycisk **OK**.  
  
   > [!NOTE]
   > Jeśli nazwa "Bank" jest już używana, wybierz inną nazwę dla projektu.  
  
    Nowy projekt o nazwie Bank, jest tworzony i wyświetlany w Eksploratorze rozwiązań z plikiem Class1.cs, otwartym w edytorze kodu.  
  
   > [!NOTE]
   > Jeśli plik Class1.cs nie jest otwarty w edytorze kodu, kliknij dwukrotnie plik Class1.cs w oknie Solution Explorer, aby go otworzyć.  
  
6. Skopiuj kod źródłowy z [przykładowy projekt dotyczący tworzenia testów jednostkowych](../test/sample-project-for-creating-unit-tests.md).  
  
7. Zamień oryginalną zawartość pliku Class1.cs na kod z [przykładowy projekt dotyczący tworzenia testów jednostkowych](../test/sample-project-for-creating-unit-tests.md).  
  
8. Zapisz plik jako BankAccount.cs  
  
9. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
   Masz teraz projekt o nazwie Bank. Zawiera on kod źródłowy do testowania i narzędzia do testowania go. Przestrzeń nazw dla banku, **BankAccountNS**, zawiera klasę publiczną **BankAccount**, której metody należy przetestować w poniższych procedurach.  
  
   W tym przewodniku Szybki start skupimy się na `Debit` metody. Metoda jest wywoływana gdy pieniądze są wybierane konta i zawiera następujący kod:  
  
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
  
## <a name="BKMK_Create_a_unit_test_project"></a> Tworzenie projektu testu jednostkowego  
 **Wymagań wstępnych**: Wykonaj kroki opisane w procedurze [Przygotuj przewodnik](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#BKMK_Prepare_the_walkthrough).  
  
#### <a name="to-create-a-unit-test-project"></a>Aby utworzyć projekt testów jednostkowych  
  
1. Na **pliku** menu, wybierz **Dodaj**, a następnie wybierz **nowy projekt...** .  
  
2. W oknie dialogowym Nowy projekt rozwiń **zainstalowane**, rozwiń węzeł **Visual C#**, a następnie wybierz **testu**.  
  
3. Z listy szablonów wybierz **projektu testu jednostkowego**.  
  
4. W **nazwa** , wpisz BankTest, a następnie wybierz **OK**.  
  
     **BankTests** projekt jest dodawany do **Bank** rozwiązania.  
  
5. W **BankTests** projektu, Dodaj odwołanie do **Bank** rozwiązania.  
  
     W Eksploratorze rozwiązań wybierz **odwołania** w **BankTests** projektu, a następnie wybierz **Dodaj odwołanie...**  z menu kontekstowego.  
  
6. W oknie dialogowym Reference Manager, rozwiń **rozwiązania** , a następnie sprawdź **Bank** elementu.  
  
## <a name="BKMK_Create_the_test_class"></a> Utwórz klasę testową  
 Potrzebujemy klasą testową w celu sprawdzenia `BankAccount` klasy. Możemy użyć pliku UnitTest1.cs, który został wygenerowany przez szablon projektu, ale firma Microsoft należy nadać plikowi i klasie bardziej opisowe nazwy. Można to zrobić w jednym kroku przez zmianę nazwy pliku w Eksploratorze rozwiązań.  
  
 **Zmiana nazwy pliku klasy**  
  
 W Eksploratorze rozwiązań wybierz plik UnitTest1.cs, z projektu BankTests. Z menu kontekstowego wybierz **Zmień nazwę**, a następnie zmień nazwę pliku na BankAccountTests.cs. Wybierz **tak** w oknie dialogowym z pytaniem, jeśli chcesz zmienić wszystkie odwołania w projekcie do elementu kodu "UnitTest1". Ten krok zmienia nazwę klasy, która ma `BankAccountTest`.  
  
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
  
 **Dodaj instrukcję using instrukcji do testowanego projektu**  
  
 Możemy również dodać, przy użyciu instrukcji, aby klasy, aby umożliwić wywołania testowanego projektu bez użycia w pełni kwalifikowanych nazw. W górnej części pliku klasy należy dodać:  
  
```csharp  
using BankAccountNS;  
```  
  
### <a name="BKMK_Test_class_requirements"></a> Wymagania klasy testowej  
 Minimalne wymagania dla klasy testowej są następujące:  
  
- `[TestClass]` Atrybut jest wymagany w jednostce Microsoft struktury testowania dla zarządzanego kodu, dla każdej klasy, która zawiera metody testów jednostkowych, które chcesz uruchomić w Eksploratorze testów.  
  
- Każdej metody testowej, który Eksploratora testów do uruchomienia musi mieć `[TestMethod]`atrybutu.  
  
  Może mieć inne klasy projekt testów jednostkowych, które nie mają `[TestClass]` atrybut, na które może mieć innych metod w klasach testowych, które nie mają `[TestMethod]` atrybutu. Te klasy i metody można użyć w swoich metod testowych.  
  
## <a name="BKMK_Create_the_first_test_method"></a> Tworzenie pierwszej metody testowej  
 W tej procedurze, zostaną napisane metody, aby sprawdzić zachowanie testów jednostkowych `Debit` metody `BankAccount` klasy. Metoda jest wymieniona powyżej.  
  
 Analizując testowaną metodę, określamy, czy są przynajmniej trzy zachowania, które muszą być sprawdzone:  
  
1. Metoda zgłasza ([Trwa wyjątku ArgumentOutOfRangeException]<!-- TODO: review code entity reference <xref:assetId:///ArgumentOutOfRangeException?qualifyHint=False&amp;autoUpgrade=True>  -->) Jeśli kwota debet jest większa niż saldo.  
  
2. Zgłasza również `ArgumentOutOfRangeException` Jeśli kwota debet jest mniejsza niż zero.  
  
3. Jeżeli kontrole w 1.) i 2.) są spełnione, metoda odejmuje kwotę od salda konta.  
  
   Pierwszy test możemy zweryfikować, czy prawidłową kwotę (po jednym jest mniejsza niż saldo konta i większa od zera) powoduje wybranie poprawnej ilości z konta.  
  
#### <a name="to-create-a-test-method"></a>Aby utworzyć metodę testową  
  
1. Dodaj instrukcję using `BankAccountNS;` instrukcji do pliku BankAccountTests.cs.  
  
2. Dodaj następującą metodę do tego `BankAccountTests` klasy:  
  
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
  
   Metoda jest dość prosta. Skonfigurowanie nowego `BankAccount` obiektu z saldem, a następnie wycofać prawidłową kwotę. Używamy środowisko testów jednostkowych Microsoft dla kodu zarządzanego <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> metodę, aby sprawdzić, czy saldo końcowe jest, jakiego się spodziewaliśmy.  
  
### <a name="BKMK_Test_method_requirements"></a> Wymagania metod testowych  
 Metoda testowa musi spełniać następujące wymagania:  
  
- Metoda musi posiadać `[TestMethod]` atrybutu.  
  
- Metoda musi zwracać `void`.  
  
- Metoda nie może mieć parametrów.  
  
## <a name="BKMK_Build_and_run_the_test"></a> Kompilowanie i uruchamianie testu  
  
#### <a name="to-build-and-run-the-test"></a>Aby skompilować i uruchomić test  
  
1. Na **kompilacji** menu, wybierz **Kompiluj rozwiązanie**.  
  
     Jeśli nie ma żadnych błędów, pojawi się okno UnitTestExplorer z **Debit_WithValidAmount_UpdatesBalance** na liście **testy nieuruchamiane** grupy. Eksplorator testów nie jest wyświetlany po pomyślnej kompilacji, wybierz opcję **testu** menu, kliknij **Windows**, a następnie wybierz **Eksplorator testów**.  
  
2. Wybierz **Uruchom wszystkie** do uruchomienia testu. Ponieważ test jest uruchomiony pasek stanu u góry okna jest animowany. Na końcu przebiegu testowego pasek zmieni kolor zielony, jeśli wszystkie metody testowe zakończy się pomyślnie lub czerwony Jeśli którykolwiek z testów nie powiedzie się.  
  
3. W takim przypadku test nie powiódł się. Metoda testowa jest przenoszona do **testy zakończone niepomyślnie**. Grupa. Wybierz metodę w Eksploratorze testów, aby wyświetlić szczegóły u dołu okna.  
  
## <a name="BKMK_Fix_your_code_and_rerun_your_tests"></a> Napraw kod i ponownego przeprowadzania testów  
 **Analizuj wyniki testu**  
  
 Wynik testu zawiera komunikat, który opisuje błąd. Dla `AreEquals` metody komunikat wyświetlany, możesz oczekiwanym ((<strong>oczekiwana\<*XXX*></strong>parametr) i co zostało rzeczywiście przesłane ( **Rzeczywiste\<*YYY*>** parametru). Rezultatem było saldo od salda początkowego, ale zamiast tego wzrosło o kwotę wycofania.  
  
 Ponowne testy kodu pokazuje, że test jednostkowy zdołały usterkę. Kwota wybrana z konta jest dodawana do salda konta, po powinna być odejmowana.  
  
 **Należy poprawić usterkę**  
  
 Aby poprawić ten błąd, wystarczy zamienić linię  
  
```csharp  
m_balance += amount;  
```  
  
 with  
  
```csharp  
m_balance -= amount;  
```  
  
 **Uruchom ponownie test**  
  
 W Eksploratorze testów wybierz **Uruchom wszystkie** do ponownego uruchomienia testu. Czerwony/zielony pasek zmienia kolor na zielony a test przenoszony jest do **testy zakończone powodzeniem** grupy.  
  
## <a name="BKMK_Use_unit_tests_to_improve_your_code"></a> Użyj testów jednostkowych, aby poprawić kod  
 W tej sekcji opisano, jak proces iteracyjny analizy, tworzenie testów jednostkowych i Refaktoryzacja może pomóc zwiększyć kodu produkcyjnego, bardziej niezawodnego i skutecznego.  
  
 **Analizuj problemy**  
  
 Po utworzeniu metody testowej, aby upewnić się, że poprawna liczba jest prawidłowo odejmowana w `Debit` metody, można przejść do pozostałych przypadków w oryginalnej analizie:  
  
1. Metoda zgłasza `ArgumentOutOfRangeException` Jeśli kwota debet jest większa niż saldo.  
  
2. Zgłasza również `ArgumentOutOfRangeException` Jeśli kwota debet jest mniejsza niż zero.  
  
   **Utwórz metody testowe**  
  
   Pierwsza próba tworzenia metody testowej w celu rozwiązania tych problemów wydaje się być obiecująca:  
  
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
  
 Używamy <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> atrybutu do potwierdzenia, że zgłoszono poprawny wyjątek. Atrybut powoduje, że test zakończył się niepowodzeniem, chyba że `ArgumentOutOfRangeException` zgłaszany. Uruchamianie testu z zarówno dodatnimi jak i ujemne `debitAmount` wartości i tymczasowe modyfikowanie testowaną metodę Aby zgłosić generyczny wyjątek <xref:System.ApplicationException> gdy kwota jest mniejsza od zera pokazuje, że test działa poprawnie. Aby przetestować przypadek, gdy wybierana kwota jest większa niż saldo, wszystko, co potrzeba zrobić to:  
  
1. Tworzenie nowej metody testowej, o nazwie `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`.  
  
2. Skopiuj ciało metody z `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` do nowej metody.  
  
3. Ustaw `debitAmount` na liczbę większą niż saldo.  
  
   **Uruchom testy**  
  
   Uruchomione dwóch metod z różnymi wartościami dla `debitAmount` pokazuje, że testy odpowiednio obsługują pozostałe przypadki. Uruchamianie wszystkich trzech testów potwierdza, że wszystkie przypadki w oryginalnej analizy są poprawnie pokryte.  
  
   **Kontynuuj analizę**  
  
   Jednak ostatnie dwie metody testowe są również nieco trudne. Nie możemy pewni który warunek w testowanym kodzie zgłosi wyjątek, kiedy uruchomiony jest każdy test. Niektóre sposób na rozróżnienie tych dwóch warunków byłoby pomocne. Ponieważ przemyśleniu problemu, staje się jasne, że, wiedząc, który warunek został naruszony, zwiększyłaby wzrośnie, nasze zaufanie do testów. Te informacje również najprawdopodobniej będzie pomocna dla mechanizmu produkcji, który obsługuje wyjątek, gdy jest generowany przez testowaną metodę. Generowanie większej ilości informacji, gdy metoda zgłasza wyjątek, by pomóc wszystkim zainteresowanym, ale `ExpectedException` atrybutu nie może dostarczyć te informacje...  
  
   Ponownie analizując testowaną metodę widzimy obie instrukcje warunkowe używają `ArgumentOutOfRangeException` Konstruktor, który pobiera nazwę argumentu jako parametr:  
  
```csharp  
throw new ArgumentOutOfRangeException("amount");  
```  
  
 Z wyszukiwania biblioteki MSDN możemy odkryć, że istnieje konstruktor, który zgłasza znacznie bogatsze informacje. <xref:System.ArgumentOutOfRangeException.%23ctor%2A>`(String, Object, String)` zawiera nazwę argumentu, wartość argumentu i wiadomość zdefiniowanych przez użytkownika. Możemy refaktoryzować testowaną metodę Aby użyć tego konstruktora. Nawet lepiej możemy użyć publicznie dostępnych typów elementów członkowskich do określenia błędów.  
  
 **Refaktoryzuj testowany kod**  
  
 Najpierw należy zdefiniować dwie stałe dla komunikatów o błędach w zakresie klasy:  
  
```csharp  
// class under test  
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";  
public const string DebitAmountLessThanZeroMessage = "Debit amount less than zero";  
```  
  
 Następnie należy zmodyfikować dwie instrukcje warunkowe w `Debit` metody:  
  
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
  
 **Refaktoryzuj metody testowe**  
  
 W metodzie testowej, należy najpierw usunąć `ExpectedException` atrybutu. W jego miejscu możemy przechwytujemy zgłoszony wyjątek i sprawdź, czy został zgłoszony w poprawnej instrukcji warunkowej. Jednak trzeba teraz zdecydować pomiędzy dwiema opcjami sprawdzenia pozostałych warunków. Na przykład w `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` metody, możemy wykonać jedną z następujących czynności:  
  
- Potwierdź, że `ActualValue` właściwości wyjątku (drugi parametr `ArgumentOutOfRangeException` konstruktora) jest większa niż saldo początkowe. Ta opcja wymaga testowania `ActualValue` właściwości wyjątku względem `beginningBalance` zmiennej metody testowej, a następnie wymaga również upewnij się, że `ActualValue` jest większa niż zero.  
  
- Potwierdź, że wiadomość (trzeci parametr konstruktora) zawiera `DebitAmountExceedsBalanceMessage` zdefiniowane w `BankAccount` klasy.  
  
  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> Metody w środowisku testów jednostkowych firmy Microsoft pozwala na sprawdzenie drugiej opcji bez obliczeń, które są wymagane przy pierwszej opcji.  
  
  Druga próba przeglądu `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` może wyglądać jak:  
  
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
  
 **Ponów test, przepisz i Analizuj ponownie**  
  
 Podczas ponownego testowania metod z różnymi wartościami, można napotkać następujące fakty:  
  
1. Zostanie przechwycony poprawny błąd przy użyciu asercja gdzie `debitAmount` jest większa niż saldo, `Contains` przekazuje assert, wyjątek jest ignorowany i dlatego metoda test kończy się powodzeniem. Jest to oczekiwane zachowanie.  
  
2. Jeśli używamy `debitAmount` jest mniejszy niż 0, asercja nie powiedzie się, ponieważ zwracany jest niewłaściwy komunikat o błędzie. Asercja również kończy się niepowodzeniem, jeśli przedstawimy tymczasowy `ArgumentOutOfRange` wyjątek w innym punkcie ścieżki kodu testowanej metody. Ten przypadek jest dobra.  
  
3. Jeśli `debitAmount` wartość jest prawidłowa (czyli mniejsza niż saldo, ale większa niż zero, żaden wyjątek nie jest przechwytywany, więc asercja nigdy nie zostanie przechwycona. Metoda test kończy się powodzeniem. To nie jest dobry, ponieważ chcemy testowanej metody, aby zakończyć się niepowodzeniem, jeśli jest zgłaszany żaden wyjątek.  
  
   Trzeci fakt jest usterką w testowanej metodzie. Aby spróbować rozwiązać ten problem, można dodać <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> assert na koniec testowanej metody, aby obsłużyć przypadek, gdzie jest zgłaszany żaden wyjątek.  
  
   Jednak ponowne przetestowanie pokazuje, że test wypadnie niepomyślnie Jeśli przechwytywany jest poprawny wyjątek. Instrukcja catch resetuje wyjątek i metoda kontynuuje wykonywanie, kończąc się niepowodzeniem przy nowej asercji. Aby rozwiązać nowy problem, można dodać `return` instrukcji znajdującej się po `StringAssert`. Ponowne przetestowanie potwierdza, że mają rozwiązaliśmy nasze problemy związane z. Ostateczna wersji `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` wygląda podobnie do następującego:  
  
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
  
 W tej sekcji końcowej praca, że wykonana nad ulepszeniem kodu testu doprowadziła do bardziej niezawodnych i wartościowych metod testowych. Ale co ważniejsze, dodatkowe analizy doprowadziły również do lepszego kodu, w testowanym projekcie.
