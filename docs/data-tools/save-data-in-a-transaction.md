---
title: 'Przewodnik: Zapisywanie danych w ramach transakcji'
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: fc2626ba0efab60921ed721b9f06fec28c66f58b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55932277"
---
# <a name="walkthrough-save-data-in-a-transaction"></a>Przewodnik: Zapisywanie danych w ramach transakcji

W tym instruktażu pokazano, jak zapisywanie danych w ramach transakcji przy użyciu <xref:System.Transactions> przestrzeni nazw. W tym instruktażu utworzysz aplikację Windows Forms. Użyjesz kreatora konfiguracji źródła danych, aby utworzyć zestaw danych dla dwóch tabel w bazie danych Northwind. Należy dodać kontrolki powiązania danych do postaci Windows i zmodyfikujesz kod BindingNavigator firmy przycisk zapisywania można zaktualizować bazy danych wewnątrz elementu TransactionScope.

## <a name="prerequisites"></a>Wymagania wstępne

Ten przewodnik korzysta z programu SQL Server Express LocalDB i bazie danych Northwind.

1.  Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [stronę pobierania programu SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), lub za pomocą **Instalatora programu Visual Studio**. W Instalatorze programu Visual Studio, można zainstalować programu SQL Server Express LocalDB, jako część **programowanie aplikacji klasycznych dla platformy .NET** obciążenie, lub jako poszczególnych składników.

2.  Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:

    1. W programie Visual Studio, otwórz **Eksplorator obiektów SQL Server** okna. (Eksplorator obiektów SQL Server jest instalowany jako część **przechowywanie i przetwarzanie danych** obciążenie w Instalatorze programu Visual Studio.) Rozwiń **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w ramach wystąpienia LocalDB, a następnie wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Kopiuj [skryptów języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt języka T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją z danymi.

    3. Wklej skrypt języka T-SQL do edytora zapytań, a następnie wybierz **Execute** przycisku.

       Po pewnym czasie odliczania zapytania i utworzeniu bazy danych Northwind.

## <a name="create-a-windows-forms-application"></a>Tworzenie aplikacji Windows Forms

Pierwszym krokiem jest utworzenie **aplikacja interfejsu Windows Forms**.

1. W programie Visual Studio na **pliku** menu, wybierz opcję **New** > **projektu**.

2. Rozwiń **Visual C#** lub **języka Visual Basic** w okienku po lewej stronie, a następnie zaznacz **pulpitu Windows**.

3. W środkowym okienku wybierz **Windows Forms App** typ projektu.

4. Nadaj projektowi nazwę **SavingDataInATransactionWalkthrough**, a następnie wybierz **OK**.

     **SavingDataInATransactionWalkthrough** projekt zostanie utworzony i dodany do **Eksploratora rozwiązań**.

## <a name="create-a-database-data-source"></a>Tworzenie źródła danych bazy danych

Ten krok używa **Kreatora konfiguracji źródła danych** można utworzyć źródła danych, na podstawie `Customers` i `Orders` tabel w bazie danych Northwind.

1.  Aby otworzyć **źródeł danych** okna na **danych** menu, wybierz opcję **Pokaż źródła danych**.

2.  W **źródeł danych** wybierz **Dodaj nowe źródło danych** można uruchomić **Kreatora konfiguracji źródła danych**.

3.  Na **wybierz typ źródła danych** ekranu, wybierz opcję **bazy danych**, a następnie wybierz pozycję **dalej**.

4.  Na **wybierz połączenie danych** wykonaj ekranu, jedną z następujących czynności:

    -   Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

         —lub—

    -   Wybierz **nowe połączenie** można uruchomić **Dodawanie/modyfikowanie połączenia** okna dialogowego pole, a następnie utwórz połączenie z bazą danych Northwind.

5.  Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie wybierz **dalej**.

6.  Na **Zapisz parametry połączenia do pliku konfiguracji aplikacji** ekranu, wybierz opcję **dalej**.

7.  Na **wybierz obiekty bazy danych** ekranu, a następnie rozwiń **tabel** węzła.

8.  Wybierz `Customers` i `Orders` tabel, a następnie wybierz **Zakończ**.

     **NorthwindDataSet** zostanie dodany do projektu i `Customers` i `Orders` tabele są wyświetlane w **źródeł danych** okna.

## <a name="add-controls-to-the-form"></a>Dodawanie formantów do formularza

Można utworzyć formanty powiązane z danymi przez przeciąganie elementów z **źródeł danych** okna do formularza.

1. W **źródeł danych** okna, rozwiń węzeł **klientów** węzła.

2. Przeciągnij główny **klientów** węzła z **źródeł danych** okna na **Form1**.

   A <xref:System.Windows.Forms.DataGridView> kontroli i pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania między rekordami wyświetlanymi w formularzu. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane w zasobniku składnika.

3. Przeciągnij powiązane **zamówienia** węzła (nie main **zamówienia** węzła, ale poniżej węzła powiązanej tabeli podrzędnej **faks** kolumny) do poniższego formularza  **CustomersDataGridView**.

   A <xref:System.Windows.Forms.DataGridView> pojawia się w formularzu. `OrdersTableAdapter` i <xref:System.Windows.Forms.BindingSource> są wyświetlane w zasobniku składnika.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Dodaj odwołanie do zestawu System.Transactions

Użyj transakcji <xref:System.Transactions> przestrzeni nazw. Odwołanie do zestawu system.transactions nie zostanie dodany domyślnie, więc trzeba ręcznie dodać ją.

### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Aby dodać odwołanie do pliku System.Transactions DLL

1.  Na **projektu** menu, wybierz opcję **Dodaj odwołanie**.

2.  Wybierz **System.Transactions** (na **.NET** karty), a następnie wybierz pozycję **OK**.

     Odwołanie do **System.Transactions** zostanie dodany do projektu.

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>Modyfikowanie kodu BindingNavigator SaveItem przycisku

Jako pierwszą tabelę upuszczone na formularzu, kod jest dodawany domyślnie `click` zdarzeń zapisu znajdujący się na <xref:System.Windows.Forms.BindingNavigator>. Należy ręcznie dodać kod, aby zaktualizować wszystkie dodatkowe tabele. W tym przewodniku refaktoryzacji istniejącego Zapisz kod poza zapisywania program obsługi zdarzeń kliknięcia przycisku. Musimy również utworzyć kilka więcej metod, które umożliwiają korzystanie z funkcji określonej aktualizacji oparte na tego, czy wiersz musi być dodane lub usunięte.

### <a name="to-modify-the-auto-generated-save-code"></a>Aby zmodyfikować wygenerowaną automatycznie zapisać kod

1.  Wybierz **Zapisz** znajdujący się na **CustomersBindingNavigator** (przycisk z ikoną dyskietki).

2.  Zastąp `CustomersBindingNavigatorSaveItem_Click` metoda następującym kodem:

     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]

