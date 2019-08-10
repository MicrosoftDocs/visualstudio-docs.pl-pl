---
title: Tworzenie prostej aplikacji danych przy użyciu pakietu ADO.NET
ms.date: 08/23/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 98185eb44bc598d83eddd2690d4a321f8880f014
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925702"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>Tworzenie prostej aplikacji danych przy użyciu pakietu ADO.NET

Gdy tworzysz aplikację, która manipuluje danymi w bazie danych, wykonujesz podstawowe zadania, takie jak definiowania ciągów połączeń, wstawiania danych i uruchamianie przechowywanych procedur. Korzystając z tego tematu, można wykryć, jak korzystać z bazy danych z w ramach prostą aplikację "formularzy nad danymi" Windows Forms przy użyciu języka Visual C# lub Visual Basic i ADO.NET.  Wszystkie technologie danych .NET — w tym zestawy danych, LINQ to SQL i Entity Framework — ostatecznie wykonaj kroki, które są bardzo podobne do tych przedstawione w tym artykule.

W tym artykule przedstawiono prosty sposób pobrać dane z bazy danych w szybki sposób. Jeśli aplikacja musi modyfikować dane w sposób nietrywialnymi i aktualizują bazę danych, należy rozważyć używający narzędzia Entity Framework i korzystanie z danych powiązywanie kontrolek interfejsu użytkownika na zmiany w danych bazowych są synchronizowane automatycznie.

> [!IMPORTANT]
> W celu uproszczenia kodu nie zawiera obsługi wyjątków gotowych do produkcji.

## <a name="prerequisites"></a>Wymagania wstępne

Aby utworzyć aplikację, będą potrzebne:

- Program Visual Studio.

- SQL Server Express LocalDB. Jeśli nie masz programu SQL Server Express LocalDB, możesz zainstalować go z [stronę pobierania programu SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express).

