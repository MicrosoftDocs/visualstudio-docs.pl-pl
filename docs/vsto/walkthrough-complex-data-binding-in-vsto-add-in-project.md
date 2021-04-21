---
title: 'Przewodnik: złożone powiązanie danych w projekcie dodatku VSTO'
description: Dowiedz się, jak dodawać kontrolki do arkusza programu Microsoft Excel i powiązać je z danymi w czasie uruchamiania.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 49f87968c545e9fcca7548cd2fbda866d18b660b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826359"
---
# <a name="walkthrough-complex-data-binding-in-vsto-add-in-project"></a>Przewodnik: złożone powiązanie danych w projekcie dodatku VSTO
  Dane można powiązać z kontrolkami hostów i Windows Forms w projektach dodatków VSTO. W tym przewodniku pokazano, jak dodać kontrolki do arkusza programu Excel Microsoft Office i powiązać kontrolki z danymi w czasie uruchamiania.

 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki do arkusza w czasie uruchamiania.

- Tworzenie obiektu <xref:System.Windows.Forms.BindingSource> , który łączy kontrolkę z wystąpieniem zestawu danych.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] lub [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Dostęp do uruchomionego wystąpienia programu SQL Server 2005 lub SQL Server 2005 Express, do których jest dołączona `AdventureWorksLT` przykładowa baza danych. Bazę danych można `AdventureWorksLT` pobrać z [repozytorium GitHub SQL Server Przykłady.](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) Aby uzyskać więcej informacji na temat dołączania bazy danych, zobacz następujące tematy:

  - Aby dołączyć bazę danych przy użyciu programu SQL Server Management Studio lub SQL Server Management Studio Express, zobacz Jak dołączyć bazę danych [(SQL Server Management Studio).](/sql/relational-databases/databases/attach-a-database)

  - Aby dołączyć bazę danych przy użyciu wiersza polecenia, zobacz [How to: Attach a database file to SQL Server Express](/previous-versions/sql/).

## <a name="create-a-new-project"></a>Tworzenie nowego projektu
 Pierwszym krokiem jest utworzenie projektu dodatku VSTO programu Excel.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt dodatku VSTO programu Excel o nazwie **Wypełnianie** arkuszy z bazy danych przy użyciu Visual Basic lub C#.

     Aby uzyskać więcej informacji, [zobacz How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio plik lub i dodaje arkusze wypełniania z projektu bazy danych `ThisAddIn.vb` `ThisAddIn.cs` do **Eksplorator rozwiązań**. 

## <a name="create-a-data-source"></a>Tworzenie źródła danych
 Użyj okna **Źródła danych,** aby dodać typowany zestaw danych do projektu.

### <a name="to-add-a-typed-dataset-to-the-project"></a>Aby dodać typowany zestaw danych do projektu

1. Jeśli **okno Źródła danych** nie jest widoczne, wyświetl je na pasku menu, wybierając pozycję **Wyświetl** inne źródła  >  danych systemu **Windows.**  >  

2. Wybierz **pozycję Dodaj nowe źródło danych,** aby uruchomić Kreatora konfiguracji źródła **danych.**

3. Kliknij **pozycję Baza** danych, a następnie kliknij przycisk **Dalej.**

4. Jeśli masz istniejące połączenie z bazą `AdventureWorksLT` danych, wybierz to połączenie i kliknij przycisk **Dalej.**

    W przeciwnym razie **kliknij pozycję Nowe** połączenie i użyj okna **dialogowego** Dodawanie połączenia, aby utworzyć nowe połączenie. Aby uzyskać więcej informacji, zobacz [Dodawanie nowych połączeń.](../data-tools/add-new-connections.md)

5. Na stronie **Zapisywanie parametrów połączenia w pliku konfiguracji aplikacji** kliknij przycisk **Dalej.**

6. Na stronie **Wybieranie obiektów bazy danych** rozwiń pozycję **Tabele** i wybierz pozycję **Adres (SalesLT).**

7. Kliknij przycisk **Finish** (Zakończ).

    Plik *AdventureWorksLTDataSet.xsd* jest dodawany do **Eksplorator rozwiązań**. Ten plik definiuje następujące elementy:

   - Typowany zestaw danych o nazwie `AdventureWorksLTDataSet` . Ten zestaw danych reprezentuje zawartość tabeli **Address (SalesLT)** w bazie danych AdventureWorksLT.

   - TableAdapter o nazwie `AddressTableAdapter` . Ten tableAdapter może służyć do odczytu i zapisu danych w `AdventureWorksLTDataSet` . Aby uzyskać więcej informacji, zobacz [Omówienie tableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Obu tych obiektów użyjemy w dalszej części tego przewodnika.

## <a name="create-controls-and-bind-controls-to-data"></a>Tworzenie kontrolek i wiązanie kontrolek z danymi
 W tym przewodniku kontrolka wyświetla wszystkie dane w wybranej tabeli, gdy tylko <xref:Microsoft.Office.Tools.Excel.ListObject> użytkownik otworzy skoroszyt. Obiekt listy używa obiektu do <xref:System.Windows.Forms.BindingSource> połączenia kontrolki z bazą danych.

 Aby uzyskać więcej informacji na temat wiązania kontrolek z danymi, zobacz [Wiązanie danych z kontrolkami w rozwiązaniach pakietu Office.](../vsto/binding-data-to-controls-in-office-solutions.md)

### <a name="to-add-the-list-object-dataset-and-table-adapter"></a>Aby dodać obiekt listy, zestaw danych i kartę tabeli

1. W klasie `ThisAddIn` zadeklaruj następujące kontrolki, aby `Address` wyświetlić tabelę zestawu `AdventureWorksLTDataSet` danych.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb" id="Snippet1":::

2. W metodzie dodaj następujący kod, aby zainicjować zestaw danych i wypełnić zestaw danych informacjami `ThisAddIn_Startup` z zestawu `AdventureWorksLTDataSet` danych.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb" id="Snippet2":::

3. Dodaj następujący kod do metody `ThisAddIn_Startup`: Powoduje to wygenerowanie elementu hosta, który rozszerza arkusz. Aby uzyskać więcej informacji, zobacz [Extend Word documents and Excel workbooks in VSTO Add-ins at run time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)(Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w czasie uruchamiania).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb" id="Snippet3":::

4. Utwórz zakres i dodaj <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolkę.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb" id="Snippet4":::

5. Powiąż obiekt listy `AdventureWorksLTDataSet` z obiektem przy użyciu obiektu <xref:System.Windows.Forms.BindingSource> . Przekaż nazwy kolumn, które chcesz powiązać z obiektem listy.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb" id="Snippet5":::

## <a name="test-the-add-in"></a>Testowanie dodatku
 Po otwarciu programu Excel <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolka wyświetla dane z `Address` tabeli zestawu `AdventureWorksLTDataSet` danych.

### <a name="to-test-the-vsto-add-in"></a>Aby przetestować dodatek VSTO

- Naciśnij klawisz **F5**.

     W <xref:Microsoft.Office.Tools.Excel.ListObject> arkuszu zostanie utworzona `addressListObject` kontrolka o nazwie . W tym samym czasie obiekt zestawu danych o `adventureWorksLTDataSet` nazwie i nazwie są dodawane do <xref:System.Windows.Forms.BindingSource> `addressBindingSource` projektu. Obiekt jest powiązany z obiektem , który z <xref:Microsoft.Office.Tools.Excel.ListObject> kolei jest powiązany z <xref:System.Windows.Forms.BindingSource> obiektem zestawu danych.

## <a name="see-also"></a>Zobacz też

- [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)
- [Wiązanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Jak wypełnić arkusze danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [How to: Populate documents with data from a database (Jak wypełnić dokumenty danymi z bazy danych)](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [How to: Populate documents with data from services (Jak wypełnić dokumenty danymi z usług)](../vsto/how-to-populate-documents-with-data-from-services.md)
- [How to: Populate documents with data from objects (Jak wypełnić dokumenty danymi z obiektów)](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Jak przewijać rekordy bazy danych w arkuszu](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Jak zaktualizować źródło danych przy użyciu danych z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Przewodnik: Proste powiązanie danych w projekcie na poziomie dokumentu](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
- [Przewodnik: złożone powiązanie danych w projekcie na poziomie dokumentu](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
- [Omówienie używania plików lokalnej bazy danych w rozwiązaniach pakietu Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)
- [Wiązanie kontrolek Windows Forms z danymi w programie Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Omówienie używania plików lokalnej bazy danych w rozwiązaniach pakietu Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource, składnik — omówienie](/dotnet/framework/winforms/controls/bindingsource-component-overview)
