---
title: Jak programowo wyświetlać komentarze do arkusza
description: Dowiedz się, jak programowo wyświetlać i ukrywać komentarze w arkuszu programu Microsoft Excel na poziomie dokumentu lub aplikacji.
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
ms.openlocfilehash: af327a6756189c73f80f624205451274abf19264
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828673"
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>Jak programowo wyświetlać komentarze do arkusza
  Komentarze można programowo pokazywać i ukrywać w Microsoft Office programu Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>Aby wyświetlić wszystkie komentarze w arkuszu w dostosowywaniu na poziomie dokumentu

1. Ustaw właściwość <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> na **wartość true,** jeśli chcesz wyświetlić komentarze. W przeciwnym razie ustaw wartość **false**. Ten kod musi być umieszczony w klasie arkusza, a nie w `ThisWorkbook` klasie .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet31":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet31":::

## <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>Aby wyświetlić wszystkie komentarze w arkuszu w dodatku VSTO na poziomie aplikacji

1. Ustaw właściwość <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> na **wartość true,** jeśli chcesz wyświetlić komentarze. W przeciwnym razie ustaw wartość **false**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet21":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet21":::

## <a name="see-also"></a>Zobacz też
- [Praca z arkuszami](../vsto/working-with-worksheets.md)
- [Jak programowo dodawać i usuwać komentarze do arkusza](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
