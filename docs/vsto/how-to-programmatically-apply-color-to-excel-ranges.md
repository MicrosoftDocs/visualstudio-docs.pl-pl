---
title: 'Instrukcje: Programowane stosowanie koloru do zakresów programu Excel'
description: Dowiedz się, że aby zastosować kolor do tekstu w zakresie komórek, użyj kontrolki NamedRange lub natywnego obiektu zakresu programu Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 63a38bb4fb6f8f8ab35b9e1104a1b93d6d757446
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848004"
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>Instrukcje: Programowane stosowanie koloru do zakresów programu Excel
  Aby zastosować kolor do tekstu w obrębie zakresu komórek, użyj <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki lub natywnego obiektu zakresu programu Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Korzystanie z kontrolki NamedRange
 Ten przykład dotyczy dostosowywania na poziomie dokumentu.

### <a name="to-apply-color-to-a-namedrange-control"></a>Aby zastosować kolor do kontrolki NamedRange

1. Utwórz <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę w komórce A1.

     [!code-csharp[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#65)]
     [!code-vb[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#65)]

2. Ustaw kolor tekstu w <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolce.

     [!code-csharp[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#66)]
     [!code-vb[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#66)]

## <a name="use-native-excel-ranges"></a>Użyj natywnych zakresów programu Excel

### <a name="to-apply-color-to-a-native-excel-range-object"></a>Aby zastosować kolor do natywnego obiektu zakresu programu Excel

1. Utwórz zakres w komórce A1, a następnie ustaw kolor tekstu.

     [!code-csharp[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#67)]
     [!code-vb[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#67)]

## <a name="see-also"></a>Zobacz także
- [Pracuj z zakresami](../vsto/working-with-ranges.md)
- [NamedRange — formant](../vsto/namedrange-control.md)
- [Instrukcje: Programowane stosowanie stylów do zakresów w skoroszytach](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Instrukcje: programowe odwoływanie się do zakresów arkusza w kodzie](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
