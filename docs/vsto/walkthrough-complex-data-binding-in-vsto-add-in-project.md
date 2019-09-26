---
title: 'Przewodnik: Złożone powiązanie danych w projekcie dodatku VSTO'
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
ms.openlocfilehash: efe99e4d12ea4ace6d6c996b816dc315c502fa47
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255565"
---
# <a name="walkthrough-complex-data-binding-in-vsto-add-in-project"></a>Przewodnik: Złożone powiązanie danych w projekcie dodatku VSTO
  Można powiązać dane z kontrolkami hosta i formantami Windows Forms w projektach dodatku VSTO. W tym instruktażu pokazano, jak dodać kontrolki do Microsoft Office arkusza programu Excel i powiązać kontrolki z danymi w czasie wykonywania.

 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- <xref:Microsoft.Office.Tools.Excel.ListObject> Dodawanie kontrolki do arkusza w czasie wykonywania.

- <xref:System.Windows.Forms.BindingSource> Tworzenie, które łączy formant z wystąpieniem zestawu danych.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)]lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Dostęp do uruchomionego wystąpienia programu SQL Server 2005 lub SQL Server 2005 Express, do którego `AdventureWorksLT` jest dołączona Przykładowa baza danych. `AdventureWorksLT` Bazę danych można pobrać z [witryny sieci Web CodePlex](http://go.microsoft.com/fwlink/?LinkId=115611). Aby uzyskać więcej informacji na temat dołączania bazy danych, zobacz następujące tematy:

  - Aby dołączyć bazę danych za pomocą SQL Server Management Studio lub SQL Server Management Studio Express, zobacz [How to: Dołącz bazę danych (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Aby dołączyć bazę danych za pomocą wiersza polecenia, zobacz [How to: Dołącz plik bazy danych do SQL Server Express](/previous-versions/sql/).

## <a name="create-a-new-project"></a>Tworzenie nowego projektu
 Pierwszym krokiem jest utworzenie projektu dodatku VSTO dla programu Excel.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt dodatku VSTO programu Excel z nazwami **wypełniania arkuszami z bazy danych**przy użyciu Visual Basic lub C#.

     Aby uzyskać więcej informacji, zobacz [jak: Utwórz projekty pakietu Office w programie](../vsto/how-to-create-office-projects-in-visual-studio.md)Visual Studio.

     Program Visual Studio otwiera `ThisAddIn.vb` plik `ThisAddIn.cs` lub i dodaje **arkusze wypełniania z projektu bazy danych** do **Eksplorator rozwiązań**.

## <a name="create-a-data-source"></a>Utwórz źródło danych
 Użyj okna **źródła danych** , aby dodać do projektu typ zestawu danych.

### <a name="to-add-a-typed-dataset-to-the-project"></a>Aby dodać typ DataSet do projektu

1. Jeśli okno **źródła danych** nie jest widoczne, Wyświetl je na pasku menu, wybierając opcję **Wyświetl** > inne**źródła danych** **systemu Windows** > .

2. Wybierz pozycję **Dodaj nowe źródło danych** , aby uruchomić **Kreatora konfiguracji źródła danych**.

3. Kliknij pozycję **baza danych**, a następnie kliknij przycisk **dalej**.

4. Jeśli masz istniejące połączenie z `AdventureWorksLT` bazą danych, wybierz to połączenie i kliknij przycisk **dalej**.

    W przeciwnym razie kliknij pozycję **nowe połączenie**, a następnie użyj okna dialogowego **Dodawanie połączenia** , aby utworzyć nowe połączenie. Aby uzyskać więcej informacji, zobacz [Dodawanie nowych połączeń](../data-tools/add-new-connections.md).

5. Na stronie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** kliknij przycisk **dalej**.

6. Na stronie **Wybierz obiekty bazy danych** rozwiń pozycję **tabele** i wybierz pozycję **adres (tabeli SalesLT)** .

7. Kliknij przycisk **Zakończ**.

    Plik *AdventureWorksLTDataSet. xsd* zostanie dodany do **Eksplorator rozwiązań**. Ten plik definiuje następujące elementy:

   - Określony zestaw danych o `AdventureWorksLTDataSet`nazwie. Ten zestaw danych reprezentuje zawartość tabeli **Address (tabeli SalesLT)** w bazie danych AdventureWorksLT.

   - TableAdapter o nazwie `AddressTableAdapter`. Ten TableAdapter może służyć do odczytywania i zapisywania danych w `AdventureWorksLTDataSet`. Aby uzyskać więcej informacji, zobacz [TableAdapter Overview (przegląd](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)).

     Oba te obiekty będą używane w dalszej części tego przewodnika.

## <a name="create-controls-and-bind-controls-to-data"></a>Tworzenie kontrolek i powiązywanie kontrolek z danymi
 W tym instruktażu <xref:Microsoft.Office.Tools.Excel.ListObject> formant Wyświetla wszystkie dane w wybranej tabeli zaraz po otwarciu skoroszytu przez użytkownika. Obiekt list używa elementu <xref:System.Windows.Forms.BindingSource> , aby połączyć formant z bazą danych.

 Aby uzyskać więcej informacji o kontrolkach powiązań z danymi, zobacz temat [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-add-the-list-object-dataset-and-table-adapter"></a>Aby dodać obiekt list, zestaw danych i adapter tabeli

1. W klasie deklaruj następujące kontrolki, aby `Address` wyświetlić tabelę `AdventureWorksLTDataSet` zestawu danych. `ThisAddIn`

     [!code-csharp[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#1)]

2. W metodzie Dodaj następujący kod, aby zainicjować zestaw danych i wypełnić zestaw danych informacjami `AdventureWorksLTDataSet` z zestawu danych. `ThisAddIn_Startup`

     [!code-csharp[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#2)]

3. Dodaj następujący kod do `ThisAddIn_Startup` metody. Spowoduje to wygenerowanie elementu hosta, który rozszerza arkusz. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

     [!code-csharp[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#3)]

4. Utwórz zakres i Dodaj <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolkę.

     [!code-csharp[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#4)]
     [!code-vb[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#4)]

5. Powiąż obiekt listy z `AdventureWorksLTDataSet` przy <xref:System.Windows.Forms.BindingSource>użyciu. Przekaż nazwy kolumn, które chcesz powiązać z obiektem listy.

     [!code-csharp[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#5)]
     [!code-vb[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#5)]

## <a name="test-the-add-in"></a>Testowanie dodatku
 Po otwarciu programu Excel, <xref:Microsoft.Office.Tools.Excel.ListObject> formant Wyświetla dane `Address` z tabeli `AdventureWorksLTDataSet` zestawu danych.

### <a name="to-test-the-vsto-add-in"></a>Aby przetestować dodatek narzędzi VSTO

- Naciśnij klawisz **F5**.

     Kontrolka o `addressListObject` nazwie została utworzona w arkuszu. <xref:Microsoft.Office.Tools.Excel.ListObject> W tym samym czasie obiekt zestawu danych o nazwie `adventureWorksLTDataSet` <xref:System.Windows.Forms.BindingSource> i nazwie `addressBindingSource` zostanie dodany do projektu. <xref:Microsoft.Office.Tools.Excel.ListObject> Jest powiązany<xref:System.Windows.Forms.BindingSource>z, który z kolei jest powiązany z obiektem DataSet.

## <a name="see-also"></a>Zobacz także

- [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)
- [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Instrukcje: Wypełnianie arkuszy danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Instrukcje: Wypełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Instrukcje: Wypełnianie dokumentów danymi z usług](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Instrukcje: Wypełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Instrukcje: Przewijanie rekordów bazy danych w arkuszu](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Instrukcje: Aktualizowanie źródła danych przy użyciu danych z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Przewodnik: Proste powiązanie danych w projekcie na poziomie dokumentu](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
- [Przewodnik: Złożone powiązanie danych w projekcie na poziomie dokumentu](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
- [Korzystanie z plików lokalnej bazy danych w rozwiązaniach pakietu Office — omówienie](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)
- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Korzystanie z plików lokalnej bazy danych w rozwiązaniach pakietu Office — omówienie](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource, składnik — Omówienie](/dotnet/framework/winforms/controls/bindingsource-component-overview)
