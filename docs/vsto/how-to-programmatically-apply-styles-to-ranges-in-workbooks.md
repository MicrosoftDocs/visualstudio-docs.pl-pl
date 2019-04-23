---
title: 'Instrukcje: Programowe stosowanie stylów do zakresów arkusza w skoroszycie'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, styles
- styles, workbook ranges
- workbooks, styles
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f74b2d08a268bc79bcd7d2fd33513b5ccf5b1415
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60115786"
---
# <a name="how-to-programmatically-apply-styles-to-ranges-in-workbooks"></a>Instrukcje: Programowe stosowanie stylów do zakresów arkusza w skoroszycie
  Style nazwanych można zastosować do regionów w skoroszycie. Program Excel zawiera szereg wstępnie zdefiniowane style.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 **Formatuj komórki** okno dialogowe wyświetla wszystkie opcje, można użyć do sformatowania komórki, a każdy z tych opcji jest dostępny w kodzie. Aby wyświetlić to okno dialogowe, w programie Excel, kliknij przycisk **komórek** na **Format** menu.

## <a name="to-apply-a-style-to-a-named-range-in-a-document-level-customization"></a>Aby zastosować styl do nazwanego zakresu w dostosowaniu na poziomie dokumentu

1. Utwórz nowy styl i ustaw jego atrybuty.

     [!code-csharp[Trin_VstcoreExcelAutomation#53](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#53)]
     [!code-vb[Trin_VstcoreExcelAutomation#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#53)]

2. Utwórz <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolować, przypisać tekstu do niej, a następnie Zastosuj nowym stylem. Ten kod muszą być umieszczone w klasie arkusza, nie w `ThisWorkbook` klasy.

     [!code-csharp[Trin_VstcoreExcelAutomation#54](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#54)]
     [!code-vb[Trin_VstcoreExcelAutomation#54](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#54)]

## <a name="to-clear-a-style-from-a-named-range-in-a-document-level-customization"></a>Aby wyczyścić styl z nazwanego zakresu w dostosowaniu na poziomie dokumentu

1. Styl normalny należała do zakresu. Ten kod muszą być umieszczone w klasie arkusza, nie w `ThisWorkbook` klasy.

     [!code-csharp[Trin_VstcoreExcelAutomation#55](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#55)]
     [!code-vb[Trin_VstcoreExcelAutomation#55](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#55)]

## <a name="to-apply-a-style-to-a-named-range-in-a-vsto-add-in"></a>Aby zastosować styl do nazwanego zakresu w dodatku narzędzi VSTO

1. Utwórz nowy styl i ustaw jego atrybuty.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#28](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#28](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#28)]

2. Utwórz <xref:Microsoft.Office.Interop.Excel.Range>, przypisać tekstu do niej, a następnie Zastosuj nowe stylu.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#29](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#29](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#29)]

## <a name="to-clear-a-style-from-a-named-range-in-a-vsto-add-in"></a>Aby wyczyścić styl z nazwanego zakresu w dodatku narzędzi VSTO

1. Styl normalny należała do zakresu.

     [!code-csharp[Trin_VstcoreExcelAutomation#56](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#56)]
     [!code-vb[Trin_VstcoreExcelAutomation#56](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#56)]

## <a name="see-also"></a>Zobacz także
- [Praca z zakresami](../vsto/working-with-ranges.md)
- [Namedrange — formant](../vsto/namedrange-control.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
