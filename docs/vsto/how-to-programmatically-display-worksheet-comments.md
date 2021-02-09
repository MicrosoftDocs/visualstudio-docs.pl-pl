---
title: 'Instrukcje: Programowane wyświetlanie komentarzy do arkusza'
description: Dowiedz się, jak można programowo pokazać i ukryć komentarze w arkuszu programu Microsoft Excel na poziomie dokumentu lub na poziomie aplikacji.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, comments
- comments, worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7de75a1846aa7261a723c87297511b7461c49f47
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885511"
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>Instrukcje: Programowane wyświetlanie komentarzy do arkusza
  Można programowo pokazać i ukryć komentarze w Microsoft Office arkuszach programu Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>Aby wyświetlić wszystkie komentarze w arkuszu w dostosowaniu na poziomie dokumentu

1. Ustaw <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> Właściwość na **wartość true** , jeśli chcesz wyświetlić komentarze; w przeciwnym razie **wartość false**. Ten kod musi być umieszczony w klasie arkusza, a nie w `ThisWorkbook` klasie.

     [!code-csharp[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#31)]

## <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>Aby wyświetlić wszystkie komentarze w arkuszu w dodatku VSTO na poziomie aplikacji

1. Ustaw <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> Właściwość na **wartość true** , jeśli chcesz wyświetlić komentarze; w przeciwnym razie **wartość false**.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#21)]

## <a name="see-also"></a>Zobacz też
- [Pracuj z arkuszami](../vsto/working-with-worksheets.md)
- [Instrukcje: Programowane dodawanie i usuwanie komentarzy do arkusza](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
