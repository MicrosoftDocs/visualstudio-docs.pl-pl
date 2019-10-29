---
title: XmlMappedRange — formant
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
ms.openlocfilehash: 01417d9c08491edc882f7f758bb36e6184500e52
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985360"
---
# <a name="xmlmappedrange-control"></a>XmlMappedRange — formant
  Formant <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> jest zakresem, który jest tworzony tylko wtedy, gdy niepowtarzany element schematu jest mapowany na komórkę w programie Microsoft Office Excel. Na przykład, gdy atrybut `maxOccurs` elementu schematu jest równy 1. Po utworzeniu mapowanego zakresu XML przez program Visual Studio można bezpośrednio programować bez konieczności przechodzenia przez model obiektów programu Excel. Po usunięciu mapowania elementu można usunąć tylko formant <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> w programie Excel.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="bind-data-to-the-control"></a>Powiąż dane z kontrolką
 Formant <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> obsługuje powiązanie z pojedynczym polem danych (prostym wiązaniem danych). Formant <xref:Microsoft.Office.Tools.Excel.ListObject> może obsługiwać złożone powiązanie danych i jest tworzony automatycznie, gdy powtarzalny element schematu jest mapowany na komórkę. Aby uzyskać więcej informacji, zobacz [formant ListObject](../vsto/listobject-control.md).

 Formant <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> jest powiązany ze źródłem danych przy użyciu właściwości <xref:System.Windows.Forms.Control.DataBindings%2A>. Gdy <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> zostanie dodana do komórki arkusza, program Visual Studio automatycznie generuje zestaw danych na podstawie danych w mapowanych komórkach i wiąże formant z tym zestawem danych. Domyślna właściwość powiązania danych <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> jest <xref:Microsoft.Office.Tools.Excel.XmlMappedRange.Value2%2A>.

 Jeśli dane w zestawie danych powiązanych są aktualizowane za pomocą dowolnego mechanizmu, formant <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> odzwierciedla zmiany.

## <a name="formatting"></a>Formatowanie
 To samo formatowanie można zastosować do kontrolki <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>, którą można zastosować do <xref:Microsoft.Office.Interop.Excel.Range>. Dotyczy to również obramowań, czcionek, formatu liczb i stylów.

## <a name="events"></a>Zdarzenia
 Zdarzenia dostępne dla formantu <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> są następujące:

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
- [Instrukcje: Dodawanie kontrolek XMLMappedRange do arkuszy](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)
- [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Instrukcje: mapowanie schematów do arkuszy w programie Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
