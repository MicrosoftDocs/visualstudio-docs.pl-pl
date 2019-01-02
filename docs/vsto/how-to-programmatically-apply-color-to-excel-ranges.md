---
title: 'Instrukcje: Programowe stosowanie koloru do zakresów programu Excel'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- color, Excel ranges
- ranges, applying color
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4cd8a9528b0bcd360fd00f700172899f1480d0ed
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868027"
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>Instrukcje: Programowe stosowanie koloru do zakresów programu Excel
  Aby zastosować kolor tekstu w zakres komórek, należy użyć <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu lub natywnego obiektu zakresu programu Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-a-namedrange-control"></a>Używanie formantu NamedRange  
 Ten przykład dotyczy dostosowywania na poziomie dokumentu.  
  
### <a name="to-apply-color-to-a-namedrange-control"></a>Aby zastosować kolor z kontrolką NamedRange  
  
1.  Utwórz <xref:Microsoft.Office.Tools.Excel.NamedRange> formant w komórce A1.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#65)]
     [!code-vb[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#65)]  
  
2.  Ustawianie koloru tekstu w <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#66)]
     [!code-vb[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#66)]  
  
## <a name="use-native-excel-ranges"></a>Użyj natywnego zakresów programu Excel  
  
### <a name="to-apply-color-to-a-native-excel-range-object"></a>Aby zastosować kolor do natywnego obiektu zakresu programu Excel  
  
1.  Utwórz zakres od komórki A1, a następnie ustaw kolor tekstu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#67)]
     [!code-vb[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#67)]  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z zakresami](../vsto/working-with-ranges.md)   
 [Namedrange — formant](../vsto/namedrange-control.md)   
 [Instrukcje: Programowe stosowanie stylów do zakresów arkusza w skoroszycie](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Instrukcje: Programowe odwoływanie do zakresów arkusza w kodzie](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
