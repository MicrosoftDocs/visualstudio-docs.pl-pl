---
title: Model obiektów programu Excel — Omówienie
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Worksheet object
- Range object
- object models [Office development in Visual Studio], Excel
- object models [Office development in Visual Studio], Office
- Workbook class
- objects [Office development in Visual Studio], Office object models
- Excel object model
- Office object models
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cf81dea230c2cfc33eb19ca001d8c9ed06b0489c
ms.sourcegitcommit: 77ef1dcc71057cd5fdc4733ff0cb6085bd6113e0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/06/2019
ms.locfileid: "73661845"
---
# <a name="excel-object-model-overview"></a>Model obiektów programu Excel — Omówienie
  Do tworzenia rozwiązań, które korzystają z programu Microsoft Office Excel, można korzystać z obiektów dostarczonych przez model obiektów programu Excel. W tym temacie przedstawiono najważniejsze obiekty:

- <xref:Microsoft.Office.Interop.Excel.Application>

- <xref:Microsoft.Office.Interop.Excel.Workbook>

- <xref:Microsoft.Office.Interop.Excel.Worksheet>

- <xref:Microsoft.Office.Interop.Excel.Range>

  [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

  Model obiektów jest ściśle opisany w interfejsie użytkownika. Obiekt <xref:Microsoft.Office.Interop.Excel.Application> reprezentuje całą aplikację, a każdy obiekt <xref:Microsoft.Office.Interop.Excel.Workbook> zawiera kolekcję obiektów `Worksheet`. Z tego miejsca główne streszczenie reprezentujące komórki jest obiektem <xref:Microsoft.Office.Interop.Excel.Range>, który umożliwia współpracę z poszczególnymi komórkami lub grupami komórek.

  Poza modelem obiektów programu Excel, projekty pakietu Office w programie Visual Studio udostępniają *elementy hosta* i *formanty hosta* , które poszerzają niektóre obiekty w modelu obiektów programu Excel. Elementy hosta i formanty hosta zachowują się jak obiekty programu Excel, które rozszerzają, ale również mają dodatkowe funkcje, takie jak możliwości powiązań danych i dodatkowe zdarzenia. Aby uzyskać więcej informacji, zobacz [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md) i [elementów hosta oraz kontrolek hosta](../vsto/host-items-and-host-controls-overview.md).

  Ten temat zawiera krótkie omówienie modelu obiektów programu Excel. Aby uzyskać więcej informacji o zasobach, w których można dowiedzieć się więcej na temat całego modelu obiektów programu Excel, zobacz [Korzystanie z dokumentacji modelu obiektów programu Excel](#ExcelOMDocumentation).

## <a name="access-objects-in-an-excel-project"></a>Dostęp do obiektów w projekcie programu Excel
 Podczas tworzenia nowego projektu dodatku VSTO dla programu Excel program Visual Studio automatycznie tworzy plik kodu *ThisAddIn. vb* lub *ThisAddIn.cs* . Dostęp do obiektu aplikacji można uzyskać za pomocą `Me.Application` lub `this.Application`.

 Podczas tworzenia nowego projektu na poziomie dokumentu dla programu Excel można utworzyć nowy skoroszyt programu Excel lub projekt szablonu programu Excel. Program Visual Studio automatycznie tworzy następujące pliki kodu w nowym projekcie programu Excel dla projektów skoroszyt i szablon.

|Visual Basic|C#|
|------------------|---------|
|ThisWorkbook. vb|ThisWorkbook.cs|
|Arkusz1. vb|Sheet1.cs|
|Arkusz Arkusz2. vb|Sheet2.cs|
|Sheet3. vb|Sheet3.cs|

 Można użyć klasy `Globals` w projekcie, aby uzyskać dostęp do `ThisWorkbook`, `Sheet1`, `Sheet2`lub `Sheet3` spoza odpowiedniej klasy. Aby uzyskać więcej informacji, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md). Poniższy przykład wywołuje metodę <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> `Sheet1` niezależnie od tego, czy kod znajduje się w jednej z klas `Sheet`*n* lub klasy `ThisWorkbook`.

 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]

 Ponieważ dane w dokumencie programu Excel są wysoce strukturalne, model obiektów jest hierarchiczny i prosty. Program Excel zawiera setki obiektów, z którymi można korzystać, ale możesz uzyskać dobry początek na modelu obiektów, skupiając się na małym podzbiorze dostępnych obiektów. Te obiekty obejmują następujące cztery:

