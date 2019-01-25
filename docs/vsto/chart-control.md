---
title: Kontrolka wykresu
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.ExcelChart
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], events
- Chart control [Office development in Visual Studio]
- Chart control [Office development in Visual Studio], data binding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f31cfeab76018658ada9cc449af287cfca4abf4f
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867055"
---
# <a name="chart-control"></a>Kontrolka wykresu
  <xref:Microsoft.Office.Tools.Excel.Chart> Kontroli jest obiektem wykresu, który opisuje zdarzenia. Po dodaniu wykresu w arkuszu programu Visual Studio tworzy <xref:Microsoft.Office.Tools.Excel.Chart> obiektu, że można programować względem bezpośrednio, bez konieczności przechodzenia z modelu obiektów programu Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="create-the-control"></a>Tworzenie formantu  
 Możesz dodać <xref:Microsoft.Office.Tools.Excel.Chart> kontrolek do arkusza programu Microsoft Office Excel, w czasie projektowania lub w czasie wykonywania w projekcie na poziomie dokumentu.  
  
 Możesz dodać <xref:Microsoft.Office.Tools.Excel.Chart> kontrolek do arkusza w czasie wykonywania w dodatku VSTO. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie formantów wykresu do arkuszy](../vsto/how-to-add-chart-controls-to-worksheets.md).  
  
> [!NOTE]  
>  Obiekty dynamicznie utworzoną wykresu nie są zachowywane w arkuszu zgodnie z kontrolki hosta po zamknięciu arkusza. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w środowisku uruchomieniowym](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="formatting"></a>Formatowanie  
 Wszystkie formatowania, który można zastosować do <xref:Microsoft.Office.Interop.Excel.Chart> również będą stosowane do <xref:Microsoft.Office.Tools.Excel.Chart> kontroli. W tym obramowania, czcionki, typ wykresu, linie siatki, legendy i etykiety danych.  
  
## <a name="events"></a>Zdarzenia  
 Następujące zdarzenia są dostępne dla <xref:Microsoft.Office.Tools.Excel.Chart> sterowania:  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.ActivateEvent>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Calculate>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Deactivate>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.DragOver>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.DragPlot>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseDown>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseMove>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseUp>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Resize>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.SelectEvent>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.SeriesChange>  
  
## <a name="see-also"></a>Zobacz także  
 [Office development ― przykłady i przewodniki](../vsto/office-development-samples-and-walkthroughs.md)   
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)   
 [Instrukcje: Dodawanie formantów wykresu do arkuszy](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
