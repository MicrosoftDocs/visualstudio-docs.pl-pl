---
title: Programowe przechowywanie & pobierania wartości daty w zakresach programu Excel
description: Dowiedz się, jak można użyć programu Visual Studio do programistycznego przechowywania i pobierania wartości daty w zakresach programu Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], retrieving date values from ranges
- ranges, retrieving data values
- dates, retrieving from Excel ranges
- Excel [Office development in Visual Studio], storing date values in ranges
- date values, storing in Excel ranges
- dates, storing in Excel ranges
- ranges, storing date values
- date values
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 892f8db0a6cbeee485c8139c2d6e4614f17c1cc2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899409"
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>Instrukcje: Programowane przechowywanie i pobieranie wartości daty w zakresach programu Excel
  Można przechowywać i pobierać wartości w <xref:Microsoft.Office.Tools.Excel.NamedRange> formancie lub natywnym obiekcie zakresu programu Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Jeśli przechowujesz wartość daty, która przypada na lub po 1/1/1900 w zakresie przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio, jest ona przechowywana w formacie OLE Automation (OA). <xref:System.DateTime.FromOADate%2A>Aby pobrać wartość dat automatyzacji OLE (OA), należy użyć metody. Jeśli data jest wcześniejsza niż 1/1/1900, jest przechowywana jako ciąg.

> [!NOTE]
> Daty programu Excel różnią się od dat automatyzacji OLE przez pierwsze dwa miesiące z 1900. Istnieją także różnice w przypadku zaznaczenia opcji **systemowej daty 1904** . Poniższe przykłady kodu nie dotyczą tych różnic.

## <a name="use-a-namedrange-control"></a>Korzystanie z kontrolki NamedRange

- Ten przykład dotyczy dostosowywania na poziomie dokumentu. Poniższy kod musi być umieszczony w klasie arkusza, a nie w `ThisWorkbook` klasie.

### <a name="to-store-a-date-value-in-a-named-range"></a>Aby zapisać wartość daty w nazwanym zakresie

1. Utwórz <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę w komórce **a1**.

     [!code-csharp[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#50)]

2. Ustaw datę dzisiejszą jako wartość parametru `NamedRange1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#51)]

### <a name="to-retrieve-a-date-value-from-a-named-range"></a>Aby pobrać wartość daty z nazwanego zakresu

1. Pobierz wartość daty z `NamedRange1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#52)]

## <a name="use-native-excel-ranges"></a>Użyj natywnych zakresów programu Excel

### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>Aby zapisać wartość daty w natywnym obiekcie zakresu programu Excel

1. Utwórz element <xref:Microsoft.Office.Interop.Excel.Range> reprezentujący komórkę **a1**.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#25)]

2. Ustaw datę dzisiejszą jako wartość parametru `rng` .

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#26)]

### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>Aby pobrać wartość daty z natywnego obiektu zakresu programu Excel

1. Pobierz wartość daty z `rng` .

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#27)]

## <a name="see-also"></a>Zobacz też
- [Pracuj z zakresami](../vsto/working-with-ranges.md)
- [Model obiektów programu Excel — Omówienie](../vsto/excel-object-model-overview.md)
- [NamedRange — formant](../vsto/namedrange-control.md)
- [Instrukcje: programowe odwoływanie się do zakresów arkusza w kodzie](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Instrukcje: Dodawanie kontrolek NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
