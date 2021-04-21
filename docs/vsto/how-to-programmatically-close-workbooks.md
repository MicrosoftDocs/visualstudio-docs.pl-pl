---
title: '2019: Programowe zamykanie skoroszytów'
description: Dowiedz się, jak zamknąć aktywny skoroszyt lub określić skoroszyt do programowego zamknięcia.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d09cbff06b1bb7048316629b7b958ee299029ec8
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825267"
---
# <a name="how-to-programmatically-close-workbooks"></a>2019: Programowe zamykanie skoroszytów
  Możesz zamknąć aktywny skoroszyt lub określić skoroszyt do zamknięcia.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="close-the-active-workbook"></a>Zamykanie aktywnego skoroszytu
 Istnieją dwie procedury zamykania aktywnego skoroszytu: jedna dla dostosowań na poziomie dokumentu i jedna dla dodatków VSTO.

### <a name="to-close-the-active-workbook-in-a-document-level-customization"></a>Aby zamknąć aktywny skoroszyt w dostosowywaniu na poziomie dokumentu

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.Workbook.Close%2A> metodę , aby zamknąć skoroszyt skojarzony z dostosowaniem. Aby użyć poniższego przykładu kodu, uruchom go w `Sheet1` klasie w projekcie na poziomie dokumentu dla programu Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet3":::

### <a name="to-close-the-active-workbook-in-a-vsto-add-in"></a>Aby zamknąć aktywny skoroszyt w dodatku VSTO

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Workbook.Close%2A> metodę , aby zamknąć aktywny skoroszyt. Aby użyć poniższego przykładu kodu, uruchom go w klasie w projekcie `ThisAddIn` dodatku VSTO dla programu Excel.

:::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet1":::
:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet1":::

## <a name="close-a-workbook-that-you-specify-by-name"></a>Zamykanie skoroszytu, który został określony przez nazwę
 Sposób zamykania skoroszytu, który określasz według nazwy, jest taki sam dla dodatków VSTO i dostosowań na poziomie dokumentu.

### <a name="to-close-a-workbook-that-you-specify-by-name"></a>Aby zamknąć skoroszyt określony przez nazwę

1. Określ nazwę skoroszytu jako argument <xref:Microsoft.Office.Interop.Excel.Workbooks> kolekcji. W poniższym przykładzie kodu przyjęto założenie, że skoroszyt o **nazwie NewWorkbook** jest otwarty w programie Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet2":::

## <a name="see-also"></a>Zobacz też
- [Praca ze skoroszytami](../vsto/working-with-workbooks.md)
- [How to: Programmatically save workbooks (2017: Programowe zapisywanie skoroszytów)](../vsto/how-to-programmatically-save-workbooks.md)
- [How to: Programmatically open workbooks (2017: Programowe otwieranie skoroszytów)](../vsto/how-to-programmatically-open-workbooks.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
