---
title: 'Instrukcje: Programowane dodawanie nowych arkuszy do skoroszytów'
description: Dowiedz się, jak można programowo utworzyć arkusz, a następnie dodać arkusz do kolekcji arkuszy w skoroszycie.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: babf029550907cb7faef77b71bdfae25a1307f38
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879465"
---
# <a name="how-to-programmatically-add-new-worksheets-to-workbooks"></a>Instrukcje: Programowane dodawanie nowych arkuszy do skoroszytów
  Można programowo utworzyć arkusz, a następnie dodać arkusz do kolekcji arkuszy w skoroszycie.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-document-level-customization"></a>Aby dodać nowy arkusz do skoroszytu w dostosowaniu na poziomie dokumentu

1. Użyj <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> metody <xref:Microsoft.Office.Interop.Excel.Sheets> kolekcji.

     [!code-csharp[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#15)]

     Nowy arkusz jest <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektem macierzystym, a nie elementem hosta. Jeśli chcesz dodać <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta, należy dodać arkusz w czasie projektowania.

## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Aby dodać nowy arkusz do skoroszytu w dodatku narzędzi VSTO

1. Użyj <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> metody <xref:Microsoft.Office.Interop.Excel.Sheets> kolekcji.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#11)]

     Nowy arkusz jest <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektem macierzystym, a nie elementem hosta. Można również wygenerować <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta z <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektu macierzystego. Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="see-also"></a>Zobacz też
- [Pracuj z arkuszami](../vsto/working-with-worksheets.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Instrukcje: programowe usuwanie arkuszy ze skoroszytów](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Instrukcje: Programowane Wybieranie arkuszy](../vsto/how-to-programmatically-select-worksheets.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
