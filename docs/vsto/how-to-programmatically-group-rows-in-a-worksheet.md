---
title: 'Instrukcje: Programowane Grupowanie wierszy w arkuszu'
description: Dowiedz się, w jaki sposób można programowo grupować jeden lub więcej całych wierszy w programie Microsoft Excel przy użyciu formantu NamedRange lub natywnego obiektu zakresu programu Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 203ea7d17a02a224c290e5dd3c6070c06a1d26e4
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525713"
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>Instrukcje: Programowane Grupowanie wierszy w arkuszu
  Można grupować jeden lub więcej całych wierszy. Aby utworzyć grupę w arkuszu, użyj <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki lub natywnego obiektu zakresu programu Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Korzystanie z kontrolki NamedRange
 Jeśli dodasz <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę do projektu na poziomie dokumentu w czasie projektowania, możesz użyć kontrolki, aby programowo utworzyć grupę. W poniższym przykładzie przyjęto założenie, że istnieją trzy <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki w tym samym arkuszu: `data2001` , `data2002` , i `dataAll` . Każdy nazwany zakres odwołuje się do całego wiersza w arkuszu.

### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>Aby utworzyć grupę kontrolek NamedRange w arkuszu

1. Grupuj trzy nazwane zakresy, wywołując <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> metodę każdego zakresu. Ten kod musi być umieszczony w klasie arkusza, a nie w `ThisWorkbook` klasie.

     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]

    > [!NOTE]
    > Aby rozgrupować wiersze, wywołaj <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> metodę.

## <a name="use-native-excel-ranges"></a>Użyj natywnych zakresów programu Excel
 W kodzie założono, że masz trzy zakresy programu Excel o nazwach `data2001` , `data2002` i `dataAll` w arkuszu.

### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>Aby utworzyć grupę zakresów programu Excel w arkuszu

1. Grupuj trzy nazwane zakresy, wywołując <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> metodę każdego zakresu. W poniższym przykładzie przyjęto założenie, że istnieją trzy <xref:Microsoft.Office.Interop.Excel.Range> kontrolki o nazwach `data2001` , `data2002` i `dataAll` w tym samym arkuszu. Każdy nazwany zakres odwołuje się do całego wiersza w arkuszu.

     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]

    > [!NOTE]
    > Aby rozgrupować wiersze, wywołaj <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> metodę.

## <a name="see-also"></a>Zobacz też
- [Pracuj z arkuszami](../vsto/working-with-worksheets.md)
- [NamedRange — formant](../vsto/namedrange-control.md)
- [Instrukcje: Dodawanie kontrolek NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