W tym temacie założono, że znasz podstawowe funkcje środowiska IDE programu Visual Studio i można utworzyć aplikacji Windows Forms, dodawać formularze do projektu, umieszczać przyciski i inne formanty w formularzach, ustaw właściwości kontrolek i kodować proste zdarzenia. Jeśli nie masz doświadczenia z tych zadań, zalecamy wykonanie [wprowadzenie do wizualizacji C# i Visual Basic](../ide/quickstart-visual-basic-console.md) tematu przed rozpoczęciem tego instruktażu.

## <a name="set-up-the-sample-database"></a>Konfigurowanie przykładowej bazy danych

Tworzenie przykładowej bazy danych, wykonując następujące czynności:

1. W programie Visual Studio, otwórz **Eksploratora serwera** okna.

2. Kliknij prawym przyciskiem myszy **połączeń danych** i wybierz polecenie **Tworzenie nowej bazy danych SQL Server**.

3. W **nazwy serwera** tekstu wprowadź **(localdb) \mssqllocaldb**.

4. W **nazwę nowej bazy danych** tekstu wprowadź **sprzedaży**, następnie wybierz **OK**.

     Pusty **sprzedaży** bazy danych zostanie utworzony i dodany do węzła połączenia danych w Eksploratorze serwera.

5. Kliknij prawym przyciskiem myszy **sprzedaży** połączenia danych i wybierz pozycję **nowe zapytanie**.

     Zostanie otwarte okno edytora zapytań.

6. Kopiuj [sprzedaży języka Transact-SQL skrypt](https://github.com/MicrosoftDocs/visualstudio-docs/raw/master/docs/data-tools/samples/sales.sql) do Schowka.

7. Wklej skrypt języka T-SQL do edytora zapytań, a następnie wybierz **Execute** przycisku.

     Po przez krótki czas odliczania zapytanie, a następnie są tworzone obiekty bazy danych. Baza danych zawiera dwie tabele: Klient i zamówienia. Te tabele zawierają początkowo żadnych danych, ale możesz dodać dane po uruchomieniu aplikacji, który utworzysz. Baza danych zawiera również czterech prostych przechowywanych procedur.

## <a name="create-the-forms-and-add-controls"></a>Tworzenie formularzy i dodawanie formantów

1. Utwórz projekt dla aplikacji Windows Forms i nadaj mu nazwę **SimpleDataApp**.

    Program Visual Studio tworzy projekt i kilka plików, w tym pusty formularz Windows o nazwie **Form1**.

2. Dodaj dwie formy Windows do projektu tak, że ma trzy formy, a następnie nadaj im następujące nazwy:

   - **Nawigacja**

   - **NewCustomer**

   - **FillOrCancel**

3. Dla każdego formularza należy dodać pola tekstowe, przyciski i inne formanty, które pojawiają się na poniższych ilustracjach. Dla każdego formantu należy ustawić właściwości opisywane przez tabele.

   > [!NOTE]
   > Formanty etykiety i pole grupy zwiększają przejrzystość, ale nie są używane w kodzie.

   **Formularz nawigacji**

   ![Okno dialogowe nawigacji](../data-tools/media/simpleappnav.png)

|Formanty formularza nawigacji|Właściwości|
| - |----------------|
|Przycisk|Nazwa = btnGoToAdd|
|Przycisk|Name = btnGoToFillOrCancel|
|Przycisk|Nazwa = btnExit|

**Formularz NewCustomer**

![Dodawanie nowego klienta i złóż zamówienie](../data-tools/media/simpleappnewcust.png)

|Formanty formularza NewCustomer|Właściwości|
| - |----------------|
|TextBox|Nazwa = txtCustomerName|
|TextBox|Nazwa = txtCustomerID<br /><br /> ReadOnly = PRAWDA|
|Przycisk|Nazwa = btnCreateAccount|
|NumericUpdown|MiejscaDziesiętne = 0<br /><br /> Maksymalna = 5000<br /><br /> Nazwa = numOrderAmount|
|DateTimePicker|Format = krótki<br /><br /> Nazwa = dtpOrderDate|
|Przycisk|Nazwa = btnPlaceOrder|
|Przycisk|Nazwa = btnAddAnotherAccount|
|Przycisk|Nazwa = btnAddFinish|

**Formularz FillOrCancel**

![Wypełnij lub Anuluj zamówienia](../data-tools/media/simpleappcancelfill.png)

|Formanty formularza FillOrCancel|Właściwości|
| - |----------------|
|TextBox|Nazwa = txtOrderID|
|Przycisk|Nazwa = btnFindByOrderID|
|DateTimePicker|Format = krótki<br /><br /> Nazwa = dtpFillDate|
|DataGridView|Nazwa = dgvCustomerOrders<br /><br /> ReadOnly = PRAWDA<br /><br /> RowHeadersVisible = False|
|Przycisk|Nazwa = btnCancelOrder|
|Przycisk|Nazwa = btnFillOrder|
|Przycisk|Nazwa = btnFinishUpdates|

## <a name="store-the-connection-string"></a>Store parametry połączenia
Gdy Twoja aplikacja próbuje otworzyć połączenie z bazą danych, aplikacja musi mieć dostęp do parametrów połączenia. Aby uniknąć wpisywania ciągu ręcznie w każdym formularzu, Przechowaj ciąg w *App.config* plik w projekcie i Utwórz metodę, która zwraca ciąg, gdy metoda jest wywoływana z jakiegokolwiek formularza w aplikacji.

Parametry połączenia można znaleźć, klikając prawym przyciskiem myszy **sprzedaży** połączenia danych w **Eksploratora serwera** i wybierając pozycję **właściwości**. Znajdź **ConnectionString** właściwości, następnie za pomocą **Ctrl**+**A**, **Ctrl**+**C**  zaznacz i skopiuj ciąg do Schowka.

1. Jeśli używasz C#w **Eksploratora rozwiązań**, rozwiń węzeł **właściwości** węzła w ramach projektu, a następnie otwórz **Settings.settings** pliku.
    Jeśli używasz języka Visual Basic w **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki**, rozwiń węzeł **mój projekt** węzeł, a następnie otwórz **Settings.settings** pliku.

2. W **nazwa** kolumny, wprowadź `connString`.

3. W **typu** listy wybierz **(parametry połączenia)** .

4. W **zakres** listy wybierz **aplikacji**.

5. W **wartość** kolumny, wprowadź parametry połączenia (bez żadnego poza cudzysłowy), a następnie zapisz zmiany.

> [!NOTE]
> W rzeczywistej aplikacji, należy przechowywać parametry połączenia bezpieczne, zgodnie z opisem w [parametry połączenia i pliki konfiguracyjne](/dotnet/framework/data/adonet/connection-strings-and-configuration-files).

## <a name="write-the-code-for-the-forms"></a>Pisanie kodu dla formularzy

Ta sekcja zawiera krótki przegląd informacji na temat działania każdego formularza. Zapewnia również kod, który definiuje podstawowej logiki po kliknięciu przycisku w formularzu.

### <a name="navigation-form"></a>Formularz nawigacji

Formularz nawigacji otwiera się po uruchomieniu aplikacji. **Dodaj konto** przycisk służy do otwierania formularza NewCustomer. **Realizuj lub Anuluj zamówienia** przycisk służy do otwierania formularza FillOrCancel. **Zakończenia** przycisk zamyka aplikację.

#### <a name="make-the-navigation-form-the-startup-form"></a>Wykonaj formularz początkowy formularz nawigacji

Jeśli używasz C#w **Eksploratora rozwiązań**, otwórz **Program.cs**, a następnie zmień `Application.Run` wiersz do tego: `Application.Run(new Navigation());`

Jeśli używasz języka Visual Basic w **Eksploratora rozwiązań**, otwórz **właściwości** wybierz **aplikacji** , a następnie wybierz pozycję  **SimpleDataApp.Navigation** w **formularz początkowy** listy.

#### <a name="create-auto-generated-event-handlers"></a>Tworzenie programów do obsługi automatycznego generowania zdarzeń

Kliknij dwukrotnie trzech przycisków w formularzu nawigacji, aby utworzyć metody obsługi zdarzeń puste. Dwukrotne kliknięcie przycisków oferuje również automatycznie wygenerowany kod, plik kodu projektanta, który umożliwia kliknięcia przycisku wywołać zdarzenie.

#### <a name="add-code-for-the-navigation-form-logic"></a>Dodaj kod logiki formularza nawigacji

Na stronie kodowej formularza nawigacji pełną treść metody dla trzech przycisku kliknij obsługi zdarzeń jak pokazano w poniższym kodzie.

[!code-csharp[Navigation#1](../data-tools/codesnippet/CSharp/SimpleDataApp/Navigation.cs#1)]
[!code-vb[Navigation#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/Navigation.vb#1)]

### <a name="newcustomer-form"></a>Formularz NewCustomer

Kiedy wpisujesz nazwę klienta, a następnie wybierz pozycję **Utwórz konto** przycisk, formularz NewCustomer tworzy konto klienta, a program SQL Server zwraca wartość IDENTITY jako nowy identyfikator klienta. Następnie można złożyć zamówienia na nowe konto, określając wielkość i datę zamówienia i wybierając **złóż zamówienie** przycisku.

#### <a name="create-auto-generated-event-handlers"></a>Tworzenie programów do obsługi automatycznego generowania zdarzeń

Utwórz puste kliknij obsługi zdarzeń dla każdego przycisku w formularzu NewCustomer przez dwukrotne kliknięcie na każdym z czterech przycisków. Dwukrotne kliknięcie przycisków oferuje również automatycznie wygenerowany kod, plik kodu projektanta, który umożliwia kliknięcia przycisku wywołać zdarzenie.

#### <a name="add-code-for-the-newcustomer-form-logic"></a>Dodaj kod logiki formularza NewCustomer

Aby wykonać logikę formularz NewCustomer, wykonaj następujące kroki.

1. Przenieś `System.Data.SqlClient` przestrzeni nazw do zakresu, aby nie trzeba było w pełni kwalifikowania nazwy składowych.

     ```csharp
     using System.Data.SqlClient;
     ```

     ```vb
     Imports System.Data.SqlClient
     ```

2. Dodaj niektóre zmienne i metody pomocnika do klasy, jak pokazano w poniższym kodzie.

     [!code-csharp[NewCustomer#1](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#1)]
     [!code-vb[NewCustomer#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#1)]

3. Pełne procedury obsługi zdarzeń kliknij treści metod dla czterech przycisku, jak pokazano w poniższym kodzie.

     [!code-csharp[NewCustomer#2](../data-tools/codesnippet/CSharp/SimpleDataApp/NewCustomer.cs#2)]
     [!code-vb[NewCustomer#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/NewCustomer.vb#2)]

### <a name="fillorcancel-form"></a>Formularz FillOrCancel

Formularz FillOrCancel uruchamia zapytanie do zwrotu zamówienia, gdy wprowadzasz identyfikator zamówienia, a następnie kliknij przycisk **Znajdź zamówienie** przycisku. Zwracany wiersz wyświetla się w siatce danych tylko do odczytu. Możesz oznaczyć porządek jako anulowany (X), jeśli zostanie wybrana **Anuluj porządek** przycisku, lub możesz oznaczyć porządek jako wypełniony (F) po wybraniu **Wypełnij porządek** przycisku. Jeśli wybierzesz **Znajdź zamówienie** przycisk ponownie, pojawi się uaktualniony wiersz.

#### <a name="create-auto-generated-event-handlers"></a>Tworzenie programów do obsługi automatycznego generowania zdarzeń

Utwórz puste kliknij obsługi zdarzeń dla czterech przycisków w formularzu FillOrCancel przez dwukrotne kliknięcie przycisków. Dwukrotne kliknięcie przycisków oferuje również automatycznie wygenerowany kod, plik kodu projektanta, który umożliwia kliknięcia przycisku wywołać zdarzenie.

#### <a name="add-code-for-the-fillorcancel-form-logic"></a>Dodaj kod logiki formularza FillOrCancel

Aby wykonać logikę formularza FillOrCancel, wykonaj następujące kroki.

1. Przenieś następujące dwie przestrzenie nazw do zakresu, dzięki czemu nie trzeba do pełnej kwalifikacji nazwy przez nie składowe.

     ```csharp
     using System.Data.SqlClient;
     using System.Text.RegularExpressions;
     ```

     ```vb
     Imports System.Data.SqlClient
     Imports System.Text.RegularExpressions
     ```

2. Dodaj zmienną i pomocnika metodę do klasy, jak pokazano w poniższym kodzie.

     [!code-csharp[FillOrCancel#1](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#1)]
     [!code-vb[FillOrCancel#1](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#1)]

3. Pełne procedury obsługi zdarzeń kliknij treści metod dla czterech przycisku, jak pokazano w poniższym kodzie.

     [!code-csharp[FillOrCancel#2](../data-tools/codesnippet/CSharp/SimpleDataApp/FillOrCancel.cs#2)]
     [!code-vb[FillOrCancel#2](../data-tools/codesnippet/VisualBasic/SimpleDataApp/FillOrCancel.vb#2)]

## <a name="test-your-application"></a>Testowanie aplikacji

Wybierz **F5** klucz, aby skompilować i przetestować aplikację po zakodowaniu każdej obsługi zdarzenia Click, a następnie po zakończenia kodowania.

## <a name="see-also"></a>Zobacz także

- [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
