---
title: 'Instrukcje: Programowe wyświetlanie listy wszystkich arkuszy w skoroszycie'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing worksheets
- worksheets, listing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fafcded82320bc97a1650f16537cea2a8f7bae5f
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874929"
---
# <a name="how-to-programmatically-list-all-worksheets-in-a-workbook"></a>Instrukcje: Programowe wyświetlanie listy wszystkich arkuszy w skoroszycie
  <xref:Microsoft.Office.Interop.Excel.Workbook> Klasa udostępnia <xref:Microsoft.Office.Interop.Excel.Worksheets> obiektu. Ten obiekt zawiera zbiór wszystkich <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektów w skoroszycie.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-document-level-customization"></a>Aby wyświetlić listę wszystkich istniejących arkuszy w skoroszycie w dostosowaniu na poziomie dokumentu  
  
1.  Iteracyjne przeglądanie <xref:Microsoft.Office.Interop.Excel.Worksheets> kolekcji i Wyślij nazwę każdego arkusza do komórki odsuniętej od <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#21)]  
  
## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-vsto-add-in"></a>Aby wyświetlić listę wszystkich istniejących arkuszy w skoroszycie w dodatku narzędzi VSTO  
  
1.  Iteracyjne przeglądanie <xref:Microsoft.Office.Interop.Excel.Worksheets> kolekcji i Wyślij nazwę każdego arkusza do komórki odsuniętej od <xref:Microsoft.Office.Interop.Excel.Range> obiektu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z arkuszami](../vsto/working-with-worksheets.md)   
 [Instrukcje: Programowe Dodawanie nowych arkuszy do skoroszytu](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Instrukcje: Programowe przenoszenie arkuszy w obrębie skoroszytu](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)  
