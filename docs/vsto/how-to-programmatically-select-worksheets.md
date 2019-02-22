---
title: 'Instrukcje: Programowe Zaznaczanie arkuszy'
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
ms.openlocfilehash: ee6e5d89bea21f58c8c5b1cc59f7c7f248630742
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56602653"
---
# <a name="how-to-programmatically-select-worksheets"></a>Instrukcje: Programowe Zaznaczanie arkuszy
  <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> Metoda wybiera określony obiekt, który przenosi wybranych przez użytkownika do nowego obiektu. Użyj <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> metody, aby przenieść fokus do obiektu bez wprowadzania zmian w wybranych przez użytkownika.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Jeśli chcesz wybrać istniejącego arkusza w dodatku narzędzi VSTO dla programów lub jeśli arkusz został utworzony w czasie wykonywania w dostosowaniu na poziomie dokumentu, należy uruchomić je przy użyciu programu Excel <xref:Microsoft.Office.Interop.Excel.Sheets> kolekcji skoroszytu programu Excel; w przeciwnym razie możesz uzyskać dostęp <xref:Microsoft.Office.Tools.Excel.Worksheet>bezpośrednio element hosta.

## <a name="use-the-worksheet-host-item"></a>Użyj element hosta arkusza
 W dostosowaniu na poziomie dokumentu, Dodaj następujący kod do *Sheet1.vb* lub *Sheet1.cs*.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>Aby wybrać pierwszego arkusza w skoroszycie, przy użyciu elementu hosta

1.  Wywołaj <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> metody `Sheet1`.

     [!code-csharp[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreExcelAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#19)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Korzystać z kolekcji arkuszy skoroszytu programu Excel
 Dostęp do arkusza za pomocą programu Excel <xref:Microsoft.Office.Interop.Excel.Sheets> kolekcji.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Aby wybrać pierwszego arkusza w skoroszycie, przy użyciu kolekcji arkuszy skoroszytu programu Excel

1.  Wywołaj <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> metody <xref:Microsoft.Office.Interop.Excel.Sheets> kolekcji, aby zaznaczyć pierwszy arkusz aktywnym skoroszycie.

     [!code-csharp[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreExcelAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#20)]

## <a name="see-also"></a>Zobacz także
- [Praca z arkuszami](../vsto/working-with-worksheets.md)
- [Instrukcje: Programowe Drukowanie arkuszy](../vsto/how-to-programmatically-print-worksheets.md)
- [Instrukcje: Programowe usuwanie arkuszy ze skoroszytu](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Instrukcje: Programowe ukrywanie arkuszy](../vsto/how-to-programmatically-hide-worksheets.md)
- [Instrukcje: Programowe Włączanie ochrony arkuszy](../vsto/how-to-programmatically-protect-worksheets.md)
- [Element hosta arkusza](../vsto/worksheet-host-item.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
- [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)
