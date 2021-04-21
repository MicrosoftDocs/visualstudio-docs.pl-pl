---
title: 'How to: Programmatically open workbooks (2017: Programowe otwieranie skoroszytów)'
description: Dowiedz się, jak za pomocą Visual Studio programowo otworzyć skoroszyt programu Microsoft Excel lub pracować z istniejącym skoroszytem.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4dba79b1b0eea03ca3aae23e98fb93e6ef776d80
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824786"
---
# <a name="how-to-programmatically-open-workbooks"></a>How to: Programmatically open workbooks (2017: Programowe otwieranie skoroszytów)
  Kolekcja w programie Microsoft Office Excel umożliwia pracę ze wszystkimi otwartymi skoroszytami <xref:Microsoft.Office.Interop.Excel.Workbooks> i otwieranie skoroszytów.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-open-an-existing-workbook"></a>Aby otworzyć istniejący skoroszyt

1. Użyj <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> metody <xref:Microsoft.Office.Interop.Excel.Workbooks> kolekcji , przekazując ścieżkę do skoroszytu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet2":::

## <a name="compile-the-code"></a>Kompilowanie kodu
 Ten przykład kodu wymaga następujących czynności:

- Skoroszyt o nazwie `YourWorkbook.xls` musi istnieć w katalogu o nazwie `Test` na dysku C.

## <a name="see-also"></a>Zobacz też
- [Praca ze skoroszytami](../vsto/working-with-workbooks.md)
- [How to: Programowe otwieranie plików tekstowych jako skoroszytów](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)
- [Tworzyć programowo nowe skoroszyty](../vsto/how-to-programmatically-create-new-workbooks.md)
- [How to: Programowe zapisywanie skoroszytów](../vsto/how-to-programmatically-save-workbooks.md)
- [How to: Programmatically close workbooks (2017: Programowe zamykanie skoroszytów)](../vsto/how-to-programmatically-close-workbooks.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
