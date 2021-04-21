---
title: Omówienie modelu obiektu programu Excel
description: Dowiedz się, że możesz wchodzić w interakcje z obiektami dostarczonymi przez model obiektów programu Excel, aby tworzyć rozwiązania korzystające z Microsoft Office Excel.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 509378b13e48f21a1148d700addd9ac4e78985e9
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825696"
---
# <a name="excel-object-model-overview"></a>Omówienie modelu obiektów programu Excel
  Aby tworzyć rozwiązania korzystające Microsoft Office excel, możesz wchodzić w interakcje z obiektami dostarczonymi przez model obiektów programu Excel. W tym temacie oprowadzono najważniejsze obiekty:

- <xref:Microsoft.Office.Interop.Excel.Application>

- <xref:Microsoft.Office.Interop.Excel.Workbook>

- <xref:Microsoft.Office.Interop.Excel.Worksheet>

- <xref:Microsoft.Office.Interop.Excel.Range>

  [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

  Model obiektów jest ściśle zgodny z interfejsem użytkownika. Obiekt <xref:Microsoft.Office.Interop.Excel.Application> reprezentuje całą aplikację, a każdy obiekt zawiera <xref:Microsoft.Office.Interop.Excel.Workbook> kolekcję `Worksheet` obiektów. Z tego względu główną abstrakcją reprezentującą komórki jest obiekt , który umożliwia pracę z poszczególnymi komórkami <xref:Microsoft.Office.Interop.Excel.Range> lub grupami komórek.

  Oprócz modelu obiektów programu Excel projekty pakietu Office  w programie Visual Studio zapewniają elementy hosta i kontrolki hosta, które rozszerzają niektóre obiekty w modelu obiektów programu Excel.  Elementy hosta i kontrolki hosta zachowują się jak obiekty programu Excel, które rozszerzają, ale mają również dodatkowe funkcje, takie jak możliwości powiązania danych i dodatkowe zdarzenia. Aby uzyskać więcej informacji, zobacz [Automate Excel by using extended objects (Automatyzowanie programu Excel przy użyciu](../vsto/automating-excel-by-using-extended-objects.md) obiektów rozszerzonych) i Host items and host controls overview [(Omówienie elementów hosta i kontrolek hosta).](../vsto/host-items-and-host-controls-overview.md)

  Ten temat zawiera krótkie omówienie modelu obiektów programu Excel. Zasoby, w których można dowiedzieć się więcej o całym modelu obiektów programu Excel, można znaleźć w dokumentacji dotyczącej używania modelu obiektów [programu Excel.](#ExcelOMDocumentation)

## <a name="access-objects-in-an-excel-project"></a>Uzyskiwanie dostępu do obiektów w projekcie programu Excel
 Podczas tworzenia nowego projektu dodatku VSTO dla programu Excel program Visual Studio automatycznie tworzy plik kodu *ThisAddIn.vb* lub *ThisAddIn.cs.* Dostęp do obiektu Application można uzyskać za pomocą narzędzia `Me.Application` lub `this.Application` .

 Podczas tworzenia nowego projektu na poziomie dokumentu dla programu Excel możesz utworzyć nowy projekt skoroszytu programu Excel lub szablonu programu Excel. Visual Studio automatycznie tworzy następujące pliki kodu w nowym projekcie programu Excel dla projektów skoroszytów i szablonów.

|Visual Basic|C#|
|------------------|---------|
|ThisWorkbook.vb|ThisWorkbook.cs|
|Arkusz1.vb|Sheet1.cs|
|Sheet2.vb|Sheet2.cs|
|Sheet3.vb|Sheet3.cs|

 Możesz użyć klasy `Globals` w projekcie, aby uzyskać dostęp `ThisWorkbook` do , , lub `Sheet1` `Sheet2` `Sheet3` spoza odpowiedniej klasy. Aby uzyskać więcej informacji, zobacz [Globalny dostęp do obiektów w projektach pakietu Office.](../vsto/global-access-to-objects-in-office-projects.md) Poniższy przykład wywołuje metodę niezależnie od tego, czy kod jest umieszczony <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> w jednej z n `Sheet1` `Sheet` *klas,* czy w klasie `ThisWorkbook` .

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet82":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet82":::

 Ponieważ dane w dokumencie programu Excel są wysoce ustrukturyzowane, model obiektów jest hierarchiczny i prosty. Program Excel udostępnia setki obiektów, z którymi możesz chcieć wchodzić w interakcje, ale możesz dobrze rozpocząć korzystanie z modelu obiektów, koncentrując się na niewielkim podzestawie dostępnych obiektów. Te obiekty obejmują następujące cztery:

- Aplikacja

- skoroszyt

- arkusz

- Zakres

  Większość pracy wykonanej w programie Excel jest wyśrodkowania wokół tych czterech obiektów i ich elementów członkowskich.

### <a name="application-object"></a>Obiekt aplikacji
 Obiekt programu Excel <xref:Microsoft.Office.Interop.Excel.Application> reprezentuje samą aplikację programu Excel. Obiekt uwidacznia dużą część informacji o uruchomionej aplikacji, opcjach zastosowanych do tego wystąpienia i obiektach bieżącego użytkownika otwartych <xref:Microsoft.Office.Interop.Excel.Application> w ramach wystąpienia.

> [!NOTE]
> Nie należy ustawiać właściwości <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> obiektu w <xref:Microsoft.Office.Interop.Excel.Application> programie Excel na wartość **false**. Ustawienie tej właściwości na wartość false uniemożliwia programowi Excel podnoszenie jakichkolwiek zdarzeń, w tym zdarzeń kontrolek hosta.

### <a name="workbook-object"></a>Obiekt skoroszytu
 Obiekt <xref:Microsoft.Office.Interop.Excel.Workbook> reprezentuje pojedynczy skoroszyt w aplikacji programu Excel.

 Narzędzia programskie pakietu Office w Visual Studio <xref:Microsoft.Office.Interop.Excel.Workbook> rozszerzają obiekt, podając <xref:Microsoft.Office.Tools.Excel.Workbook> typ . Ten typ zapewnia dostęp do wszystkich funkcji <xref:Microsoft.Office.Interop.Excel.Workbook> obiektu. Aby uzyskać więcej informacji, zobacz [Element hosta skoroszytu](../vsto/workbook-host-item.md).

### <a name="worksheet-object"></a>obiekt arkusza
 Obiekt <xref:Microsoft.Office.Interop.Excel.Worksheet> jest członkiem <xref:Microsoft.Office.Interop.Excel.Worksheets> kolekcji. Wiele właściwości, metod i zdarzeń obiektu jest identycznych lub podobnych do elementów <xref:Microsoft.Office.Interop.Excel.Worksheet> członkowskich dostarczanych przez <xref:Microsoft.Office.Interop.Excel.Application> obiekty lub <xref:Microsoft.Office.Interop.Excel.Workbook> .

 Program Excel <xref:Microsoft.Office.Interop.Excel.Sheets> udostępnia kolekcję jako właściwość <xref:Microsoft.Office.Interop.Excel.Workbook> obiektu. Każdy członek <xref:Microsoft.Office.Interop.Excel.Sheets> kolekcji jest obiektem <xref:Microsoft.Office.Interop.Excel.Worksheet> lub <xref:Microsoft.Office.Interop.Excel.Chart> .

 Narzędzia programskie pakietu Office w Visual Studio <xref:Microsoft.Office.Interop.Excel.Worksheet> rozszerzają obiekt, podając <xref:Microsoft.Office.Tools.Excel.Worksheet> typ . Ten typ zapewnia dostęp do wszystkich funkcji obiektu, a także nowych funkcji, takich jak możliwość hostowania kontrolek zarządzanych <xref:Microsoft.Office.Interop.Excel.Worksheet> i obsługi nowych zdarzeń. Aby uzyskać więcej informacji, zobacz [Element hosta arkusza](../vsto/worksheet-host-item.md).

### <a name="range-object"></a>obiekt zakresu
 Obiekt <xref:Microsoft.Office.Interop.Excel.Range> jest obiektem, który będzie najczęściej używać w aplikacjach programu Excel. Aby można było manipulować dowolnym regionem w programie Excel, musisz wyrazić go jako obiekt i pracować z metodami <xref:Microsoft.Office.Interop.Excel.Range> i właściwościami tego zakresu. Obiekt reprezentuje komórkę, wiersz, kolumnę, zaznaczenie komórek, które zawierają co najmniej jeden blok komórek, który może lub nie być ciągły, a nawet grupę komórek w wielu <xref:Microsoft.Office.Interop.Excel.Range> arkuszach.

 Visual Studio rozszerza obiekt <xref:Microsoft.Office.Interop.Excel.Range> przez podanie <xref:Microsoft.Office.Tools.Excel.NamedRange> typów <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> i . Te typy mają większość tych samych funkcji co obiekt, a także nowe funkcje, takie jak możliwość powiązania <xref:Microsoft.Office.Interop.Excel.Range> danych i nowe zdarzenia. Aby uzyskać więcej informacji, zobacz [namedrange formantu](../vsto/namedrange-control.md) [i XmlMappedRange formantu](../vsto/xmlmappedrange-control.md).

## <a name="use-the-excel-object-model-documentation"></a><a name="ExcelOMDocumentation"></a> Korzystanie z dokumentacji modelu obiektów programu Excel
 Aby uzyskać pełne informacje na temat modelu obiektów programu Excel, można zapoznać się z informacjami w temacie Excel primary interop assembly (PIA) (Podstawowy zestaw międzyoptykowy programu Excel) i VBA object model reference (Odwołanie do modelu obiektów VBA).

### <a name="primary-interop-assembly-reference"></a>Odwołanie do podstawowego zestawu międzyopłacowego
 W dokumentacji referencyjnej dotyczącej danych osobowych programu Excel opisano typy w podstawowym zestawie międzyoptyku dla programu Excel. Ta dokumentacja jest dostępna w następującej lokalizacji: Dokumentacja podstawowego zestawu [międzyoptykowego programu Excel 2010.](office-primary-interop-assemblies.md)

 Aby uzyskać więcej informacji na temat projektowania danych osobowych programu Excel, takich jak różnice między klasami i interfejsami w danych osobowych oraz sposób implementowania zdarzeń w ramach stosunku do danych osobowych, zobacz Overview of classes and [interfaces in the Office primary interop assemblies](/previous-versions/office/office-12/ms247299(v=office.12))(Omówienie klas i interfejsów w podstawowych zestawach międzyoptykowych pakietu Office).

### <a name="vba-object-model-reference"></a>Odwołanie do modelu obiektów VBA
 Odwołanie do modelu obiektów VBA dokumentuje model obiektów programu Excel, gdy jest on narażony na Visual Basic for Applications (VBA). Aby uzyskać więcej informacji, zobacz Informacje o modelu obiektów [programu Excel 2010.](/office/vba/api/overview/Excel/object-model)

 Wszystkie obiekty i elementy członkowskie w odwołaniach do modelu obiektów VBA odpowiadają typom i członkom w danych pianych programu Excel. Na przykład obiekt Arkusz w odwołaniach do modelu obiektów VBA odpowiada <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektowi w danych piA programu Excel. Mimo że odwołanie do modelu obiektów VBA zawiera przykłady kodu dla większości właściwości, metod i zdarzeń, należy przetłumaczyć kod VBA w tym odwołaniu na język Visual Basic lub Visual C#, jeśli chcesz używać ich w projekcie programu Excel, który został przez Ciebie Visual Studio.

### <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Rozwiązania programu Excel](../vsto/excel-solutions.md)|Wyjaśnia, jak można tworzyć dostosowania na poziomie dokumentu i dodatki VSTO dla Microsoft Office Excel.|
|[Praca z zakresami](../vsto/working-with-ranges.md)|Zawiera przykłady, które pokazują, jak wykonywać typowe zadania z zakresami.|
|[Praca z arkuszami](../vsto/working-with-worksheets.md)|Zawiera przykłady, które pokazują, jak wykonywać typowe zadania za pomocą arkuszy.|
|[Praca ze skoroszytami](../vsto/working-with-workbooks.md)|Zawiera przykłady, które pokazują, jak wykonywać typowe zadania za pomocą skoroszytów.|
