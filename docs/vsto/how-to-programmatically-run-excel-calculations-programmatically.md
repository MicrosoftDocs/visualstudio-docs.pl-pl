---
title: Jak programowo uruchamiać obliczenia programu Excel
description: Dowiedz się, jak używać Visual Studio do programowego uruchamiania obliczeń w skoroszycie programu Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, running calculations
- calculations, running in Excel
- Excel [Office development in Visual Studio], running calculations programmatically
- workbooks, running calculations
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9fdc9cbc1966ac0fd862b795d66c7004f5089499
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823967"
---
# <a name="how-to-programmatically-run-excel-calculations"></a>Jak programowo uruchamiać obliczenia programu Excel
  Podobny proces umożliwia uruchamianie obliczeń w kontrolce lub natywnym obiekcie <xref:Microsoft.Office.Tools.Excel.NamedRange> zakresu programu Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="run-calculations-in-a-namedrange-control"></a>Uruchamianie obliczeń w kontrolce NamedRange
 Poniższy przykład tworzy w <xref:Microsoft.Office.Tools.Excel.NamedRange> komórce A1, a następnie oblicza komórkę. Ten kod musi być umieszczony w klasie arkusza, a nie w `ThisWorkbook` klasie .

### <a name="to-run-calculations-in-a-namedrange-control"></a>Aby uruchomić obliczenia w kontrolce NamedRange

1. Utwórz nazwany zakres.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet75":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet75":::

2. Wywołaj <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> metodę określonego zakresu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet76":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet76":::

## <a name="run-calculations-in-a-native-excel-range"></a>Uruchamianie obliczeń w natywnym zakresie programu Excel

### <a name="to-run-calculations-in-a-native-excel-range"></a>Uruchamianie obliczeń w natywnym zakresie programu Excel

1. Utwórz nazwany zakres.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet30":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet30":::

2. Wywołaj <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> metodę określonego zakresu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet31":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet31":::

## <a name="see-also"></a>Zobacz też
- [Praca z zakresami](../vsto/working-with-ranges.md)
- [NamedRange, kontrolka](../vsto/namedrange-control.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
