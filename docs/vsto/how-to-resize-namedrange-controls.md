---
title: 'Instrukcje: Zmiana rozmiaru formantów NamedRange'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- NamedRange control, resizing
- ranges, resizing in Excel
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 199f3551b8d5cf0e9be4220809bc6af281263e0c
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869947"
---
# <a name="how-to-resize-namedrange-controls"></a>Instrukcje: Zmiana rozmiaru formantów NamedRange
  Można ustawić rozmiar <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli po dodaniu go do dokumentu programu Microsoft Office Excel; Jednakże, możesz chcieć zmienić jej rozmiar w późniejszym czasie.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Można zmienić rozmiar nazwanego zakresu, w czasie projektowania lub w czasie wykonywania w projektach na poziomie dokumentu. Nazwane zakresy można również zmienić rozmiar w czasie wykonywania w dodatkach VSTO dodatku poziomu aplikacji.  
  
 W tym temacie opisano następujące zadania:  
  
-   [Zmiana rozmiaru formantów NamedRange w czasie projektowania](#designtime)  
  
-   [Zmiana rozmiaru formantów NamedRange w czasie wykonywania w projekcie na poziomie dokumentu](#runtimedoclevel)  
  
-   [Zmiana rozmiaru formantów NamedRange w czasie wykonywania w projekcie dodatku narzędzi VSTO](#runtimeaddin)  
  
##  <a name="designtime"></a> Zmiana rozmiaru formantów NamedRange w czasie projektowania  
 Możesz zmienić rozmiar nazwany zakres poprzez zmianę definicji jej rozmiaru w **Definiowanie nazwy** okno dialogowe.  
  
### <a name="to-resize-a-named-range-by-using-the-define-name-dialog-box"></a>Aby zmienić rozmiar nazwany zakres przy użyciu nazwy zdefiniować okno dialogowe  
  
1.  Kliknij prawym przyciskiem myszy <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli.  
  
2.  Kliknij przycisk **Zarządzaj nazwane zakresy** w menu skrótów.  
  
     **Definiowanie nazwy** pojawi się okno dialogowe.  
  
3.  Wybierz zakres nazwanych, który chcesz zmienić.  
  
4.  Wyczyść **odwołuje się do** pola.  
  
5.  Zaznacz komórki, które chcesz użyć do zdefiniowania rozmiaru nazwanym zakresie.  
  
6.  Kliknij przycisk **OK**.  
  
##  <a name="runtimedoclevel"></a> Zmiana rozmiaru formantów NamedRange w czasie wykonywania w projekcie na poziomie dokumentu  
 Możesz zmienić rozmiar nazwany zakres programowo przy użyciu <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> właściwości.  
  
> [!NOTE]  
>  W **właściwości** oknie <xref:Microsoft.Office.Tools.Excel.NamedRange.RefersTo%2A> właściwość jest oznaczona jako tylko do odczytu.  
  
### <a name="to-resize-a-named-range-programmatically"></a>Aby programowo zmienić rozmiar nazwany zakres  
  
1.  Tworzenie <xref:Microsoft.Office.Tools.Excel.NamedRange> formant w komórce **A1** z `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#4)]
     [!code-vb[Trin_VstcoreHostControlsExcel#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#4)]  
  
2.  Zmień rozmiar nazwany zakres obejmujący komórki **B1**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreHostControlsExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#5)]  
  
##  <a name="runtimeaddin"></a> Zmiana rozmiaru formantów NamedRange w czasie wykonywania w projekcie dodatku narzędzi VSTO  
 Możesz zmienić rozmiar <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki w dowolnym otwartego arkusza w czasie wykonywania. Aby uzyskać więcej informacji o sposobie dodawania <xref:Microsoft.Office.Tools.Excel.NamedRange> sterowania do arkusza za pomocą dodatków narzędzi VSTO dla programów, zobacz [jak: Dodawanie formantów NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
### <a name="to-resize-a-named-range-programmatically"></a>Aby programowo zmienić rozmiar nazwany zakres  
  
1.  Tworzenie <xref:Microsoft.Office.Tools.Excel.NamedRange> formant w komórce **A1** z `Sheet1`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#10)]
     [!code-vb[Trin_Excel_Dynamic_Controls#10](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#10)]  
  
2.  Zmień rozmiar nazwany zakres obejmujący komórki **B1**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#11)]
     [!code-vb[Trin_Excel_Dynamic_Controls#11](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#11)]  
  
## <a name="see-also"></a>Zobacz także  
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Namedrange — formant](../vsto/namedrange-control.md)   
 [Instrukcje: Dodawanie formantów NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Instrukcje: Zmiana rozmiaru formantów zakładki](../vsto/how-to-resize-bookmark-controls.md)   
 [Instrukcje: Zmiana rozmiaru formantów ListObject](../vsto/how-to-resize-listobject-controls.md)  
