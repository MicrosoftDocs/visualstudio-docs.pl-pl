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
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 0f4c77e4d2f8d0c75f71942cf61213210bc680ba
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53944830"
---
# <a name="pass-data-between-forms"></a>Przekazywanie danych między formularzami

Ten przewodnik zawiera instrukcje krok po kroku do przekazywania danych z jednego formularza do innego. Przy użyciu klientów i zamówień tabel z Northwind, jeden formularz pozwala użytkownikom na wybór klienta, a drugi formularz zawiera wybranego zamówienia. W tym instruktażu przedstawiono sposób tworzenia metody na drugi formularz, który odbiera dane z pierwszego formularza.

> [!NOTE]
> W tym instruktażu pokazano tylko jeden sposób przekazywania danych między formularzami. Istnieją inne opcje przekazywania danych do postaci, w tym tworzenie drugi Konstruktor na odbieranie danych, lub tworzenie właściwości publicznej, które można ustawić za pomocą danych z pierwszego formularza.

Zadania zilustrowane w tym przewodniku obejmują:

-   Tworzenie nowego **aplikacja interfejsu Windows Forms** projektu.

-   Tworzenie i konfigurowanie zestawu danych za pomocą [Kreatora konfiguracji źródła danych](../data-tools/media/data-source-configuration-wizard.png).

-   Wybieranie formantu do utworzenia w formularzu podczas przeciągania elementów z **źródeł danych** okna. Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

-   Tworzenie kontrolki powiązane z danymi przez przeciąganie elementów z **źródeł danych** okna w formularzu.

-   Tworzenie drugiej formy z siatki, aby wyświetlić dane.

-   Tworzenie zapytań TableAdapter, można pobrać zamówienia dla danego klienta.

-   Przekazywanie danych pomiędzy formularzami.

## <a name="prerequisites"></a>Wymagania wstępne

Ten przewodnik korzysta z programu SQL Server Express LocalDB i bazie danych Northwind.

1.  Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [stronę pobierania programu SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), lub za pomocą **Instalatora programu Visual Studio**. W Instalatorze programu Visual Studio, można zainstalować programu SQL Server Express LocalDB, jako część **przechowywanie i przetwarzanie danych** obciążenie, lub jako poszczególnych składników.

