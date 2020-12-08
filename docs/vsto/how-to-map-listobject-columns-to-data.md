---
title: 'Instrukcje: Mapowanie kolumn ListObject na dane'
description: Dowiedz się, jak można mapować kolumny, które mają być wyświetlane na Liścieobject po wywołaniu metody SetDataBinding.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: aa24e4a0f0dab9c01de8e5a2960f28d71a9dad6e
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848238"
---
# <a name="how-to-map-listobject-columns-to-data"></a>Instrukcje: Mapowanie kolumn ListObject na dane
  Po powiązaniu <xref:Microsoft.Office.Tools.Excel.ListObject> formantu z <xref:System.Data.DataTable> , możesz nie chcieć wyświetlać wszystkich kolumn na liście lub mogą istnieć pewne kolumny, które nie są powiązane z danymi. Można mapować kolumny, które mają być wyświetlane w <xref:Microsoft.Office.Tools.Excel.ListObject> czasie wywoływania <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> metody.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="map-columns"></a>Mapuj kolumny

### <a name="to-map-a-data-table-to-columns-in-a-list"></a>Aby zmapować tabelę danych na kolumny na liście

1. Utwórz <xref:System.Data.DataTable> na poziomie klasy.

     [!code-csharp[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#16)]
     [!code-vb[Trin_VstcoreHostControlsExcel#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#16)]

2. Dodaj przykładowe kolumny i dane do `Startup` procedury obsługi zdarzeń `Sheet1` klasy (w projekcie na poziomie dokumentu) lub `ThisAddIn` klasy (w projekcie dodatku VSTO).

     [!code-csharp[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#17)]
     [!code-vb[Trin_VstcoreHostControlsExcel#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#17)]

3. Wywołaj <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> metodę i przekaż nazwy kolumn w kolejności, w jakiej powinny się pojawiać. Obiekt list zostanie powiązany z nowo utworzonym <xref:System.Data.DataTable> , ale kolejność kolumn w obiekcie list będzie różna od kolejności, w której się znajdują <xref:System.Data.DataTable> .

     [!code-csharp[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#18)]
     [!code-vb[Trin_VstcoreHostControlsExcel#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#18)]

## <a name="specify-unmapped-columns"></a>Określ niezamapowane kolumny
 Podczas mapowania kolumn do <xref:System.Data.DataTable> , można również określić, że niektóre kolumny nie powinny być powiązane z danymi przez przekazanie pustego ciągu. Nowa kolumna, która nie jest powiązana z danymi, jest następnie dodawana do <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki.

### <a name="to-specify-an-unmapped-column-when-mapping-listobject-columns"></a>Aby określić niezamapowanej kolumny podczas mapowania kolumn ListObject

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.ListObject.SetDataBinding%2A> metodę i przekaż nazwy kolumn w kolejności, w jakiej powinny się pojawiać. Użyj pustego ciągu, aby wskazać miejsce dodania niezamapowanej kolumny; w tym przypadku między kolumną tytuł i kolumną nazwisko.

     [!code-csharp[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet3.cs#19)]
     [!code-vb[Trin_VstcoreHostControlsExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet3.vb#19)]

## <a name="compile-the-code"></a>Kompiluj kod
 W tym przykładzie kodu założono, że masz istniejącą <xref:Microsoft.Office.Tools.Excel.ListObject> nazwę `list1` w arkuszu, w którym znajduje się ten kod.

## <a name="see-also"></a>Zobacz także
- [Rozwiń dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Instrukcje: wypełnianie kontrolek ListObject danymi](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [ListObject — formant](../vsto/listobject-control.md)
