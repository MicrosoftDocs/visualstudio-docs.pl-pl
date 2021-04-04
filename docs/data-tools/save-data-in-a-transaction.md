---
title: 'Przewodnik: zapisywanie danych w transakcji'
description: W tym instruktażu zapoznaj się z tematem zapisywanie danych w transakcji przy użyciu przestrzeni nazw System. Transactions w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/08/2017
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: a5933a8713a1d4b371672be83a56d0323f5043b9
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216088"
---
# <a name="walkthrough-save-data-in-a-transaction"></a>Przewodnik: zapisywanie danych w transakcji

W tym instruktażu pokazano, jak zapisywać dane w transakcji przy użyciu <xref:System.Transactions> przestrzeni nazw. W tym instruktażu utworzysz aplikację Windows Formsową. Użyjesz Kreatora konfiguracji źródła danych, aby utworzyć zestaw danych dla dwóch tabel w przykładowej bazie danych Northwind. Dodasz kontrolki powiązane z danymi do formularza systemu Windows, a następnie zmodyfikujesz kod dla przycisku zapisu BindingNavigator, aby zaktualizować bazę danych wewnątrz elementu TransactionScope.

## <a name="prerequisites"></a>Wymagania wstępne

W tym instruktażu jest stosowana SQL Server Express LocalDB i Przykładowa baza danych Northwind.

1. Jeśli nie masz SQL Server Express LocalDB, zainstaluj go na [stronie pobierania SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)lub za pośrednictwem **Instalator programu Visual Studio**. W Instalator programu Visual Studio SQL Server Express LocalDB można zainstalować w ramach obciążeń **programistycznych programu .NET Desktop** lub pojedynczego składnika.

