---
title: 'Instrukcje: Programowe wyświetlanie komentarzy do arkusza'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, comments
- comments, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cc030fed25409f5c034abfd07f1f9358bfea593b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62812699"
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>Instrukcje: Programowe wyświetlanie komentarzy do arkusza
  Można programowo pokazywanie i ukrywanie komentarzy w arkuszach programu Microsoft Office Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>Aby wyświetlić wszystkie komentarze w skoroszycie w dostosowaniu na poziomie dokumentu

1. Ustaw <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> właściwości **true** Jeśli chcesz wyświetlić komentarze; w przeciwnym razie **false**. Ten kod muszą być umieszczone w klasie arkusza, nie w `ThisWorkbook` klasy.

     [!code-csharp[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#31)]

## <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>Aby wyświetlić wszystkie komentarze w skoroszycie w dodatku narzędzi VSTO dla dodatku poziomu aplikacji

1. Ustaw <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> właściwości **true** Jeśli chcesz wyświetlić komentarze; w przeciwnym razie **false**.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#21)]

## <a name="see-also"></a>Zobacz także
- [Praca z arkuszami](../vsto/working-with-worksheets.md)
- [Instrukcje: Programowe Dodawanie i usuwanie komentarzy do arkusza](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)
- [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)
