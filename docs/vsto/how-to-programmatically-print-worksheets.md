---
title: 'How to: Programmatically print arkusze'
description: Dowiedz się, jak używać Visual Studio do programowego drukowania dowolnego arkusza w skoroszycie programu Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- worksheets, printing
- print preview, worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 129493f726967776aa669eb92f6e912ed9c1b11b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827152"
---
# <a name="how-to-programmatically-print-worksheets"></a>How to: Programmatically print arkusze

Możesz wydrukować dowolny arkusz w skoroszycie.

[!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="print-a-worksheet-in-a-document-level-customization"></a>Drukowanie arkusza w dostosowywaniu na poziomie dokumentu

### <a name="to-print-a-worksheet"></a>Aby wydrukować arkusz

1. Wywołaj metodę , zażądaj dwóch kopii i wyświetl `PrintOut` podgląd dokumentu przed `Sheet1` wydrukowaniem.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet22":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet22":::

   Metoda <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> umożliwia wyświetlenie określonego obiektu w oknie **Podgląd** wydruku. W poniższym kodzie przyjęto założenie, że masz <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta o nazwie `Sheet1` .

### <a name="to-preview-a-page-before-printing"></a>Aby wyświetlić podgląd strony przed drukowaniem

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> metodę arkusza.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet23":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet23":::

## <a name="print-a-worksheet-in-a-vsto-add-in"></a>Drukowanie arkusza w dodatku VSTO

### <a name="to-print-a-worksheet"></a>Aby wydrukować arkusz

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> metodę aktywnego arkusza, zażądaj dwóch kopii i wyświetl podgląd dokumentu przed wydrukowaniem.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet14":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet14":::

   Metoda <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> umożliwia wyświetlenie określonego obiektu w oknie **Podgląd** wydruku.

### <a name="to-preview-a-page-before-printing"></a>Aby wyświetlić podgląd strony przed drukowaniem

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> metodę aktywnego arkusza.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet15":::

## <a name="see-also"></a>Zobacz też

- [Praca z arkuszami](../vsto/working-with-worksheets.md)
- [Jak programowo sprawdzać pisownię w arkuszach](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Element hosta arkusza](../vsto/worksheet-host-item.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
