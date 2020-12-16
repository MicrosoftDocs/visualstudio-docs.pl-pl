---
title: 'Instrukcje: Programowane usuwanie ochrony z arkuszy'
description: Dowiedz się, jak za pomocą programu Visual Studio programowo usunąć ochronę z arkusza programu Microsoft Excel.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 86140e5595fc539a06a9eb8381e50b503e31708d
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526638"
---
# <a name="how-to-programmatically-remove-protection-from-worksheets"></a>Instrukcje: Programowane usuwanie ochrony z arkuszy
  Można programowo usunąć ochronę z arkusza programu Excel Microsoft Office.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Poniższy przykład używa zmiennej `getPasswordFromUser` , która zawiera hasło uzyskane od użytkownika.

## <a name="to-unprotect-a-worksheet-in-a-document-level-customization"></a>Aby wyłączyć ochronę arkusza w dostosowaniu na poziomie dokumentu

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.Worksheet.Unprotect%2A> metodę arkusza i przekaż hasło, w razie potrzeby. W tym przykładzie założono, że pracujesz z arkuszem o nazwie `Sheet1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#28)]
     [!code-vb[Trin_VstcoreExcelAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#28)]

## <a name="to-unprotect-a-worksheet-in-a-vsto-add-in"></a>Aby wyłączyć ochronę arkusza w dodatku narzędzi VSTO

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Worksheet.Unprotect%2A> metodę aktywnego arkusza i przekaż hasło, w razie potrzeby.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#18](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#18)]

## <a name="see-also"></a>Zobacz też
- [Pracuj z arkuszami](../vsto/working-with-worksheets.md)
- [Instrukcje: programowe Włączanie ochrony arkuszy](../vsto/how-to-programmatically-protect-worksheets.md)
- [Instrukcje: programowane włączanie ochrony skoroszytów](../vsto/how-to-programmatically-protect-workbooks.md)
- [Instrukcje: programowe ukrywanie arkuszy](../vsto/how-to-programmatically-hide-worksheets.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
