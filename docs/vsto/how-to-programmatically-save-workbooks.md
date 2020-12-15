---
title: 'Instrukcje: programowe zapisywanie skoroszytów'
description: Programowo zapisuj skoroszyty programu Microsoft Excel bez zmiany ścieżki i Zapisz kopię skoroszytu bez modyfikowania otwartych skoroszytów w pamięci.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dbc228a703d6c9224fda545a93132ccb45c94b0f
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524626"
---
# <a name="how-to-programmatically-save-workbooks"></a>Instrukcje: programowe zapisywanie skoroszytów
  Istnieje kilka sposobów zapisywania skoroszytu. Skoroszyt można zapisać bez zmiany ścieżki. Jeśli skoroszyt nie został wcześniej zapisany, Zapisz go, określając ścieżkę. Bez ścieżki jawnej Microsoft Office program Excel zapisuje plik w bieżącym folderze z nazwą, która została podaną podczas tworzenia. Możesz również zapisać kopię skoroszytu bez modyfikowania otwartego skoroszytu w pamięci.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="save-a-workbook-without-changing-the-path"></a>Zapisz skoroszyt bez zmiany ścieżki

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Aby zapisać skoroszyt skojarzony z dostosowywaniem na poziomie dokumentu

1. Wywoływanie <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> metody `ThisWorkbook` klasy.

     [!code-csharp[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#4)]

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Aby zapisać aktywny skoroszyt w dodatku narzędzi VSTO

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A> metodę, aby zapisać aktywny skoroszyt. Aby użyć następującego przykładu kodu, uruchom go w `ThisAddIn` klasie w projekcie dodatku VSTO dla programu Excel.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#3)]

## <a name="save-a-workbook-with-a-new-path"></a>Zapisz skoroszyt z nową ścieżką
 Określony skoroszyt można zapisać w nowej lokalizacji lub z nową nazwą, opcjonalnie określając format pliku, hasło, tryb dostępu i inne.

> [!NOTE]
> Możesz chcieć ustawić <xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A> Właściwość na **false** przed zapisaniem skoroszytu z nową ścieżką, ponieważ zapis w niektórych formatach wymaga interakcji. Ustawienie dla tej właściwości **wartości false** powoduje, że program Excel będzie używać wszystkich wartości domyślnych.

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Aby zapisać skoroszyt skojarzony z dostosowywaniem na poziomie dokumentu

1. Wywoływanie <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> metody `ThisWorkbook` klasy. Aby użyć następującego przykładu kodu, uruchom go w `ThisWorkbook` klasie.

     [!code-csharp[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#5)]

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Aby zapisać aktywny skoroszyt w dodatku narzędzi VSTO

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A> metodę, aby zapisać aktywny skoroszyt w nowej ścieżce. Aby użyć następującego przykładu kodu, uruchom go w `ThisAddIn` klasie w projekcie dodatku VSTO dla programu Excel.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#4)]

## <a name="save-a-copy-of-the-workbook"></a>Zapisz kopię skoroszytu
 Kopię skoroszytu można zapisać do pliku bez modyfikowania otwartych skoroszytów w pamięci. Jest to przydatne, gdy chcesz utworzyć kopię zapasową bez modyfikowania lokalizacji skoroszytu.

### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>Aby zapisać skoroszyt skojarzony z dostosowywaniem na poziomie dokumentu

1. Wywoływanie <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> metody `ThisWorkbook` klasy. Aby użyć następującego przykładu kodu, uruchom go w `ThisWorkbook` klasie.

     [!code-csharp[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#6)]

### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>Aby zapisać aktywny skoroszyt w dodatku narzędzi VSTO

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A> metodę, aby zapisać kopię aktywnego skoroszytu. Aby użyć następującego przykładu kodu, uruchom go w `ThisAddIn` klasie w projekcie dodatku VSTO dla programu Excel.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#5)]

## <a name="robust-programming"></a>Niezawodne programowanie
 Interaktywnie anuluje wszystkie metody, które zapisują lub kopiują skoroszyt zgłaszają błąd czasu wykonywania w kodzie. Na przykład jeśli procedura wywołuje <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> metodę, ale nie wyłącza monitów z programu Excel, a użytkownik kliknie przycisk **Anuluj** po wyświetleniu monitu, program Excel zgłosi błąd czasu wykonywania.

## <a name="see-also"></a>Zobacz też
- [Pracuj ze skoroszytami](../vsto/working-with-workbooks.md)
- [Element hosta skoroszytu](../vsto/workbook-host-item.md)
- [Instrukcje: programowe zamykanie skoroszytów](../vsto/how-to-programmatically-close-workbooks.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
