---
title: 'Przewodnik: Złożone powiązanie danych w projekcie dodatku narzędzi VSTO'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], Excel
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0cb4fc7b43ab3ae48f83f4497fe6fd0042d0c51a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60070618"
---
# <a name="walkthrough-complex-data-binding-in-vsto-add-in-project"></a>Przewodnik: Złożone powiązanie danych w projekcie dodatku narzędzi VSTO
  Dane można powiązać formanty hosta i kontrolek Windows Forms w projektach dodatku narzędzi VSTO. W tym instruktażu pokazano, jak dodawanie formantów do arkusza programu Microsoft Office Excel i powiązać formanty z danymi w czasie wykonywania.

 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie <xref:Microsoft.Office.Tools.Excel.ListObject> formantu do arkusza w czasie wykonywania.

- Tworzenie <xref:System.Windows.Forms.BindingSource> , formant łączy się z wystąpieniem zestawu danych.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Dostęp do uruchomionego wystąpienia programu SQL Server 2005 lub SQL Server 2005 Express, który ma `AdventureWorksLT` przykładowej bazy danych dołączono do niego. Możesz pobrać `AdventureWorksLT` bazy danych z [witryny sieci Web CodePlex](http://go.microsoft.com/fwlink/?LinkId=115611). Aby uzyskać więcej informacji na temat dołączania bazy danych zobacz następujące tematy:

    - Aby dołączyć bazę danych przy użyciu programu SQL Server Management Studio lub SQL Server Management Studio Express, zobacz [jak: Dołączanie bazy danych (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

    - Aby dołączyć bazę danych przy użyciu wiersza polecenia, zobacz [jak: Dołączanie pliku bazy danych do programu SQL Server Express](/previous-versions/sql/).

## <a name="create-a-new-project"></a>Tworzenie nowego projektu
 Pierwszym krokiem jest utworzenie projektu dodatku narzędzi VSTO programu Excel.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt dodatku narzędzi VSTO programu Excel o nazwie **zapełnianie arkuszy z bazy danych**, za pomocą Visual Basic lub C#.

     Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w programie Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Zostanie otwarty program Visual Studio `ThisAddIn.vb` lub `ThisAddIn.cs` plików i dodaje **zapełnianie arkuszy z bazy danych** projekt **Eksploratora rozwiązań**.

## <a name="create-a-data-source"></a>Utwórz źródło danych
 Użyj **źródeł danych** okna, aby dodać typizowany zestaw danych do projektu.

### <a name="to-add-a-typed-dataset-to-the-project"></a>Aby dodać typizowany zestaw danych do projektu

1. Jeśli **źródeł danych** okno nie jest widoczne, wyświetlić je, na pasku menu, wybierając **widoku** > **Windows inne**  >   **Źródła danych**.

2. Wybierz **Dodaj nowe źródło danych** można uruchomić **Kreatora konfiguracji źródła danych**.

3. Kliknij przycisk **bazy danych**, a następnie kliknij przycisk **dalej**.

4. Jeśli masz istniejące połączenie z programem `AdventureWorksLT` bazy danych, wybierz to połączenie i kliknij przycisk **dalej**.

    W przeciwnym razie kliknij przycisk **nowe połączenie**i użyj **Dodaj połączenie** okno dialogowe, aby utworzyć nowe połączenie. Aby uzyskać więcej informacji, zobacz [dodać nowe połączenia](../data-tools/add-new-connections.md).

5. W **Zapisz parametry połączenia do pliku konfiguracji aplikacji** kliknij **dalej**.

6. W **wybierz obiekty bazy danych** rozwiń **tabel** i wybierz **adresu (SalesLT)**.

7. Kliknij przycisk **Zakończ**.

    *AdventureWorksLTDataSet.xsd* plik zostanie dodany do **Eksploratora rozwiązań**. Ten plik definiuje następujące elementy:

   - Typizowany zestaw danych o nazwie `AdventureWorksLTDataSet`. Ten zestaw danych reprezentuje zawartość **adresu (SalesLT)** tabeli w bazie danych AdventureWorksLT.

   - TableAdapter o nazwie `AddressTableAdapter`. Ten obiekt TableAdapter można odczytywać i zapisywać dane `AdventureWorksLTDataSet`. Aby uzyskać więcej informacji, zobacz [TableAdapter — Przegląd](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Użyje obu tych obiektów w dalszej części tego przewodnika.

## <a name="create-controls-and-bind-controls-to-data"></a>Tworzenie formantów i powiązywanie kontrolek z danymi
 W tym przewodniku <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolka Wyświetla wszystkie dane w tabeli zaznaczonej zaraz po otwarciu skoroszytu. Obiekt listy używa <xref:System.Windows.Forms.BindingSource> do połączenia z bazą danych formantu.

 Aby uzyskać więcej informacji na temat powiązanie kontrolek z danymi, zobacz [wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-add-the-list-object-dataset-and-table-adapter"></a>Aby dodać obiekt listy, zestaw danych i tabeli karty

1. W `ThisAddIn` klasy, Zadeklaruj następujące formanty do wyświetlania `Address` tabeli `AdventureWorksLTDataSet` zestawu danych.

     [!code-csharp[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#1)]

2. W `ThisAddIn_Startup` metody, Dodaj następujący kod, aby zainicjować zestaw danych i wypełnić dataset przy użyciu informacji z `AdventureWorksLTDataSet` zestawu danych.

     [!code-csharp[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#2)]

3. Dodaj następujący kod do `ThisAddIn_Startup` metody. Spowoduje to wygenerowanie element hosta, która rozszerza arkusza. Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

     [!code-csharp[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#3)]

4. Utwórz zakres i Dodaj <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli.

     [!code-csharp[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#4)]
     [!code-vb[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#4)]

5. Obiekt listy, aby powiązać `AdventureWorksLTDataSet` przy użyciu <xref:System.Windows.Forms.BindingSource>. Przekaż w nazwach kolumn, które chcesz powiązać z obiekt listy.

     [!code-csharp[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#5)]
     [!code-vb[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#5)]

## <a name="test-the-add-in"></a>Testowanie dodatku programu
 Po otwarciu programu Excel, <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolka wyświetla dane z `Address` tabeli `AdventureWorksLTDataSet` zestawu danych.

### <a name="to-test-the-vsto-add-in"></a>Aby przetestować dodatku narzędzi VSTO

- Naciśnij klawisz **F5**.

     A <xref:Microsoft.Office.Tools.Excel.ListObject> formantu o nazwie `addressListObject` jest tworzony w arkuszu. Jednocześnie, obiekt zestawu danych o nazwie `adventureWorksLTDataSet` i <xref:System.Windows.Forms.BindingSource> o nazwie `addressBindingSource` są dodawane do projektu. <xref:Microsoft.Office.Tools.Excel.ListObject> Jest powiązany z <xref:System.Windows.Forms.BindingSource>, która z kolei jest powiązana z obiektem zestawu danych.

## <a name="see-also"></a>Zobacz także

- [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)
- [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Instrukcje: Zapełnianie arkuszy danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Instrukcje: Zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Instrukcje: Zapełnianie dokumentów danymi z usług](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Instrukcje: Zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Instrukcje: Przewijanie rekordów bazy danych w arkuszu](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Instrukcje: Aktualizowanie źródła danych danymi z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Przewodnik: Proste powiązanie danych w projekcie na poziomie dokumentu](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
- [Przewodnik: Złożone powiązanie danych w projekcie na poziomie dokumentu](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
- [Korzystać z plików lokalnej bazy danych w rozwiązań Office ― omówienie](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)
- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Korzystać z plików lokalnej bazy danych w rozwiązań Office ― omówienie](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource, składnik — omówienie](/dotnet/framework/winforms/controls/bindingsource-component-overview)