2. Zainstaluj przykładową bazę danych Northwind, wykonując następujące kroki:

    1. W programie Visual Studio Otwórz okno **Eksplorator obiektów SQL Server** . (Eksplorator obiektów SQL Server jest instalowany jako część obciążenia **magazynu i przetwarzania danych** w Instalator programu Visual Studio). Rozwiń węzeł **SQL Server** . Kliknij prawym przyciskiem myszy wystąpienie LocalDB i wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Skopiuj [skrypt języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją danymi.

    3. Wklej skrypt T-SQL do edytora zapytań, a następnie wybierz przycisk Execute ( **Wykonaj** ).

       Po krótkim czasie zapytanie kończy działanie i zostanie utworzona baza danych Northwind.

## <a name="create-a-windows-forms-application"></a>Tworzenie aplikacji Windows Forms

Pierwszym krokiem jest utworzenie **aplikacji Windows Forms**.

1. W programie Visual Studio w menu **plik** wybierz pozycję **Nowy**  >  **projekt**.

2. Rozwiń pozycję **Visual C#** lub **Visual Basic** w okienku po lewej stronie, a następnie wybierz pozycję **Windows Desktop**.

3. W środkowym okienku wybierz typ projektu **aplikacji Windows Forms** .

4. Nazwij projekt **SavingDataInATransactionWalkthrough**, a następnie wybierz przycisk **OK**.

     Projekt **SavingDataInATransactionWalkthrough** został utworzony i dodany do **Eksplorator rozwiązań**.

## <a name="create-a-database-data-source"></a>Tworzenie źródła danych bazy danych

Ten krok powoduje użycie **Kreatora konfiguracji źródła danych** w celu utworzenia źródła danych na podstawie `Customers` tabel i `Orders` w przykładowej bazie danych Northwind.

1. Aby otworzyć okno **źródła danych** , w menu **dane** wybierz pozycję **Pokaż źródła danych**.

2. W oknie **źródła danych** wybierz pozycję **Dodaj nowe źródło danych** , aby uruchomić **Kreatora konfiguracji źródła danych**.

3. Na ekranie **Wybierz typ źródła danych** wybierz pozycję **baza danych**, a następnie wybierz przycisk **dalej**.

4. Na ekranie **Wybierz połączenie danych** wykonaj jedną z następujących czynności:

    - Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

         -lub-

    - Wybierz pozycję **nowe połączenie** , aby uruchomić okno dialogowe **Dodawanie/modyfikowanie połączenia** i utworzyć połączenie z bazą danych Northwind.

5. Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie wybierz przycisk **dalej**.

6. Na ekranie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** wybierz pozycję **dalej**.

7. Na ekranie **Wybierz obiekty bazy danych** rozwiń węzeł **tabele** .

8. Wybierz `Customers` tabele i `Orders` , a następnie wybierz pozycję **Zakończ**.

     **NorthwindDataSet** jest dodawany do projektu, a `Customers` `Orders` tabele i są wyświetlane w oknie **źródła danych** .

## <a name="add-controls-to-the-form"></a>Dodawanie kontrolek do formularza

Można utworzyć formanty powiązane z danymi, przeciągając elementy z okna **źródła danych** na formularz.

1. W oknie **źródła danych** rozwiń węzeł **klienci** .

2. Przeciągnij główny węzeł **Customers** z okna **źródła danych** na **formularz Form1**.

   <xref:System.Windows.Forms.DataGridView>Kontrolka i pasek narzędzi ( <xref:System.Windows.Forms.BindingNavigator> ) na potrzeby nawigowania po rekordach pojawiają się w formularzu. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter` , <xref:System.Windows.Forms.BindingSource> i <xref:System.Windows.Forms.BindingNavigator> pojawia się na pasku składnika.

3. Przeciągnij węzeł powiązane **zamówienia** (nie główny węzeł **zamówienia** , ale węzeł powiązanej tabeli podrzędnej poniżej kolumny **faks** ) na formularzu poniżej **customersDataGridView**.

   <xref:System.Windows.Forms.DataGridView>Pojawia się w formularzu. `OrdersTableAdapter`I <xref:System.Windows.Forms.BindingSource> pojawia się na pasku składnika.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Dodawanie odwołania do zestawu System. Transactions

Transakcje korzystają z <xref:System.Transactions> przestrzeni nazw. Odwołanie projektu do zestawu System. Transactions nie jest domyślnie dodawane, więc należy je dodać ręcznie.

### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Aby dodać odwołanie do pliku DLL system. Transactions

1. W menu **projekt** wybierz polecenie **Dodaj odwołanie**.

2. Wybierz pozycję **System. Transactions** (na karcie **.NET** ), a następnie wybierz przycisk **OK**.

     Odwołanie do elementu **System. Transactions** jest dodawane do projektu.

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>Modyfikuj kod na przycisku SaveItem BindingNavigator

W przypadku pierwszej tabeli opuszczonej w formularzu kod jest domyślnie dodawany do `click` zdarzenia przycisku Zapisz w <xref:System.Windows.Forms.BindingNavigator> . Musisz ręcznie dodać kod, aby zaktualizować wszystkie dodatkowe tabele. W tym instruktażu Refaktoryzacja istniejący kod Zapisz z programu obsługi zdarzeń kliknięcia przycisku Zapisz. Tworzymy również kilka metod, aby zapewnić określoną funkcję aktualizacji w zależności od tego, czy należy dodać czy usunąć wiersz.

### <a name="to-modify-the-auto-generated-save-code"></a>Aby zmodyfikować wygenerowany automatycznie kod zapisu

1. Wybierz przycisk **Zapisz** na **CustomersBindingNavigator** (przycisk z ikoną dyskietki).

2. Zastąp metodę `CustomersBindingNavigatorSaveItem_Click` poniższym kodem:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet4":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet4":::

Kolejność uzgadniania zmian związanych z danymi jest następująca:

- Usuń rekordy podrzędne. (W tym przypadku Usuń rekordy z `Orders` tabeli).

- Usuń rekordy nadrzędne. (W tym przypadku Usuń rekordy z `Customers` tabeli).

- Wstaw rekordy nadrzędne. (W tym przypadku Wstaw rekordy w `Customers` tabeli).

- Wstaw rekordy podrzędne. (W tym przypadku Wstaw rekordy w `Orders` tabeli).

### <a name="to-delete-existing-orders"></a>Aby usunąć istniejące zamówienia

- Dodaj następującą `DeleteOrders` metodę do **formularza Form1**:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet5":::

### <a name="to-delete-existing-customers"></a>Aby usunąć istniejących klientów

- Dodaj następującą `DeleteCustomers` metodę do **formularza Form1**:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet6":::

### <a name="to-add-new-customers"></a>Aby dodać nowych klientów

- Dodaj następującą `AddNewCustomers` metodę do **formularza Form1**:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet7":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet7":::

### <a name="to-add-new-orders"></a>Aby dodać nowe zamówienia

- Dodaj następującą `AddNewOrders` metodę do **formularza Form1**:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet8":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet8":::

## <a name="run-the-application"></a>Uruchamianie aplikacji

Naciśnij klawisz **F5** , aby uruchomić aplikację.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: zapisywanie danych przy użyciu transakcji](../data-tools/save-data-by-using-a-transaction.md)
- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