Uzgadnianie zmian do powiązanych danych kolejność jest następująca:

-   Usuń rekordy podrzędne. (W tym przypadku usuwania rekordów z `Orders` tabeli.)

-   Usuwanie rekordów nadrzędnych. (W tym przypadku usuwania rekordów z `Customers` tabeli.)

-   Wstawianie rekordów nadrzędnych. (W tym przypadku wstawiania rekordów w `Customers` tabeli.)

-   Wstaw rekordy podrzędne. (W tym przypadku wstawiania rekordów w `Orders` tabeli.)

### <a name="to-delete-existing-orders"></a>Aby usunąć istniejące zamówienia

-   Dodaj następujący kod `DeleteOrders` metody **Form1**:

     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-csharp[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]

### <a name="to-delete-existing-customers"></a>Aby usunąć istniejący klienci

-   Dodaj następujący kod `DeleteCustomers` metody **Form1**:

     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-csharp[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]

### <a name="to-add-new-customers"></a>Aby dodać nowych klientów

-   Dodaj następujący kod `AddNewCustomers` metody **Form1**:

     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-csharp[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]

### <a name="to-add-new-orders"></a>Aby dodać nowe zamówienia

-   Dodaj następujący kod `AddNewOrders` metody **Form1**:

     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-csharp[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]

## <a name="run-the-application"></a>Uruchamianie aplikacji

Naciśnij klawisz **F5** do uruchomienia aplikacji.

## <a name="see-also"></a>Zobacz także

- [Porady: zapisywanie danych przy użyciu transakcji](../data-tools/save-data-by-using-a-transaction.md)
- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)