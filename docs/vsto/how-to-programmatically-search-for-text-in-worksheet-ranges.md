---
title: 'Instrukcje: programowe wyszukiwanie tekstu w zakresach arkusza'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4d35d24f9132a9b279316b53fbb13e3bfa094994
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547033"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Instrukcje: programowe wyszukiwanie tekstu w zakresach arkusza
  <xref:Microsoft.Office.Interop.Excel.Range.Find%2A>Metoda <xref:Microsoft.Office.Interop.Excel.Range> obiektu umożliwia wyszukiwanie tekstu w zakresie. Ten tekst może być również dowolnym z ciągów błędów, które mogą pojawić się w komórce arkusza, takiej jak `#NULL!` lub `#VALUE!` . Aby uzyskać więcej informacji o ciągach błędów, zobacz [komórki wartości błędów](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Poniższy przykład przeszukuje zakres o nazwie `Fruits` i modyfikuje czcionkę dla komórek zawierających wyraz "jabłka". Ta procedura używa również <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> metody, która używa wcześniej ustawionych ustawień wyszukiwania do powtarzania wyszukiwania. Należy określić komórkę, która ma być przeszukiwana, a <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> Metoda obsługuje resztę.

> [!NOTE]
> <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A>Wyszukiwanie metody zawija się z powrotem do początku zakresu wyszukiwania po osiągnięciu końca zakresu. Kod musi upewnić się, że wyszukiwanie nie jest zawijane wokół pętli nieskończonej. Przykładowa procedura pokazuje jeden ze sposobów obsługi tego przy użyciu <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> właściwości.

## <a name="to-search-for-text-in-a-worksheet-range"></a>Aby wyszukać tekst w zakresie arkusza

1. Zadeklaruj zmienne do śledzenia całego zakresu, pierwszego znalezionego zakresu i bieżącego znalezionego zakresu.

    [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
    [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]

2. Wyszukaj pierwsze dopasowanie, określając wszystkie parametry, z wyjątkiem komórki do przeszukania.

    [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
    [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]

3. Kontynuuj wyszukiwanie pod warunkiem, że są one zgodne.

    [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
    [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]

4. Porównaj pierwszy znaleziony zakres ( `firstFind` ) z **Nothing**. Jeśli `firstFind` nie zawiera żadnej wartości, kod przechowuje znaleziony zakres ( `currentFind` ).

    [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
    [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]

5. Opuść pętlę, jeśli adres znalezionego zakresu jest zgodny z adresem pierwszego znalezionego zakresu.

    [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
    [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]

6. Ustaw wygląd znalezionego zakresu.

    [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
    [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]

7. Wykonaj inne wyszukiwanie.

    [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
    [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]

   Poniższy przykład przedstawia metodę Complete.

## <a name="example"></a>Przykład
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]

## <a name="see-also"></a>Zobacz też
- [Pracuj z zakresami](../vsto/working-with-ranges.md)
- [Instrukcje: Programowane stosowanie stylów do zakresów w skoroszytach](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Instrukcje: programowe odwoływanie się do zakresów arkusza w kodzie](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
