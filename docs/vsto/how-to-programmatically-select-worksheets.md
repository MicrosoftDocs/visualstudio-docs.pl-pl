---
title: 'Instrukcje: Programowane Wybieranie arkuszy'
description: Program Visual Studio umożliwia programistyczne Wybieranie arkuszy programu Microsoft Excel z elementami hosta arkusza lub kolekcjami arkuszy skoroszytu programu Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, selecting
- Excel projects, selecting worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8a58c4cc53597714eb65010c2fdbb423dd20a35a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899394"
---
# <a name="how-to-programmatically-select-worksheets"></a>Instrukcje: Programowane Wybieranie arkuszy
  <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A>Metoda wybiera określony obiekt, który przenosi zaznaczenie użytkownika do nowego obiektu. Użyj <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> metody, jeśli chcesz przenieść fokus do obiektu bez zmiany wyboru użytkownika.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Jeśli chcesz wybrać istniejący arkusz w dodatku VSTO lub jeśli arkusz został utworzony w czasie wykonywania w dostosowaniu na poziomie dokumentu, musisz uzyskać do niego dostęp przy użyciu kolekcji programu Excel <xref:Microsoft.Office.Interop.Excel.Sheets> skoroszytu programu Excel. w przeciwnym razie możesz uzyskać bezpośredni dostęp do <xref:Microsoft.Office.Tools.Excel.Worksheet> elementu hosta.

## <a name="use-the-worksheet-host-item"></a>Użyj elementu hosta arkusza
 W dostosowaniu na poziomie dokumentu Dodaj następujący kod do *Arkusz1. vb* lub *Sheet1.cs*.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>Aby wybrać pierwszy arkusz w skoroszycie przy użyciu elementu hosta

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> metodę `Sheet1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#19)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Korzystanie z kolekcji arkuszy skoroszytu programu Excel
 Dostęp do arkusza przy użyciu kolekcji programu Excel <xref:Microsoft.Office.Interop.Excel.Sheets> .

### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Aby zaznaczyć pierwszy arkusz w skoroszycie przy użyciu kolekcji arkusze skoroszytu programu Excel

1. Wywołaj <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> metodę kolekcji, <xref:Microsoft.Office.Interop.Excel.Sheets> Aby zaznaczyć pierwszy arkusz aktywnego skoroszytu.

     [!code-csharp[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#20)]

## <a name="see-also"></a>Zobacz też
- [Pracuj z arkuszami](../vsto/working-with-worksheets.md)
- [Instrukcje: Programowane drukowanie arkuszy](../vsto/how-to-programmatically-print-worksheets.md)
- [Instrukcje: programowe usuwanie arkuszy ze skoroszytów](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Instrukcje: programowe ukrywanie arkuszy](../vsto/how-to-programmatically-hide-worksheets.md)
- [Instrukcje: programowe Włączanie ochrony arkuszy](../vsto/how-to-programmatically-protect-worksheets.md)
- [Element hosta arkusza](../vsto/worksheet-host-item.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
