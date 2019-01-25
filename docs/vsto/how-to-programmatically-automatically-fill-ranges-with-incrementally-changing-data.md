---
title: 'Instrukcje: Programowe automatyczne wypełnienie zakresów przyrostowo zmieniającymi się danymi'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 94652358e18b18255a92444672cc59528cb0b2e2
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866497"
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>Instrukcje: Programowe automatyczne wypełnienie zakresów przyrostowo zmieniającymi się danymi
  <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> Metody <xref:Microsoft.Office.Interop.Excel.Range> obiektu umożliwia automatyczne wypełnianie zakres w arkuszu za pomocą wartości. W większości przypadków <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metoda jest używana do przechowywania przyrostowo zwiększenie lub zmniejszenie wartości w zakresie. Można określić zachowanie, podając opcjonalną stałą z <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> wyliczenia.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Należy określić dwa zakresy, korzystając z <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>:  
  
-   Zakres, który wywołuje <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metody, która określa początkowy punkt wypełnienia i zawiera wartość początkową.  
  
-   Zakres, który chcesz wypełnić, przekazana jako parametr do <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> metody. Ten zakres docelowy musi zawierać zakres, który zawiera wartość początkową.  
  
    > [!NOTE]  
    >  Nie można przekazać <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolować zamiast <xref:Microsoft.Office.Interop.Excel.Range>. Aby uzyskać więcej informacji, zobacz [ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#49)]  
  
## <a name="compile-the-code"></a>Skompilować kod  
 Pierwsza komórka zakres, który chcesz wypełnić musi zawierać wartość początkową.  
  
 Przykład wymaga wypełnienie trzech regionach:  
  
-   W kolumnie B jest obejmują pięć dni tygodnia. Początkowa wartość wpisz **poniedziałek** w komórce B1.  
  
-   Kolumna C jest uwzględnienie pięć miesięcy. Początkowa wartość wpisz **stycznia** w komórce C1.  
  
-   Kolumna D jest obejmują szereg numerów, zwiększając przez dwa dla każdego wiersza. Dla wartości początkowej, wpisz **4** w komórce D1 i **6** w komórce D2.  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z zakresami](../vsto/working-with-ranges.md)   
 [Instrukcje: Programowe odwoływanie do zakresów arkusza w kodzie](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Instrukcje: Programowe stosowanie stylów do zakresów arkusza w skoroszycie](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Instrukcje: Programowe wykonywanie obliczeń programu Excel](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
