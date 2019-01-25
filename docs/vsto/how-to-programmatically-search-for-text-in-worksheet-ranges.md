---
title: 'Instrukcje: Programowe wyszukiwanie tekstu w zakresach arkusza'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 37f59f2888fc5a572029f4c21116281df008706e
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868592"
---
# <a name="how-to-programmatically-search-for-text-in-worksheet-ranges"></a>Instrukcje: Programowe wyszukiwanie tekstu w zakresach arkusza
  <xref:Microsoft.Office.Interop.Excel.Range.Find%2A> Metody <xref:Microsoft.Office.Interop.Excel.Range> obiektu umożliwia wyszukiwanie tekstu w zakresie. Ten tekst może być również dowolne ciągi błędów, które mogą wystąpić w komórce arkusza, takich jak `#NULL!` lub `#VALUE!`. Aby uzyskać więcej informacji na temat ciągi błędów, zobacz [komórki wartości błędów](/office/vba/excel/Concepts/Cells-and-Ranges/cell-error-values).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Poniższy przykład wyszukuje zakres o nazwie `Fruits` i modyfikuje czcionki komórek zawierających wyraz "apples". Ta procedura korzysta również <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> metody, która korzysta z poprzednio ustawionych ustawienia, aby powtórzyć wyszukiwanie wyszukiwania. Określ komórki, po którym do wyszukiwania, a <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> obsługiwała pozostałe.  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Interop.Excel.Range.FindNext%2A> Metody wyszukiwania jest zawijany do początku zakresu wyszukiwania po osiągnięciu końca zakresu. Kod należy się upewnić, że wyszukiwanie nie otacza w pętli nieskończonej. Przykładowa procedura pokazuje, jak rozwiązać przy użyciu <xref:Microsoft.Office.Interop.Excel.Range.Address%2A> właściwości.  
  
 ![Link do wideo](../vsto/media/playvideo.gif "link do wideo") powiązane demonstracyjne wideo – zobacz [jak: Użyj metody Find, w dodatku programu Excel? ](http://go.microsoft.com/fwlink/?LinkID=130294).  
  
## <a name="to-search-for-text-in-a-worksheet-range"></a>Aby wyszukać tekst w zakresie arkusza  
  
1. Zadeklaruj zmienne do śledzenia całego zakresu, pierwszy znaleziony zakres i znaleziono bieżącego zakresu.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#58)]
    [!code-vb[Trin_VstcoreExcelAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#58)]  
  
2. Wyszukaj pierwsze dopasowanie, określając wszystkie parametry z wyjątkiem komórki do wyszukiwania po.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#59)]
    [!code-vb[Trin_VstcoreExcelAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#59)]  
  
3. Kontynuuj wyszukiwanie, tak długo, jak są zgodne.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#60)]
    [!code-vb[Trin_VstcoreExcelAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#60)]  
  
4. Porównaj pierwszego znaleziono zakresu (`firstFind`) do **nic**. Jeśli `firstFind` nie zawiera wartości, natychmiast magazynów kodu znaleziono zakresu (`currentFind`).  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#61)]
    [!code-vb[Trin_VstcoreExcelAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#61)]  
  
5. Wyjście z pętli, jeśli adres znaleziono zakresu jest zgodny z adresem, pierwszy znaleziony zakresu.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#62)]
    [!code-vb[Trin_VstcoreExcelAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#62)]  
  
6. Ustaw efekt znaleziono zakresu.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#63)]
    [!code-vb[Trin_VstcoreExcelAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#63)]  
  
7. Wykonaj innych kryteriów wyszukiwania.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#64)]
    [!code-vb[Trin_VstcoreExcelAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#64)]  
  
   Poniższy przykład pokazuje całą metodę.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#57)]
 [!code-vb[Trin_VstcoreExcelAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#57)]  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z zakresami](../vsto/working-with-ranges.md)   
 [Instrukcje: Programowe stosowanie stylów do zakresów arkusza w skoroszycie](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Instrukcje: Programowe odwoływanie do zakresów arkusza w kodzie](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
