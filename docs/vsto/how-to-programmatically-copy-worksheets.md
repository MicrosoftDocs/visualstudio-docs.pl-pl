---
title: 'How to: Programowe kopiowanie arkuszy'
description: Dowiedz się, jak utworzyć kopię arkusza i wstawić ten arkusz przed istniejącym arkuszem w skoroszycie lub po nim.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2a5b24d7896ec1f81c7e8d5d4c41a5e6af807b13
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828582"
---
# <a name="how-to-programmatically-copy-worksheets"></a>How to: Programowe kopiowanie arkuszy
  Można utworzyć kopię arkusza i wstawić ten arkusz przed lub po istniejącym arkuszu w skoroszycie. Jeśli nie określisz miejsca wstawienia arkusza, program Excel utworzy nowy skoroszyt zawierający nowy arkusz.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

> [!NOTE]
> Niezależnie od tego, czy arkusz jest kopiowany programowo, czy też użytkownik końcowy ręcznie kopiuje arkusz, nowy arkusz nie ma kodu, a kontrolki w nowym arkuszu nie działają. Wynika to z tego, że nowo skopiowany arkusz jest <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektem, a nie <xref:Microsoft.Office.Tools.Excel.Worksheet> elementem hosta. Windows Forms i kontrolki hosta można dodawać tylko do elementów hosta. Aby uzyskać więcej informacji, zobacz [Programowe ograniczenia elementów hosta i kontrolek hosta.](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)

## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-document-level-customization"></a>Aby dodać skopiowany arkusz do skoroszytu w dostosowywaniu na poziomie dokumentu

1. Użyj metody <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> , aby skopiować pierwszy arkusz w bieżącym skoroszycie i umieścić kopię po trzecim arkuszu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet16":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet16":::

## <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Aby dodać skopiowany arkusz do skoroszytu w dodatku VSTO

1. Użyj metody <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A> , aby skopiować pierwszy arkusz w bieżącym skoroszycie i umieścić kopię po trzecim arkuszu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet12":::

## <a name="see-also"></a>Zobacz też
- [Praca z arkuszami](../vsto/working-with-worksheets.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
- [How to: Programowe dodawanie nowych arkuszy do skoroszytów](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [How to: Programowe usuwanie arkuszy ze skoroszytów](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [How to: Programowe zaznaczanie arkuszy](../vsto/how-to-programmatically-select-worksheets.md)
- [Automatyzowanie programu Excel przy użyciu obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
