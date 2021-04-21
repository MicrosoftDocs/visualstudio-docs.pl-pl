---
title: 'How to: Programmatically save workbooks (2017: Programowe zapisywanie skoroszytów)'
description: Programowe zapisywanie skoroszytów programu Microsoft Excel bez zmiany ścieżki i zapisywanie kopii skoroszytu bez modyfikowania otwartego skoroszytu w pamięci.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, saving in XML format
- workbooks, saving
- workbooks, saving backup copies
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4559d098a80a1dfd8f1d3f5c2c21cbebc992fcb7
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828985"
---
# <a name="how-to-programmatically-save-workbooks"></a>How to: Programmatically save workbooks (2017: Programowe zapisywanie skoroszytów)
  Istnieje kilka sposobów zapisywania skoroszytu. Skoroszyt można zapisać bez zmiany ścieżki. Jeśli skoroszyt nie został zapisany wcześniej, należy zapisać skoroszyt, określając ścieżkę. Bez jawnej ścieżki program Microsoft Office Excel zapisuje plik w bieżącym folderze o nazwie nadanej podczas jego tworzenia. Możesz również zapisać kopię skoroszytu bez modyfikowania otwartego skoroszytu w pamięci.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="save-a-workbook-without-changing-the-path"></a>Zapisywanie skoroszytu bez zmiany ścieżki

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Aby zapisać skoroszyt skojarzony z dostosowaniem na poziomie dokumentu

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> metodę `ThisWorkbook` klasy .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet4":::

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Aby zapisać aktywny skoroszyt w dodatku VSTO

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A> metodę , aby zapisać aktywny skoroszyt. Aby użyć poniższego przykładu kodu, uruchom go w klasie w projekcie `ThisAddIn` dodatku VSTO dla programu Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet3":::

## <a name="save-a-workbook-with-a-new-path"></a>Zapisywanie skoroszytu z nową ścieżką
 Określony skoroszyt można zapisać w nowej lokalizacji lub pod nową nazwą, opcjonalnie określając format pliku, hasło, tryb dostępu i inne.

> [!NOTE]
> Przed zapisaniem skoroszytu z nową ścieżką możesz ustawić dla właściwości wartość False, ponieważ zapisywanie w niektórych formatach <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A> wymaga interakcji.  Ustawienie tej właściwości na **False powoduje,** że program Excel będzie używać wszystkich wartości domyślnych.

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Aby zapisać skoroszyt skojarzony z dostosowaniem na poziomie dokumentu

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> metodę `ThisWorkbook` klasy . Aby użyć poniższego przykładu kodu, uruchom go w `ThisWorkbook` klasie .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet5":::

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Aby zapisać aktywny skoroszyt w dodatku VSTO

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A> metodę , aby zapisać aktywny skoroszyt w nowej ścieżce. Aby użyć poniższego przykładu kodu, uruchom go w `ThisAddIn` klasie w projekcie dodatku VSTO dla programu Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet4":::

## <a name="save-a-copy-of-the-workbook"></a>Zapisywanie kopii skoroszytu
 Kopię skoroszytu można zapisać w pliku bez modyfikowania otwartego skoroszytu w pamięci. Jest to przydatne, gdy chcesz utworzyć kopię zapasową bez modyfikowania lokalizacji skoroszytu.

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Aby zapisać skoroszyt skojarzony z dostosowaniem na poziomie dokumentu

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> metodę `ThisWorkbook` klasy . Aby użyć poniższego przykładu kodu, uruchom go w `ThisWorkbook` klasie .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet6":::

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Aby zapisać aktywny skoroszyt w dodatku VSTO

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A> metodę , aby zapisać kopię aktywnego skoroszytu. Aby użyć poniższego przykładu kodu, uruchom go w `ThisAddIn` klasie w projekcie dodatku VSTO dla programu Excel.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet5":::

## <a name="robust-programming"></a>Niezawodne programowanie
 Interaktywne anulowanie dowolnej metody zapisu lub kopiowania skoroszytu zgłasza błąd w czasie działania w kodzie. Jeśli na przykład procedura wywołuje metodę , ale nie wyłącza monitów z programu Excel, a użytkownik klika przycisk Anuluj po wyświetleniu monitu, program Excel zgłasza błąd <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> w czasie działania. 

## <a name="see-also"></a>Zobacz też
- [Praca ze skoroszytami](../vsto/working-with-workbooks.md)
- [Element hosta skoroszytu](../vsto/workbook-host-item.md)
- [How to: Programmatically close workbooks (2017: Programowe zamykanie skoroszytów)](../vsto/how-to-programmatically-close-workbooks.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
