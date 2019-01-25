---
title: 'Instrukcje: Programowe kopiowanie arkuszy'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying
- Excel [Office development in Visual Studio], copying worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 64121ffcb69eb4bc3cdaa901ffe3d52014630779
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865388"
---
# <a name="how-to-programmatically-copy-worksheets"></a>Instrukcje: Programowe kopiowanie arkuszy
  Możesz utworzyć kopię arkusza i Wstaw ten arkusz, przed lub po istniejącego arkusza w skoroszycie. Jeśli nie określisz miejsca do wstawienia w arkuszu Excel utworzy nowy skoroszyt w celu uwzględnienia nowego arkusza.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
> [!NOTE]  
>  Czy programowe Kopiowanie arkusza, użytkownik końcowy kopiuje arkusza ręcznie, istnieje nie kod związany z nowego arkusza i formantów na nowy arkusz nie działają. Jest to spowodowane nowo skopiowany arkusz jest <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektu i nie <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta. Kontrolek formularzy Windows Forms i kontrolek hosta może być dodane tylko do elementów hosta. Aby uzyskać więcej informacji, zobacz [ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-document-level-customization"></a>Aby dodać skopiowany arkusz w skoroszycie w dostosowaniu na poziomie dokumentu  
  
1.  Użyj <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> metodę, aby skopiować pierwszy arkusz w bieżącym skoroszycie i umieszczenie kopii po trzecie arkusza.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#16)]  
  
## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Aby dodać skopiowany arkusz w skoroszycie w dodatku narzędzi VSTO  
  
1.  Użyj <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> metodę, aby skopiować pierwszy arkusz w bieżącym skoroszycie i umieszczenie kopii po trzecie arkusza.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z arkuszami](../vsto/working-with-worksheets.md)   
 [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)   
 [Instrukcje: Programowe Dodawanie nowych arkuszy do skoroszytu](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Instrukcje: Programowe usuwanie arkuszy ze skoroszytu](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Instrukcje: Programowe Zaznaczanie arkuszy](../vsto/how-to-programmatically-select-worksheets.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
