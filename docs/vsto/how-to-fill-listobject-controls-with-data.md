---
title: 'Instrukcje: Wypełnianie formantów ListObject danymi'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disconnecting from data sources
- ListObject control, disconnecting from a data source
- ListObject control, filling with data
- data [Office development in Visual Studio], adding to worksheets
- data binding, ListObject controls
- worksheets, populating with data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f65f6de7cfb336eb001de47fb6562b7200391419
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050104"
---
# <a name="how-to-fill-listobject-controls-with-data"></a>Instrukcje: Wypełnianie formantów ListObject danymi
  Powiązanie danych można użyć jako sposób, aby szybko dodać dane do dokumentu. Po powiązaniu danych na obiekt listy, możesz odłączyć na obiekt listy, wyświetla dane, ale nie jest już powiązany ze źródłem danych.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 ![Link do wideo](../vsto/media/playvideo.gif "link do wideo") powiązane demonstracyjne wideo – zobacz [jak: Utwórz listę w programie Excel, która jest połączona z listą programu SharePoint? ](http://go.microsoft.com/fwlink/?LinkID=130263).

### <a name="to-bind-data-to-a-listobject-control"></a>Aby powiązać dane do formantu ListObject

1. Utwórz <xref:System.Data.DataTable> na poziomie klasy.

     [!code-csharp[Trin_VstcoreHostControlsExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#20)]
     [!code-vb[Trin_VstcoreHostControlsExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#20)]

2. Dodawanie przykładowe kolumny i dane w `Startup` program obsługi zdarzeń `Sheet1` klasy (w projekcie poziomie dokumentu) lub `ThisAddIn` klasy (w projekcie dodatku poziomu aplikacji).

     [!code-csharp[Trin_VstcoreHostControlsExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#21)]
     [!code-vb[Trin_VstcoreHostControlsExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#21)]

3. Wywołaj <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> metody i przekazać w nazwach kolumn w kolejności, powinny one zostać wyświetlone. Kolejność kolumn w obiekcie listy mogą różnić się od kolejności, w jakiej występują w <xref:System.Data.DataTable>.

     [!code-csharp[Trin_VstcoreHostControlsExcel#22](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#22)]
     [!code-vb[Trin_VstcoreHostControlsExcel#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#22)]

### <a name="to-disconnect-the-listobject-control-from-the-data-source"></a>Aby odłączyć kontrolki ListObject ze źródła danych

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.ListObject.Disconnect%2A> metody `List1`.

     [!code-csharp[Trin_VstcoreHostControlsExcel#23](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet4.cs#23)]
     [!code-vb[Trin_VstcoreHostControlsExcel#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet4.vb#23)]

## <a name="compile-the-code"></a>Skompilować kod
 Ten przykład kodu zakłada, masz istniejącą <xref:Microsoft.Office.Tools.Excel.ListObject> o nazwie `list1` w arkuszu, w której występuje ten kod.

## <a name="see-also"></a>Zobacz także
- [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Instrukcje: Mapowanie kolumn ListObject do danych](../vsto/how-to-map-listobject-columns-to-data.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject — formant](../vsto/listobject-control.md)
- [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Instrukcje: Zapełnianie arkuszy danymi z bazy danych](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Instrukcje: Zapełnianie dokumentów danymi z usług](../vsto/how-to-populate-documents-with-data-from-services.md)
