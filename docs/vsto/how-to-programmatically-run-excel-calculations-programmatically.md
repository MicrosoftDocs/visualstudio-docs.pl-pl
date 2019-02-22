---
title: 'Instrukcje: Programowe wykonywanie obliczeń programu Excel'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, running calculations
- calculations, running in Excel
- Excel [Office development in Visual Studio], running calculations programmatically
- workbooks, running calculations
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a81bcfc6c9f5db47c2140e68a7b609efc92bf8fe
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56610518"
---
# <a name="how-to-programmatically-run-excel-calculations"></a>Instrukcje: Programowe wykonywanie obliczeń programu Excel
  Używasz podobnej do wykonywania obliczeń <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu lub natywnego obiektu zakresu programu Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="run-calculations-in-a-namedrange-control"></a>Wykonywanie obliczeń w kontrolki NamedRange
 Poniższy przykład tworzy <xref:Microsoft.Office.Tools.Excel.NamedRange> od komórki A1, a następnie oblicza komórki. Ten kod muszą być umieszczone w klasie arkusza, nie w `ThisWorkbook` klasy.

### <a name="to-run-calculations-in-a-namedrange-control"></a>Aby uruchomić obliczeń w kontrolki NamedRange

1.  Utwórz nazwanym zakresie.

     [!code-csharp[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#75)]
     [!code-vb[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#75)]

2.  Wywołaj <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> metoda określony zakres.

     [!code-csharp[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#76)]
     [!code-vb[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#76)]

## <a name="run-calculations-in-a-native-excel-range"></a>Wykonywanie obliczeń w macierzystym zakresu programu Excel

### <a name="to-run-calculations-in-a-native-excel-range"></a>Aby uruchomić obliczeń w macierzystym zakresu programu Excel

1.  Utwórz nazwanym zakresie.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#30)]

2.  Wywołaj <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> metoda określony zakres.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#31)]

## <a name="see-also"></a>Zobacz także
- [Praca z zakresami](../vsto/working-with-ranges.md)
- [Namedrange — formant](../vsto/namedrange-control.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
