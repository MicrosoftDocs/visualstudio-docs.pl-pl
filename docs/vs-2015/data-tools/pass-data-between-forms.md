---
title: Przekazywanie danych między formularzami | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e14165ba2111f40898c00b3d01950425c042070
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652912"
---
# <a name="pass-data-between-forms"></a>Przekazywanie danych między formularzami
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten Instruktaż zawiera instrukcje krok po kroku dotyczące przekazywania danych z jednego formularza do drugiego. Przy użyciu tabel klienci i zamówienia z Northwind, jeden formularz umożliwia użytkownikom wybranie klienta, a drugi formularz wyświetla zamówienia wybranego klienta. W tym instruktażu pokazano, jak utworzyć metodę w drugim formularzu, który odbiera dane z pierwszego formularza.

> [!NOTE]
> W tym instruktażu przedstawiono tylko jeden sposób przekazywania danych między formularzami. Istnieją inne opcje przekazywania danych do formularza, w tym tworzenie drugiego konstruktora do odbierania danych lub Tworzenie właściwości publicznej, którą można ustawić przy użyciu danych z pierwszego formularza.

 Zadania przedstawione w tym instruktażu obejmują:

- Tworzenie nowego projektu **aplikacji systemu Windows** .

- Tworzenie i Konfigurowanie zestawu danych za pomocą [Kreatora konfiguracji źródła danych](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).

