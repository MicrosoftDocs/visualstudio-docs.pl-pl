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
ms.openlocfilehash: e2b5b5d246e1033148bc199da6e7d2bdfb7aa9b3
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254713"
---
# <a name="namedrange-control"></a>NamedRange — formant
  <xref:Microsoft.Office.Tools.Excel.NamedRange> Kontrolka jest zakresem, który ma unikatową nazwę, uwidacznia zdarzenia i może być powiązany z danymi. Aby uzyskać więcej informacji, zobacz [model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="create-the-control"></a>Tworzenie kontrolki
 Możesz dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki do Microsoft Office arkusza programu Excel w czasie projektowania lub w czasie wykonywania w projektach na poziomie dokumentu.

 Możesz dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki do arkusza w czasie wykonywania w dodatku narzędzi VSTO. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie kontrolek NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md).

> [!NOTE]
> Domyślnie utworzone nazwane zakresy nie są utrwalane w arkuszu jako kontrolki hosta, gdy arkusz jest zamknięty. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).

 <xref:Microsoft.Office.Tools.Excel.NamedRange>kontrolki mogą zawierać tylko zakresy w określonych arkuszach. <xref:Microsoft.Office.Tools.Excel.NamedRange>kontrolki nie mogą zawierać nazw względnych, które mają zastosowanie do wszystkich arkuszy i nie mogą zawierać zakresów obejmujących dwa lub więcej arkuszy w skoroszycie (zakresy trójwymiarowe).

## <a name="bind-data-to-the-control"></a>Powiąż dane z kontrolką
 Nazwany zakres będzie wyglądał jako dobry kandydat dla złożonego powiązania danych, ponieważ może zawierać wiele komórek; Jednak zakres jest tylko kolekcją komórek, która nie może być łatwo mapowana na określoną kolumnę z zestawu danych. W związku <xref:Microsoft.Office.Tools.Excel.NamedRange> z tym formanty obsługują tylko proste powiązanie danych. <xref:Microsoft.Office.Tools.Excel.ListObject> Kontrolka może służyć do tworzenia złożonych powiązań danych. Aby uzyskać więcej informacji, zobacz [formant ListObject](../vsto/listobject-control.md).

 Formant można powiązać ze źródłem danych <xref:System.Windows.Forms.Control.DataBindings%2A> przy użyciu właściwości. <xref:Microsoft.Office.Tools.Excel.NamedRange> Domyślną właściwością <xref:Microsoft.Office.Tools.Excel.NamedRange> powiązania danych formantu jest <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A>.

 Jeśli dane w powiązanym zestawie danych są aktualizowane za pomocą dowolnego mechanizmu <xref:Microsoft.Office.Tools.Excel.NamedRange> , formant odzwierciedla zmiany.

## <a name="formatting"></a>Formatowanie
 Formatowanie, które można zastosować do elementu <xref:Microsoft.Office.Interop.Excel.Range> , można zastosować <xref:Microsoft.Office.Tools.Excel.NamedRange> do kontrolki. Obejmuje to obramowania, czcionki, formaty liczb i style.

## <a name="rename-the-control"></a>Zmiana nazwy kontrolki
 Po dodaniu <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki do arkusza z **przybornika**program Visual Studio automatycznie generuje nazwę dla kontrolki. Nazwę można zmienić w oknie **Właściwości** .

## <a name="events"></a>Zdarzenia
 Dla <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki dostępne są następujące zdarzenia:

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
- [Przykłady i przewodniki dotyczące programowania pakietu Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Rozwiń dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Instrukcje: Dodawanie kontrolek NamedRange do arkuszy](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Instrukcje: Zmień rozmiar kontrolek NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Przewodnik: Program przed zdarzeniami kontrolki NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
