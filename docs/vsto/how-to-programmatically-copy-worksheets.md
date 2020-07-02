---
title: 'Instrukcje: Programowane kopiowanie arkuszy'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 8226f337994c686d4d370e91831bc1262d3ef85e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546084"
---
# <a name="how-to-programmatically-copy-worksheets"></a>Instrukcje: Programowane kopiowanie arkuszy
  Możesz utworzyć kopię arkusza i wstawić ten arkusz przed lub po istniejącym arkuszu w skoroszycie. Jeśli nie określisz miejsca, w którym ma zostać wstawiony arkusz, program Excel utworzy nowy skoroszyt zawierający nowy arkusz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

> [!NOTE]
> Bez względu na to, czy kopiowany jest arkusz, czy użytkownik końcowy kopiuje arkusz ręcznie, nie istnieje żaden kod związany z nowym arkuszem, a kontrolki w nowym arkuszu nie działają. Dzieje się tak, ponieważ nowo skopiowany arkusz jest <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektem, a nie <xref:Microsoft.Office.Tools.Excel.Worksheet> elementem hosta. Kontrolki Windows Forms i kontrolki hosta mogą być dodawane tylko do elementów hosta. Aby uzyskać więcej informacji, zobacz Ograniczenia programowe [elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-document-level-customization"></a>Aby dodać skopiowany arkusz do skoroszytu w dostosowaniu na poziomie dokumentu

1. Użyj <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> metody, aby skopiować pierwszy arkusz w bieżącym skoroszycie i umieścić kopię po trzecim arkuszu.

     [!code-csharp[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#16)]

## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Aby dodać skopiowany arkusz do skoroszytu w dodatku narzędzi VSTO

1. Użyj <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> metody, aby skopiować pierwszy arkusz w bieżącym skoroszycie i umieścić kopię po trzecim arkuszu.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#12)]

## <a name="see-also"></a>Zobacz także
- [Pracuj z arkuszami](../vsto/working-with-worksheets.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Instrukcje: Programowane dodawanie nowych arkuszy do skoroszytów](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [Instrukcje: programowe usuwanie arkuszy ze skoroszytów](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Instrukcje: Programowane Wybieranie arkuszy](../vsto/how-to-programmatically-select-worksheets.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
