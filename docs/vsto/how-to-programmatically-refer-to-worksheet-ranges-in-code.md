---
title: Jak programowo odwoływać się do zakresów arkusza w kodzie
description: Dowiedz się, jak za pomocą Visual Studio programowo odwoływać się do zawartości kontrolki NamedRange lub natywnego obiektu zakresu programu Excel w arkuszu programu Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6ea4e3da3c67d55aedea0d85a0a35b8ed2cf93b6
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827087"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Jak programowo odwoływać się do zakresów arkusza w kodzie
  Podobny proces umożliwia odwołowanie się do zawartości kontrolki lub <xref:Microsoft.Office.Tools.Excel.NamedRange> natywnego obiektu zakresu programu Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Używanie kontrolki NamedRange
 Poniższy przykład dodaje do arkusza, a następnie <xref:Microsoft.Office.Tools.Excel.NamedRange> dodaje tekst do komórki w zakresie.

### <a name="to-refer-to-a-namedrange-control"></a>Aby odwołać się do kontrolki NamedRange

1. Przypisz ciąg do <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> właściwości <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki. Ten kod należy umieścić w klasie arkusza, a nie w `ThisWorkbook` klasie .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet46":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet46":::

## <a name="use-native-excel-ranges"></a>Używanie natywnych zakresów programu Excel
 Poniższy przykład dodaje natywny zakres programu Excel do arkusza, a następnie dodaje tekst do komórki w zakresie.

### <a name="to-refer-to-a-native-range-object"></a>Aby odwołać się do natywnego obiektu zakresu

1. Przypisz ciąg do <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> właściwości zakresu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet47":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet47":::

## <a name="see-also"></a>Zobacz też
- [Praca z zakresami](../vsto/working-with-ranges.md)
- [Jak programowo sprawdzać pisownię w arkuszach](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [How to: Programowe stosowanie stylów do zakresów w skoroszytach](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Jak programowo automatycznie wypełniać zakresy przyrostowo zmieniającymi się danymi](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [How to: Programowe wyszukiwanie tekstu w zakresach arkusza](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)
- [NamedRange, kontrolka](../vsto/namedrange-control.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
- [Programowe ograniczenia elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
