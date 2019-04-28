---
title: Model obiektu Excel ― omówienie
ms.date: 02/02/2017
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
ms.openlocfilehash: df1045cd0b35a2c8d4afa765167693032c6d9936
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441820"
---
# <a name="excel-object-model-overview"></a>Model obiektu Excel ― omówienie
  Do opracowywania rozwiązań korzystających z programu Microsoft Office Excel, możesz korzystać z obiektami dostarczonych przez model obiektów programu Excel. W tym temacie przedstawiono najważniejsze obiekty:

- <xref:Microsoft.Office.Interop.Excel.Application>

- <xref:Microsoft.Office.Interop.Excel.Workbook>

- <xref:Microsoft.Office.Interop.Excel.Worksheet>

- <xref:Microsoft.Office.Interop.Excel.Range>

  [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

  Model obiektów jest ściśle zgodna interfejsu użytkownika. <xref:Microsoft.Office.Interop.Excel.Application> Obiekt reprezentuje całej aplikacji, a każdy <xref:Microsoft.Office.Interop.Excel.Workbook> obiekt zawiera zbiór `Worksheet` obiektów. Z tego miejsca jest główną abstrakcji, który reprezentuje komórki <xref:Microsoft.Office.Interop.Excel.Range> obiektu, który umożliwia pracę z poszczególnych komórek lub grupami komórek.

  Oprócz modelu obiektów programu Excel projektów pakietu Office w Visual Studio zapewniają *hostować elementy* i *hostowania kontrolek* które rozszerzają niektóre obiekty w modelu obiektów programu Excel. Obiekty hosta i kontrolek hosta zachowują się jak obiekty programu Excel, które rozszerzają, ale mają także dodatkowe funkcje, takie jak możliwości wiązania danych i dodatkowych zdarzeń. Aby uzyskać więcej informacji, zobacz [automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md) i [elementów, a omówienie kontrolek](../vsto/host-items-and-host-controls-overview.md).

  Ten temat zawiera krótkie omówienie modelu obiektów programu Excel. Dla zasobów można znaleźć więcej informacji na temat całego modelu obiektów programu Excel, zobacz [zapoznaj się z dokumentacją model obiektu Excel](#ExcelOMDocumentation).

  ![Link do wideo](../vsto/media/playvideo.gif "link do wideo") powiązane demonstracyjne wideo – zobacz [jak: Użyj procedur obsługi zdarzeń w dodatek programu Excel 2007? ](http://go.microsoft.com/fwlink/?LinkID=130291), i [jak: Za pomocą kształtów można utworzyć wykres bąbelkowy w programie Excel? ](http://go.microsoft.com/fwlink/?LinkID=130313).

## <a name="access-objects-in-an-excel-project"></a>Uzyskiwanie dostępu do obiektów w projekcie programu Excel
 Podczas tworzenia nowego projektu dodatku narzędzi VSTO dla programu Excel, programu Visual Studio automatycznie tworzy *ThisAddIn.vb* lub *ThisAddIn.cs* pliku kodu. Dostęp do obiektu aplikacji przy użyciu `Me.Application` lub `this.Application`.

 Podczas tworzenia nowego projektu poziomie dokumentu dla programu Excel, istnieje możliwość tworzenia nowego projektu skoroszyt programu Excel lub szablon programu Excel. Visual Studio automatycznie tworzy następujące pliki kodu w nowym projekcie programu Excel skoroszyt i szablonów projektów.

|Visual Basic|C#|
|------------------|---------|
|ThisWorkbook.vb|ThisWorkbook.cs|
|Sheet1.vb|Sheet1.CS|
|Sheet2.vb|Sheet2.CS|
|Sheet3.vb|Sheet3.CS|

 Możesz użyć `Globals` klasy w projekcie w celu uzyskania dostępu do `ThisWorkbook`, `Sheet1`, `Sheet2`, lub `Sheet3` z poza odpowiedniej klasy. Aby uzyskać więcej informacji, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md). Poniższy przykład wywołuje <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> metody `Sheet1` niezależnie od tego, czy kod jest umieszczany w jednym z `Sheet` *n* klasy lub `ThisWorkbook` klasy.

 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]

 Ponieważ mają zaawansowaną strukturę danych w dokumencie programu Excel, model obiektów jest hierarchiczne i proste. Program Excel oferuje setki obiektów, z którymi możesz wchodzić w interakcje, ale możesz uzyskać dobry początek object model, skupiając się na małego podzbioru dostępnych obiektów. Te obiekty obejmują następujące cztery:

- Aplikacja

- skoroszyt

- arkusz

- Zakres

  Większość pracy z programem Excel koncentruje się wokół tych czterech obiektów i ich elementów członkowskich.

### <a name="application-object"></a>Obiekt aplikacji
 Excel <xref:Microsoft.Office.Interop.Excel.Application> obiekt reprezentuje sama aplikacja programu Excel. <xref:Microsoft.Office.Interop.Excel.Application> Obiekt udostępnia wiele informacji na temat uruchomionej aplikacji, opcje zastosowane do tego wystąpienia, a następnie otwórz bieżące obiekty użytkownika, w ramach wystąpienia.

> [!NOTE]
> Nie należy ustawiać <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> właściwość <xref:Microsoft.Office.Interop.Excel.Application> obiektu w programie Excel, aby **false**. Ustawienie tej właściwości wartości false zapobiega podnoszenie żadnych wydarzeń, takich jak zdarzenia kontrolki hosta programu Excel.

### <a name="workbook-object"></a>Obiekt skoroszytu
 <xref:Microsoft.Office.Interop.Excel.Workbook> Obiekt reprezentuje pojedynczy skoroszytu w aplikacji programu Excel.

 Rozszerzanie narzędzi programistycznych pakietu Office w programie Visual Studio <xref:Microsoft.Office.Interop.Excel.Workbook> obiektu, zapewniając <xref:Microsoft.Office.Tools.Excel.Workbook> typu. Ten typ zapewnia dostęp do wszystkich funkcji <xref:Microsoft.Office.Interop.Excel.Workbook> obiektu. Aby uzyskać więcej informacji, zobacz [element hosta skoroszytu](../vsto/workbook-host-item.md).

### <a name="worksheet-object"></a>obiekt arkusza
 <xref:Microsoft.Office.Interop.Excel.Worksheet> Obiektu jest elementem członkowskim <xref:Microsoft.Office.Interop.Excel.Worksheets> kolekcji. Wiele właściwości, metod i zdarzeń <xref:Microsoft.Office.Interop.Excel.Worksheet> identyczne lub podobne do elementów członkowskich, dostarczone przez <xref:Microsoft.Office.Interop.Excel.Application> lub <xref:Microsoft.Office.Interop.Excel.Workbook> obiektów.

 Program Excel oferuje <xref:Microsoft.Office.Interop.Excel.Sheets> kolekcji jako właściwość <xref:Microsoft.Office.Interop.Excel.Workbook> obiektu. Każdy element członkowski <xref:Microsoft.Office.Interop.Excel.Sheets> kolekcji jest <xref:Microsoft.Office.Interop.Excel.Worksheet> lub <xref:Microsoft.Office.Interop.Excel.Chart> obiektu.

 Rozszerzanie narzędzi programistycznych pakietu Office w programie Visual Studio <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektu, zapewniając <xref:Microsoft.Office.Tools.Excel.Worksheet> typu. Ten typ zapewnia dostęp do wszystkich funkcji <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektu, a także nowe funkcje, takie jak możliwość hostowania zarządzane formanty i obsługiwać nowe zdarzenia. Aby uzyskać więcej informacji, zobacz [element hosta arkusza](../vsto/worksheet-host-item.md).

### <a name="range-object"></a>obiekt zakresu
 <xref:Microsoft.Office.Interop.Excel.Range> Obiekt jest obiektem użyje większość w aplikacjach programu Excel. Zanim można manipulować dowolny region w ramach programu Excel, należy go jako express <xref:Microsoft.Office.Interop.Excel.Range> obiektu i pracować z metody i właściwości tego zakresu. A <xref:Microsoft.Office.Interop.Excel.Range> obiekt reprezentuje komórkę, wiersz, kolumna zaznaczonych komórek, który zawiera jeden lub więcej bloków komórek, które może być lub może nie być ciągłe, lub nawet grupę komórek na wiele arkuszy.

 Program Visual Studio rozszerza <xref:Microsoft.Office.Interop.Excel.Range> obiektu, zapewniając <xref:Microsoft.Office.Tools.Excel.NamedRange> i <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> typów. Te typy mają większość te same funkcje co <xref:Microsoft.Office.Interop.Excel.Range> obiektu, a także nowe funkcje, takie jak możliwość powiązania danych i nowe zdarzenia. Aby uzyskać więcej informacji, zobacz [kontrolki NamedRange](../vsto/namedrange-control.md) i [xmlmappedrange — formant](../vsto/xmlmappedrange-control.md).

## <a name="ExcelOMDocumentation"></a> Zapoznaj się z dokumentacją modelu obiektów programu Excel
 Aby uzyskać pełne informacje na temat modelu obiektów programu Excel mogą odwoływać się do programu Excel odwołanie do zestawu podstawowej usługi międzyoperacyjnej (PIA) i dokumentacja modelu obiektów języka VBA.

### <a name="primary-interop-assembly-reference"></a>Odwołanie do zestawu podstawowej usługi międzyoperacyjnej
 Dokumentacja referencyjna programu Excel PIA opisano typy w podstawowy zestaw międzyoperacyjny dla programu Excel. Ta dokumentacja jest dostępna z następującej lokalizacji: [Odwołanie do zestawu podstawowej usługi międzyoperacyjnej Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).

 Aby uzyskać więcej informacji na temat projektowania PIA programu Excel, takich jak różnice między klasami i interfejsy, które PIA i sposobu implementacji zdarzenia w PIA, zobacz [Przegląd klasy i interfejsy podstawowe zestawy międzyoperacyjne pakietu Office](http://go.microsoft.com/fwlink/?LinkId=189592).

### <a name="vba-object-model-reference"></a>Dokumentacja modelu obiektów VBA
 Dokumentacja modelu obiektów VBA dokumenty modelu obiektów programu Excel, ponieważ jest narażony na język Visual Basic for Applications (VBA) kod. Aby uzyskać więcej informacji, zobacz [dokumentacja modelu obiektów programu Excel 2010](http://go.microsoft.com/fwlink/?LinkId=199768).

 Wszystkie obiekty i elementy członkowskie w dokumentacja modelu obiektów VBA odnoszą się do typów i członków w PIA programu Excel. Na przykład obiekt arkusza w dokumentacja modelu obiektów VBA odpowiada <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektu w programie Excel PIA. Mimo że dokumentacja modelu obiektów VBA zawiera przykłady kodu dla większości właściwości, metody i zdarzenia, należy translacji kodu VBA w ramach tego odwołania do kodu języka Visual Basic lub Visual C#, jeśli chcesz korzystać z nich w projekcie programu Excel utworzonym przy użyciu programu Visual Studio.

### <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Rozwiązania programu Excel](../vsto/excel-solutions.md)|Wyjaśnia sposób tworzenia dostosowań poziomie dokumentu i dodatków narzędzi VSTO dla programu Microsoft Office Excel.|
|[Praca z zakresami](../vsto/working-with-ranges.md)|Przykłady pokazujące, jak wykonywać typowe zadania z zakresami.|
|[Praca z arkuszami](../vsto/working-with-worksheets.md)|Przykłady pokazujące, jak wykonywać typowe zadania związane z arkuszy.|
|[Praca ze skoroszytami](../vsto/working-with-workbooks.md)|Przykłady pokazujące, jak wykonywać typowe zadania za pomocą skoroszytów.|
