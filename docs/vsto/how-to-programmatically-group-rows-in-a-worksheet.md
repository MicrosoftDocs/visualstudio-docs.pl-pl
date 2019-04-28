---
title: 'Instrukcje: Programowe grupowanie wierszy w arkuszu'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, creating groups
- groups, creating in worksheets
- ranges, creating groups
- worksheets, clearing groups
- groups
- groups [Office development in Visual Studio], clearing in worksheets
- worksheets, ungrouping rows and columns
- rows [Office development in Visual Studio], ungrouping
- columns [Office development in Visual Studio], ungrouping
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 269ecdb67fe58a5ad2aff6af63ba6ea45647811a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412616"
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>Instrukcje: Programowe grupowanie wierszy w arkuszu
  Można grupować jedną lub więcej całych wierszy. Aby utworzyć grupę w arkuszu, należy użyć <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu lub natywnego obiektu zakresu programu Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Używanie formantu NamedRange
 Jeśli dodasz <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli na poziomie dokumentu projekt w czasie projektowania, możesz użyć formantu, aby programowo utworzyć grupę. W poniższym przykładzie założono, że dostępne są trzy <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolek na tym samym arkuszu: `data2001`, `data2002`, i `dataAll`. Każdy z zakresów, o nazwie odwołuje się do całego wiersza w arkuszu.

### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>Aby utworzyć grupę kontrolek NamedRange do arkusza

1. Grupa trzech nazwane zakresy, wywołując <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> metoda każdego zakresu. Ten kod muszą być umieszczone w klasie arkusza, nie w `ThisWorkbook` klasy.

     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]

    > [!NOTE]
    > Aby rozgrupować wierszy, należy wywołać <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> metody.

## <a name="use-native-excel-ranges"></a>Użyj natywnego zakresów programu Excel
 W kodzie założono, że masz trzy zakresy programu Excel o nazwie `data2001`, `data2002`, i `dataAll` w arkuszu.

### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>Aby utworzyć grupę zakresów programu Excel w arkuszu

1. Grupa trzech nazwane zakresy, wywołując <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> metoda każdego zakresu. W poniższym przykładzie założono, że dostępne są trzy <xref:Microsoft.Office.Interop.Excel.Range> kontrolki o nazwie `data2001`, `data2002`, i `dataAll` na tym samym arkuszu. Każdy z zakresów, o nazwie odwołuje się do całego wiersza w arkuszu.

     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]

    > [!NOTE]
    > Aby rozgrupować wierszy, należy wywołać <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> metody.

## <a name="see-also"></a>Zobacz także
- [Praca z arkuszami](../vsto/working-with-worksheets.md)
- [Namedrange — formant](../vsto/namedrange-control.md)
- [Instrukcje: Dodawanie formantów NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
