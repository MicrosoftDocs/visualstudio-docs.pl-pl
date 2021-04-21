---
title: Jak programowo sortować dane w arkuszach
description: Dowiedz się, jak za pomocą Visual Studio programowo sortować dane zawarte w zakresach arkusza i listach w czasie uruchamiania.
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
ms.openlocfilehash: 024bf53b7fc7f3a6e32e10b7107c9a62d8c40cee
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825020"
---
# <a name="how-to-programmatically-sort-data-in-worksheets"></a>Jak programowo sortować dane w arkuszach
  Dane zawarte w zakresach arkusza i listach arkusza można sortować w czasie uruchamiania. Poniższy kod sortuje zakres wielu kolumn nazwany według danych w pierwszej kolumnie, a następnie według danych `Fruits` w drugiej kolumnie.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="sort-data-in-a-document-level-customization"></a>Sortowanie danych w dostosowywaniu na poziomie dokumentu

### <a name="to-sort-data-in-a-namedrange-control"></a>Aby posortować dane w kontrolce NamedRange

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.NamedRange.Sort%2A> metodę <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki . Poniższy przykład wymaga <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki o `Fruits` nazwie w arkuszu. Ten kod należy umieścić w klasie arkusza, a nie w `ThisWorkbook` klasie .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet78":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet78":::

   Umieść następujący kod w *1.vb* lub *Sheet1.cs,* aby posortować dane w <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolce. W kodzie założono, że masz <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolkę o nazwie `fruitList` w arkuszu o nazwie `Sheet1` .

### <a name="to-sort-data-in-a-listobject-control"></a>Aby posortować dane w kontrolce ListObject

1. Wywołaj <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> metodę <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> właściwości <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki hosta.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet79":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet79":::

## <a name="sort-data-in-a-vsto-add-in"></a>Sortowanie danych w dodatku VSTO

### <a name="to-sort-data-in-a-native-range"></a>Aby posortować dane w zakresie natywnym

1. Wywołaj <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> metodę natywnej kontrolki programu <xref:Microsoft.Office.Interop.Excel.Range> Excel. Poniższy przykład wymaga natywnej kontrolki programu Excel o `Fruits` nazwie w arkuszu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet23":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet23":::

### <a name="to-sort-data-in-a-listobject-control"></a>Aby posortować dane w kontrolce ListObject

1. Wywołaj <xref:Microsoft.Office.Interop.Excel.Range.Sort%2A> metodę właściwości <xref:Microsoft.Office.Tools.Excel.ListObject.Range%2A> natywnej kontrolki programu <xref:Microsoft.Office.Interop.Excel.ListObject> Excel. W poniższym przykładzie przyjęto założenie, że w aktywnym arkuszu znajduje się natywna kontrolka programu Excel <xref:Microsoft.Office.Interop.Excel.ListObject> `fruitList` o nazwie .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet24":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet24":::

## <a name="see-also"></a>Zobacz też
- [Praca z arkuszami](../vsto/working-with-worksheets.md)
- [Jak programowo automatycznie wypełniać zakresy przyrostowo zmieniającymi się danymi](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Jak programowo odwoływać się do zakresów arkusza w kodzie](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [How to: Programowe stosowanie stylów do zakresów w skoroszytach](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [NamedRange, kontrolka](../vsto/namedrange-control.md)
- [ListObject, kontrolka](../vsto/listobject-control.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
