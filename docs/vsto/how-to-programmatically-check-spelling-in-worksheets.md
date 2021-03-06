---
title: Jak programowo sprawdzać pisownię w arkuszach
description: Dowiedz się, jak programowo sprawdzać pisownię wyrazów w arkuszu programu Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1bf35e225def686ae2424a89b7e5d6b77207ccee
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826060"
---
# <a name="how-to-programmatically-check-spelling-in-worksheets"></a>Jak programowo sprawdzać pisownię w arkuszach
  Można programowo sprawdzać pisownię wyrazów w arkuszu. Jeśli **w arkuszu** znajdują się niepoprawnie napisane wyrazy, zostanie automatycznie wyświetlone okno dialogowe Pisownia.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-check-spelling-in-a-worksheet-in-a-document-level-customization"></a>Aby sprawdzić pisownię w arkuszu w dostosowywaniu na poziomie dokumentu

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> metodę arkusza.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet45":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet45":::

## <a name="to-check-spelling-in-a-worksheet-in-a-vsto-add-in"></a>Aby sprawdzić pisownię w arkuszu w dodatku VSTO

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Worksheet.CheckSpelling%2A> metodę aktywnego arkusza.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet22":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet22":::

## <a name="see-also"></a>Zobacz też
- [Praca z arkuszami](../vsto/working-with-worksheets.md)
- [Jak programowo uruchamiać obliczenia programu Excel](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [NamedRange, kontrolka](../vsto/namedrange-control.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
