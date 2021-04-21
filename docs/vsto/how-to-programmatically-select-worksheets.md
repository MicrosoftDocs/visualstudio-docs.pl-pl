---
title: Jak programowo wybierać arkusze
description: Użyj Visual Studio, aby programowo wybierać arkusze programu Microsoft Excel z elementem hosta arkusza lub kolekcją arkuszy skoroszytu programu Excel.
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
ms.openlocfilehash: 04f410292fff686e7604e917e6c3fa7002c65273
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826255"
---
# <a name="how-to-programmatically-select-worksheets"></a>Jak programowo wybierać arkusze
  Metoda wybiera określony obiekt, który przenosi wybór użytkownika <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> do nowego obiektu. Użyj metody , jeśli chcesz skupić się na obiekcie bez zmiany <xref:Microsoft.Office.Tools.Excel.Worksheet.Activate%2A> wyboru użytkownika.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Jeśli chcesz wybrać istniejący arkusz w dodatku VSTO lub jeśli arkusz został utworzony w czasie uruchamiania w dostosowywaniu na poziomie dokumentu, musisz uzyskać do niego dostęp przy użyciu kolekcji programu Excel skoroszytu programu Excel. W przeciwnym razie możesz uzyskać bezpośredni dostęp do elementu <xref:Microsoft.Office.Interop.Excel.Sheets> <xref:Microsoft.Office.Tools.Excel.Worksheet> hosta.

## <a name="use-the-worksheet-host-item"></a>Używanie elementu hosta arkusza
 W dostosowywaniu na poziomie dokumentu dodaj następujący kod do *pliku Sheet1.vb* lub *Sheet1.cs.*

### <a name="to-select-the-first-worksheet-in-a-workbook-using-a-host-item"></a>Aby wybrać pierwszy arkusz w skoroszycie przy użyciu elementu hosta

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.Worksheet.Select%2A> metodę `Sheet1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet19":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet19":::

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Używanie kolekcji arkuszy skoroszytu programu Excel
 Uzyskiwanie dostępu do arkusza przy użyciu kolekcji programu <xref:Microsoft.Office.Interop.Excel.Sheets> Excel.

### <a name="to-select-the-first-worksheet-in-a-workbook-using-the-sheets-collection-of-the-excel-workbook"></a>Aby wybrać pierwszy arkusz w skoroszycie przy użyciu kolekcji Arkusze skoroszytu programu Excel

1. Wywołaj <xref:Microsoft.Office.Interop.Excel.Sheets.Select%2A> metodę <xref:Microsoft.Office.Interop.Excel.Sheets> kolekcji, aby wybrać pierwszy arkusz aktywnego skoroszytu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet20":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet20":::

## <a name="see-also"></a>Zobacz też
- [Praca z arkuszami](../vsto/working-with-worksheets.md)
- [How to: Programmatically print arkusze](../vsto/how-to-programmatically-print-worksheets.md)
- [How to: Programowe usuwanie arkuszy ze skoroszytów](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [How to: Programmatically hide arkusze](../vsto/how-to-programmatically-hide-worksheets.md)
- [Jak programowo chronić arkusze](../vsto/how-to-programmatically-protect-worksheets.md)
- [Element hosta arkusza](../vsto/worksheet-host-item.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Programowe ograniczenia elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
