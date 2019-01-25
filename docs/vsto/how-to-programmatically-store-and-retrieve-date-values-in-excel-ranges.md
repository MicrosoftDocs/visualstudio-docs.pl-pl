---
title: 'Instrukcje: Programowe przechowywanie i pobieranie wartości daty w zakresach programu Excel'
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 24155f9ea8703d7089714a9b0adce9310612a4ea
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54872719"
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>Instrukcje: Programowe przechowywanie i pobieranie wartości daty w zakresach programu Excel
  Można przechowywać i pobierać wartości w <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu lub natywnego obiektu zakresu programu Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 W przypadku przechowywania wartości daty, która znajduje się na lub po 1/1/1900 w zakresie za pomocą narzędzi programistycznych pakietu Office w programie Visual Studio znajduje się w formacie OLE automatyzacji OA. Należy użyć <xref:System.DateTime.FromOADate%2A> metodę, aby pobrać wartość daty OLE automatyzacji OA. Jeśli data jest wcześniejsza niż 1/1/1900, są przechowywane w postaci ciągu.  
  
> [!NOTE]  
>  Daty Excel różnią się od daty automatyzacji OLE na pierwszych dwóch miesięcy 1900. Różnią się także jeśli **system daty 1904** opcja jest zaznaczona. Poniższe przykłady kodu nie dotyczą te różnice.  
  
## <a name="use-a-namedrange-control"></a>Używanie formantu NamedRange  
  
-   Ten przykład dotyczy dostosowywania na poziomie dokumentu. Poniższy kod muszą być umieszczone w klasie arkusza, nie w `ThisWorkbook` klasy.  
  
### <a name="to-store-a-date-value-in-a-named-range"></a>Przechowywanie wartości daty w nazwany zakres  
  
1.  Tworzenie <xref:Microsoft.Office.Tools.Excel.NamedRange> formant w komórce **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#50)]  
  
2.  Ustaw bieżącą datę jako wartość `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#51)]  
  
### <a name="to-retrieve-a-date-value-from-a-named-range"></a>Aby pobrać wartość typu date z nazwanego zakresu  
  
1.  Pobierz wartość daty na podstawie `NamedRange1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#52)]  
  
## <a name="use-native-excel-ranges"></a>Użyj natywnego zakresów programu Excel  
  
### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>Przechowywanie wartości daty w macierzystym obiektu zakresu programu Excel  
  
1.  Tworzenie <xref:Microsoft.Office.Interop.Excel.Range> reprezentujący komórkę **A1**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#25)]  
  
2.  Ustaw bieżącą datę jako wartość `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#26)]  
  
### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>Aby pobrać wartość typu date z natywnego obiektu zakresu programu Excel  
  
1.  Pobierz wartość daty na podstawie `rng`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#27)]  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z zakresami](../vsto/working-with-ranges.md)   
 [Model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md)   
 [Namedrange — formant](../vsto/namedrange-control.md)   
 [Instrukcje: Programowe odwoływanie do zakresów arkusza w kodzie](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Instrukcje: Dodawanie formantów NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
