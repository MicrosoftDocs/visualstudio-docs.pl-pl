---
title: 'Instrukcje: aktualizowanie źródła danych przy użyciu danych z kontrolki hosta'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], data source updates
- data [Office development in Visual Studio], updating a data source from a document
- host controls [Office development in Visual Studio], data source updates
- Office documents [Office development in Visual Studio, data sources
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 52540f0cf94a12efda891657ec4aae9452ad6f86
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585122"
---
# <a name="how-to-update-a-data-source-with-data-from-a-host-control"></a>Instrukcje: aktualizowanie źródła danych przy użyciu danych z kontrolki hosta
  Formant hosta można powiązać ze źródłem danych i zaktualizować źródło danych przy użyciu zmian wprowadzonych w danych w formancie. W tym procesie istnieją dwa główne kroki:

1. Zaktualizuj źródło danych w pamięci za pomocą zmodyfikowanych danych w formancie. Zazwyczaj źródłem danych w pamięci jest <xref:System.Data.DataSet> , a <xref:System.Data.DataTable> lub inny obiekt danych.

2. Zaktualizuj bazę danych o zmienione dane w źródle danych w pamięci. Ma to zastosowanie tylko wtedy, gdy źródło danych jest połączone z bazą danych zaplecza, taką jak SQL Server lub baza danych Microsoft Office Access.

   Aby uzyskać więcej informacji na temat kontrolek hosta i powiązania danych, zobacz temat [elementy hosta i kontrolki hosta](../vsto/host-items-and-host-controls-overview.md) oraz [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).

   [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="update-the-in-memory-data-source"></a>Aktualizowanie źródła danych znajdującego się w pamięci
 Domyślnie formanty hosta, które włączają proste powiązanie danych (takie jak kontrolki zawartości w dokumencie programu Word lub kontrolka nazwanego zakresu w arkuszu programu Excel), nie zapisują zmian danych w źródle danych w pamięci. Oznacza to, że gdy użytkownik końcowy zmieni wartość w formancie hosta, a następnie nawiguje poza formantem, Nowa wartość w kontrolce nie jest automatycznie zapisywana w źródle danych.

 Aby zapisać dane w źródle danych, można napisać kod, który aktualizuje źródło danych w odpowiedzi na konkretne zdarzenie w czasie wykonywania, lub można skonfigurować kontrolkę tak, aby automatycznie aktualizowana źródła danych po zmianie wartości w kontrolce.

 Nie trzeba zapisywać <xref:Microsoft.Office.Tools.Excel.ListObject> zmian w źródle danych w pamięci. Po powiązaniu <xref:Microsoft.Office.Tools.Excel.ListObject> formantu z danymi, <xref:Microsoft.Office.Tools.Excel.ListObject> formant automatycznie zapisuje zmiany w źródle danych w pamięci bez konieczności dodatkowego kodu.

### <a name="to-update-the-in-memory-data-source-at-run-time"></a>Aby zaktualizować źródło danych znajdujące się w pamięci w czasie wykonywania

- Wywołaj <xref:System.Windows.Forms.Binding.WriteValue%2A> metodę <xref:System.Windows.Forms.Binding> obiektu, który wiąże formant ze źródłem danych.

     Poniższy przykład zapisuje zmiany wprowadzone do <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki w arkuszu programu Excel do źródła danych. W tym przykładzie przyjęto założenie, że masz <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę o nazwie `namedRange1` z <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> właściwością powiązaną z polem w źródle danych.

     [!code-csharp[Trin_VstcoreDataExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreDataExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#1)]

### <a name="automatically-update-the-in-memory-data-source"></a>Automatycznie Aktualizuj źródło danych w pamięci
 Można również skonfigurować kontrolkę tak, aby automatycznie aktualizowana źródła danych znajdującego się w pamięci. W projekcie na poziomie dokumentu można to zrobić za pomocą kodu lub projektanta. W projekcie dodatku VSTO należy użyć kodu.

#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-code"></a>Aby ustawić kontrolkę do automatycznej aktualizacji źródła danych znajdującego się w pamięci przy użyciu kodu

1. Użyj trybu system. Windows. Forms. DataSourceUpdateMode. OnPropertyChanged <xref:System.Windows.Forms.Binding> obiektu, który wiąże formant ze źródłem danych. Dostępne są dwie opcje aktualizacji źródła danych:

   - Aby zaktualizować źródło danych po sprawdzeniu poprawności kontrolki, należy ustawić tę właściwość na system. Windows. Forms. DataSourceUpdateMode. onwalidacja.

   - Aby zaktualizować źródło danych po zmianie wartości właściwości powiązanej z danymi kontrolki, należy ustawić tę właściwość na system. Windows. Forms. DataSourceUpdateMode. OnPropertyChanged.

     > [!NOTE]
     > Opcja system. Windows. Forms. DataSourceUpdateMode. OnPropertyChanged nie ma zastosowania do kontrolek hosta programu Word, ponieważ program Word nie oferuje powiadomień o zmianach lub kontroli nad dokumentami. Jednak ta opcja może służyć do Windows Forms formantów w dokumentach programu Word.

     Poniższy przykład konfiguruje <xref:Microsoft.Office.Tools.Excel.NamedRange> formant do automatycznej aktualizacji źródła danych, gdy wartość w formancie zostanie zmieniona. W tym przykładzie przyjęto założenie, że masz <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę o nazwie `namedRange1` z <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> właściwością powiązaną z polem w źródle danych.

     [!code-csharp[Trin_VstcoreDataExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreDataExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#19)]

#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-the-designer"></a>Aby ustawić kontrolkę do automatycznej aktualizacji źródła danych znajdującego się w pamięci przy użyciu narzędzia Projektant

1. W programie Visual Studio Otwórz dokument programu Word lub skoroszyt programu Excel w projektancie.

2. Kliknij formant, który ma automatycznie aktualizować źródło danych.

3. W oknie **Właściwości** rozwiń Właściwość **(DataBindings)** .

4. Obok właściwości **(Zaawansowane)** kliknij przycisk wielokropka (![VisualStudioEllipsesButton zrzut ekranu](../vsto/media/vbellipsesbutton.png "Zrzut ekranu VisualStudioEllipsesButton")).

5. W oknie dialogowym **Formatowanie i zaawansowane powiązanie** kliknij listę rozwijaną **Tryb aktualizacji źródła danych** i wybierz jedną z następujących wartości:

    - Aby zaktualizować źródło danych po sprawdzeniu poprawności kontrolki, wybierz pozycję **Onwalidacja**.

    - Aby zaktualizować źródło danych po zmianie wartości właściwości powiązanej z danymi kontrolki, wybierz pozycję **OnPropertyChanged**.

        > [!NOTE]
        > Opcja **OnPropertyChanged** nie ma zastosowania do kontrolek hosta programu Word, ponieważ program Word nie oferuje powiadomień o zmianach dokumentu ani kontroli nad zmianami. Jednak ta opcja może służyć do Windows Forms formantów w dokumentach programu Word.

6. Zamknij okno dialogowe **Formatowanie i powiązanie zaawansowane** .

## <a name="update-the-database"></a>Aktualizowanie bazy danych
 Jeśli źródło danych znajdujące się w pamięci jest skojarzone z bazą danych, należy zaktualizować bazę danych ze zmianami w źródle danych. Aby uzyskać więcej informacji o aktualizowaniu bazy danych, zobacz [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)  i [Aktualizowanie danych przy użyciu TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md) .

### <a name="to-update-the-database"></a>Aby zaktualizować bazę danych

1. Wywoływanie <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metody <xref:System.Windows.Forms.BindingSource> dla kontrolki.

     <xref:System.Windows.Forms.BindingSource>Jest generowany automatycznie po dodaniu kontrolki powiązanej z danymi do dokumentu lub skoroszytu w czasie projektowania. <xref:System.Windows.Forms.BindingSource>Łączy formant z określonym zestawem danych w projekcie. Aby uzyskać więcej informacji, zobacz [źródło BindingSource — Omówienie](/dotnet/framework/winforms/controls/bindingsource-component-overview).

     W poniższym przykładzie kodu założono, że projekt zawiera <xref:System.Windows.Forms.BindingSource> nazwę `customersBindingSource` .

     [!code-csharp[Trin_VstcoreDataExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreDataExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#20)]

2. Wywołaj `Update` metodę wygenerowanego TableAdapter w projekcie.

     TableAdapter jest generowany automatycznie po dodaniu kontrolki powiązanej z danymi do dokumentu lub skoroszytu w czasie projektowania. TableAdapter nawiązuje połączenie określonego zestawu danych w projekcie z bazą danych. Aby uzyskać więcej informacji, zobacz [TableAdapter Overview (przegląd](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)).

     W poniższym przykładzie kodu założono, że masz połączenie z tabelą Customers w bazie danych Northwind i że projekt zawiera TableAdapter o nazwie `customersTableAdapter` i z określonym typem danych o nazwie `northwindDataSet` .

     [!code-csharp[Trin_VstcoreDataExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreDataExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#21)]

## <a name="see-also"></a>Zobacz też
- [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
- [Aktualizowanie danych za pomocą adaptera TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)
- [Instrukcje: przewijanie rekordów bazy danych w arkuszu](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Instrukcje: zapełnianie arkuszy danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Instrukcje: zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Instrukcje: zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Instrukcje: zapełnianie dokumentów danymi z usług](../vsto/how-to-populate-documents-with-data-from-services.md)
