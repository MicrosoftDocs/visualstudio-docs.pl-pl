---
title: Programistyczne wprowadzanie przyrostowo zakresów danych
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Autofill method [Excel]
- filling ranges automatically
- ranges, automatically filling
- workbooks, filling ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 076381c93d11c2d13bdd89ea5c36c0039e15ef71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547475"
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>Instrukcje: Programowane automatyczne wypełnianie zakresów przyrostowo zmieniającymi się danymi
  <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>Metoda <xref:Microsoft.Office.Interop.Excel.Range> obiektu umożliwia wypełnienie zakresu w arkuszu z wartościami automatycznie. Najczęściej <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> Metoda jest używana do przechowywania przyrostowo rosnących lub malejących wartości w zakresie. Możesz określić zachowanie, dostarczając opcjonalną stałą z <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> wyliczenia.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Podczas korzystania z programu należy określić dwa zakresy <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> :

- Zakres, który wywołuje <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metodę, która określa punkt początkowy wypełnienia i zawiera początkową wartość.

- Zakres, który ma zostać wypełniony, przekazaną jako parametr do <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metody. Ten zakres docelowy musi zawierać zakres, który zawiera wartość początkową.

    > [!NOTE]
    > Nie można przekazać <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki zamiast <xref:Microsoft.Office.Interop.Excel.Range> . Aby uzyskać więcej informacji, zobacz Ograniczenia programowe [elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="example"></a>Przykład
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#49)]

## <a name="compile-the-code"></a>Kompiluj kod
 Pierwsza komórka zakresu, który ma zostać wypełniony, musi zawierać wartość początkową.

 Przykład wymaga wypełnienia trzech regionów:

- Kolumna B obejmuje pięć dni tygodnia. Jako wartość początkową wpisz **poniedziałek** w komórce B1.

- Kolumna C ma zawierać pięć miesięcy. Jako wartość początkową wpisz **styczeń** w komórce C1.

- Kolumna D ma zawierać serie liczb, które zwiększają się o dwa dla każdego wiersza. Dla początkowych wartości wpisz **4** w komórce D1 i **6** w komórce D2.

## <a name="see-also"></a>Zobacz też
- [Pracuj z zakresami](../vsto/working-with-ranges.md)
- [Instrukcje: programowe odwoływanie się do zakresów arkusza w kodzie](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Instrukcje: Programowane stosowanie stylów do zakresów w skoroszytach](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Instrukcje: Programowane uruchamianie obliczeń programu Excel](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
