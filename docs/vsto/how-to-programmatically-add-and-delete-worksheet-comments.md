---
title: 'How to: Programowe dodawanie i usuwanie komentarzy do arkusza'
description: Dowiedz się, jak programowo dodawać i usuwać komentarze Microsoft Office arkuszach programu Excel. Komentarze można dodawać tylko do pojedynczych komórek, a nie do zakresów z wieloma komórkami.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, comments
- worksheets, comments
- comments, worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 20b718be3bec6cac3ee6c0b0985fa6efca867189
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826944"
---
# <a name="how-to-programmatically-add-and-delete-worksheet-comments"></a>How to: Programowe dodawanie i usuwanie komentarzy do arkusza
  Możesz programowo dodawać i usuwać komentarze w Microsoft Office programu Excel. Komentarze można dodawać tylko do pojedynczych komórek, a nie do zakresów z wieloma komórkami.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="add-and-delete-a-comment-in-a-document-level-project"></a>Dodawanie i usuwanie komentarza w projekcie na poziomie dokumentu
 W poniższych przykładach przyjęto założenie, że w arkuszu istnieje kontrolka z jedną komórką o <xref:Microsoft.Office.Tools.Excel.NamedRange> `dateComment` nazwie `Sheet1` .

### <a name="to-add-a-new-comment-to-a-named-range"></a>Aby dodać nowy komentarz do nazwanego zakresu

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.NamedRange.AddComment%2A> metodę <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki i podać tekst komentarza. Ten kod należy umieścić w `Sheet1` klasie .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet30":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet30":::

#### <a name="to-delete-a-comment-from-a-named-range"></a>Aby usunąć komentarz z nazwanego zakresu

1. Sprawdź, czy istnieje komentarz dla zakresu i usuń go. Ten kod należy umieścić w `Sheet1` klasie .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet29":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet29":::

## <a name="add-and-delete-a-comment-in-a-vsto-add-in-project"></a>Dodawanie i usuwanie komentarza w projekcie dodatku VSTO
 W poniższych przykładach przyjęto założenie, że w aktywnym arkuszu znajduje się pojedyncza <xref:Microsoft.Office.Interop.Excel.Range> `dateComment` komórka o nazwie .

### <a name="to-add-a-new-comment-to-an-excel-range"></a>Aby dodać nowy komentarz do zakresu programu Excel

1. Wywołaj <xref:Microsoft.Office.Interop.Excel.Range.AddComment%2A> metodę metody i podać tekst <xref:Microsoft.Office.Interop.Excel.Range> komentarza.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet20":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet20":::

### <a name="to-delete-a-comment-from-an-excel-range"></a>Aby usunąć komentarz z zakresu programu Excel

1. Sprawdź, czy istnieje komentarz dla zakresu i usuń go.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet19":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet19":::

## <a name="see-also"></a>Zobacz też
- [Praca z arkuszami](../vsto/working-with-worksheets.md)
- [Jak programowo wyświetlać komentarze do arkusza](../vsto/how-to-programmatically-display-worksheet-comments.md)
- [NamedRange, kontrolka](../vsto/namedrange-control.md)
