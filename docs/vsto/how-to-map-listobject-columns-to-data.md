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
ms.openlocfilehash: cffd9f009d193f5ed687560b4f13940273fd82ad
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985899"
---
# <a name="how-to-map-listobject-columns-to-data"></a>Instrukcje: Mapowanie kolumn ListObject na dane
  Po powiązaniu formantu <xref:Microsoft.Office.Tools.Excel.ListObject> z <xref:System.Data.DataTable>, możesz nie chcieć wyświetlać wszystkich kolumn na liście lub mogą istnieć pewne kolumny, które nie są powiązane z danymi. Można mapować kolumny, które mają być wyświetlane w <xref:Microsoft.Office.Tools.Excel.ListObject> po wywołaniu metody <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A>.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="map-columns"></a>Mapuj kolumny

### <a name="to-map-a-data-table-to-columns-in-a-list"></a>Aby zmapować tabelę danych na kolumny na liście

1. Utwórz <xref:System.Data.DataTable> na poziomie klasy.

     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#16)]

2. Dodaj przykładowe kolumny i dane w obsłudze zdarzeń `Startup` klasy `Sheet1` (w projekcie na poziomie dokumentu) lub klasy `ThisAddIn` (w projekcie dodatku VSTO).

     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#17)]

3. Wywołaj metodę <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> i przekaż nazwy kolumn w kolejności, w jakiej powinny się pojawiać. Obiekt list zostanie powiązany z nowo utworzonym <xref:System.Data.DataTable>, ale kolejność kolumn w obiekcie list będzie różna od kolejności, w której pojawiają się w <xref:System.Data.DataTable>.

     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#18)]

## <a name="specify-unmapped-columns"></a>Określ niezamapowane kolumny
 Podczas mapowania kolumn do <xref:System.Data.DataTable>można także określić, że niektóre kolumny nie powinny być powiązane z danymi przez przekazanie pustego ciągu. Nowa kolumna, która nie jest powiązana z danymi, jest następnie dodawana do kontrolki <xref:Microsoft.Office.Tools.Excel.ListObject>.

### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>Aby określić niezamapowanej kolumny podczas mapowania kolumn ListObject

1. Wywołaj metodę <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> i przekaż nazwy kolumn w kolejności, w jakiej powinny się pojawiać. Użyj pustego ciągu, aby wskazać miejsce dodania niezamapowanej kolumny; w tym przypadku między kolumną tytuł i kolumną nazwisko.

     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#19)]

## <a name="compile-the-code"></a>Kompiluj kod
 W tym przykładzie kodu założono, że masz istniejące <xref:Microsoft.Office.Tools.Excel.ListObject> o nazwie `list1` w arkuszu, w którym ten kod pojawia się.

## <a name="see-also"></a>Zobacz także
- [Rozwiń dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Instrukcje: wypełnianie kontrolek ListObject danymi](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject — formant](../vsto/listobject-control.md)
