---
title: 'Instrukcje: Mapowanie kolumn ListObject do danych'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], mapping to ListObject column
- ListObject control, mapping data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a37c0f12943d60f67ee0d17b15315ac85af509d5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60092698"
---
# <a name="how-to-map-listobject-columns-to-data"></a>Instrukcje: Mapowanie kolumn ListObject do danych
  Po powiązaniu <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolę <xref:System.Data.DataTable>, możesz nie chcieć wyświetlić wszystkie kolumny na liście lub może być określone kolumny, które nie są powiązane z danymi. Można mapować kolumny, które mają być wyświetlane w <xref:Microsoft.Office.Tools.Excel.ListObject> podczas wywoływania <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> metody.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 ![Link do wideo](../vsto/media/playvideo.gif "link do wideo") powiązane demonstracyjne wideo – zobacz [jak: Utwórz listę w programie Excel, która jest połączona z listą programu SharePoint? ](http://go.microsoft.com/fwlink/?LinkID=130263).

## <a name="map-columns"></a>Mapowanie kolumn

### <a name="to-map-a-data-table-to-columns-in-a-list"></a>Do mapowania kolumn na liście tabeli danych

1. Utwórz <xref:System.Data.DataTable> na poziomie klasy.

     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#16)]

2. Dodawanie przykładowe kolumny i dane w `Startup` program obsługi zdarzeń `Sheet1` klasy (w projekcie poziomie dokumentu) lub `ThisAddIn` klasy (w projekcie dodatku narzędzi VSTO).

     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#17)]

3. Wywołaj <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> metody i przekazać w nazwach kolumn w kolejności, powinny one zostać wyświetlone. Obiekt listy, który zostanie powiązany do nowo utworzonego <xref:System.Data.DataTable>, ale kolejność kolumn w obiekcie listy różnią się od kolejności, pojawiają się na <xref:System.Data.DataTable>.

     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#18)]

## <a name="specify-unmapped-columns"></a>Określ kolumny niezamapowane
 Podczas mapowania kolumn <xref:System.Data.DataTable>, można również określić, że niektóre kolumny ma nie zostać powiązana z danych, przekazując ciąg pusty. Nową kolumnę, która nie jest powiązany z danymi jest dodawane do <xref:Microsoft.Office.Tools.Excel.ListObject> kontroli.

### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>Aby określić niezamapowaną kolumnę, gdy mapowanie kolumn ListObject

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> metody i przekazać w nazwach kolumn w kolejności, powinny one zostać wyświetlone. Użyj pustego ciągu, aby wskazać, gdzie jest dodać niezamapowaną kolumnę; w tym przypadku między kolumny title i ostatniej kolumnie Nazwa.

     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#19)]

## <a name="compile-the-code"></a>Skompilować kod
 Ten przykład kodu zakłada, masz istniejącą <xref:Microsoft.Office.Tools.Excel.ListObject> o nazwie `list1` w arkuszu, w której występuje ten kod.

## <a name="see-also"></a>Zobacz także
- [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Instrukcje: Wypełnianie formantów ListObject danymi](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject — formant](../vsto/listobject-control.md)