- Wybieranie kontrolki, która ma zostać utworzona w formularzu podczas przeciągania elementów z okna **źródła danych** . Aby uzyskać więcej informacji, zobacz [Ustawianie kontrolki do utworzenia podczas przeciągania z okna źródła danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Tworzenie kontrolki powiązanej z danymi przez przeciąganie elementów z okna **źródła danych** na formularz.

- Tworzenie drugiego formularza z siatką służącą do wyświetlania danych.

- Tworzenie zapytania TableAdapter w celu pobrania zamówień dla określonego klienta.

- Przekazywanie danych między formularzami.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby ukończyć ten Instruktaż, potrzebne są:

- Dostęp do przykładowej bazy danych Northwind.

## <a name="create-the-windows-application"></a>Tworzenie aplikacji systemu Windows

#### <a name="to-create-the-new-windows-project"></a>Aby utworzyć nowy projekt systemu Windows

1. Z menu **plik** Utwórz nowy projekt.

2. Nadaj nazwę projektowi `PassingDataBetweenForms` .

3. Wybierz pozycję **aplikacja Windows Forms**i kliknij przycisk **OK**. Aby uzyskać więcej informacji, zobacz [aplikacje klienckie](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Projekt **PassingDataBetweenForms** został utworzony i dodany do **Eksplorator rozwiązań**.

## <a name="create-the-data-source"></a>Tworzenie źródła danych

#### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych

1. W menu **dane** kliknij przycisk **Pokaż źródła danych**.

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
 Można utworzyć siatkę powiązaną z danymi ( <xref:System.Windows.Forms.DataGridView> formant), przeciągając węzeł **Customers** z okna **źródła danych** na formularz.

#### <a name="to-create-a-data-bound-grid-on-the-form"></a>Aby utworzyć siatkę powiązaną z danymi w formularzu

- Przeciągnij główny węzeł **Customers** z okna **źródła danych** na **formularz Form1**.

     <xref:System.Windows.Forms.DataGridView>A i pasek narzędzi ( <xref:System.Windows.Forms.BindingNavigator> ) do nawigowania po rekordach pojawia się na **formularzu Form1**. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> i <xref:System.Windows.Forms.BindingNavigator> pojawiają się na pasku składnika.

## <a name="create-the-second-form-form2"></a>Utwórz drugi formularz (Form2)

#### <a name="to-create-a-second-form-to-pass-the-data-to"></a>Aby utworzyć drugi formularz do przekazywania danych do

1. W menu **projekt** wybierz polecenie **Dodaj formularz systemu Windows**.

2. Pozostaw domyślną nazwę **Form2**, a następnie kliknij przycisk **Dodaj**.

3. Przeciągnij główny węzeł **zamówień** z okna **źródła danych** na **Form2**.

     <xref:System.Windows.Forms.DataGridView>A i pasek narzędzi ( <xref:System.Windows.Forms.BindingNavigator> ) dla nawigowania po rekordach pojawia się na **Form2**. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> i <xref:System.Windows.Forms.BindingNavigator> pojawiają się na pasku składnika.

4. Usuń **OrdersBindingNavigator** z paska składnika.

     **OrdersBindingNavigator** znika z **Form2**.

## <a name="add-a-tableadapter-query-to-form2-to-load-orders-for-the-selected-customer-on-form1"></a>Dodaj zapytanie TableAdapter do Form2 w celu załadowania zamówień dla wybranego klienta na formularzu Form1

#### <a name="to-create-a-tableadapter-query"></a>Aby utworzyć zapytanie TableAdapter

1. Kliknij dwukrotnie plik **NorthwindDataSet. xsd** w **Eksplorator rozwiązań**.

2. Kliknij prawym przyciskiem myszy **OrdersTableAdapter**, a następnie wybierz polecenie **Dodaj zapytanie**.

3. Pozostaw domyślną opcję **Użyj instrukcji SQL**, a następnie kliknij przycisk **dalej**.

4. Pozostaw domyślną opcję Select, **która zwraca wiersze**, a następnie kliknij przycisk **dalej**.

5. Dodaj klauzulę WHERE do zapytania, aby zwrócić ją na `Orders` podstawie `CustomerID` . Zapytanie powinno być podobne do następujących:

    ```
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    > Sprawdź poprawność składni parametrów dla bazy danych. Na przykład w programie Microsoft Access klauzula WHERE będzie wyglądać następująco: `WHERE CustomerID = ?` .

6. Kliknij przycisk **Dalej**.

7. Dla pola **Wypełnij wpisz nazwę DataTableMethod** `FillByCustomerID` .

8. Usuń zaznaczenie opcji **Zwróć element DataTable** , a następnie kliknij przycisk **dalej**.

9. Kliknij przycisk **Zakończ**.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Utwórz metodę na Form2, aby przekazać dane do

#### <a name="to-create-a-method-to-pass-data-to"></a>Aby utworzyć metodę przekazywania danych do

1. Kliknij prawym przyciskiem myszy pozycję **Form2**, a następnie wybierz pozycję **Wyświetl kod** , aby otworzyć **Form2** w **edytorze kodu**.

2. Dodaj następujący kod do **Form2** po `Form2_Load` metodzie:

     [!code-csharp[VbRaddataDisplaying#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form2.cs#1)]
     [!code-vb[VbRaddataDisplaying#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form2.vb#1)]

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Utwórz metodę na formularzu Form1, aby przekazać dane i wyświetlić Form2

#### <a name="to-create-a-method-to-pass-data-to-form2"></a>Aby utworzyć metodę przekazywania danych do Form2

1. W **formularzu Form1**kliknij prawym przyciskiem myszy siatkę danych klienta, a następnie kliknij polecenie **Właściwości**.

2. W oknie **Właściwości** kliknij pozycję **zdarzenia**.

3. Kliknij dwukrotnie zdarzenie **CellDoubleClick** .

     Zostanie wyświetlony Edytor kodu.

4. Zaktualizuj definicję metody, aby pasowała do poniższego przykładu:

     [!code-csharp[VbRaddataDisplaying#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#2)]
     [!code-vb[VbRaddataDisplaying#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#2)]

## <a name="run-the-application"></a>Uruchom aplikację

#### <a name="to-run-the-application"></a>Aby uruchomić aplikację

- Naciśnij klawisz F5, aby uruchomić aplikację.

- Kliknij dwukrotnie rekord klienta w **formularzu Form1** , aby otworzyć **Form2** z zamówieniami tego klienta.

## <a name="next-steps"></a>Następne kroki
 W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po przekazaniu danych między formularzami. Niektóre udoskonalenia, których można dokonać w tym instruktażu obejmują:

- Edytowanie zestawu danych, aby dodać lub usunąć obiekty bazy danych. Aby uzyskać więcej informacji, zobacz [Tworzenie i konfigurowanie zestawów danych](../data-tools/create-and-configure-datasets-in-visual-studio.md).

- Dodawanie funkcji do zapisywania danych z powrotem w bazie danych. Aby uzyskać więcej informacji, zobacz [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md).

## <a name="see-also"></a>Zobacz też
 [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
