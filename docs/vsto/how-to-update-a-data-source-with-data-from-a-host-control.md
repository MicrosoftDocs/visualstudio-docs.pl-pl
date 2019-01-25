---
title: 'Instrukcje: Aktualizowanie źródła danych danymi z kontrolki hosta'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: f35b5a67ce43d2e727aa052a8165fbdf7123eda0
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863122"
---
# <a name="how-to-update-a-data-source-with-data-from-a-host-control"></a>Instrukcje: Aktualizowanie źródła danych danymi z kontrolki hosta
  Można powiązać kontrolki hosta ze źródłem danych i zaktualizować źródło danych ze zmianami, które zostały wprowadzone do danych w formancie. Istnieją dwa podstawowe kroki w ramach tego procesu:  
  
1. Zaktualizuj źródło danych w pamięci przy użyciu zmodyfikowanych danych w formancie. Zazwyczaj jest źródło danych w pamięci <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, lub inny obiekt danych.  
  
2. Aktualizacji bazy danych przy użyciu zmienionych danych w źródle danych w pamięci. Ma to zastosowanie tylko wtedy, gdy źródło danych jest podłączony do wewnętrznej bazy danych, na przykład w bazie danych programu SQL Server lub programu Microsoft Office Access.  
  
   Aby uzyskać więcej informacji na temat formantów hosta i powiązania danych, zobacz [elementów, a omówienie kontrolek](../vsto/host-items-and-host-controls-overview.md) i [wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
   [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="update-the-in-memory-data-source"></a>Zaktualizuj źródło danych w pamięci  
 Domyślnie formanty hosta, które umożliwiają proste powiązanie danych (na przykład formanty zawartości w dokumencie programu Word lub kontrolka nazwany zakres na arkuszu programu Excel) nie należy zapisywać zmian danych do źródła danych w pamięci. Oznacza to po użytkownik końcowy zmienia wartość w kontrolce hosta, a następnie powoduje przejście od formantu, nową wartość w formancie nie są automatycznie zapisywane do źródła danych.  
  
 Aby zapisać dane do źródła danych, można napisać kod, który aktualizuje źródło danych w odpowiedzi na zdarzenia w czasie wykonywania, lub możesz skonfigurować kontrolę, można automatycznie zaktualizować źródła danych, po zmianie wartości w kontrolce.  
  
 Nie musisz zapisać <xref:Microsoft.Office.Tools.Excel.ListObject> zmienia się ze źródłem danych w pamięci. Po powiązaniu <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki z danymi, <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli automatycznie zapisze zmiany w źródle danych w pamięci bez konieczności dodatkowego kodu.  
  
### <a name="to-update-the-in-memory-data-source-at-runtime"></a>Aby zaktualizować źródło danych w pamięci w czasie wykonywania  
  
-   Wywołaj <xref:System.Windows.Forms.Binding.WriteValue%2A> metody <xref:System.Windows.Forms.Binding> obiekt, który wiąże formant ze źródłem danych.  
  
     Poniższy przykład zapisuje zmiany wprowadzone do <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki w arkuszu programu Excel do źródła danych. W tym przykładzie przyjęto założenie, iż <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu o nazwie `namedRange1` z jego <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> właściwości powiązany z polem w źródle danych.  
  
     [!code-csharp[Trin_VstcoreDataExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreDataExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#1)]  
  
### <a name="automatically-update-the-in-memory-data-source"></a>Automatycznie Aktualizuj źródło danych w pamięci  
 Można również skonfigurować kontrolkę tak, aby automatycznie aktualizuje źródło danych w pamięci. W projekcie na poziomie dokumentu możesz to zrobić przy użyciu kodu lub Projektant. W projekcie dodatku narzędzi VSTO dla programów należy użyć kodu.  
  
#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-code"></a>Aby ustawić kontroli można automatycznie zaktualizować źródło danych w pamięci przy użyciu kodu  
  
1. Użyj trybu System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged <xref:System.Windows.Forms.Binding> obiekt, który wiąże formant ze źródłem danych. Dostępne są dwie opcje do aktualizowania źródła danych:  
  
   - Aby zaktualizować źródła danych, gdy kontrolka jest weryfikowana, należy ustawić tę właściwość na System.Windows.Forms.DataSourceUpdateMode.OnValidation.  
  
   - Aby zaktualizować źródło danych, po zmianie wartości właściwości powiązanych z danymi formantu, należy ustawić tę właściwość na System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged.  
  
     > [!NOTE]  
     >  Opcja System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged nie dotyczą kontrolki hosta programu Word, ponieważ program Word jest nie oferty dokumentu zmian lub zmiana sterowania powiadomień. Jednak ta opcja może służyć dla formantów Windows Forms w dokumentach programu Word.  
  
     Poniższy przykład umożliwia skonfigurowanie <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli można automatycznie zaktualizować źródła danych, po zmianie wartości w kontrolce. W tym przykładzie przyjęto założenie, iż <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu o nazwie `namedRange1` z jego <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> właściwości powiązany z polem w źródle danych.  
  
     [!code-csharp[Trin_VstcoreDataExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreDataExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#19)]  
  
#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-the-designer"></a>Aby ustawić kontroli można automatycznie zaktualizować źródło danych w pamięci przy użyciu narzędzia Projektant  
  
1.  W programie Visual Studio Otwórz dokument programu Word lub skoroszyt programu Excel w projektancie.  
  
2.  Kliknij formant, który ma być automatycznie zaktualizować źródło danych.  
  
3.  W **właściwości** okna, rozwiń węzeł **(powiązania danych)** właściwości.  
  
4.  Obok pozycji **(zaawansowane)** właściwości, kliknij przycisk oznaczony wielokropkiem (![VisualStudioEllipsesButton — zrzut ekranu](../vsto/media/vbellipsesbutton.png "VisualStudioEllipsesButton — zrzut ekranu")).  
  
5.  W **formatowanie i powiązywanie zaawansowane** okno dialogowe, kliknij przycisk **tryb aktualizacji źródła danych** listy rozwijanej i wybierz jedną z następujących wartości:  
  
    -   Aby zaktualizować źródła danych, gdy kontrolka jest weryfikowana, wybierz pozycję **OnValidation**.  
  
    -   Aby zaktualizować źródło danych, po zmianie wartości właściwości powiązanych z danymi formantu, wybierz **onpropertychanged —**.  
  
        > [!NOTE]  
        >  **Onpropertychanged —** opcji nie ma zastosowania do kontrolki hosta programu Word, ponieważ program Word jest nie oferty dokumentu zmian lub zmiana sterowania powiadomień. Jednak ta opcja może służyć dla formantów Windows Forms w dokumentach programu Word.  
  
6.  Zamknij **formatowanie i powiązywanie zaawansowane** okno dialogowe.  
  
## <a name="update-the-database"></a>Aktualizowanie bazy danych  
 Jeśli źródło danych w pamięci jest skojarzona z bazą danych, należy zaktualizować bazy danych zmian w źródle danych. Aby uzyskać więcej informacji na temat aktualizowania bazy danych, zobacz [zapisać dane w bazie danych](../data-tools/save-data-back-to-the-database.md) i [aktualizowanie danych za pomocą adaptera TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md) .  
  
### <a name="to-update-the-database"></a>Aby zaktualizować bazę danych  
  
1.  Wywołaj <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metody <xref:System.Windows.Forms.BindingSource> dla formantu.  
  
     <xref:System.Windows.Forms.BindingSource> Jest generowany automatycznie po dodaniu kontrolki powiązania danych na dokument lub skoroszyt w czasie projektowania. <xref:System.Windows.Forms.BindingSource> Łączy kontrolki do zestawu danych w projekcie. Aby uzyskać więcej informacji, zobacz [— informacje o składniku BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).  
  
     Poniższy przykład kodu zakłada, że projekt zawiera <xref:System.Windows.Forms.BindingSource> o nazwie `customersBindingSource`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreDataExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#20)]  
  
2.  Wywołaj `Update` metody TableAdapter wygenerowany w projekcie.  
  
     TableAdapter jest generowany automatycznie po dodaniu kontrolki powiązania danych na dokument lub skoroszyt w czasie projektowania. TableAdapter łączy z zestawu danych w projekcie w bazie danych. Aby uzyskać więcej informacji, zobacz [TableAdapter — Przegląd](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
     Poniższy przykład kodu zakłada, czy masz połączenie z tabeli Customers w bazie danych Northwind i że projekt zawiera TableAdapter o nazwie `customersTableAdapter` i typizowany zestaw danych o nazwie `northwindDataSet`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreDataExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#21)]  
  
## <a name="see-also"></a>Zobacz także  
 [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Zapisywanie danych w bazie danych](../data-tools/save-data-back-to-the-database.md)    
 [Aktualizowanie danych za pomocą adaptera TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)    
 [Instrukcje: Przewijanie rekordów bazy danych w arkuszu](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [Instrukcje: Zapełnianie arkuszy danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Instrukcje: Zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Instrukcje: Zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Instrukcje: Zapełnianie dokumentów danymi z usług](../vsto/how-to-populate-documents-with-data-from-services.md)  
