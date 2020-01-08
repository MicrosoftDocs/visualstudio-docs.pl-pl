---
title: Przekazywanie danych między formularzami
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 358cdc4822aa0da1d980f22196618aeaada4b1be
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586370"
---
# <a name="pass-data-between-forms"></a>Przekazywanie danych między formularzami

Ten Instruktaż zawiera instrukcje krok po kroku dotyczące przekazywania danych z jednego formularza do drugiego. Przy użyciu tabel klienci i zamówienia z Northwind, jeden formularz umożliwia użytkownikom wybranie klienta, a drugi formularz wyświetla zamówienia wybranego klienta. W tym instruktażu pokazano, jak utworzyć metodę w drugim formularzu, który odbiera dane z pierwszego formularza.

> [!NOTE]
> W tym instruktażu przedstawiono tylko jeden sposób przekazywania danych między formularzami. Istnieją inne opcje przekazywania danych do formularza, w tym tworzenie drugiego konstruktora do odbierania danych lub Tworzenie właściwości publicznej, którą można ustawić przy użyciu danych z pierwszego formularza.

Zadania przedstawione w tym instruktażu obejmują:

- Tworzenie nowego projektu **aplikacji Windows Forms** .

- Tworzenie i Konfigurowanie zestawu danych za pomocą [Kreatora konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png).

- Wybieranie kontrolki, która ma zostać utworzona w formularzu podczas przeciągania elementów z okna **źródła danych** . Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Tworzenie kontrolki powiązanej z danymi przez przeciąganie elementów z okna **źródła danych** na formularz.

- Tworzenie drugiego formularza z siatką służącą do wyświetlania danych.

- Tworzenie zapytania TableAdapter w celu pobrania zamówień dla określonego klienta.

- Przekazywanie danych między formularzami.

## <a name="prerequisites"></a>Wymagania wstępne

W tym instruktażu jest stosowana SQL Server Express LocalDB i Przykładowa baza danych Northwind.

1. Jeśli nie masz SQL Server Express LocalDB, zainstaluj go na [stronie pobierania SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)lub za pośrednictwem **Instalator programu Visual Studio**. W Instalator programu Visual Studio, SQL Server Express LocalDB można zainstalować w ramach obciążenia **magazynu i przetwarzania danych** albo jako pojedynczy składnik.

