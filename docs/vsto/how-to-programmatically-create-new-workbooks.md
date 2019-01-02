---
title: 'Instrukcje: Programowe tworzenie nowych skoroszytów'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], creating workbooks
- workbooks, creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5e68b2c955c2e44fb9f721850be2fa4dac9cf875
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958280"
---
# <a name="how-to-programmatically-create-new-workbooks"></a>Instrukcje: Programowe tworzenie nowych skoroszytów
  Programowo utworzyć skoroszyt jest natywny <xref:Microsoft.Office.Interop.Excel.Workbook> obiektu nie <xref:Microsoft.Office.Tools.Excel.Workbook> element hosta.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Możesz wygenerować <xref:Microsoft.Office.Tools.Excel.Workbook> element hosta dla elementu <xref:Microsoft.Office.Interop.Excel.Workbook> obiektu w projekcie dodatku narzędzi VSTO. Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="to-create-a-new-workbook"></a>Aby utworzyć nowy skoroszyt  
  
1.  Użyj <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> metody <xref:Microsoft.Office.Interop.Excel.Workbooks> kolekcji.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#1)]  
  
    > [!NOTE]  
    >  Można utworzyć na podstawie szablonu innym niż domyślny szablon skoroszytu: szablonu, którego chcesz użyć jako parametru, aby przekazać <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> metody.  
  
## <a name="see-also"></a>Zobacz także  
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Praca ze skoroszytami](../vsto/working-with-workbooks.md)   
 [Instrukcje: Programowe otwieranie skoroszytów](../vsto/how-to-programmatically-open-workbooks.md)   
 [Instrukcje: Programowe zapisywanie skoroszytów](../vsto/how-to-programmatically-save-workbooks.md)   
 [Instrukcje: Programowe zamykanie skoroszytów](../vsto/how-to-programmatically-close-workbooks.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)  
