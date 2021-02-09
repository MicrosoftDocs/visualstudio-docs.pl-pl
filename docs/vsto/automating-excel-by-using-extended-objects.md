---
title: Automatyzowanie programu Excel za pomocą obiektów rozszerzonych
description: Dowiedz się, że podczas opracowywania rozwiązań programu Excel w programie Visual Studio można używać elementów hosta i kontrolek hosta w swoich rozwiązaniach.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], automating
- automation [Office development in Visual Studio], Excel
- host controls, Excel
- Excel [Office development in Visual Studio], host controls
- extended objects [Office development in Visual Studio], Excel
- host controls [Office development in Visual Studio], Excel
- automating Excel
- host items [Office development in Visual Studio], Excel
- controls [Office development in Visual Studio], Excel host controls
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e20251d695f36940fec3831d3fa78fd995a058e9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882495"
---
# <a name="automate-excel-by-using-extended-objects"></a>Automatyzowanie programu Excel za pomocą obiektów rozszerzonych
  Podczas opracowywania rozwiązań programu Excel w programie Visual Studio można używać *elementów hosta* i *kontrolek hosta* w swoich rozwiązaniach. Są to obiekty rozszerzające niektóre często używane obiekty w modelu obiektów programu Excel (czyli model obiektów, który jest udostępniany przez podstawowy zestaw międzyoperacyjny dla programu Excel), taki jak <xref:Microsoft.Office.Interop.Excel.Worksheet> obiekty i <xref:Microsoft.Office.Interop.Excel.Range> . Obiekty rozszerzone zachowują się jak obiekty programu Excel, na których się opierają, ale dodają do obiektów dodatkowe funkcje, takie jak nowe zdarzenia i możliwości powiązania danych.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Elementy hosta i formanty hosta są dostępne zarówno w dodatku programu VSTO, jak i na poziomie dokumentu, chociaż kontekst, w którym mogą być używane, różni się w zależności od typu rozwiązania. Aby uzyskać więcej informacji, zobacz [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md).

## <a name="excel-host-items"></a>Elementy hosta programu Excel
 Projekty programu Excel zapewniają dostęp do kilku elementów hosta:

- <xref:Microsoft.Office.Tools.Excel.Worksheet>. Ten element hosta zawiera i reprezentuje arkusz w projekcie. Pełni również funkcję kontenera dla formantów zarządzanych, w tym kontrolek hosta i kontrolek Windows Forms, i utrzymuje informacje o kontrolkach na jego powierzchni. Aby uzyskać więcej informacji, zobacz [arkusz elementów hosta](../vsto/worksheet-host-item.md).

- <xref:Microsoft.Office.Tools.Excel.Workbook>. Ten element hosta reprezentuje skoroszyt w projekcie i działa jako kontener dla składników, które są współużytkowane przez wszystkie arkusze w skoroszycie. Aby uzyskać więcej informacji, zobacz [skoroszyt element hosta](../vsto/workbook-host-item.md).

- <xref:Microsoft.Office.Tools.Excel.ChartSheet>. Ten element hosta znajduje się w arkuszu programu Excel, który zawiera tylko wykres i uwidacznia zdarzenia.

     Po dodaniu arkusza wykresu w czasie projektowania jako nowego arkusza w projekcie dostosowania Microsoft Office na poziomie dokumentu programu Excel program Visual Studio automatycznie tworzy <xref:Microsoft.Office.Tools.Excel.ChartSheet> element hosta.

     Mimo że <xref:Microsoft.Office.Tools.Excel.ChartSheet> element hosta jest arkuszem w programie Excel, nie można dodać żadnych formantów do arkusza wykresu. Jeśli chcesz mieć inne kontrolki arkusza z wykresem, nie używaj arkusza wykresu. Zamiast tego można umieścić wykres jako osadzony obiekt w arkuszu przy użyciu <xref:Microsoft.Office.Tools.Excel.Chart> kontrolki hosta. Aby uzyskać więcej informacji, zobacz [kontrolka wykres](../vsto/chart-control.md).

## <a name="excel-host-controls"></a>kontrolki hosta programu Excel
 Istnieje kilka kontrolek hosta dla programu Excel, które ułatwiają tworzenie, organizowanie i automatyzowanie skoroszytów oraz arkuszy. Te kontrolki hosta zapewniają zdarzenia i możliwości powiązań danych, których odpowiedniki w natywnym modelu obiektów programu Excel nie są dostępne.

 Aby uzyskać więcej informacji na temat kontrolek hosta, których można używać w projektach programu Excel, zobacz następujące tematy:

- [Kontrolka wykresu](../vsto/chart-control.md)

- [ListObject — formant](../vsto/listobject-control.md)

- [NamedRange — formant](../vsto/namedrange-control.md)

- [XmlMappedRange — formant](../vsto/xmlmappedrange-control.md)

## <a name="see-also"></a>Zobacz też
- [Instrukcje: wypełnianie kontrolek ListObject danymi](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Instrukcje: Dodawanie kontrolek wykresu do arkuszy](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Instrukcje: Dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Instrukcje: Dodawanie kontrolek NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Instrukcje: Dodawanie kontrolek XMLMappedRange do arkuszy](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Instrukcje: zmiana rozmiaru kontrolek NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Instrukcje: Zmienianie rozmiaru formantów ListObject](../vsto/how-to-resize-listobject-controls.md)
- [Instrukcje: sprawdzanie poprawności danych po dodaniu nowego wiersza do kontrolki ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)
- [Instrukcje: Mapowanie kolumn ListObject na dane](../vsto/how-to-map-listobject-columns-to-data.md)
- [Przewodnik: program dla zdarzeń kontrolki NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Rozwiń dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
