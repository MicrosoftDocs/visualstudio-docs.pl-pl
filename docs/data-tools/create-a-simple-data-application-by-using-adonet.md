---
title: Tworzenie prostej aplikacji do obsługi danych za pomocą pakietu ADO.NET
description: Dowiedz się, jak utworzyć prostą aplikację typu "formularze do danych" przy użyciu Windows Forms i ADO.NET w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 08/23/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: c499e36b7ee6bb15980fe89c6185a105681d4d05
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216504"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>Tworzenie prostej aplikacji do obsługi danych za pomocą pakietu ADO.NET

Podczas tworzenia aplikacji, która operuje na danych w bazie danych, wykonywane są podstawowe zadania, takie jak Definiowanie parametrów połączenia, wstawianie danych i uruchamianie procedur składowanych. Postępując zgodnie z tym tematem, można dowiedzieć się, jak korzystać z bazy danych z poziomu prostej Windows Forms "Formularze danych" przy użyciu języka Visual C# lub Visual Basic i ADO.NET.  Wszystkie technologie danych platformy .NET, w tym zestawy, LINQ to SQL i Entity Framework, ostatecznie wykonują czynności, które są bardzo podobne do tych, które przedstawiono w tym artykule.

W tym artykule przedstawiono prosty sposób pobierania danych z bazy danych w sposób szybki. Jeśli aplikacja wymaga modyfikacji danych w sposób nieuproszczony i zaktualizowania bazy danych, należy rozważyć użycie Entity Framework i użycie powiązania danych w celu automatycznego synchronizowania kontrolek interfejsu użytkownika z zmianami danych źródłowych.

> [!IMPORTANT]
> Aby zachować prosty kod, nie obejmuje obsługi wyjątków gotowych do produkcji.

## <a name="prerequisites"></a>Wymagania wstępne

Aby można było utworzyć aplikację, potrzebne są:

- Programu Visual Studio.

- SQL Server Express LocalDB. Jeśli nie masz SQL Server Express LocalDB, możesz go zainstalować ze [strony pobierania SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express).

