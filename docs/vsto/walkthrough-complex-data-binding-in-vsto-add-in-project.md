---
title: 'Przewodnik: złożone powiązanie danych w projekcie dodatku VSTO'
titleSuffix: ''
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
ms.openlocfilehash: c0d65bd96a3860070addc6dc05a791d71959f5ea
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585044"
---
# <a name="walkthrough-complex-data-binding-in-vsto-add-in-project"></a>Przewodnik: złożone powiązanie danych w projekcie dodatku VSTO
  Można powiązać dane z kontrolkami hosta i formantami Windows Forms w projektach dodatku VSTO. W tym instruktażu pokazano, jak dodać kontrolki do Microsoft Office arkusza programu Excel i powiązać kontrolki z danymi w czasie wykonywania.

 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki do arkusza w czasie wykonywania.

- Tworzenie <xref:System.Windows.Forms.BindingSource> , które łączy formant z wystąpieniem zestawu danych.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Dostęp do uruchomionego wystąpienia programu SQL Server 2005 lub SQL Server 2005 Express, do którego jest `AdventureWorksLT` Dołączona przykładowa baza danych. Bazę danych można pobrać `AdventureWorksLT` z repozytorium w witrynie [GitHub SQL Server Samples](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). Aby uzyskać więcej informacji na temat dołączania bazy danych, zobacz następujące tematy:

  - Aby dołączyć bazę danych za pomocą SQL Server Management Studio lub SQL Server Management Studio Express, zobacz [How to: dołączanie bazy danych (SQL Server Management Studio)](/sql/relational-databases/databases/attach-a-database).

  - Aby dołączyć bazę danych za pomocą wiersza polecenia, zobacz [How to: Dołączanie pliku bazy danych do SQL Server Express](/previous-versions/sql/).

## <a name="create-a-new-project"></a>Tworzenie nowego projektu
 Pierwszym krokiem jest utworzenie projektu dodatku VSTO dla programu Excel.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt dodatku VSTO programu Excel z nazwami **zapełniania arkuszami z bazy danych**przy użyciu Visual Basic lub C#.

     Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Program Visual Studio otwiera `ThisAddIn.vb` `ThisAddIn.cs` plik lub i dodaje **arkusze wypełniania z projektu bazy danych** do **Eksplorator rozwiązań**.

## <a name="create-a-data-source"></a>Tworzenie źródła danych
 Użyj okna **źródła danych** , aby dodać do projektu typ zestawu danych.

### <a name="to-add-a-typed-dataset-to-the-project"></a>Aby dodać typ DataSet do projektu

1. Jeśli okno **źródła danych** nie jest widoczne, Wyświetl je na pasku menu, wybierając opcję **Wyświetl**  >  **inne**  >  **źródła danych**systemu Windows.

2. Wybierz pozycję **Dodaj nowe źródło danych** , aby uruchomić **Kreatora konfiguracji źródła danych**.

3. Kliknij pozycję **baza danych**, a następnie kliknij przycisk **dalej**.

4. Jeśli masz istniejące połączenie z `AdventureWorksLT` bazą danych, wybierz to połączenie i kliknij przycisk **dalej**.

    W przeciwnym razie kliknij pozycję **nowe połączenie**, a następnie użyj okna dialogowego **Dodawanie połączenia** , aby utworzyć nowe połączenie. Aby uzyskać więcej informacji, zobacz [Dodawanie nowych połączeń](../data-tools/add-new-connections.md).

5. Na stronie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** kliknij przycisk **dalej**.

6. Na stronie **Wybierz obiekty bazy danych** rozwiń pozycję **tabele** i wybierz pozycję **adres (tabeli SalesLT)**.

