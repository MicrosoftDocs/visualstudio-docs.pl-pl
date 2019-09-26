---
title: 'Instrukcje: Programowe Wybieranie arkuszy'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, selecting
- Excel projects, selecting worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 20ebc8fea14b3dc52c802543f97318ec7fae7529
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255630"
---
# <a name="how-to-programmatically-select-worksheets"></a>Porady: Programowe Wybieranie arkuszy
  <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> Metoda wybiera określony obiekt, który przenosi zaznaczenie użytkownika do nowego obiektu. Użyj metody <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> , jeśli chcesz przenieść fokus do obiektu bez zmiany wyboru użytkownika.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Jeśli chcesz wybrać istniejący arkusz w dodatku VSTO lub jeśli arkusz został utworzony w czasie wykonywania w dostosowaniu na poziomie dokumentu, musisz uzyskać do niego dostęp przy użyciu kolekcji programu Excel <xref:Microsoft.Office.Interop.Excel.Sheets> skoroszytu programu Excel. w przeciwnym razie możesz uzyskać dostęp do <xref:Microsoft.Office.Tools.Excel.Worksheet>element hosta bezpośrednio.

## <a name="use-the-worksheet-host-item"></a>Użyj elementu hosta arkusza
 W dostosowaniu na poziomie dokumentu Dodaj następujący kod do *Arkusz1. vb* lub *Sheet1.cs*.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>Aby wybrać pierwszy arkusz w skoroszycie przy użyciu elementu hosta

1. Wywołaj`Sheet1`metodę <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> .

     [!code-csharp[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#19)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Korzystanie z kolekcji arkuszy skoroszytu programu Excel
 Dostęp do arkusza przy użyciu kolekcji programu <xref:Microsoft.Office.Interop.Excel.Sheets> Excel.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Aby zaznaczyć pierwszy arkusz w skoroszycie przy użyciu kolekcji arkusze skoroszytu programu Excel

1. Wywołaj <xref:Microsoft.Office.Interop.Excel.Sheets> metodę kolekcji, aby zaznaczyć pierwszy arkusz aktywnego skoroszytu. <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A>

     [!code-csharp[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#20)]

## <a name="see-also"></a>Zobacz także
- [Pracuj z arkuszami](../vsto/working-with-worksheets.md)
- [Instrukcje: Programowe drukowanie arkuszy](../vsto/how-to-programmatically-print-worksheets.md)
- [Instrukcje: Programowe usuwanie arkuszy ze skoroszytów](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Instrukcje: Programowe ukrywanie arkuszy](../vsto/how-to-programmatically-hide-worksheets.md)
- [Instrukcje: Programowe Włączanie ochrony arkuszy](../vsto/how-to-programmatically-protect-worksheets.md)
- [Element hosta arkusza](../vsto/worksheet-host-item.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
