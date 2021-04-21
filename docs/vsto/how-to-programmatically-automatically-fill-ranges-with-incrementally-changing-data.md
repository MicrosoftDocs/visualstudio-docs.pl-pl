---
title: Automatyczne uzupełnianie przyrostowo zmieniających się zakresów danych programowo
description: Dowiedz się, jak metoda autowypełniania obiektu Range umożliwia automatyczne wypełnianie zakresu w arkuszu wartościami.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 615331181b9402e0d2062142ad266bdd41dca4eb
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824942"
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>Jak programowo automatycznie wypełniać zakresy przyrostowo zmieniającymi się danymi
  Metoda obiektu umożliwia automatyczne wypełnienie zakresu w <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> <xref:Microsoft.Office.Interop.Excel.Range> arkuszu wartościami. Najczęściej metoda jest używana do przechowywania przyrostowo rosnących lub <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> malejących wartości w zakresie. Zachowanie można określić, określając opcjonalną stałą z <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> wyliczenia.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 W przypadku korzystania z programu należy określić dwa <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> zakresy:

- Zakres, który wywołuje metodę , która określa punkt początkowy wypełnienia i <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> zawiera wartość początkową.

- Zakres, który chcesz wypełnić, przekazany jako parametr do <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metody . Ten zakres docelowy musi zawierać zakres, który zawiera wartość początkową.

    > [!NOTE]
    > Nie można przekazać <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki w miejsce <xref:Microsoft.Office.Interop.Excel.Range> . Aby uzyskać więcej informacji, zobacz [Programowe ograniczenia elementów hosta i kontrolek hosta.](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)

## <a name="example"></a>Przykład
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet49":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet49":::

## <a name="compile-the-code"></a>Kompilowanie kodu
 Pierwsza komórka zakresu, który chcesz wypełnić, musi zawierać wartość początkową.

 W tym przykładzie wymagane jest wypełnienie trzech regionów:

- Kolumna B ma zawierać pięć dni roboczych. Jako wartość początkową wpisz **Monday** w komórce B1.

- Kolumna C ma zawierać pięć miesięcy. Jako wartość początkową wpisz **January** w komórce C1.

- Kolumna D ma zawierać serię liczb, która zwiększa się o dwie wartości dla każdego wiersza. Dla wartości początkowych wpisz **4** w komórce D1 i **6** w komórce D2.

## <a name="see-also"></a>Zobacz też
- [Praca z zakresami](../vsto/working-with-ranges.md)
- [Jak programowo odwoływać się do zakresów arkusza w kodzie](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [How to: Programowe stosowanie stylów do zakresów w skoroszytach](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Jak programowo uruchamiać obliczenia programu Excel](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
