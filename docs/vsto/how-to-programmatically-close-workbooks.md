---
title: 'Instrukcje: programowe zamykanie skoroszytów'
description: Dowiedz się, jak zamknąć aktywny skoroszyt lub można określić skoroszyt do zamykania programistycznie.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, closing
- Excel [Office development in Visual Studio], closing workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 13b487054e4e8a12c2479ddfc167ca0b8e90285a
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846067"
---
# <a name="how-to-programmatically-close-workbooks"></a>Instrukcje: programowe zamykanie skoroszytów
  Możesz zamknąć aktywny skoroszyt lub określić skoroszyt do zamknięcia.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="close-the-active-workbook"></a>Zamknij aktywny skoroszyt
 Istnieją dwie procedury zamykania aktywnego skoroszytu: jeden dla dostosowań na poziomie dokumentu i jeden dla dodatków narzędzi VSTO.

### <a name="to-close-the-active-workbook-in-a-document-level-customization"></a>Aby zamknąć aktywny skoroszyt w dostosowaniu na poziomie dokumentu

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.Workbook.Close%2A> metodę, aby zamknąć skoroszyt skojarzony z dostosowaniem. Aby użyć następującego przykładu kodu, należy uruchomić go w `Sheet1` klasie w projekcie na poziomie dokumentu dla programu Excel.

     [!code-csharp[Trin_VstcoreExcelAutomation#3](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomation#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#3)]

### <a name="to-close-the-active-workbook-in-a-vsto-add-in"></a>Aby zamknąć aktywny skoroszyt w dodatku narzędzi VSTO

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Workbook.Close%2A> metodę, aby zamknąć aktywny skoroszyt. Aby użyć następującego przykładu kodu, uruchom go w `ThisAddIn` klasie w projekcie dodatku VSTO dla programu Excel.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#1)]

## <a name="close-a-workbook-that-you-specify-by-name"></a>Zamknij skoroszyt określony przez nazwę
 Sposób zamykania skoroszytu określonego za pomocą nazwy jest taki sam dla dodatków narzędzi VSTO i dostosowań na poziomie dokumentu.

### <a name="to-close-a-workbook-that-you-specify-by-name"></a>Aby zamknąć skoroszyt, który określisz według nazwy

1. Określ nazwę skoroszytu jako argument <xref:Microsoft.Office.Interop.Excel.Workbooks> kolekcji. W poniższym przykładzie kodu założono, że skoroszyt o nazwie **NewWorkbook** jest otwarty w programie Excel.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#2)]

## <a name="see-also"></a>Zobacz także
- [Pracuj ze skoroszytami](../vsto/working-with-workbooks.md)
- [Instrukcje: programowe zapisywanie skoroszytów](../vsto/how-to-programmatically-save-workbooks.md)
- [Instrukcje: Programowane otwieranie skoroszytów](../vsto/how-to-programmatically-open-workbooks.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
