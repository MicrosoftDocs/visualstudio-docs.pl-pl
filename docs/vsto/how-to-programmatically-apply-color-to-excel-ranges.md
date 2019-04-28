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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 56ecbfcdaf22132f63df1ecf5eadba97dee426af
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62817276"
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>Instrukcje: Programowe stosowanie koloru do zakresów programu Excel
  Aby zastosować kolor tekstu w zakres komórek, należy użyć <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu lub natywnego obiektu zakresu programu Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Używanie formantu NamedRange
 Ten przykład dotyczy dostosowywania na poziomie dokumentu.

### <a name="to-apply-color-to-a-namedrange-control"></a>Aby zastosować kolor z kontrolką NamedRange

1. Utwórz <xref:Microsoft.Office.Tools.Excel.NamedRange> formant w komórce A1.

     [!code-csharp[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#65)]
     [!code-vb[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#65)]

2. Ustawianie koloru tekstu w <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli.

     [!code-csharp[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#66)]
     [!code-vb[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#66)]

## <a name="use-native-excel-ranges"></a>Użyj natywnego zakresów programu Excel

### <a name="to-apply-color-to-a-native-excel-range-object"></a>Aby zastosować kolor do natywnego obiektu zakresu programu Excel

1. Utwórz zakres od komórki A1, a następnie ustaw kolor tekstu.

     [!code-csharp[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#67)]
     [!code-vb[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#67)]

## <a name="see-also"></a>Zobacz także
- [Praca z zakresami](../vsto/working-with-ranges.md)
- [Namedrange — formant](../vsto/namedrange-control.md)
- [Instrukcje: Programowe stosowanie stylów do zakresów arkusza w skoroszycie](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Instrukcje: Programowe odwoływanie do zakresów arkusza w kodzie](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
