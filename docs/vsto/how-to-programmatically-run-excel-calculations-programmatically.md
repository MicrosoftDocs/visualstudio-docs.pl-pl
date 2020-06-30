---
title: 'Instrukcje: Programowane uruchamianie obliczeń programu Excel'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: a02e86864065d2c626de2f6e7fea7528554f1391
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547384"
---
# <a name="how-to-programmatically-run-excel-calculations"></a>Instrukcje: Programowane uruchamianie obliczeń programu Excel
  Podobny proces służy do uruchamiania obliczeń w <xref:Microsoft.Office.Tools.Excel.NamedRange> formancie lub natywnym obiekcie zakresu programu Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="run-calculations-in-a-namedrange-control"></a>Uruchamianie obliczeń w kontrolce NamedRange
 Poniższy przykład tworzy <xref:Microsoft.Office.Tools.Excel.NamedRange> w komórce A1, a następnie oblicza komórkę. Ten kod musi być umieszczony w klasie arkusza, a nie w `ThisWorkbook` klasie.

### <a name="to-run-calculations-in-a-namedrange-control"></a>Aby uruchomić obliczenia w kontrolce NamedRange

1. Utwórz nazwany zakres.

     [!code-csharp[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#75)]
     [!code-vb[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#75)]

2. Wywołaj <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> metodę o określonym zakresie.

     [!code-csharp[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#76)]
     [!code-vb[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#76)]

## <a name="run-calculations-in-a-native-excel-range"></a>Uruchamianie obliczeń w natywnym zakresie programu Excel

### <a name="to-run-calculations-in-a-native-excel-range"></a>Aby uruchomić obliczenia w natywnym zakresie programu Excel

1. Utwórz nazwany zakres.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#30)]

2. Wywołaj <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> metodę o określonym zakresie.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#31)]

## <a name="see-also"></a>Zobacz też
- [Pracuj z zakresami](../vsto/working-with-ranges.md)
- [NamedRange — formant](../vsto/namedrange-control.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