2.  Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:

    1. W programie Visual Studio, otwórz **Eksplorator obiektów SQL Server** okna. (Eksplorator obiektów SQL Server jest instalowany jako część **przechowywanie i przetwarzanie danych** obciążenie w Instalatorze programu Visual Studio.) Rozwiń **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w ramach wystąpienia LocalDB, a następnie wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Kopiuj [skryptów języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt języka T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją z danymi.

    3. Wklej skrypt języka T-SQL do edytora zapytań, a następnie wybierz **Execute** przycisku.

       Po pewnym czasie odliczania zapytania i utworzeniu bazy danych Northwind.

## <a name="create-the-windows-forms-app-project"></a>Utwórz projekt aplikacji Windows Forms

1. W programie Visual Studio na **pliku** menu, wybierz opcję **New** > **projektu**.

2. Rozwiń **Visual C#** lub **języka Visual Basic** w okienku po lewej stronie, a następnie zaznacz **pulpitu Windows**.

3. W środkowym okienku wybierz **Windows Forms App** typ projektu.

4. Nadaj projektowi nazwę **PassingDataBetweenForms**, a następnie wybierz **OK**.

     **PassingDataBetweenForms** projekt zostanie utworzony i dodany do **Eksploratora rozwiązań**.

## <a name="create-the-data-source"></a>Utwórz źródło danych

1.  Aby otworzyć **źródeł danych** okna na **danych** menu, kliknij przycisk **Pokaż źródła danych**.

2.  W **źródeł danych** wybierz **Dodaj nowe źródło danych** można uruchomić **konfiguracji źródła danych** kreatora.

3.  Wybierz **bazy danych** na **wybierz typ źródła danych** strony, a następnie kliknij przycisk **dalej**.

4.  Na **wybierz model bazy danych** Sprawdź, czy **Dataset** jest określony, a następnie kliknij przycisk **dalej**.

5.  Na **wybierz połączenie danych** wykonaj jedną z następujących czynności:

    -   Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

    -   Wybierz **nowe połączenie** można uruchomić **Dodawanie/modyfikowanie połączenia** okno dialogowe.

6.  Jeśli baza danych wymaga hasła i jest włączona opcja dołączenia danych poufnych, wybierz opcję, a następnie kliknij przycisk **dalej**.

7.  Na **Zapisz parametry połączenia do pliku konfiguracji aplikacji** kliknij **dalej**.

8.  Na **wybierz obiekty bazy danych** rozwiń **tabel** węzła.

9. Wybierz **klientów** i **zamówienia** tabel, a następnie kliknij **Zakończ**.

     **NorthwindDataSet** zostanie dodany do projektu, a **klientów** i **zamówienia** tabele są wyświetlane w **źródeł danych** okna.

## <a name="create-the-first-form-form1"></a>Utwórz pierwszy formularz (formularz Form1)

Można utworzyć siatki powiązanych z danymi ( <xref:System.Windows.Forms.DataGridView> sterowania), przeciągając **klientów** węzła z **źródeł danych** okna na formularzu.

### <a name="to-create-a-data-bound-grid-on-the-form"></a>Aby utworzyć grid powiązane z danymi w formularzu

-   Przeciągnij główny **klientów** węzła z **źródeł danych** okna na **Form1**.

     A <xref:System.Windows.Forms.DataGridView> i pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania między rekordami wyświetlanymi w **Form1**. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane w zasobniku składnika.

## <a name="create-the-second-form"></a>Utwórz drugi formularz

Utwórz drugi formularz do przekazania danych.

1.  Z **projektu** menu, wybierz **Dodaj formularz Windows**.

2.  Pozostaw domyślną nazwę **formularz2**i kliknij przycisk **Dodaj**.

3.  Przeciągnij główny **zamówienia** węzła z **źródeł danych** okna na **formularz2**.

     A <xref:System.Windows.Forms.DataGridView> i pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania między rekordami wyświetlanymi w **formularz2**. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane w zasobniku składnika.

4.  Usuń **OrdersBindingNavigator** do zasobnika składnika.

     **OrdersBindingNavigator** znika z **formularz2**.

## <a name="add-a-tableadapter-query"></a>Dodaj zapytanie TableAdapter

Dodaj zapytanie TableAdapter do formularz2 załadować zamówień dla zaznaczonego klienta na formularzu Form1.

1.  Kliknij dwukrotnie **NorthwindDataSet.xsd** w pliku **Eksploratora rozwiązań**.

2.  Kliknij prawym przyciskiem myszy **OrdersTableAdapter**i wybierz **Dodaj zapytanie**.

3.  Pozostaw opcję domyślną **użyj instrukcji SQL**, a następnie kliknij przycisk **dalej**.

4.  Pozostaw opcję domyślną **SELECT, która zwraca wiersze**, a następnie kliknij przycisk **dalej**.

5.  Dodaj klauzulę WHERE do zapytania, aby zwrócić `Orders` na podstawie `CustomerID`. Zapytanie powinny wyglądać podobnie do następującego:

    ```sql
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    > Sprawdź składnię odpowiedni parametr dla bazy danych. Na przykład w programie Microsoft Access klauzuli WHERE będzie wyglądać: `WHERE CustomerID = ?`.

6.  Kliknij przycisk **Dalej**.

7.  Aby uzyskać **Wypełnij nazwę DataTableMethod**, typ `FillByCustomerID`.

8.  Wyczyść **róć tabelę DataTable** opcji, a następnie kliknij przycisk **dalej**.

9. Kliknij przycisk **Zakończ**.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Utwórz metodę na formularz2 do przekazywania danych do

1.  Kliknij prawym przyciskiem myszy **formularz2**i wybierz **Wyświetl kod** otworzyć **formularz2** w **Edytor kodu**.

2.  Dodaj następujący kod do **formularz2** po `Form2_Load` metody:

     [!code-vb[VbRaddataDisplaying#1](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_1.vb)]
     [!code-csharp[VbRaddataDisplaying#1](../data-tools/codesnippet/CSharp/pass-data-between-forms_1.cs)]

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Utwórz metodę na formularzu Form1, aby przekazać dane i wyświetlić formularz2

1.  W **Form1**, kliknij prawym przyciskiem myszy siatki danych klienta, a następnie kliknij przycisk **właściwości**.

2.  W **właściwości** okna, kliknij przycisk **zdarzenia**.

3.  Kliknij dwukrotnie **CellDoubleClick** zdarzeń.

     Zostanie wyświetlony Edytor kodu.

4.  Aktualizacja definicji metody, aby dopasować następujący przykład:

     [!code-csharp[VbRaddataDisplaying#2](../data-tools/codesnippet/CSharp/pass-data-between-forms_2.cs)]
     [!code-vb[VbRaddataDisplaying#2](../data-tools/codesnippet/VisualBasic/pass-data-between-forms_2.vb)]

## <a name="run-the-app"></a>Uruchamianie aplikacji

-   Naciśnij klawisz **F5** do uruchomienia aplikacji.

-   Kliknij dwukrotnie rekord klienta w **Form1** otworzyć **formularz2** zamówień tego klienta.

## <a name="next-steps"></a>Następne kroki

W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po przekazywanie danych pomiędzy formularzami. Niektóre udoskonalenia, których można dokonać w tym instruktażu obejmują:

-   Edytowanie zestawu danych, aby dodać lub usunąć obiekty bazy danych. Aby uzyskać więcej informacji, zobacz [tworzenie i konfigurowanie zestawów danych](../data-tools/create-and-configure-datasets-in-visual-studio.md).

-   Dodawanie funkcji do zapisać dane w bazie danych. Aby uzyskać więcej informacji, zobacz [zapisać dane w bazie danych](../data-tools/save-data-back-to-the-database.md).

## <a name="see-also"></a>Zobacz także

- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)