W tym temacie założono, że znasz podstawowe funkcje środowiska IDE programu Visual Studio i można utworzyć Windows Forms aplikację, dodać formularze do projektu, umieścić przyciski i inne kontrolki na formularzach, ustawić właściwości kontrolek i kod prostych zdarzeń. Jeśli nie masz doświadczenia z tymi zadaniami, zalecamy zakończenie pracy [z programem Visual C# i Visual Basic](../ide/quickstart-visual-basic-console.md) tematu przed rozpoczęciem tego instruktażu.

## <a name="set-up-the-sample-database"></a>Konfigurowanie przykładowej bazy danych

Utwórz przykładową bazę danych, wykonując następujące czynności:

1. W programie Visual Studio Otwórz okno **Eksplorator serwera** .

2. Kliknij prawym przyciskiem myszy pozycję **połączenia danych** , a następnie wybierz pozycję **Utwórz nową bazę danych SQL Server**.

3. W polu tekstowym **Nazwa serwera** wprowadź **(LocalDB) \mssqllocaldb**.

4. W polu tekstowym **Nowa nazwa bazy danych** wprowadź **Sales**, a następnie wybierz **OK**.

     Pusta baza danych **sprzedaży** jest tworzona i dodawana do węzła połączenia danych w Eksplorator serwera.

5. Kliknij prawym przyciskiem myszy połączenie danych **sprzedaży** , a następnie wybierz pozycję **nowe zapytanie**.

     Zostanie otwarte okno edytora zapytań.

6. Skopiuj [skrypt Transact-SQL Sales](https://github.com/MicrosoftDocs/visualstudio-docs/raw/master/docs/data-tools/samples/sales.sql) do Schowka.

7. Wklej skrypt T-SQL do edytora zapytań, a następnie wybierz przycisk Execute ( **Wykonaj** ).

     Po krótkim czasie zapytanie kończy działanie i tworzone są obiekty bazy danych. Baza danych zawiera dwie tabele: klient i zamówienia. Te tabele nie zawierają początkowo żadnych danych, ale możesz dodać dane podczas uruchamiania aplikacji, którą utworzysz. Baza danych zawiera również cztery proste procedury składowane.

## <a name="create-the-forms-and-add-controls"></a>Tworzenie formularzy i Dodawanie kontrolek

1. Utwórz projekt dla Windows Forms aplikacji, a następnie nadaj mu nazwę **SimpleDataApp**.

    Program Visual Studio tworzy projekt i kilka plików, w tym pusty formularz systemu Windows o nazwie **Form1**.

2. Dodaj dwa formularze systemu Windows do projektu, tak aby miało trzy formy, a następnie nadaj im następujące nazwy:

   - **Nawigacja**

   - **NewCustomer**

   - **FillOrCancel**

3. Dla każdego formularza Dodaj pola tekstowe, przyciski i inne kontrolki, które pojawiają się na poniższych ilustracjach. Dla każdej kontrolki ustaw właściwości, które opisano w tabelach.

   > [!NOTE]
   > Pola Grupa i kontrolki etykieta umożliwiają dodawanie przejrzystości, ale nie są używane w kodzie.

   **Formularz nawigacji**

   ![Okno dialogowe nawigacji](../data-tools/media/simpleappnav.png)

|Kontrolki formularza nawigacji|Właściwości|
| - |----------------|
|Przycisk|Nazwa = btnGoToAdd|
|Przycisk|Nazwa = btnGoToFillOrCancel|
|Przycisk|Nazwa = btnExit|

**Formularz NewCustomer**

![Dodaj nowego klienta i umieść zamówienie](../data-tools/media/simpleappnewcust.png)

|Kontrolki formularza NewCustomer|Właściwości|
| - |----------------|
|TextBox|Nazwa = txtCustomerName|
|TextBox|Nazwa = txtCustomerID<br /><br /> ReadOnly = true|
|Przycisk|Nazwa = btnCreateAccount|
|NumericUpdown|DecimalPlaces = 0<br /><br /> Maksimum = 5000<br /><br /> Nazwa = numOrderAmount|
|DateTimePicker|Format = Short<br /><br /> Nazwa = dtpOrderDate|
|Przycisk|Nazwa = btnPlaceOrder|
|Przycisk|Nazwa = btnAddAnotherAccount|
|Przycisk|Nazwa = btnAddFinish|

**Formularz FillOrCancel**

![Wypełnij lub Anuluj zamówienia](../data-tools/media/simpleappcancelfill.png)

|Kontrolki formularza FillOrCancel|Właściwości|
| - |----------------|
|TextBox|Nazwa = txtOrderID|
|Przycisk|Nazwa = btnFindByOrderID|
|DateTimePicker|Format = Short<br /><br /> Nazwa = dtpFillDate|
|DataGridView|Nazwa = dgvCustomerOrders<br /><br /> ReadOnly = true<br /><br /> RowHeadersVisible = FAŁSZ|
|Przycisk|Nazwa = btnCancelOrder|
|Przycisk|Nazwa = btnFillOrder|
|Przycisk|Nazwa = btnFinishUpdates|

## <a name="store-the-connection-string"></a>Przechowywanie parametrów połączenia
Gdy aplikacja próbuje otworzyć połączenie z bazą danych, aplikacja musi mieć dostęp do parametrów połączenia. Aby uniknąć wprowadzania ciągu ręcznie w każdym formularzu, należy przechowywać ciąg w pliku *App.config* w projekcie i utworzyć metodę zwracającą ciąg, gdy metoda jest wywoływana z dowolnej formy w aplikacji.

Parametry połączenia można znaleźć, klikając prawym przyciskiem myszy połączenie danych **sprzedaży** w **Eksplorator serwera** i wybierając pozycję **Właściwości**. Znajdź właściwość **ConnectionString** , a następnie użyj **klawiszy CTRL** + **a**, **Ctrl** + **C** , aby zaznaczyć i skopiować ciąg do Schowka.

1. Jeśli używasz języka C#, w **Eksplorator rozwiązań** rozwiń węzeł **Właściwości** w obszarze projektu, a następnie otwórz plik **Settings. Settings** .
    Jeśli używasz Visual Basic, w **Eksplorator rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki**, rozwiń węzeł **mój projekt** , a następnie otwórz plik **Settings. Settings** .

2. W kolumnie **Nazwa** wprowadź wartość `connString` .

3. Na liście **Typ** wybierz pozycję **(parametry połączenia)**.

4. Z listy **zakres** wybierz pozycję **aplikacja**.

5. W kolumnie **wartość** wprowadź parametry połączenia (bez żadnych cudzysłowów zewnętrznych), a następnie Zapisz zmiany.

> [!NOTE]
> W prawdziwej aplikacji należy przechowywać parametry połączenia bezpiecznie, zgodnie z opisem w temacie [Parametry połączenia i pliki konfiguracji](/dotnet/framework/data/adonet/connection-strings-and-configuration-files).

## <a name="write-the-code-for-the-forms"></a>Napisz kod dla formularzy

Ta sekcja zawiera krótkie przeglądy działania poszczególnych formularzy. Udostępnia również kod, który definiuje podstawową logikę, gdy zostanie kliknięty przycisk na formularzu.

### <a name="navigation-form"></a>Formularz nawigacji

Po uruchomieniu aplikacji zostanie otwarty formularz nawigacji. Przycisk **Dodaj konto** otwiera formularz newCustomer. Przycisk **Wypełnij lub Anuluj zamówienia** powoduje otwarcie formularza FillOrCancel. Przycisk **Zakończ** zamyka aplikację.

#### <a name="make-the-navigation-form-the-startup-form"></a>Ustaw nawigację formularza startowego

Jeśli używasz języka C#, w **Eksplorator rozwiązań** Otwórz **program programu**, a następnie zmień `Application.Run` wiersz na następujący: `Application.Run(new Navigation());`

Jeśli używasz Visual Basic, w **Eksplorator rozwiązań**, Otwórz okno **Właściwości** , wybierz kartę **aplikacja** , a następnie wybierz pozycję **SimpleDataApp. Nawigacja** na liście **formularz startowy** .

#### <a name="create-auto-generated-event-handlers"></a>Utwórz automatycznie generowane programy obsługi zdarzeń

Kliknij dwukrotnie trzy przyciski w formularzu nawigacji, aby utworzyć puste metody obsługi zdarzeń. Dwukrotne kliknięcie przycisków powoduje również dodanie automatycznie generowanego kodu w pliku kodu projektanta, który umożliwia kliknięcie przycisku w celu wygenerowania zdarzenia.

#### <a name="add-code-for-the-navigation-form-logic"></a>Dodawanie kodu dla logiki formularza nawigacji

Na stronie kodowej formularza nawigacji Wypełnij treść metody dla trzech przycisków procedury obsługi zdarzeń, jak pokazano w poniższym kodzie.

:::code language="csharp" source="../data-tools/codesnippet/CSharp/SimpleDataApp/Navigation.cs" id="Snippet1":::
:::code language="vb" source="../data-tools/codesnippet/VisualBasic/SimpleDataApp/Navigation.vb" id="Snippet1":::

### <a name="newcustomer-form"></a>Formularz NewCustomer

Po wprowadzeniu nazwy klienta i wybraniu przycisku **Utwórz konto** formularz newCustomer tworzy konto klienta, a SQL Server zwraca wartość tożsamości jako nowy identyfikator klienta. Następnie możesz złożyć zamówienie dla nowego konta, określając kwotę i datę zamówienia, a następnie wybierając przycisk **Umieść zamówienie** .

#### <a name="create-auto-generated-event-handlers"></a>Utwórz automatycznie generowane programy obsługi zdarzeń

Utwórz pustą procedurę obsługi zdarzeń kliknięcia dla każdego przycisku w formularzu NewCustomer przez dwukrotne kliknięcie każdego z czterech przycisków. Dwukrotne kliknięcie przycisków powoduje również dodanie automatycznie generowanego kodu w pliku kodu projektanta, który umożliwia kliknięcie przycisku w celu wygenerowania zdarzenia.

#### <a name="add-code-for-the-newcustomer-form-logic"></a>Dodawanie kodu dla logiki formularza NewCustomer

Aby ukończyć logikę formularza NewCustomer, wykonaj następujące kroki.

1. Przenieś `System.Data.SqlClient` przestrzeń nazw do zakresu, aby nie trzeba było w pełni kwalifikować nazw jego członków.

     ```csharp
     using System.Data.SqlClient;
     ```

     ```vb
     Imports System.Data.SqlClient
     ```

2. Dodaj do klasy pewne zmienne i metody pomocnicze, jak pokazano w poniższym kodzie.

     :::code language="csharp" source="../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs" id="Snippet1":::
     :::code language="vb" source="../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb" id="Snippet1":::

3. Wypełnij treść metody dla czterech przycisków obsługi zdarzeń, jak pokazano w poniższym kodzie.

     :::code language="csharp" source="../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs" id="Snippet2":::
     :::code language="vb" source="../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb" id="Snippet2":::

### <a name="fillorcancel-form"></a>Formularz FillOrCancel

Formularz FillOrCancel uruchamia zapytanie w celu zwrócenia zamówienia po wprowadzeniu identyfikatora zamówienia, a następnie kliknij przycisk **Znajdź zamówienie** . Zwrócony wiersz pojawia się w siatce danych tylko do odczytu. Możesz oznaczyć zamówienie jako anulowane (X), jeśli wybierzesz przycisk **Anuluj zamówienie** lub możesz oznaczyć zamówienie jako wypełnione (F), jeśli wybierzesz przycisk **Wypełnij zamówienie** . Jeśli wybierzesz przycisk **Znajdź zamówienie** ponownie, zostanie wyświetlony zaktualizowany wiersz.

#### <a name="create-auto-generated-event-handlers"></a>Utwórz automatycznie generowane programy obsługi zdarzeń

Utwórz puste procedury obsługi zdarzeń kliknięcia dla czterech przycisków w formularzu FillOrCancel przez dwukrotne kliknięcie przycisków. Dwukrotne kliknięcie przycisków powoduje również dodanie automatycznie generowanego kodu w pliku kodu projektanta, który umożliwia kliknięcie przycisku w celu wygenerowania zdarzenia.

#### <a name="add-code-for-the-fillorcancel-form-logic"></a>Dodawanie kodu dla logiki formularza FillOrCancel

Aby ukończyć logikę formularza FillOrCancel, wykonaj następujące kroki.

1. Przenieś następujące dwie przestrzenie nazw do zakresu, aby nie trzeba było w pełni kwalifikować się do nazw ich członków.

     ```csharp
     using System.Data.SqlClient;
     using System.Text.RegularExpressions;
     ```

     ```vb
     Imports System.Data.SqlClient
     Imports System.Text.RegularExpressions
     ```

2. Dodaj zmienną i metodę pomocnika do klasy, jak pokazano w poniższym kodzie.

     :::code language="csharp" source="../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs" id="Snippet1":::
     :::code language="vb" source="../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb" id="Snippet1":::

3. Wypełnij treść metody dla czterech przycisków obsługi zdarzeń, jak pokazano w poniższym kodzie.

     :::code language="csharp" source="../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs" id="Snippet2":::
     :::code language="vb" source="../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb" id="Snippet2":::

## <a name="test-your-application"></a>Testowanie aplikacji

Wybierz klawisz **F5** , aby skompilować i przetestować aplikację po wprowadzeniu kodu dla każdej procedury obsługi zdarzeń, a następnie po zakończeniu kodowania.

## <a name="see-also"></a>Zobacz też

- [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
