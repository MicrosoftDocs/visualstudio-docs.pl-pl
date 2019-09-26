---
title: 'Instrukcje: Mapowanie kolumn ListObject na dane'
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
ms.openlocfilehash: 6e0056687e8ca28af4dbc9032d7bbee0cf976378
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253682"
---
# <a name="how-to-map-listobject-columns-to-data"></a>Instrukcje: Mapowanie kolumn ListObject na dane
  Po powiązaniu <xref:Microsoft.Office.Tools.Excel.ListObject> formantu <xref:System.Data.DataTable>z, możesz nie chcieć wyświetlać wszystkich kolumn na liście lub mogą istnieć pewne kolumny, które nie są powiązane z danymi. Można mapować kolumny, które mają być wyświetlane w <xref:Microsoft.Office.Tools.Excel.ListObject> czasie <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> wywoływania metody.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 ![link do wideo](../vsto/media/playvideo.gif "link do wideo") Aby zapoznać się z pokrewną [prezentacją wideo, zobacz Jak mogę: Utworzyć listę w programie Excel, która jest połączona z listą programu SharePoint? ](http://go.microsoft.com/fwlink/?LinkID=130263).

## <a name="map-columns"></a>Mapuj kolumny

### <a name="to-map-a-data-table-to-columns-in-a-list"></a>Aby zmapować tabelę danych na kolumny na liście

1. <xref:System.Data.DataTable> Utwórz na poziomie klasy.

     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#16)]

2. Dodaj przykładowe kolumny i dane do `Startup` procedury obsługi `Sheet1` zdarzeń klasy (w projekcie na poziomie dokumentu) lub `ThisAddIn` klasy (w projekcie dodatku VSTO).

     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#17)]

3. Wywołaj <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> metodę i przekaż nazwy kolumn w kolejności, w jakiej powinny się pojawiać. Obiekt list zostanie powiązany z nowo utworzonym <xref:System.Data.DataTable>, ale kolejność kolumn w obiekcie list będzie różna od kolejności, w której <xref:System.Data.DataTable>się znajdują.

     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#18)]

## <a name="specify-unmapped-columns"></a>Określ niezamapowane kolumny
 Podczas mapowania kolumn do <xref:System.Data.DataTable>, można również określić, że niektóre kolumny nie powinny być powiązane z danymi przez przekazanie pustego ciągu. Nowa kolumna, która nie jest powiązana z danymi, jest następnie dodawana do <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki.

### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>Aby określić niezamapowanej kolumny podczas mapowania kolumn ListObject

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> metodę i przekaż nazwy kolumn w kolejności, w jakiej powinny się pojawiać. Użyj pustego ciągu, aby wskazać miejsce dodania niezamapowanej kolumny; w tym przypadku między kolumną tytuł i kolumną nazwisko.

     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#19)]

## <a name="compile-the-code"></a>Skompilować kod
 W tym przykładzie kodu założono, że <xref:Microsoft.Office.Tools.Excel.ListObject> masz `list1` istniejącą nazwę w arkuszu, w którym znajduje się ten kod.

## <a name="see-also"></a>Zobacz także
- [Rozwiń dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Instrukcje: Wypełnij kontrolki ListObject danymi](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject — formant](../vsto/listobject-control.md)
