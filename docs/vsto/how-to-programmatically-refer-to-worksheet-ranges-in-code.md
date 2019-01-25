---
title: 'Instrukcje: Programowe odwoływanie do zakresów arkusza w kodzie'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2b1a1f0f6c37bca2d545e3b689bc72c553ffc6c6
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867146"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Instrukcje: Programowe odwoływanie do zakresów arkusza w kodzie
  Użyj podobnej do odwoływania się do zawartości <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu lub natywnego obiektu zakresu programu Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-a-namedrange-control"></a>Używanie formantu NamedRange  
 W poniższym przykładzie dodano <xref:Microsoft.Office.Tools.Excel.NamedRange> do arkusza, a następnie dodaje tekst do komórki w zakresie.  
  
### <a name="to-refer-to-a-namedrange-control"></a>Aby odwołać się do kontrolki NamedRange  
  
1.  Ciąg do przypisywania <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> właściwość <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli. Ten kod muszą być umieszczone w klasie arkusza, nie w `ThisWorkbook` klasy.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]  
  
## <a name="use-native-excel-ranges"></a>Użyj natywnego zakresów programu Excel  
 Poniższy przykład dodaje macierzysty zakresu programu Excel w arkuszu, a następnie dodaje tekst do komórki w zakresie.  
  
### <a name="to-refer-to-a-native-range-object"></a>Aby odwołać się do obiektu zakresu natywne  
  
1.  Ciąg do przypisywania <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> właściwości zakresu.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z zakresami](../vsto/working-with-ranges.md)   
 [Instrukcje: Programowe sprawdzanie pisowni w arkuszach](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Instrukcje: Programowe stosowanie stylów do zakresów arkusza w skoroszycie](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Instrukcje: Programowe automatyczne wypełnienie zakresów przyrostowo zmieniającymi się danymi](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)   
 [Instrukcje: Programowe wyszukiwanie tekstu w zakresach arkusza](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)   
 [Namedrange — formant](../vsto/namedrange-control.md)   
 [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
