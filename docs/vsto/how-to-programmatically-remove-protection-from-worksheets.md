---
title: 'Instrukcje: Programowe usuwanie ochrony z arkuszy'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, unprotecting
- documents [Office development in Visual Studio], document protection
- document protection, removing from worksheets
- Unprotect method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b94375b54e7e0c0c774adc7b8054fc4219456a40
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870090"
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>Instrukcje: Programowe usuwanie ochrony z arkuszy
  Możesz programowo usunąć ochronę z arkusza kalkulacyjnego programu Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 W poniższym przykładzie użyto zmiennej `getPasswordFromUser`, zawierającą hasła, uzyskanych od użytkownika.  
  
## <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>Można wyłączyć ochrony arkusza w dostosowaniu na poziomie dokumentu  
  
1.  Wywołaj <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> metody skoroszyt i przekaż hasła, jeśli to konieczne. W tym przykładzie założono, że pracujesz z arkusza o nazwie `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#28)]  
  
## <a name="to-unprotect-a-worksheet-in-a-vsto-add-in"></a>Można wyłączyć ochrony arkusza w dodatku narzędzi VSTO  
  
1.  Wywołaj <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> metoda aktywnego arkusza i przekaż hasła, jeśli to konieczne.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#18)]  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z arkuszami](../vsto/working-with-worksheets.md)   
 [Instrukcje: Programowe Włączanie ochrony arkuszy](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Instrukcje: Programowe Włączanie ochrony skoroszytów](../vsto/how-to-programmatically-protect-workbooks.md)   
 [Instrukcje: Programowe ukrywanie arkuszy](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)  
