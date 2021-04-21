---
title: Jak zaktualizować źródło danych przy użyciu danych z kontrolki hosta
description: Dowiedz się, jak powiązać kontrolkę hosta ze źródłem danych i zaktualizować źródło danych za pomocą zmian wprowadzonych w danych w kontrolce.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9aab30b9c2fa363ef68d7d3f70ca05ca6c387a3c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828933"
---
# <a name="how-to-update-a-data-source-with-data-from-a-host-control"></a>Jak zaktualizować źródło danych przy użyciu danych z kontrolki hosta
  Kontrolkę hosta można powiązać ze źródłem danych i zaktualizować źródło danych za pomocą zmian wprowadzonych w danych w kontrolce. Ten proces ma dwa główne kroki:

1. Zaktualizuj źródło danych w pamięci przy użyciu zmodyfikowanych danych w kontrolce. Zwykle źródłem danych w pamięci jest <xref:System.Data.DataSet> obiekt , lub inny obiekt <xref:System.Data.DataTable> danych.

2. Zaktualizuj bazę danych przy użyciu zmienionych danych w źródle danych w pamięci. Ma to zastosowanie tylko wtedy, gdy źródło danych jest połączone z bazą danych back-end, taką jak baza danych SQL Server lub Microsoft Office Access.

   Aby uzyskać więcej informacji na temat kontrolek hosta i powiązań danych, zobacz [Host items and host controls overview (Elementy](../vsto/host-items-and-host-controls-overview.md) hosta i kontrolki hosta — omówienie) i Bind data to controls in Office solutions (Wiązanie danych z kontrolkami w [rozwiązaniach pakietu Office).](../vsto/binding-data-to-controls-in-office-solutions.md)

   [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="update-the-in-memory-data-source"></a>Aktualizowanie źródła danych w pamięci
 Domyślnie kontrolki hosta, które umożliwiają proste powiązanie danych (takie jak kontrolki zawartości w dokumencie programu Word lub nazwana kontrolka zakresu w arkuszu programu Excel), nie zapisują zmian danych w źródle danych w pamięci. Oznacza to, że gdy użytkownik końcowy zmienia wartość w kontrolce hosta, a następnie odchodzi od kontrolki, nowa wartość w kontrolce nie jest automatycznie zapisywana w źródle danych.

 Aby zapisać dane w źródle danych, możesz napisać kod, który aktualizuje źródło danych w odpowiedzi na określone zdarzenie w czasie działania, lub skonfigurować kontrolkę tak, aby automatycznie aktualizowała źródło danych po zmianie wartości w kontrolce.

 Nie trzeba zapisywać <xref:Microsoft.Office.Tools.Excel.ListObject> zmian w źródle danych w pamięci. W przypadku powiązania kontrolki z danymi kontrolka automatycznie zapisuje zmiany w źródle danych w pamięci bez <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:Microsoft.Office.Tools.Excel.ListObject> konieczności użycia dodatkowego kodu.

### <a name="to-update-the-in-memory-data-source-at-run-time"></a>Aby zaktualizować źródło danych w pamięci w czasie uruchamiania

- Wywołaj <xref:System.Windows.Forms.Binding.WriteValue%2A> metodę obiektu , która wiąże <xref:System.Windows.Forms.Binding> kontrolkę ze źródłem danych.

     Poniższy przykład zapisuje zmiany wprowadzone w kontrolce <xref:Microsoft.Office.Tools.Excel.NamedRange> w arkuszu programu Excel w źródle danych. W tym przykładzie przyjęto założenie, że masz <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę o nazwie `namedRange1` z jej <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> właściwością powiązaną z polem w źródle danych.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet1":::

### <a name="automatically-update-the-in-memory-data-source"></a>Automatyczne aktualizowanie źródła danych w pamięci
 Można również skonfigurować kontrolkę tak, aby automatycznie aktualizowana była źródło danych w pamięci. W projekcie na poziomie dokumentu można to zrobić przy użyciu kodu lub projektanta. W projekcie dodatku VSTO należy użyć kodu.

#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-code"></a>Aby ustawić kontrolkę w celu automatycznego aktualizowania źródła danych w pamięci przy użyciu kodu

1. Użyj trybu System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged obiektu, który wiąże kontrolkę <xref:System.Windows.Forms.Binding> ze źródłem danych. Istnieją dwie opcje aktualizowania źródła danych:

   - Aby zaktualizować źródło danych podczas walidacji kontrolki, ustaw tę właściwość na System.Windows.Forms.DataSourceUpdateMode.OnValidation.

   - Aby zaktualizować źródło danych po zmianie wartości właściwości powiązanej z danymi kontrolki, ustaw tę właściwość na System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged.

     > [!NOTE]
     > Opcja System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged nie ma zastosowania do kontrolek hosta programu Word, ponieważ program Word nie oferuje powiadomień o zmianie dokumentu lub zmianie kontrolki. Ta opcja może być jednak używana w przypadku kontrolek Windows Forms dokumentów programu Word.

     Poniższy przykład umożliwia skonfigurowanie kontrolki do automatycznego aktualizowania źródła danych po <xref:Microsoft.Office.Tools.Excel.NamedRange> zmianie wartości w kontrolce. W tym przykładzie przyjęto założenie, że masz <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę o nazwie `namedRange1` z jej <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> właściwością powiązaną z polem w źródle danych.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet19":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet19":::

#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-the-designer"></a>Aby ustawić kontrolkę w celu automatycznego aktualizowania źródła danych w pamięci przy użyciu projektanta

1. W Visual Studio otwórz dokument programu Word lub skoroszyt programu Excel w projektancie.

2. Kliknij kontrolkę, którą chcesz automatycznie zaktualizować źródło danych.

3. W **oknie** Właściwości rozwiń właściwość **(DataBindings).**

4. Obok właściwości **(Zaawansowane)** kliknij przycisk wielokropka ![(VisualStudioEllipsesButton zrzut ekranu).](../vsto/media/vbellipsesbutton.png "Zrzut ekranu visualStudioEllipsesButton")

5. W **oknie dialogowym Formatowanie** i powiązanie zaawansowane kliknij listę **rozwijaną Tryb** aktualizacji źródła danych i wybierz jedną z następujących wartości:

    - Aby zaktualizować źródło danych po weryfikacji kontrolki, wybierz **pozycję OnValidation**.

    - Aby zaktualizować źródło danych po zmianie wartości właściwości powiązanej z danymi kontrolki, wybierz **pozycję OnPropertyChanged**.

        > [!NOTE]
        > Opcja **OnPropertyChanged** nie ma zastosowania do kontrolek hosta programu Word, ponieważ program Word nie oferuje powiadomień o zmianie dokumentu ani zmianie kontrolki. Ta opcja może być jednak używana w przypadku kontrolek Windows Forms dokumentów programu Word.

6. Zamknij okno **dialogowe Formatowanie i Powiązanie** zaawansowane.

## <a name="update-the-database"></a>Aktualizowanie bazy danych
 Jeśli źródło danych w pamięci jest skojarzone z bazą danych, należy zaktualizować bazę danych przy użyciu zmian w źródle danych. Aby uzyskać więcej informacji na temat aktualizowania bazy danych, zobacz [Zapisywanie danych z](../data-tools/save-data-back-to-the-database.md) powrotem w bazie danych i Aktualizowanie danych przy użyciu narzędzia [TableAdapter.](../data-tools/update-data-by-using-a-tableadapter.md)

### <a name="to-update-the-database"></a>Aby zaktualizować bazę danych

1. Wywołaj <xref:System.Windows.Forms.BindingSource.EndEdit%2A> metodę <xref:System.Windows.Forms.BindingSource> dla kontrolki .

     Kontrolka <xref:System.Windows.Forms.BindingSource> jest generowana automatycznie podczas dodawania kontrolki powiązanej z danymi do dokumentu lub skoroszytu w czasie projektowania. Element <xref:System.Windows.Forms.BindingSource> łączy kontrolkę z typem zestawu danych w projekcie. Aby uzyskać więcej informacji, zobacz [BindingSource component overview (Omówienie składnika BindingSource).](/dotnet/framework/winforms/controls/bindingsource-component-overview)

     W poniższym przykładzie kodu przyjęto założenie, że projekt zawiera nazwę <xref:System.Windows.Forms.BindingSource> `customersBindingSource` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet20":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet20":::

2. Wywołaj `Update` metodę wygenerowanego tableadapter w projekcie.

     Kontrolka TableAdapter jest generowana automatycznie po dodaniu kontrolki powiązanej z danymi do dokumentu lub skoroszytu w czasie projektowania. Element TableAdapter łączy typowany zestaw danych w projekcie z bazą danych. Aby uzyskać więcej informacji, zobacz [Omówienie tableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     W poniższym przykładzie kodu przyjęto założenie, że masz połączenie z tabelą Customers w bazie danych Northwind oraz że projekt zawiera element TableAdapter o nazwie i typowany zestaw `customersTableAdapter` danych o nazwie `northwindDataSet` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet21":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet21":::

## <a name="see-also"></a>Zobacz też
- [Wiązanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Zapisywanie danych z powrotem w bazie danych](../data-tools/save-data-back-to-the-database.md)
- [Aktualizowanie danych za pomocą adaptera TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)
- [How to: Scroll through database records in a worksheet (Jak przewijać rekordy bazy danych w arkuszu)](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Jak wypełnić arkusze danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Jak wypełnić dokumenty danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [How to: Populate documents with data from a database (Jak wypełnić dokumenty danymi z bazy danych)](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Jak wypełnić dokumenty danymi z usług](../vsto/how-to-populate-documents-with-data-from-services.md)
