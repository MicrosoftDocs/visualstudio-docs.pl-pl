---
title: 'Instrukcje: Programowe zapisywanie skoroszytów'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, saving in XML format
- workbooks, saving
- workbooks, saving backup copies
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0ac57569802bbab5317f59e5311e4871a6e74ba1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60093062"
---
# <a name="how-to-programmatically-save-workbooks"></a>Instrukcje: Programowe zapisywanie skoroszytów
  Istnieje kilka sposobów, aby zapisać skoroszyt. Skoroszyt programu bez wprowadzania zmian w ścieżce. Jeśli skoroszyt nie zostały zapisane, zanim należy zapisać skoroszyt, określając ścieżkę. Bez jawnej ścieżki program Microsoft Office Excel zapisuje plik w bieżącym folderze o nazwie, które podano podczas jej tworzenia. Można również zapisać kopię skoroszytu bez modyfikowania Otwórz skoroszyt w pamięci.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="save-a-workbook-without-changing-the-path"></a>Zapisz skoroszyt bez wprowadzania zmian w ścieżce

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Aby zapisać skoroszyt, skojarzone z dostosowywania poziomie dokumentu

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> metody `ThisWorkbook` klasy.

     [!code-csharp[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#4)]

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Aby zapisać aktywnym skoroszycie w dodatku narzędzi VSTO

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A> metodę, aby zapisać skoroszyt active. Aby użyć w poniższym przykładzie kodu, należy uruchomić go `ThisAddIn` klasy w projekcie dodatku narzędzi VSTO dla programu Excel.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#3)]

## <a name="save-a-workbook-with-a-new-path"></a>Zapisz skoroszyt za pomocą nowej ścieżki
 Można zapisać skoroszyt określony do nowej lokalizacji lub pod nową nazwą, opcjonalnie określając format pliku, hasła, tryb dostępu i inne.

> [!NOTE]
>  Warto ustawić <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A> właściwości **False** przed zapisanie skoroszytu przy użyciu nowej ścieżki, ponieważ zapisywanie w niektóre formaty wymaga interakcji. Ustawienie tej właściwości na **False** powoduje, że program Excel użyj wszystkich ustawień domyślnych.

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Aby zapisać skoroszyt, skojarzone z dostosowywania poziomie dokumentu

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> metody `ThisWorkbook` klasy. Aby użyć w poniższym przykładzie kodu, należy uruchomić go `ThisWorkbook` klasy.

     [!code-csharp[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#5)]

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Aby zapisać aktywnym skoroszycie w dodatku narzędzi VSTO

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A> metodę, aby zapisać skoroszyt active nową ścieżkę. Aby użyć w poniższym przykładzie kodu, należy uruchomić go `ThisAddIn` klasy w projekcie dodatku narzędzi VSTO dla programu Excel.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#4)]

## <a name="save-a-copy-of-the-workbook"></a>Zapisz kopię skoroszytu
 Można zapisać kopię skoroszytu do pliku bez modyfikowania Otwórz skoroszyt w pamięci. Jest to przydatne, gdy chcesz utworzyć kopię zapasową bez modyfikowania lokalizacji skoroszytu.

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Aby zapisać skoroszyt, skojarzone z dostosowywania poziomie dokumentu

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> metody `ThisWorkbook` klasy. Aby użyć w poniższym przykładzie kodu, należy uruchomić go `ThisWorkbook` klasy.

     [!code-csharp[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#6)]

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Aby zapisać aktywnym skoroszycie w dodatku narzędzi VSTO

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A> metodę, aby zapisać kopię aktywnego skoroszytu. Aby użyć w poniższym przykładzie kodu, należy uruchomić go `ThisAddIn` klasy w projekcie dodatku narzędzi VSTO dla programu Excel.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#5)]

## <a name="robust-programming"></a>Skuteczne programowanie
 Interaktywnie anulowanie dowolnej z metod, które zapisać lub skopiować skoroszyt zgłasza błąd w czasie wykonywania w kodzie. Na przykład, jeśli procedura wymaga <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> metoda, ale ma nie Wyłącz monity w programie Excel i użytkownik klika polecenie **anulować** po wyświetleniu monitu Excel zgłasza błąd w czasie wykonywania.

## <a name="see-also"></a>Zobacz także
- [Praca ze skoroszytami](../vsto/working-with-workbooks.md)
- [Element hosta skoroszytu](../vsto/workbook-host-item.md)
- [Instrukcje: Programowe zamykanie skoroszytów](../vsto/how-to-programmatically-close-workbooks.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
- [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)
