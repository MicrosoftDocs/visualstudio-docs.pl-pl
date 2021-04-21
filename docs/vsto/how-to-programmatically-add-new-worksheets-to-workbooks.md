---
title: 'How to: Programowe dodawanie nowych arkuszy do skoroszytów'
description: Dowiedz się, jak programowo utworzyć arkusz, a następnie dodać arkusz do kolekcji arkuszy w skoroszycie.
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
ms.openlocfilehash: c093d61e38b3416fbef1e85dcf5af052c64db590
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827412"
---
# <a name="how-to-programmatically-add-new-worksheets-to-workbooks"></a>How to: Programowe dodawanie nowych arkuszy do skoroszytów
  Można programowo utworzyć arkusz, a następnie dodać arkusz do kolekcji arkuszy w skoroszycie.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-document-level-customization"></a>Aby dodać nowy arkusz do skoroszytu w dostosowywaniu na poziomie dokumentu

1. Użyj <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> metody <xref:Microsoft.Office.Interop.Excel.Sheets> kolekcji .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet15":::

     Nowy arkusz jest obiektem <xref:Microsoft.Office.Interop.Excel.Worksheet> natywnym, a nie elementem hosta. Jeśli chcesz dodać element <xref:Microsoft.Office.Tools.Excel.Worksheet> hosta, należy dodać arkusz w czasie projektowania.

## <a name="to-add-a-new-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Aby dodać nowy arkusz do skoroszytu w dodatku VSTO

1. Użyj <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> metody <xref:Microsoft.Office.Interop.Excel.Sheets> kolekcji .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet11":::

     Nowy arkusz jest obiektem <xref:Microsoft.Office.Interop.Excel.Worksheet> natywnym, a nie elementem hosta. Można również wygenerować element <xref:Microsoft.Office.Tools.Excel.Worksheet> hosta na podstawie obiektu <xref:Microsoft.Office.Interop.Excel.Worksheet> natywnego. Aby uzyskać więcej informacji, zobacz [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)(Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w czasie uruchamiania).

## <a name="see-also"></a>Zobacz też
- [Praca z arkuszami](../vsto/working-with-worksheets.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
- [How to: Programowe usuwanie arkuszy ze skoroszytów](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [How to: Programowe zaznaczanie arkuszy](../vsto/how-to-programmatically-select-worksheets.md)
- [Automatyzowanie programu Excel przy użyciu obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
