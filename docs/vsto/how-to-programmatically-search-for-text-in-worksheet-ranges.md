---
title: 'How to: Programowe wyszukiwanie tekstu w zakresach arkusza'
description: Dowiedz się, jak używać Visual Studio do programowego wyszukiwania tekstu w zakresach arkuszy programu Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, searching
- text [Office development in Visual Studio], searching in worksheets
- text searches, worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 762cb3fc35b43bfd3ad15aea669adff2d370b632
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827945"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>How to: Programowe wyszukiwanie tekstu w zakresach arkusza
  Metoda <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> obiektu <xref:Microsoft.Office.Interop.Excel.Range> umożliwia wyszukiwanie tekstu w zakresie. Ten tekst może być również dowolnym z ciągów błędów, które mogą pojawić się w komórce arkusza, takiej jak `#NULL!` lub `#VALUE!` . Aby uzyskać więcej informacji na temat ciągów błędów, zobacz [Wartości błędów komórek](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Poniższy przykład wyszukuje zakres o nazwie i modyfikuje czcionkę dla komórek zawierających `Fruits` wyraz "apples". Ta procedura używa również <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> metody , która używa wcześniej ustawionych ustawień wyszukiwania w celu powtórzenia wyszukiwania. Należy określić komórkę, po której ma być wyszukiwany, a <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> metoda obsługuje resztę.

> [!NOTE]
> Wyszukiwanie metody jest zawijany z powrotem do początku zakresu wyszukiwania po <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> osiągnięciu końca zakresu. Kod musi zapewniać, że wyszukiwanie nie zawija się w nieskończoną pętlę. Przykładowa procedura przedstawia jeden ze sposobów obsługi tego przy użyciu <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> właściwości .

## <a name="to-search-for-text-in-a-worksheet-range"></a>Aby wyszukać tekst w zakresie arkusza

1. Zadeklaruj zmienne do śledzenia całego zakresu, pierwszego znalezionego zakresu i bieżącego znalezionego zakresu.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet58":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet58":::

2. Wyszukaj pierwsze dopasowanie, określając wszystkie parametry z wyjątkiem komórki do wyszukania.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet59":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet59":::

3. Kontynuuj wyszukiwanie, o ile istnieją dopasowania.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet60":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet60":::

4. Porównaj pierwszy znaleziony zakres ( `firstFind` ) z **niczym**. Jeśli `firstFind` nie zawiera żadnej wartości, kod przechowuje znaleziony zakres ( `currentFind` ).

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet61":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet61":::

5. Zakończ pętlę, jeśli adres znalezionego zakresu odpowiada adresowi pierwszego znalezionego zakresu.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet62":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet62":::

6. Ustaw wygląd znalezionego zakresu.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet63":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet63":::

7. Wykonaj kolejne wyszukiwanie.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet64":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet64":::

   W poniższym przykładzie przedstawiono metodę complete.

## <a name="example"></a>Przykład
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet57":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet57":::

## <a name="see-also"></a>Zobacz także
- [Praca z zakresami](../vsto/working-with-ranges.md)
- [How to: Programowe stosowanie stylów do zakresów w skoroszytach](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Jak programowo odwoływać się do zakresów arkusza w kodzie](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
