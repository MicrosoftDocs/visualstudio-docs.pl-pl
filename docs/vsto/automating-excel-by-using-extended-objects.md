---
title: Automatyzowanie programu Excel za pomocą obiektów rozszerzonych
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 03ea220bf886352a05cc67bdd44a9504dcd86964
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56600857"
---
# <a name="automate-excel-by-using-extended-objects"></a>Automatyzowanie programu Excel za pomocą obiektów rozszerzonych
  Podczas opracowywania rozwiązań programu Excel w programie Visual Studio, możesz użyć *hostować elementy* i *kontrolki hosta*s w posiadanych rozwiązaniach. Są to obiekty, które rozszerzają niektóre powszechnie używane obiekty w modelu obiektów programu Excel (oznacza to, że model obiektu, który jest udostępniany przez podstawowy zestaw międzyoperacyjny dla programu Excel), takie jak <xref:Microsoft.Office.Interop.Excel.Worksheet> i <xref:Microsoft.Office.Interop.Excel.Range> obiektów. Obiekty rozszerzone zachowują się jak obiekty programu Excel, które są one oparte na, ale dodają dodatkowe funkcje, takie jak nowe zdarzenia i możliwości wiązania danych do obiektów.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Obiekty hosta i kontrolek hosta są dostępne w obu dodatku narzędzi VSTO dla programów dokumentu na poziomie dostosowania, mimo że kontekst, w którym mogą one być używane jest inna dla każdego typu rozwiązania. Aby uzyskać więcej informacji, zobacz [elementów, a omówienie kontrolek](../vsto/host-items-and-host-controls-overview.md).

## <a name="excel-host-items"></a>Obiekty hosta programu Excel
 Projekty programu Excel dają dostęp do kilku elementów hosta:

-   <xref:Microsoft.Office.Tools.Excel.Worksheet>. Ten element hosta zawiera i reprezentuje arkusza w projekcie. Działa również jako kontener dla formantów zarządzanych, w tym formanty hosta i kontrolek Windows Forms i utrzymuje informacji na temat formantów na powierzchni. Aby uzyskać więcej informacji, zobacz [element hosta arkusza](../vsto/worksheet-host-item.md).

-   <xref:Microsoft.Office.Tools.Excel.Workbook>. Ten element hosta skoroszytu w projekcie reprezentuje i działa jako kontener dla składników, które są współużytkowane przez wszystkich arkuszy w skoroszycie. Aby uzyskać więcej informacji, zobacz [element hosta skoroszytu](../vsto/workbook-host-item.md).

-   <xref:Microsoft.Office.Tools.Excel.ChartSheet>. Ten host elementu arkusza programu Excel zawierający tylko wykres, który przedstawia zdarzenia.

     Po dodaniu wykresu w arkuszu w czasie projektowania, jako nowy arkusz w projekcie dostosowania poziomu dokumentu Microsoft Office Excel, programu Visual Studio automatycznie tworzy <xref:Microsoft.Office.Tools.Excel.ChartSheet> element hosta.

     Mimo że <xref:Microsoft.Office.Tools.Excel.ChartSheet> element hosta ma postać arkusza programu Excel, nie można dodać formanty do arkusza wykresu. Jeśli chcesz mieć innych kontrolek w arkuszu za pomocą wykresu, nie należy używać wykresu w arkuszu. Zamiast tego umieść wykres jako obiekt osadzony w arkuszu za pomocą <xref:Microsoft.Office.Tools.Excel.Chart> kontrolki hosta. Aby uzyskać więcej informacji, zobacz [wykresu kontroli](../vsto/chart-control.md).

## <a name="excel-host-controls"></a>kontrolki hosta programu Excel
 Istnieje kilka hosta formantów dla programu Excel, które ułatwiają tworzenie, organizowanie i automatyzowanie skoroszyty i arkusze. Te kontrolki hosta zapewniają zdarzenia oraz funkcje wiązania danych, które nie mają ich odpowiedników w macierzystym modelu obiektów programu Excel.

 Aby uzyskać informacje o kontrolkach hosta, którego można używać w projektach programu Excel zobacz następujące tematy:

-   [Kontrolka wykresu](../vsto/chart-control.md)

-   [ListObject — formant](../vsto/listobject-control.md)

-   [Namedrange — formant](../vsto/namedrange-control.md)

-   [Xmlmappedrange — formant](../vsto/xmlmappedrange-control.md)

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Wypełnianie formantów ListObject danymi](../vsto/how-to-fill-listobject-controls-with-data.md)
- [Instrukcje: Dodawanie formantów wykresu do arkuszy](../vsto/how-to-add-chart-controls-to-worksheets.md)
- [Instrukcje: Dodawanie formantów ListObject do arkuszy](../vsto/how-to-add-listobject-controls-to-worksheets.md)
- [Instrukcje: Dodawanie formantów NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Instrukcje: Dodawanie formantów XMLMappedRange do arkuszy](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Instrukcje: Zmiana rozmiaru formantów NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Instrukcje: Zmiana rozmiaru formantów ListObject](../vsto/how-to-resize-listobject-controls.md)
- [Instrukcje: Walidacja danych po dodaniu nowego rzędu do kontrolki ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md)
- [Instrukcje: Mapowanie kolumn ListObject do danych](../vsto/how-to-map-listobject-columns-to-data.md)
- [Przewodnik: Program w odniesieniu do zdarzeń formantu NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
