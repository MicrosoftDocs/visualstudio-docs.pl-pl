---
title: 'How to: Programowe ukrywanie arkuszy'
description: Dowiedz się, jak programowo pokazać lub ukryć dowolny arkusz w skoroszycie programu Microsoft Excel przy użyciu elementu hosta arkusza.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden worksheets
- worksheets, hiding
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b859ea468db86d57347553f9fd10b44fea99026b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826476"
---
# <a name="how-to-programmatically-hide-worksheets"></a>How to: Programowe ukrywanie arkuszy
  Każdy arkusz w skoroszycie można pokazać lub ukryć. Aby ukryć arkusz, użyj elementu hosta arkusza lub uzyskaj dostęp do arkusza przy użyciu kolekcji arkuszy skoroszytu.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>Używanie elementu hosta arkusza
 Jeśli arkusz został dodany w czasie projektowania w dostosowywaniu na poziomie dokumentu, użyj właściwości , <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> aby ukryć określony arkusz.

### <a name="to-hide-a-worksheet-using-a-worksheet-host-item"></a>Aby ukryć arkusz przy użyciu elementu hosta arkusza

1. Ustaw właściwość <xref:Microsoft.Office.Tools.Excel.Worksheet.Visible%2A> elementu hosta na wartość `Sheet1` <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> wyliczenia.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet25":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet25":::

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Używanie kolekcji Arkuszy skoroszytu programu Excel
 Dostęp do arkuszy za pośrednictwem Microsoft Office programu Excel <xref:Microsoft.Office.Interop.Excel.Sheets> można uzyskać w następujących przypadkach:

- Chcesz ukryć arkusz w dodatku VSTO.

- Arkusz, który chcesz ukryć, został utworzony w czasie uruchamiania w dostosowywaniu na poziomie dokumentu.

### <a name="to-hide-a-worksheet-using-the-sheets-collection-of-the-excel-workbook"></a>Aby ukryć arkusz przy użyciu kolekcji Arkusze skoroszytu programu Excel

1. Ustaw <xref:Microsoft.Office.Interop.Excel.Worksheets.Visible%2A> właściwość arkusza na wartość <xref:Microsoft.Office.Interop.Excel.XlSheetVisibility.xlSheetHidden> wyliczenia.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet26":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet26":::

## <a name="see-also"></a>Zobacz też
- [Praca z arkuszami](../vsto/working-with-worksheets.md)
- [How to: Programowe usuwanie arkuszy ze skoroszytów](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [How to: Programmatically move worksheets Within workbooks (2017: Programowe przenoszenie arkuszy w obrębie skoroszytów)](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [How to: Programmatically protect arkusze](../vsto/how-to-programmatically-protect-worksheets.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
