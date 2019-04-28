---
title: Xmlmappedrange — formant
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLMappedRange control, data binding
- XMLMappedRange control
- XMLMappedRange control, events
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cde5489d970de02afbce28ab9c60c677ab199c84
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62810760"
---
# <a name="xmlmappedrange-control"></a>Xmlmappedrange — formant
  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Formant jest zakres, który jest tworzony tylko wtedy, gdy element schematu niepowtarzający jest mapowany na komórkę w programie Microsoft Office Excel. Na przykład, gdy `maxOccurs` atrybutu elementu schematu jest równa 1. Gdy program Visual Studio utworzy zakresu XML mapowane, można programować względem go bezpośrednio, bez konieczności przechodzenia z modelu obiektów programu Excel. Usuwać można tylko <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> sterowania w programie Excel, gdy jest usuwany mapowanie elementu.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 ![Link do wideo](../vsto/media/playvideo.gif "link do wideo") powiązane demonstracyjne wideo – zobacz [jak: Używanie mapowania XML w programie Excel? ](http://go.microsoft.com/fwlink/?LinkID=130288).

## <a name="bind-data-to-the-control"></a>Wiązanie danych do kontrolki
 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Kontrolka obsługuje powiązanie danych jednego pola (proste powiązanie danych). <xref:Microsoft.Office.Tools.Excel.ListObject> Kontroli może obsługuje złożone powiązanie danych i jest tworzony automatycznie podczas powtarzający się element schematu jest mapowany na komórkę. Aby uzyskać więcej informacji, zobacz [kontrolki ListObject](../vsto/listobject-control.md).

 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> Kontrolka jest powiązana z źródła danych przy użyciu <xref:System.Windows.Forms.Control.DataBindings%2A> właściwości. Gdy <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> zostanie dodany do komórki arkusza, Visual Studio automatycznie generuje zestaw danych na podstawie danych w mapowanych komórek i powiąże formant z tego zestawu danych. Domyślne właściwości powiązania danych z <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> jest <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>.

 Jeśli dane w zestawie danych powiązane są aktualizowane przy użyciu dowolnego mechanizmu <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> kontroli zmiany zostały uwzględnione.

## <a name="formatting"></a>Formatowanie
 Można zastosować, to samo formatowanie <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> formant, który można zastosować do <xref:Microsoft.Office.Interop.Excel.Range>. W tym obramowania, czcionki, format liczb i stylów.

## <a name="events"></a>Zdarzenia
 Zdarzenia dostępne dla <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> kontrola to:

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Change>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Selected>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Deselected>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.SelectionChange>

## <a name="see-also"></a>Zobacz także
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Instrukcje: Dodawanie formantów XMLMappedRange do arkuszy](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Instrukcje: Mapowanie schematów z arkuszami w programie Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
