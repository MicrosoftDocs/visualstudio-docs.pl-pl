---
title: 'Instrukcje: Programowe Dodawanie nowych arkuszy do skoroszytu'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, adding worksheets
- workbooks, creating worksheets
- worksheets, creating
- worksheets, adding to workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4d357fd6028fd080f2c1e37895c8d4256bea56a0
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865245"
---
# <a name="how-to-programmatically-add-new-worksheets-to-workbooks"></a>Instrukcje: Programowe Dodawanie nowych arkuszy do skoroszytu
  Można programowo utworzyć arkusz, a następnie dodaj arkusz do kolekcji arkuszy w skoroszycie.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-document-level-customization"></a>Aby dodać nowy arkusz w skoroszycie w dostosowaniu na poziomie dokumentu  
  
1.  Użyj <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> metody <xref:Microsoft.Office.Interop.Excel.Sheets> kolekcji.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#15)]  
  
     Nowy arkusz jest natywny <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektu i nie element hosta. Jeśli chcesz dodać <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta arkusza należy dodać w czasie projektowania.  
  
## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Aby dodać nowy arkusz w skoroszycie w dodatku narzędzi VSTO  
  
1.  Użyj <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> metody <xref:Microsoft.Office.Interop.Excel.Sheets> kolekcji.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#11)]  
  
     Nowy arkusz jest natywny <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektu i nie element hosta. Możesz również generować <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta z natywnym <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektu. Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z arkuszami](../vsto/working-with-worksheets.md)   
 [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)   
 [Instrukcje: Programowe usuwanie arkuszy ze skoroszytu](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Instrukcje: Programowe Zaznaczanie arkuszy](../vsto/how-to-programmatically-select-worksheets.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
