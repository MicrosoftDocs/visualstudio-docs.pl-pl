---
title: 'How to: Programowe stosowanie stylów do zakresów w skoroszytach'
description: Dowiedz się, jak stosować style nazwane do regionów w skoroszytach. Program Excel dostarcza wiele wstępnie zdefiniowanych stylów.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, styles
- styles, workbook ranges
- workbooks, styles
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b1ce30c9a0e21bd4b8860f7a4d17191c48cd2ad9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828309"
---
# <a name="how-to-programmatically-apply-styles-to-ranges-in-workbooks"></a>How to: Programowe stosowanie stylów do zakresów w skoroszytach
  Style nazwane można stosować do regionów w skoroszytach. Program Excel dostarcza wiele wstępnie zdefiniowanych stylów.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 W **oknie** dialogowym Formatowanie komórek są wyświetlane wszystkie opcje, których można użyć do formatowania komórek. Każda z tych opcji jest dostępna w kodzie. Aby wyświetlić to okno dialogowe w programie Excel, kliknij pozycję **Komórki** w menu **Format.**

## <a name="to-apply-a-style-to-a-named-range-in-a-document-level-customization"></a>Aby zastosować styl do nazwanego zakresu w dostosowywaniu na poziomie dokumentu

1. Utwórz nowy styl i ustaw jego atrybuty.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet53":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet53":::

2. Utwórz <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę, przypisz do niego tekst, a następnie zastosuj nowy styl. Ten kod musi być umieszczony w klasie arkusza, a nie w `ThisWorkbook` klasie .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet54":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet54":::

## <a name="to-clear-a-style-from-a-named-range-in-a-document-level-customization"></a>Aby wyczyścić styl z nazwanego zakresu w dostosowywaniu na poziomie dokumentu

1. Zastosuj styl Normalny do zakresu. Ten kod musi być umieszczony w klasie arkusza, a nie w `ThisWorkbook` klasie .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet55":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet55":::

## <a name="to-apply-a-style-to-a-named-range-in-a-vsto-add-in"></a>Aby zastosować styl do nazwanego zakresu w dodatku VSTO

1. Utwórz nowy styl i ustaw jego atrybuty.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet28":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet28":::

2. Utwórz , <xref:Microsoft.Office.Interop.Excel.Range> przypisz do niego tekst, a następnie zastosuj nowy styl.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet29":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet29":::

## <a name="to-clear-a-style-from-a-named-range-in-a-vsto-add-in"></a>Aby wyczyścić styl z nazwanego zakresu w dodatku VSTO

1. Zastosuj styl Normalny do zakresu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet56":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet56":::

## <a name="see-also"></a>Zobacz też
- [Praca z zakresami](../vsto/working-with-ranges.md)
- [NamedRange, kontrolka](../vsto/namedrange-control.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