7. Kliknij przycisk **Zakończ**.

    Plik *AdventureWorksLTDataSet. xsd* zostanie dodany do **Eksplorator rozwiązań**. Ten plik definiuje następujące elementy:

   - Określony zestaw danych o nazwie `AdventureWorksLTDataSet` . Ten zestaw danych reprezentuje zawartość tabeli **Address (tabeli SalesLT)** w bazie danych AdventureWorksLT.

   - TableAdapter o nazwie `AddressTableAdapter` . Ten TableAdapter może służyć do odczytywania i zapisywania danych w `AdventureWorksLTDataSet` . Aby uzyskać więcej informacji, zobacz [TableAdapter Overview (przegląd](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)).

     Oba te obiekty będą używane w dalszej części tego przewodnika.

## <a name="create-controls-and-bind-controls-to-data"></a>Tworzenie kontrolek i powiązywanie kontrolek z danymi
 W tym instruktażu <xref:Microsoft.Office.Tools.Excel.ListObject> formant Wyświetla wszystkie dane w wybranej tabeli zaraz po otwarciu skoroszytu przez użytkownika. Obiekt list używa elementu, <xref:System.Windows.Forms.BindingSource> Aby połączyć formant z bazą danych.

 Aby uzyskać więcej informacji o kontrolkach powiązań z danymi, zobacz temat [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-add-the-list-object-dataset-and-table-adapter"></a>Aby dodać obiekt list, zestaw danych i adapter tabeli

1. W `ThisAddIn` klasie deklaruj następujące kontrolki, aby wyświetlić `Address` tabelę `AdventureWorksLTDataSet` zestawu danych.

     [!code-csharp[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#1)]

2. W `ThisAddIn_Startup` metodzie Dodaj następujący kod, aby zainicjować zestaw danych i wypełnić zestaw danych informacjami z `AdventureWorksLTDataSet` zestawu danych.

     [!code-csharp[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#2)]

3. Dodaj następujący kod do metody `ThisAddIn_Startup`: Spowoduje to wygenerowanie elementu hosta, który rozszerza arkusz. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

     [!code-csharp[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#3)]

4. Utwórz zakres i Dodaj <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolkę.

     [!code-csharp[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#4)]
     [!code-vb[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#4)]

5. Powiąż obiekt listy z przy `AdventureWorksLTDataSet` użyciu <xref:System.Windows.Forms.BindingSource> . Przekaż nazwy kolumn, które chcesz powiązać z obiektem listy.

     [!code-csharp[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#5)]
     [!code-vb[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#5)]

## <a name="test-the-add-in"></a>Testowanie dodatku
 Po otwarciu programu Excel, <xref:Microsoft.Office.Tools.Excel.ListObject> formant Wyświetla dane z `Address` tabeli `AdventureWorksLTDataSet` zestawu danych.

### <a name="to-test-the-vsto-add-in"></a>Aby przetestować dodatek narzędzi VSTO

- Naciśnij klawisz **F5**.

     <xref:Microsoft.Office.Tools.Excel.ListObject>Kontrolka o nazwie `addressListObject` została utworzona w arkuszu. W tym samym czasie obiekt zestawu danych o nazwie `adventureWorksLTDataSet` i <xref:System.Windows.Forms.BindingSource> nazwie `addressBindingSource` zostanie dodany do projektu. <xref:Microsoft.Office.Tools.Excel.ListObject>Jest powiązany z <xref:System.Windows.Forms.BindingSource> , który z kolei jest powiązany z obiektem DataSet.

## <a name="see-also"></a>Zobacz też

- [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)
- [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Instrukcje: zapełnianie arkuszy danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Instrukcje: zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Instrukcje: zapełnianie dokumentów danymi z usług](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Instrukcje: zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Instrukcje: przewijanie rekordów bazy danych w arkuszu](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Instrukcje: aktualizowanie źródła danych przy użyciu danych z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Przewodnik: proste powiązanie danych w projekcie na poziomie dokumentu](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
- [Przewodnik: złożone powiązanie danych w projekcie na poziomie dokumentu](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
- [Korzystanie z plików lokalnej bazy danych w rozwiązaniach pakietu Office — omówienie](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)
- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Korzystanie z plików lokalnej bazy danych w rozwiązaniach pakietu Office — omówienie](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource, składnik — Omówienie](/dotnet/framework/winforms/controls/bindingsource-component-overview)
