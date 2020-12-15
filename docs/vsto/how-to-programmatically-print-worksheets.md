---
title: 'Instrukcje: Programowane drukowanie arkuszy'
description: Dowiedz się, jak za pomocą programu Visual Studio programowo wydrukować każdy arkusz w skoroszycie programu Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 356c47ec3275c1442082f367dd08fe6901f9c0a3
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523760"
---
# <a name="how-to-programmatically-print-worksheets"></a>Instrukcje: Programowane drukowanie arkuszy

Można wydrukować każdy arkusz w skoroszycie.

[!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="print-a-worksheet-in-a-document-level-customization"></a>Drukowanie arkusza w dostosowaniu na poziomie dokumentu

### <a name="to-print-a-worksheet"></a>Aby wydrukować arkusz

1. Wywołaj `PrintOut` metodę `Sheet1` , zażądaj dwóch kopii i Wyświetl podgląd dokumentu przed rozpoczęciem drukowania.

    [!code-csharp[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#22)]
    [!code-vb[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#22)]

   <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A>Metoda umożliwia wyświetlenie określonego obiektu w oknie **podglądu wydruku** . Poniższy kod założono, że masz <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta o nazwie `Sheet1` .

### <a name="to-preview-a-page-before-printing"></a>Aby wyświetlić podgląd strony przed rozpoczęciem drukowania

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> metodę arkusza.

     [!code-csharp[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#23)]

## <a name="print-a-worksheet-in-a-vsto-add-in"></a>Drukowanie arkusza w dodatku narzędzi VSTO

### <a name="to-print-a-worksheet"></a>Aby wydrukować arkusz

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> metodę aktywnego arkusza, zażądaj dwóch kopii i Wyświetl podgląd dokumentu przed rozpoczęciem drukowania.

    [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#14)]
    [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#14)]

   <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A>Metoda umożliwia wyświetlenie określonego obiektu w oknie **podglądu wydruku** .

### <a name="to-preview-a-page-before-printing"></a>Aby wyświetlić podgląd strony przed rozpoczęciem drukowania

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> metodę aktywnego arkusza.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#15)]

## <a name="see-also"></a>Zobacz też

- [Pracuj z arkuszami](../vsto/working-with-worksheets.md)
- [Instrukcje: Programowane sprawdzanie pisowni w arkuszach](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Element hosta arkusza](../vsto/worksheet-host-item.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
