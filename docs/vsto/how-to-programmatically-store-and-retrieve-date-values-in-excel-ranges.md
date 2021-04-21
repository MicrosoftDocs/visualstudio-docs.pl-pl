---
title: Programowe & pobieranie wartości dat w zakresach programu Excel
description: Dowiedz się, jak używać Visual Studio do programowego przechowywania i pobierania wartości dat w zakresach programu Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], retrieving date values from ranges
- ranges, retrieving data values
- dates, retrieving from Excel ranges
- Excel [Office development in Visual Studio], storing date values in ranges
- date values, storing in Excel ranges
- dates, storing in Excel ranges
- ranges, storing date values
- date values
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6e3115e00147a5dff850f6e0c051ffc3b6733218
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826242"
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>Jak programowo przechowywać i pobierać wartości dat w zakresach programu Excel
  Wartości można przechowywać i pobierać w <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolce lub natywnym obiekcie zakresu programu Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Jeśli przechowujesz wartość daty przypadaną w dniu 1.1.1900 r. lub późniejszą w zakresie przy użyciu narzędzi deweloperskiej pakietu Office w usłudze Visual Studio, jest ona przechowywana w formacie OLE Automation (OA). Należy użyć metody <xref:System.DateTime.FromOADate%2A> , aby pobrać wartość dat automatyzacji OLE (OA). Jeśli data jest wcześniejsza niż 1/1/1900, jest przechowywana jako ciąg.

> [!NOTE]
> Daty programu Excel różnią się od dat automatyzacji OLE dla pierwszych dwóch miesięcy 1900 r. Istnieją również różnice, jeśli zaznaczono opcję systemu dat **1904.** Poniższe przykłady kodu nie obejmują tych różnic.

## <a name="use-a-namedrange-control"></a>Używanie kontrolki NamedRange

- Ten przykład dotyczy dostosowań na poziomie dokumentu. Poniższy kod należy umieścić w klasie arkusza, a nie w `ThisWorkbook` klasie .

### <a name="to-store-a-date-value-in-a-named-range"></a>Aby przechowywać wartość daty w nazwanych zakresach

1. Utwórz <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę w komórce **A1**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet50":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet50":::

2. Ustaw dzisiejszą datę jako wartość dla `NamedRange1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet51":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet51":::

### <a name="to-retrieve-a-date-value-from-a-named-range"></a>Aby pobrać wartość daty z nazwanego zakresu

1. Pobierz wartość daty z `NamedRange1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet52":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet52":::

## <a name="use-native-excel-ranges"></a>Używanie natywnych zakresów programu Excel

### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>Aby przechowywać wartość daty w natywnym obiekcie zakresu programu Excel

1. Utwórz <xref:Microsoft.Office.Interop.Excel.Range> komórkę reprezentującą **komórkę A1**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet25":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet25":::

2. Ustaw dzisiejszą datę jako wartość dla `rng` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet26":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet26":::

### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>Aby pobrać wartość daty z natywnego obiektu zakresu programu Excel

1. Pobierz wartość daty z `rng` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet27":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet27":::

## <a name="see-also"></a>Zobacz też
- [Praca z zakresami](../vsto/working-with-ranges.md)
- [Omówienie modelu obiektu programu Excel](../vsto/excel-object-model-overview.md)
- [NamedRange, kontrolka](../vsto/namedrange-control.md)
- [Jak programowo odwoływać się do zakresów arkusza w kodzie](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [2017: Dodawanie kontrolek NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
