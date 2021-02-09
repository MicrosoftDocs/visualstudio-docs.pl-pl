---
title: 'Instrukcje: programowane sortowanie danych w arkuszach'
description: Dowiedz się, jak za pomocą programu Visual Studio programistycznie sortować dane zawarte w zakresach arkusza i listach w czasie wykonywania.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data sorting, worksheets
- data [Office development in Visual Studio], sorting in worksheets
- worksheets, sorting data
- sorting data, in worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c01dfb8af04d94453065a79c8f183bee355d8ab4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877762"
---
# <a name="how-to-programmatically-sort-data-in-worksheets"></a>Instrukcje: programowane sortowanie danych w arkuszach
  Można sortować dane, które znajdują się w zakresach arkusza i listy w czasie wykonywania. Poniższy kod sortuje zakres wielu kolumn o nazwie `Fruits` przez dane w pierwszej kolumnie, a następnie według danych w drugiej kolumnie.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="sort-data-in-a-document-level-customization"></a>Sortowanie danych w dostosowaniu na poziomie dokumentu

### <a name="to-sort-data-in-a-namedrange-control"></a>Aby posortować dane w kontrolce NamedRange

1. Wywoływanie <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> metody <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu. Poniższy przykład wymaga <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki o nazwie `Fruits` w arkuszu. Ten kod musi być umieszczony w klasie arkusza, a nie w `ThisWorkbook` klasie.

    [!code-csharp[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#78)]
    [!code-vb[Trin_VstcoreExcelAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#78)]

   Umieść poniższy kod w *Arkusz1. vb* lub *Sheet1.cs* , aby posortować dane w <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolce. W kodzie założono, że masz <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolkę o nazwie `fruitList` w arkuszu o nazwie `Sheet1` .

### <a name="to-sort-data-in-a-listobject-control"></a>Aby posortować dane w formancie ListObject

1. Wywołaj <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> metodę <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> właściwości <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki hosta.

     [!code-csharp[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#79)]
     [!code-vb[Trin_VstcoreExcelAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#79)]

## <a name="sort-data-in-a-vsto-add-in"></a>Sortowanie danych w dodatku narzędzi VSTO

### <a name="to-sort-data-in-a-native-range"></a>Aby posortować dane w zakresie natywnym

1. Wywoływanie <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> metody natywnego formantu programu Excel <xref:Microsoft.Office.Interop.Excel.Range> . Poniższy przykład wymaga natywnego formantu programu Excel o nazwie `Fruits` w arkuszu.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#23](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#23)]

### <a name="to-sort-data-in-a-listobject-control"></a>Aby posortować dane w formancie ListObject

1. Wywoływanie <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> metody <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> Właściwości natywnego formantu programu Excel <xref:Microsoft.Office.Interop.Excel.ListObject> . W poniższym przykładzie założono, że masz natywny <xref:Microsoft.Office.Interop.Excel.ListObject> formant programu Excel o nazwie `fruitList` w aktywnym arkuszu.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#24](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#24)]

## <a name="see-also"></a>Zobacz też
- [Pracuj z arkuszami](../vsto/working-with-worksheets.md)
- [Instrukcje: Programowane automatyczne wypełnianie zakresów przyrostowo zmieniającymi się danymi](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Instrukcje: programowe odwoływanie się do zakresów arkusza w kodzie](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Instrukcje: Programowane stosowanie stylów do zakresów w skoroszytach](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [NamedRange — formant](../vsto/namedrange-control.md)
- [ListObject — formant](../vsto/listobject-control.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
