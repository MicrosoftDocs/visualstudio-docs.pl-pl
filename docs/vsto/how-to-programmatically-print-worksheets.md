---
title: 'Instrukcje: Programowe drukowanie arkuszy'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- worksheets, printing
- print preview, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 764723d0749cd82739d8e67ee71104f41a0f9065
ms.sourcegitcommit: 5b34052a1c7d86179d7898ed532babb2d9dad4a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69490583"
---
# <a name="how-to-programmatically-print-worksheets"></a>Instrukcje: Programowe drukowanie arkuszy

Można wydrukować każdy arkusz w skoroszycie.

[!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="print-a-worksheet-in-a-document-level-customization"></a>Drukowanie arkusza w dostosowaniu na poziomie dokumentu

### <a name="to-print-a-worksheet"></a>Aby wydrukować arkusz

1. Wywołaj `PrintOut` `Sheet1`metodę, zażądaj dwóch kopii i Wyświetl podgląd dokumentu przed rozpoczęciem drukowania.

    [!code-csharp[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#22)]
    [!code-vb[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#22)]

   Metoda umożliwia wyświetlenie określonego obiektu w oknie **podglądu wydruku.** <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> Poniższy kod założono, że masz <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta o `Sheet1`nazwie.

### <a name="to-preview-a-page-before-printing"></a>Aby wyświetlić podgląd strony przed rozpoczęciem drukowania

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> metodę arkusza.

     [!code-csharp[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#23)]

## <a name="print-a-worksheet-in-a-vsto-add-in"></a>Drukowanie arkusza w dodatku narzędzi VSTO

### <a name="to-print-a-worksheet"></a>Aby wydrukować arkusz

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> metodę aktywnego arkusza, zażądaj dwóch kopii i Wyświetl podgląd dokumentu przed rozpoczęciem drukowania.

    [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#14)]
    [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#14)]

   Metoda umożliwia wyświetlenie określonego obiektu w oknie **podglądu wydruku.** <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A>

### <a name="to-preview-a-page-before-printing"></a>Aby wyświetlić podgląd strony przed rozpoczęciem drukowania

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> metodę aktywnego arkusza.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#15)]

## <a name="see-also"></a>Zobacz także

- [Pracuj z arkuszami](../vsto/working-with-worksheets.md)
- [Instrukcje: Programowe sprawdzanie pisowni w arkuszach](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Element hosta arkusza](../vsto/worksheet-host-item.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
