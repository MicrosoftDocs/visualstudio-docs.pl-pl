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
ms.openlocfilehash: 864422aac695fbf474e6ed6b8cf6d765247eabf9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255308"
---
# <a name="chart-control"></a>Kontrolka wykresu
  <xref:Microsoft.Office.Tools.Excel.Chart>Kontrolka jest obiektem wykresu, który uwidacznia zdarzenia. Po dodaniu wykresu do arkusza program Visual Studio tworzy <xref:Microsoft.Office.Tools.Excel.Chart> obiekt, który można bezpośrednio programować bez konieczności przechodzenia do Microsoft Office modelu obiektów programu Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>Tworzenie kontrolki
 Możesz dodać <xref:Microsoft.Office.Tools.Excel.Chart> kontrolki do Microsoft Office arkusza programu Excel w czasie projektowania lub w czasie wykonywania w projekcie na poziomie dokumentu.

 Możesz dodać <xref:Microsoft.Office.Tools.Excel.Chart> kontrolki do arkusza w czasie wykonywania w dodatku narzędzi VSTO. Aby uzyskać więcej informacji, zobacz [jak: dodać kontrolki wykresu do arkuszy](../vsto/how-to-add-chart-controls-to-worksheets.md).

> [!NOTE]
> Obiekty wykresu utworzone dynamicznie nie są utrwalane w arkuszu jako kontrolki hosta, gdy arkusz jest zamknięty. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="formatting"></a>Formatowanie
 Wszystkie formatowania, które mogą być stosowane do elementu, <xref:Microsoft.Office.Interop.Excel.Chart> można również zastosować do <xref:Microsoft.Office.Tools.Excel.Chart> kontrolki. Obejmuje to obramowania, czcionki, typ wykresu, linie siatki, legendę i etykiety danych.

## <a name="events"></a>Zdarzenia
 Dla kontrolki dostępne są następujące zdarzenia <xref:Microsoft.Office.Tools.Excel.Chart> :

- <xref:Microsoft.Office.Tools.Excel.Chart.ActivateEvent>

- <xref:Microsoft.Office.Tools.Excel.Chart.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.Chart.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.Chart.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.Chart.Calculate>

- <xref:Microsoft.Office.Tools.Excel.Chart.Deactivate>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.Chart.DragOver>

- <xref:Microsoft.Office.Tools.Excel.Chart.DragPlot>

- <xref:Microsoft.Office.Tools.Excel.Chart.MouseDown>

- <xref:Microsoft.Office.Tools.Excel.Chart.MouseMove>

- <xref:Microsoft.Office.Tools.Excel.Chart.MouseUp>

- <xref:Microsoft.Office.Tools.Excel.Chart.Resize>

- <xref:Microsoft.Office.Tools.Excel.Chart.SelectEvent>

- <xref:Microsoft.Office.Tools.Excel.Chart.SeriesChange>

## <a name="see-also"></a>Zobacz też
- [Przykłady i przewodniki dotyczące programowania pakietu Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Rozwiń dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Instrukcje: Dodawanie kontrolek wykresu do arkuszy](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