- Aplikacja

- skoroszyt

- arkusz

- Zakres

  Większość pracy odbywa się z centrami programu Excel wokół tych czterech obiektów i ich członków.

### <a name="application-object"></a>Obiekt aplikacji
 Obiekt <xref:Microsoft.Office.Interop.Excel.Application> programu Excel reprezentuje samą aplikację programu Excel. Obiekt <xref:Microsoft.Office.Interop.Excel.Application> umożliwia uzyskanie dużej ilości informacji o działającej aplikacji, opcjach zastosowanych do tego wystąpienia oraz bieżących obiektów użytkownika otwartych w ramach tego wystąpienia.

> [!NOTE]
> Nie należy ustawiać właściwości <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> obiektu <xref:Microsoft.Office.Interop.Excel.Application> w programie Excel na **wartość false**. Ustawienie dla tej właściwości wartości false uniemożliwia programowi Excel podnoszenie jakichkolwiek zdarzeń, w tym zdarzeń kontrolek hosta.

### <a name="workbook-object"></a>Obiekt skoroszytu
 Obiekt <xref:Microsoft.Office.Interop.Excel.Workbook> reprezentuje pojedynczy skoroszyt w aplikacji programu Excel.

 Narzędzia programistyczne pakietu Office w programie Visual Studio zwiększają <xref:Microsoft.Office.Interop.Excel.Workbook> obiektu, dostarczając typ <xref:Microsoft.Office.Tools.Excel.Workbook>. Ten typ zapewnia dostęp do wszystkich funkcji obiektu <xref:Microsoft.Office.Interop.Excel.Workbook>. Aby uzyskać więcej informacji, zobacz [skoroszyt element hosta](../vsto/workbook-host-item.md).

### <a name="worksheet-object"></a>obiekt arkusza
 Obiekt <xref:Microsoft.Office.Interop.Excel.Worksheet> jest członkiem kolekcji <xref:Microsoft.Office.Interop.Excel.Worksheets>. Wiele właściwości, metod i zdarzeń <xref:Microsoft.Office.Interop.Excel.Worksheet> są identyczne lub podobne do elementów członkowskich dostarczonych przez <xref:Microsoft.Office.Interop.Excel.Application> lub <xref:Microsoft.Office.Interop.Excel.Workbook> obiektów.

 Program Excel udostępnia <xref:Microsoft.Office.Interop.Excel.Sheets>ą kolekcję jako właściwość obiektu <xref:Microsoft.Office.Interop.Excel.Workbook>. Każdy element członkowski kolekcji <xref:Microsoft.Office.Interop.Excel.Sheets> jest obiektem <xref:Microsoft.Office.Interop.Excel.Worksheet> lub <xref:Microsoft.Office.Interop.Excel.Chart>.

 Narzędzia programistyczne pakietu Office w programie Visual Studio zwiększają <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektu, dostarczając typ <xref:Microsoft.Office.Tools.Excel.Worksheet>. Ten typ zapewnia dostęp do wszystkich funkcji obiektu <xref:Microsoft.Office.Interop.Excel.Worksheet>, a także nowe funkcje, takie jak możliwość hostowania zarządzanych formantów i obsługi nowych zdarzeń. Aby uzyskać więcej informacji, zobacz [arkusz elementów hosta](../vsto/worksheet-host-item.md).

