---
title: 'Instrukcje: Programowe Drukowanie arkuszy'
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
ms.openlocfilehash: e76b53488f1375606980e504bf94dae6343ff267
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863425"
---
# <a name="how-to-programmatically-print-worksheets"></a>Instrukcje: Programowe Drukowanie arkuszy
  Aby wydrukować dowolnego arkusza w skoroszycie.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="print-a-worksheet-in-a-document-level-customization"></a>Drukuj arkusz w dostosowaniu na poziomie dokumentu  
  
### <a name="to-print-a-worksheet"></a>Aby Drukowanie arkuszy  
  
1. Wywołaj <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintOut%2A> metody `Sheet1`, dwie kopie żądania, a następnie przejrzyj dokumentu przed rozpoczęciem drukowania.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#22)]
    [!code-vb[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#22)]  
  
   <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> Metoda pozwala na wyświetlanie określonego obiektu w **Podgląd wydruku** okna. Poniższy kod zakłada się, masz <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta o nazwie `Sheet1`.  
  
### <a name="to-preview-a-page-before-printing"></a>Aby wyświetlić podgląd strony przed rozpoczęciem drukowania  
  
1.  Wywołaj <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> metoda arkusza.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#23)]  
  
## <a name="print-a-worksheet-in-a-vsto-add-in"></a>Drukuj arkusz w dodatku narzędzi VSTO  
  
### <a name="to-print-a-worksheet"></a>Aby Drukowanie arkuszy  
  
1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> metoda aktywnego arkusza żądania dwie kopie, a następnie przejrzyj dokumentu przed rozpoczęciem drukowania.  
  
    [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#14)]
    [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#14)]  
  
   <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> Metoda pozwala na wyświetlanie określonego obiektu w **Podgląd wydruku** okna.  
  
### <a name="to-preview-a-page-before-printing"></a>Aby wyświetlić podgląd strony przed rozpoczęciem drukowania  
  
1.  Wywołaj <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> metoda aktywnego arkusza.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#15)]  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z arkuszami](../vsto/working-with-worksheets.md)   
 [Instrukcje: Programowe sprawdzanie pisowni w arkuszach](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Element hosta arkusza](../vsto/worksheet-host-item.md)   
 [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
