---
title: 'Instrukcje: Programowane stosowanie stylów do zakresów w skoroszytach'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: b8b511d195a40f42bf0b1224dd828b6c6d2b9671
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585356"
---
# <a name="how-to-programmatically-apply-styles-to-ranges-in-workbooks"></a>Instrukcje: Programowane stosowanie stylów do zakresów w skoroszytach
  Można stosować nazwane style do regionów w skoroszytach. Program Excel udostępnia wiele wstępnie zdefiniowanych stylów.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 W oknie dialogowym **Formatowanie komórek** są wyświetlane wszystkie opcje, których można użyć do formatowania komórek, a każda z tych opcji jest dostępna w kodzie. Aby wyświetlić to okno dialogowe w programie Excel, kliknij **komórki** w menu **Format** .

## <a name="to-apply-a-style-to-a-named-range-in-a-document-level-customization"></a>Aby zastosować styl do nazwanego zakresu w dostosowaniu na poziomie dokumentu

1. Utwórz nowy styl i ustaw jego atrybuty.

     [!code-csharp[Trin_VstcoreExcelAutomation#53](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#53)]
     [!code-vb[Trin_VstcoreExcelAutomation#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#53)]

2. Utwórz <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę, przypisz do niej tekst, a następnie Zastosuj nowy styl. Ten kod musi być umieszczony w klasie arkusza, a nie w `ThisWorkbook` klasie.

     [!code-csharp[Trin_VstcoreExcelAutomation#54](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#54)]
     [!code-vb[Trin_VstcoreExcelAutomation#54](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#54)]

## <a name="to-clear-a-style-from-a-named-range-in-a-document-level-customization"></a>Aby wyczyścić styl z nazwanego zakresu w dostosowaniu na poziomie dokumentu

1. Zastosuj styl Normalny do zakresu. Ten kod musi być umieszczony w klasie arkusza, a nie w `ThisWorkbook` klasie.

     [!code-csharp[Trin_VstcoreExcelAutomation#55](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#55)]
     [!code-vb[Trin_VstcoreExcelAutomation#55](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#55)]

## <a name="to-apply-a-style-to-a-named-range-in-a-vsto-add-in"></a>Aby zastosować styl do nazwanego zakresu w dodatku narzędzi VSTO

1. Utwórz nowy styl i ustaw jego atrybuty.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#28](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#28](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#28)]

2. Utwórz <xref:Microsoft.Office.Interop.Excel.Range> , przypisz do niego tekst, a następnie Zastosuj nowy styl.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#29](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#29)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#29](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#29)]

## <a name="to-clear-a-style-from-a-named-range-in-a-vsto-add-in"></a>Aby wyczyścić styl z nazwanego zakresu w dodatku narzędzi VSTO

1. Zastosuj styl Normalny do zakresu.

     [!code-csharp[Trin_VstcoreExcelAutomation#56](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#56)]
     [!code-vb[Trin_VstcoreExcelAutomation#56](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#56)]

## <a name="see-also"></a>Zobacz też
- [Pracuj z zakresami](../vsto/working-with-ranges.md)
- [NamedRange — formant](../vsto/namedrange-control.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
