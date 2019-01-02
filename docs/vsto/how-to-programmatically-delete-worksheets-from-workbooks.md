---
title: 'Instrukcje: Programowe usuwanie arkuszy ze skoroszytu'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, deleting worksheets
- worksheets, deleting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7254ba703c0e25d37dd3582d4443a6bdf1653a96
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53843388"
---
# <a name="how-to-programmatically-delete-worksheets-from-workbooks"></a>Instrukcje: Programowe usuwanie arkuszy ze skoroszytu
  Możesz usunąć dowolnego arkusza w skoroszycie. Aby usunąć arkusza, użyj element hosta arkusza lub dostęp do arkusza za pomocą kolekcji arkuszy skoroszytu.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-the-worksheet-host-item"></a>Użyj element hosta arkusza  
 Jeśli arkusz został dodany w czasie projektowania w dostosowaniu na poziomie dokumentu, należy użyć <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> metodę, aby usunąć określonego arkusza. Poniższy kod usuwa arkusz ze skoroszytu, odwołując się bezpośrednio element hosta arkusza.  
  
> [!IMPORTANT]
>  Ten kod zadziała tylko w projektach, które tworzysz przy użyciu dowolnej z poniższych szablonów projektu:  
> 
> - Skoroszyt programu Excel 2013  
> - Szablon programu Excel 2013  
> - Skoroszyt programu Excel 2010  
> - Szablon programu Excel 2010  
> 
>   Jeśli chcesz wykonać to zadanie w typie projektu, należy dodać odwołanie do **Microsoft.Office.Interop.Excel** zestawu, a następnie należy użyć klas z tego zestawu do otwierania skoroszytu i usuwanie arkusza. Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie pod kątem aplikacji pakietu Office przy użyciu podstawowych zestawów międzyoperacyjnych](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) i [odwołanie do zestawu podstawowej usługi międzyoperacyjnej Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
### <a name="to-delete-a-worksheet-by-using-a-worksheet-host-item"></a>Aby usunąć arkusza za pomocą element hosta arkusza  
  
1.  Wywołaj <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> metody `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#17](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#17)]  
  
## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Korzystać z kolekcji arkuszy skoroszytu programu Excel  
 Dostęp do arkuszy za pomocą programu Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Sheets> kolekcji w następujących przypadkach:  
  
- Chcesz usunąć arkusza w dodatku VSTO.  
  
- Arkusz kalkulacyjny, który chcesz usunąć został utworzony w czasie wykonywania w dostosowaniu na poziomie dokumentu.  
  
  Poniższy kod usuwa arkusz ze skoroszytu, odwołując się do arkusza za pomocą numer indeksu **arkusze** kolekcji. Ten kod zakłada, że nowy arkusz został utworzony programowo.  
  
> [!IMPORTANT]  
>  Jeśli chcesz wykonać to zadanie w typie projektu, należy dodać odwołanie do **Microsoft.Office.Interop.Excel** zestawu, a następnie należy użyć klas z tego zestawu do otwierania skoroszytu i usuwanie arkusza. Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie pod kątem aplikacji pakietu Office przy użyciu podstawowych zestawów międzyoperacyjnych](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) i [odwołanie do zestawu podstawowej usługi międzyoperacyjnej Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
### <a name="to-delete-a-worksheet-by-using-the-sheets-collection-of-the-excel-workbook"></a>Aby usunąć arkusza za pomocą kolekcji arkuszy skoroszytu programu Excel  
  
1.  Wywołaj <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> metody <xref:Microsoft.Office.Interop.Excel.Sheets> kolekcji.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#18)]  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z arkuszami](../vsto/working-with-worksheets.md)   
 [Instrukcje: Programowe ukrywanie arkuszy](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Instrukcje: Programowe przenoszenie arkuszy w obrębie skoroszytu](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Instrukcje: Programowe Zaznaczanie arkuszy](../vsto/how-to-programmatically-select-worksheets.md)   
 [Instrukcje: Programowe Dodawanie nowych arkuszy do skoroszytu](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Element hosta arkusza](../vsto/worksheet-host-item.md)   
 [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
