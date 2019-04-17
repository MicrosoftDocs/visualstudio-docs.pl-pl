---
title: Przekazywanie danych pomiędzy formularzami | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9a109490c4ff89c6a9f45533fc1305d915522621
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59668941"
---
# <a name="pass-data-between-forms"></a>Przekazywanie danych między formularzami
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten przewodnik zawiera instrukcje krok po kroku do przekazywania danych z jednego formularza do innego. Przy użyciu klientów i zamówień tabel z Northwind, jeden formularz pozwala użytkownikom na wybór klienta, a drugi formularz zawiera wybranego zamówienia. W tym instruktażu przedstawiono sposób tworzenia metody na drugi formularz, który odbiera dane z pierwszego formularza.  
  
> [!NOTE]
>  W tym instruktażu pokazano tylko jeden sposób przekazywania danych między formularzami. Istnieją inne opcje przekazywania danych do postaci, w tym tworzenie drugi Konstruktor na odbieranie danych, lub tworzenie właściwości publicznej, które można ustawić za pomocą danych z pierwszego formularza.  
  
 Zadania zilustrowane w tym przewodniku obejmują:  
  
-   Tworzenie nowego **aplikacji Windows** projektu.  
  
-   Tworzenie i konfigurowanie zestawu danych za pomocą [Kreatora konfiguracji źródła danych](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Wybieranie formantu do utworzenia w formularzu podczas przeciągania elementów z **źródeł danych** okna. Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Tworzenie kontrolki powiązane z danymi przez przeciąganie elementów z **źródeł danych** okna w formularzu.  
  
-   Tworzenie drugiej formy z siatki, aby wyświetlić dane.  
  
-   Tworzenie zapytań TableAdapter, można pobrać zamówienia dla danego klienta.  
  
-   Przekazywanie danych pomiędzy formularzami.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W celu przeprowadzenia tego instruktażu, należy:  
  
-   Dostęp do przykładowej bazy danych Northwind.
  
## <a name="create-the-windows-application"></a>Tworzenie aplikacji Windows  
  
#### <a name="to-create-the-new-windows-project"></a>Aby utworzyć nowy projekt Windows  
  
1.  Z **pliku** menu, Utwórz nowy projekt.  
  
2.  Nadaj projektowi nazwę `PassingDataBetweenForms`.  
  
3.  Wybierz **aplikacja interfejsu Windows Forms**i kliknij przycisk **OK**. Aby uzyskać więcej informacji, zobacz [aplikacje klienckie](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     **PassingDataBetweenForms** projekt zostanie utworzony i dodany do **Eksploratora rozwiązań**.  
  
## <a name="create-the-data-source"></a>Utwórz źródło danych  
  
#### <a name="to-create-the-data-source"></a>Aby utworzyć źródło danych  
  
1.  Na **danych** menu, kliknij przycisk **Pokaż źródła danych**.  
  
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
  
#### <a name="to-create-a-data-bound-grid-on-the-form"></a>Aby utworzyć grid powiązane z danymi w formularzu  
  
-   Przeciągnij główny **klientów** węzła z **źródeł danych** okna na **Form1**.  
  
     A <xref:System.Windows.Forms.DataGridView> i pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania między rekordami wyświetlanymi w **Form1**. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane w zasobniku składnika.  
  
## <a name="create-the-second-form-form2"></a>Utwórz drugi formularz (formularz2)  
  
#### <a name="to-create-a-second-form-to-pass-the-data-to"></a>Aby utworzyć drugi formularz do przekazywania danych do  
  
1.  Z **projektu** menu, wybierz **Dodaj formularz Windows**.  
  
2.  Pozostaw domyślną nazwę **formularz2**i kliknij przycisk **Dodaj**.  
  
3.  Przeciągnij główny **zamówienia** węzła z **źródeł danych** okna na **formularz2**.  
  
     A <xref:System.Windows.Forms.DataGridView> i pasek narzędzi (<xref:System.Windows.Forms.BindingNavigator>) do nawigowania między rekordami wyświetlanymi w **formularz2**. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource>, i <xref:System.Windows.Forms.BindingNavigator> są wyświetlane w zasobniku składnika.  
  
4.  Usuń **OrdersBindingNavigator** do zasobnika składnika.  
  
     **OrdersBindingNavigator** znika z **formularz2**.  
  
## <a name="add-a-tableadapter-query-to-form2-to-load-orders-for-the-selected-customer-on-form1"></a>Dodaj zapytanie TableAdapter do formularz2 załadować zamówień dla zaznaczonego klienta na formularzu Form1  
  
#### <a name="to-create-a-tableadapter-query"></a>Aby utworzyć zapytanie TableAdapter  
  
1.  Kliknij dwukrotnie **NorthwindDataSet.xsd** w pliku **Eksploratora rozwiązań**.  
  
2.  Kliknij prawym przyciskiem myszy **OrdersTableAdapter**i wybierz **Dodaj zapytanie**.  
  
3.  Pozostaw opcję domyślną **użyj instrukcji SQL**, a następnie kliknij przycisk **dalej**.  
  
4.  Pozostaw opcję domyślną **SELECT, która zwraca wiersze**, a następnie kliknij przycisk **dalej**.  
  
5.  Dodaj klauzulę WHERE do zapytania, aby zwrócić `Orders` na podstawie `CustomerID`. Zapytanie powinny wyglądać podobnie do następującego:  
  
    ```  
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry  
    FROM Orders   
    WHERE CustomerID = @CustomerID  
    ```  
  
    > [!NOTE]
    >  Sprawdź składnię odpowiedni parametr dla bazy danych. Na przykład w programie Microsoft Access klauzuli WHERE będzie wyglądać: `WHERE CustomerID = ?`.  
  
6.  Kliknij przycisk **Dalej**.  
  
7.  Aby uzyskać **Wypełnij nazwę DataTableMethod**, typ `FillByCustomerID`.  
  
8.  Wyczyść **róć tabelę DataTable** opcji, a następnie kliknij przycisk **dalej**.  
  
9. Kliknij przycisk **Zakończ**.  
  
## <a name="create-a-method-on-form2-to-pass-data-to"></a>Utwórz metodę na formularz2 do przekazywania danych do  
  
#### <a name="to-create-a-method-to-pass-data-to"></a>Aby utworzyć metodę do przekazywania danych do  
  
1.  Kliknij prawym przyciskiem myszy **formularz2**i wybierz **Wyświetl kod** otworzyć **formularz2** w **Edytor kodu**.  
  
2.  Dodaj następujący kod do **formularz2** po `Form2_Load` metody:  
  
     [!code-csharp[VbRaddataDisplaying#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form2.cs#1)]
     [!code-vb[VbRaddataDisplaying#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form2.vb#1)]  
  
## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Utwórz metodę na formularzu Form1, aby przekazać dane i wyświetlić formularz2  
  
#### <a name="to-create-a-method-to-pass-data-to-form2"></a>Aby utworzyć metodę, aby przekazać dane do formularz2  
  
1.  W **Form1**, kliknij prawym przyciskiem myszy siatki danych klienta, a następnie kliknij przycisk **właściwości**.  
  
2.  W **właściwości** okna, kliknij przycisk **zdarzenia**.  
  
3.  Kliknij dwukrotnie **CellDoubleClick** zdarzeń.  
  
     Zostanie wyświetlony Edytor kodu.  
  
4.  Aktualizacja definicji metody, aby dopasować następujący przykład:  
  
     [!code-csharp[VbRaddataDisplaying#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#2)]
     [!code-vb[VbRaddataDisplaying#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#2)]  
  
## <a name="run-the-application"></a>Uruchamianie aplikacji  
  
#### <a name="to-run-the-application"></a>Aby uruchomić aplikację  
  
-   Naciśnij klawisz F5, aby uruchomić aplikację.  
  
-   Kliknij dwukrotnie rekord klienta w **Form1** otworzyć **formularz2** zamówień tego klienta.  
  
## <a name="next-steps"></a>Następne kroki  
 W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po przekazywanie danych pomiędzy formularzami. Niektóre udoskonalenia, których można dokonać w tym instruktażu obejmują:  
  
-   Edytowanie zestawu danych, aby dodać lub usunąć obiekty bazy danych. Aby uzyskać więcej informacji, zobacz [tworzenie i konfigurowanie zestawów danych](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
-   Dodawanie funkcji do zapisać dane w bazie danych. Aby uzyskać więcej informacji, zobacz [zapisać dane w bazie danych](../data-tools/save-data-back-to-the-database.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
