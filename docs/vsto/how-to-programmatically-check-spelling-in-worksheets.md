---
title: 'Instrukcje: Programowe sprawdzanie pisowni w arkuszach'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- spellchecking
- spelling checker, worksheets
- worksheets, checking spelling
- spelling, checking in worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 93a9377579e9b299fd2a3b0a34e8e90a1f7f2bb6
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633268"
---
# <a name="how-to-programmatically-check-spelling-in-worksheets"></a>Instrukcje: Programowe sprawdzanie pisowni w arkuszach
  Można programowe sprawdzanie pisowni wyrazów w arkuszu. **Pisownia** automatycznie pojawi się okno dialogowe w przypadku niepoprawnie właściwej słów w arkuszu.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-check-spelling-in-a-worksheet-in-a-document-level-customization"></a>Aby sprawdzić pisownię w arkuszu w dostosowaniu na poziomie dokumentu

1.  Wywołaj <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> metoda arkusza.

     [!code-csharp[Trin_VstcoreExcelAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#45)]
     [!code-vb[Trin_VstcoreExcelAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#45)]

## <a name="to-check-spelling-in-a-worksheet-in-a-vsto-add-in"></a>Sprawdzanie pisowni w skoroszycie w dodatku narzędzi VSTO

1.  Wywołaj <xref:Microsoft.Office.Interop.Excel._Worksheet.CheckSpelling%2A> metoda aktywnego arkusza.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#22](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#22)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#22](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#22)]

## <a name="see-also"></a>Zobacz także
- [Praca z arkuszami](../vsto/working-with-worksheets.md)
- [Instrukcje: Programowe wykonywanie obliczeń programu Excel](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [Namedrange — formant](../vsto/namedrange-control.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