2. Zainstaluj przykładową bazę danych Northwind, wykonując następujące kroki:

    1. W programie Visual Studio Otwórz okno **Eksplorator obiektów SQL Server** . (Eksplorator obiektów SQL Server jest instalowany jako część obciążenia **magazynu i przetwarzania danych** w Instalator programu Visual Studio). Rozwiń węzeł **SQL Server** . Kliknij prawym przyciskiem myszy wystąpienie LocalDB i wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Skopiuj [skrypt języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją danymi.

    3. Wklej skrypt języka T-SQL do edytora zapytań, a następnie wybierz **Execute** przycisku.

       Po krótkim czasie zapytanie kończy działanie i zostanie utworzona baza danych Northwind.

## <a name="create-the-windows-forms-app-project"></a>Tworzenie projektu aplikacji Windows Forms

1. W programie Visual Studio w menu **plik** wybierz pozycję **Nowy** **projekt** > .

2. Rozwiń pozycję **Wizualizacja C#**  lub **Visual Basic** w okienku po lewej stronie, a następnie wybierz pozycję **pulpit systemu Windows**.

3. W środkowym okienku wybierz typ projektu **aplikacji Windows Forms** .

4. Nazwij projekt **PassingDataBetweenForms**, a następnie wybierz przycisk **OK**.

     Projekt **PassingDataBetweenForms** został utworzony i dodany do **Eksplorator rozwiązań**.

## <a name="create-the-data-source"></a>Tworzenie źródła danych

1. Aby otworzyć okno **źródła danych** , w menu **dane** kliknij polecenie **Pokaż źródła danych**.

2. W oknie **źródła danych** wybierz pozycję **Dodaj nowe źródło danych** , aby uruchomić kreatora **konfiguracji źródła danych** .

3. Wybierz pozycję **baza danych** na stronie **Wybierz typ źródła danych** , a następnie kliknij przycisk **dalej**.

4. Na stronie **Wybierz model bazy danych** Sprawdź, czy określono **zestaw danych** , a następnie kliknij przycisk **dalej**.

5. Na stronie **Wybierz połączenie danych** wykonaj jedną z następujących czynności:

    - Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

    - Wybierz pozycję **nowe połączenie** , aby uruchomić okno dialogowe **Dodawanie/modyfikowanie połączenia** .

6. Jeśli baza danych wymaga hasła i jeśli włączono opcję dołączenia danych poufnych, wybierz opcję, a następnie kliknij przycisk **dalej**.

7. Na stronie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** kliknij przycisk **dalej**.

8. Na stronie **Wybierz obiekty bazy danych** rozwiń węzeł **tabele** .

9. Wybierz tabele **Customers** i **Orders** , a następnie kliknij przycisk **Zakończ**.

     **NorthwindDataSet** jest dodawany do projektu, a tabele **Customers** i **Orders** są wyświetlane w oknie **źródła danych** .

## <a name="create-the-first-form-form1"></a>Utwórz pierwszy formularz (Form1)

Można utworzyć siatkę powiązaną z danymi (formant <xref:System.Windows.Forms.DataGridView>), przeciągając węzeł **Customers** z okna **źródła danych** na formularz.

### <a name="to-create-a-data-bound-grid-on-the-form"></a>Aby utworzyć siatkę powiązaną z danymi w formularzu

- Przeciągnij główny węzeł **Customers** z okna **źródła danych** na **formularz Form1**.

     <xref:System.Windows.Forms.DataGridView> i pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania po rekordach pojawia się na **formularzu Form1**. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>i <xref:System.Windows.Forms.BindingNavigator> pojawiają się na pasku składnika.

## <a name="create-the-second-form"></a>Tworzenie drugiego formularza

Utwórz drugi formularz, do którego mają zostać przekazane dane.

1. W menu **projekt** wybierz polecenie **Dodaj formularz systemu Windows**.

2. Pozostaw domyślną nazwę **Form2**, a następnie kliknij przycisk **Dodaj**.

3. Przeciągnij główny węzeł **zamówień** z okna **źródła danych** na **Form2**.

     <xref:System.Windows.Forms.DataGridView> i pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania po rekordach pojawia się na **Form2**. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>i <xref:System.Windows.Forms.BindingNavigator> pojawiają się na pasku składnika.

4. Usuń **OrdersBindingNavigator** z paska składnika.

     **OrdersBindingNavigator** znika z **Form2**.

## <a name="add-a-tableadapter-query"></a>Dodawanie zapytania TableAdapter

Dodaj zapytanie TableAdapter do Form2 w celu załadowania zamówień dla wybranego klienta na formularzu Form1.

1. Kliknij dwukrotnie plik **NorthwindDataSet. xsd** w **Eksplorator rozwiązań**.

2. Kliknij prawym przyciskiem myszy **OrdersTableAdapter**, a następnie wybierz polecenie **Dodaj zapytanie**.

3. Pozostaw domyślną opcję **Użyj instrukcji SQL**, a następnie kliknij przycisk **dalej**.

4. Pozostaw domyślną opcję Select, **która zwraca wiersze**, a następnie kliknij przycisk **dalej**.

5. Dodaj klauzulę WHERE do zapytania, aby zwrócić `Orders` w oparciu o `CustomerID`. Zapytanie powinno być podobne do następujących:

    ```sql
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    > Sprawdź poprawność składni parametrów dla bazy danych. Na przykład w programie Microsoft Access klauzula WHERE będzie wyglądać następująco: `WHERE CustomerID = ?`.

6. Kliknij przycisk **Dalej**.

7. Dla pola **Wypełnij nazwę DataTableMethod**wpisz `FillByCustomerID`.

8. Usuń zaznaczenie opcji **Zwróć element DataTable** , a następnie kliknij przycisk **dalej**.

9. Kliknij przycisk **Zakończ**.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Utwórz metodę na Form2, aby przekazać dane do

1. Kliknij prawym przyciskiem myszy pozycję **Form2**, a następnie wybierz pozycję **Wyświetl kod** , aby otworzyć **Form2** w **edytorze kodu**.

2. Dodaj następujący kod do **Form2** po metodzie `Form2_Load`:

     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-csharp[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Utwórz metodę na formularzu Form1, aby przekazać dane i wyświetlić Form2

1. W **formularzu Form1**kliknij prawym przyciskiem myszy siatkę danych klienta, a następnie kliknij polecenie **Właściwości**.

2. W oknie **Właściwości** kliknij pozycję **zdarzenia**.

3. Kliknij dwukrotnie zdarzenie **CellDoubleClick** .

     Zostanie wyświetlony Edytor kodu.

4. Zaktualizuj definicję metody, aby pasowała do poniższego przykładu:

     [!code-csharp[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]

## <a name="run-the-app"></a>Uruchamianie aplikacji

- Naciśnij klawisz **F5**, aby uruchomić aplikację.

- Kliknij dwukrotnie rekord klienta w **formularzu Form1** , aby otworzyć **Form2** z zamówieniami tego klienta.

## <a name="next-steps"></a>Następne kroki

W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po przekazaniu danych między formularzami. Niektóre udoskonalenia, których można dokonać w tym instruktażu obejmują:

- Edytowanie zestawu danych w celu dodania lub usunięcia obiektów bazy danych. Aby uzyskać więcej informacji, zobacz [tworzenie i konfigurowanie zestawów danych](../data-tools/create-and-configure-datasets-in-visual-studio.md).

- Dodawanie funkcji do zapisywania danych z powrotem w bazie danych. Aby uzyskać więcej informacji, zobacz [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md).

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
