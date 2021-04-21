---
title: 'How to: Programowe usuwanie ochrony z arkuszy'
description: Dowiedz się, jak za pomocą Visual Studio programowo usunąć ochronę z arkusza programu Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, unprotecting
- documents [Office development in Visual Studio], document protection
- document protection, removing from worksheets
- Unprotect method
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c392ee3434edf9211a4a3061e7a83a8621960430
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824162"
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>How to: Programowe usuwanie ochrony z arkuszy
  Ochronę można programowo usunąć z arkusza programu Microsoft Office Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 W poniższym przykładzie użyto zmiennej `getPasswordFromUser` , która zawiera hasło uzyskane od użytkownika.

## <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>Aby wyłączyć ochronę arkusza w dostosowywaniu na poziomie dokumentu

1. Wywołaj metodę arkusza i w razie potrzeby <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> przekaż hasło. W tym przykładzie przyjęto założenie, że pracujesz z arkuszem o nazwie `Sheet1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet28":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet28":::

## <a name="to-unprotect-a-worksheet-in-a-vsto-add-in"></a>Aby wyłączyć ochronę arkusza w dodatku VSTO

1. Wywołaj metodę aktywnego arkusza i w razie potrzeby <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> przekaż hasło.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet18":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet18":::

## <a name="see-also"></a>Zobacz też
- [Praca z arkuszami](../vsto/working-with-worksheets.md)
- [Jak programowo chronić arkusze](../vsto/how-to-programmatically-protect-worksheets.md)
- [Jak programowo chronić skoroszyty](../vsto/how-to-programmatically-protect-workbooks.md)
- [How to: Programmatically hide arkusze](../vsto/how-to-programmatically-hide-worksheets.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