### <a name="range-object"></a>obiekt zakresu
 Obiekt <xref:Microsoft.Office.Interop.Excel.Range> jest obiektem, który będzie używany w aplikacjach programu Excel. Aby można było manipulować dowolnym regionem w programie Excel, należy wyrazić go jako obiekt <xref:Microsoft.Office.Interop.Excel.Range> i współpracować z metodami i właściwościami tego zakresu. Obiekt <xref:Microsoft.Office.Interop.Excel.Range> reprezentuje komórkę, wiersz, kolumnę, zaznaczenie komórek, które zawierają jeden lub więcej bloków komórek, które mogą lub nie mogą być ciągłe, a nawet grupy komórek w wielu arkuszach.

 Program Visual Studio rozszerza obiekt <xref:Microsoft.Office.Interop.Excel.Range>, dostarczając typy <xref:Microsoft.Office.Tools.Excel.NamedRange> i <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>. Te typy mają większość tych samych funkcji co obiekt <xref:Microsoft.Office.Interop.Excel.Range>, a także nowe funkcje, takie jak możliwość powiązania danych i nowe zdarzenia. Aby uzyskać więcej informacji, zobacz [NamedRange Control](../vsto/namedrange-control.md) and [XmlMappedRange Control](../vsto/xmlmappedrange-control.md).

## <a name="ExcelOMDocumentation"></a>Korzystanie z dokumentacji modelu obiektów programu Excel
 Aby uzyskać pełne informacje na temat modelu obiektów programu Excel, można odwołać się do odwołania do podstawowego zestawu międzyoperacyjnego (PIA) programu Excel i odwołania do modelu obiektów VBA.

### <a name="primary-interop-assembly-reference"></a>Odwołanie do podstawowego zestawu międzyoperacyjnego
 Dokumentacja zestawu PIA programu Excel zawiera opis typów w podstawowym zestawie międzyoperacyjnym dla programu Excel. Ta dokumentacja jest dostępna w następującej lokalizacji: [odwołanie do podstawowego zestawu międzyoperacyjnego programu Excel 2010](/visualstudio/vsto/office-primary-interop-assemblies).

 Aby uzyskać więcej informacji o projektowaniu PIA programu Excel, takich jak różnice między klasami i interfejsami w PIAu i sposobie implementacji zdarzeń w PIA, zobacz [Omówienie klas i interfejsów w podstawowych zestawach międzyoperacyjnych pakietu Office](/previous-versions/office/office-12/ms247299(v=office.12)).

### <a name="vba-object-model-reference"></a>Odwołanie do modelu obiektów VBA
 Dokumentacja modelu obiektów VBA dokumentuje model obiektów programu Excel, który jest udostępniany w kodzie Visual Basic for Applications (VBA). Aby uzyskać więcej informacji, zobacz [Dokumentacja modelu obiektów programu Excel 2010](/office/vba/api/overview/Excel/object-model).

 Wszystkie obiekty i elementy członkowskie w odwołaniach modelu obiektów VBA odpowiadają typom i elementom członkowskim w PIA programu Excel. Na przykład obiekt arkusza w odniesieniu do modelu obiektów VBA odpowiada obiektowi <xref:Microsoft.Office.Interop.Excel.Worksheet> w PIA programu Excel. Mimo że dokumentacja modelu obiektów VBA zawiera przykłady kodu dla większości właściwości, metod i zdarzeń, należy przetłumaczyć kod VBA w tym odwołaniu do Visual Basic lub wizualizacji C# , jeśli chcesz użyć ich w projekcie programu Excel, który tworzysz przy użyciu wizualizacji Studio.

### <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Rozwiązania programu Excel](../vsto/excel-solutions.md)|Wyjaśnia, jak można tworzyć dostosowania na poziomie dokumentu i dodatki narzędzi VSTO dla programu Microsoft Office Excel.|
|[Pracuj z zakresami](../vsto/working-with-ranges.md)|Zawiera przykłady pokazujące, jak wykonywać typowe zadania z zakresami.|
|[Pracuj z arkuszami](../vsto/working-with-worksheets.md)|Zawiera przykłady, które pokazują, jak wykonywać typowe zadania z arkuszami.|
|[Pracuj ze skoroszytami](../vsto/working-with-workbooks.md)|Zawiera przykłady, które pokazują, jak wykonywać typowe zadania ze skoroszytami.|
