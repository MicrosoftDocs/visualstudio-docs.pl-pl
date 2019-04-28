---
title: NamedRange — formant
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.Range
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, named
- NamedRange control, events
- NamedRange control, data binding
- NamedRange control
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8dd8627c4e9baaa790a5d97a8021220a820356fb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442433"
---
# <a name="namedrange-control"></a>NamedRange — formant
  <xref:Microsoft.Office.Tools.Excel.NamedRange> Kontrolka jest w zakresie, który ma unikatową nazwę, udostępnia zdarzenia i może być powiązana z danymi. Aby uzyskać więcej informacji, zobacz [model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>Tworzenie formantu
 Możesz dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolek do arkusza programu Microsoft Office Excel, w czasie projektowania lub w czasie wykonywania w projektach na poziomie dokumentu.

 Możesz dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolek do arkusza w czasie wykonywania w dodatku VSTO. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie formantów NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md).

> [!NOTE]
> Domyślnie przez utworzony dynamicznie nazwane zakresy nie są zachowywane w arkuszu zgodnie z kontrolki hosta po zamknięciu arkusza. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w środowisku uruchomieniowym](../vsto/adding-controls-to-office-documents-at-run-time.md).

 <xref:Microsoft.Office.Tools.Excel.NamedRange> Formanty może zawierać wyłącznie z zakresów określonych arkuszy. <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki nie mogą mieć względne nazwy, które są stosowane do wszystkich arkuszy, a nie składają się one z zakresów, które rozciągają się dwa lub więcej arkuszy w skoroszycie (3-zakresami).

## <a name="bind-data-to-the-control"></a>Wiązanie danych do kontrolki
 Nazwany zakres wydają się być dobrym kandydatem do złożonych danych powiązania, ponieważ może mieć wiele komórek. jednak zakres jest tylko kolekcja komórki, które nie łatwo można mapować do określonej kolumny zestawu danych. W związku z tym <xref:Microsoft.Office.Tools.Excel.NamedRange> formantów obsługują tylko proste powiązanie danych. <xref:Microsoft.Office.Tools.Excel.ListObject> Kontroli może służyć do złożone powiązanie danych. Aby uzyskać więcej informacji, zobacz [kontrolki ListObject](../vsto/listobject-control.md).

 <xref:Microsoft.Office.Tools.Excel.NamedRange> Kontroli można powiązać źródła danych przy użyciu <xref:System.Windows.Forms.Control.DataBindings%2A> właściwości. Domyślne właściwości powiązania danych z <xref:Microsoft.Office.Tools.Excel.NamedRange> formant jest <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>.

 Jeśli dane w zestawie danych powiązane są aktualizowane przy użyciu dowolnego mechanizmu <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli zmiany zostały uwzględnione.

## <a name="formatting"></a>Formatowanie
 Formatowanie, które mogą być stosowane do <xref:Microsoft.Office.Interop.Excel.Range> mogą być stosowane do <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli. W tym obramowania, czcionki, formaty liczb i stylów.

## <a name="rename-the-control"></a>Zmień nazwę kontrolki
 Po dodaniu <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu do arkusza z **przybornika**, program Visual Studio automatycznie generuje nazwę dla formantu. Możesz zmienić nazwę w **właściwości** okna.

## <a name="events"></a>Zdarzenia
 Następujące zdarzenia są dostępne dla <xref:Microsoft.Office.Tools.Excel.NamedRange> sterowania:

- <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeRightClick>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.Deselected>

- <xref:System.ComponentModel.Component.Disposed>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected>

- <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>

## <a name="see-also"></a>Zobacz także
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Office development ― przykłady i przewodniki](../vsto/office-development-samples-and-walkthroughs.md)
- [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Instrukcje: Dodawanie formantów NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Instrukcje: Zmiana rozmiaru formantów NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Przewodnik: Program w odniesieniu do zdarzeń formantu NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
