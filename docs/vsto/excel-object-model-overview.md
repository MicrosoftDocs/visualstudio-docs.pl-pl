---
title: Omówienie modelu obiektu programu Excel
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
ms.openlocfilehash: a823692a5cc0f154c514edff4fe9398de0efd212
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649423"
---
# <a name="excel-object-model-overview"></a>Omówienie modelu obiektów programu Excel
  Aby opracować rozwiązania korzystające z programu Microsoft Office Excel, można wchodzić w interakcje z obiektami dostarczonymi przez model obiektów programu Excel. W tym temacie przedstawiono najważniejsze obiekty:

- <xref:Microsoft.Office.Interop.Excel.Application>

- <xref:Microsoft.Office.Interop.Excel.Workbook>

- <xref:Microsoft.Office.Interop.Excel.Worksheet>

- <xref:Microsoft.Office.Interop.Excel.Range>

  [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

  Model obiektu ściśle podąża za interfejsem użytkownika. Obiekt <xref:Microsoft.Office.Interop.Excel.Application> reprezentuje całą aplikację, <xref:Microsoft.Office.Interop.Excel.Workbook> a każdy obiekt `Worksheet` zawiera kolekcję obiektów. Stamtąd główną abstrakcją reprezentującą <xref:Microsoft.Office.Interop.Excel.Range> komórki jest obiekt, który umożliwia pracę z poszczególnymi komórkami lub grupami komórek.

  Oprócz modelu obiektów programu Excel projekty pakietu Office w programie Visual Studio zapewniają *elementy hosta* i *formanty hosta,* które rozszerzają niektóre obiekty w modelu obiektów programu Excel. Elementy hosta i formanty hosta zachowują się jak obiekty programu Excel, które rozszerzają, ale mają również dodatkowe funkcje, takie jak możliwości wiązania danych i dodatkowe zdarzenia. Aby uzyskać więcej informacji, zobacz [Automatyzacja programu Excel przy użyciu omówionego](../vsto/automating-excel-by-using-extended-objects.md) omówienie obiektów rozszerzonych i [hosta oraz formantów hosta](../vsto/host-items-and-host-controls-overview.md).

  Ten temat zawiera krótkie omówienie modelu obiektów programu Excel. Aby uzyskać informacje o zasobach, w których można dowiedzieć się więcej o całym modelu obiektów programu Excel, zobacz [Korzystanie z dokumentacji modelu obiektów programu Excel](#ExcelOMDocumentation).

## <a name="access-objects-in-an-excel-project"></a>Uzyskiwanie dostępu do obiektów w projekcie programu Excel
 Podczas tworzenia nowego projektu dodatku VSTO dla programu Excel program Visual Studio automatycznie tworzy plik kodu *ThisAddIn.vb* lub *ThisAddIn.cs.* Dostęp do obiektu Application `Me.Application` można `this.Application`uzyskać za pomocą lub .

 Podczas tworzenia nowego projektu na poziomie dokumentu dla programu Excel można utworzyć nowy skoroszyt programu Excel lub projekt szablonu programu Excel. Program Visual Studio automatycznie tworzy następujące pliki kodu w nowym projekcie programu Excel zarówno dla projektów skoroszytu, jak i szablonów.

|Visual Basic|C#|
|------------------|---------|
|ThisWorkbook.vb|ThisWorkbook.cs|
|Arkusz1.vb|Sheet1.cs|
|Arkusz2.vb|Sheet2.cs|
|Arkusz3.vb|Sheet3.cs|

 Klasy w `Globals` projekcie można użyć, `ThisWorkbook` `Sheet1`aby `Sheet2`uzyskać `Sheet3` dostęp do , , lub spoza odpowiedniej klasy. Aby uzyskać więcej informacji, zobacz [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md). Poniższy przykład <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> wywołuje `Sheet1` metodę niezależnie od tego, czy kod `Sheet`jest umieszczony `ThisWorkbook` w jednej z *n* klas lub klasy.

 [!code-csharp[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#82)]

 Ponieważ dane w dokumencie programu Excel mają bardzo uporządkowaną strukturę, model obiektu jest hierarchiczny i prosty. Program Excel udostępnia setki obiektów, z którymi można wchodzić w interakcje, ale można uzyskać dobry początek modelu obiektu, koncentrując się na małym podzbiorze dostępnych obiektów. Obiekty te obejmują następujące cztery:

- Aplikacja

- skoroszyt

- arkusz

- Zakres

  Większość pracy wykonanej z programem Excel skupia się wokół tych czterech obiektów i ich członków.

### <a name="application-object"></a>Obiekt aplikacji
 Obiekt <xref:Microsoft.Office.Interop.Excel.Application> programu Excel reprezentuje samą aplikację programu Excel. Obiekt <xref:Microsoft.Office.Interop.Excel.Application> udostępnia wiele informacji o uruchomionej aplikacji, opcje stosowane do tego wystąpienia i bieżących obiektów użytkownika otwarte w wystąpieniu.

> [!NOTE]
> Nie należy ustawiać <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> właściwości <xref:Microsoft.Office.Interop.Excel.Application> obiektu w programie Excel na **false**. Ustawienie tej właściwości na false uniemożliwia programowi Excel wywoływanie żadnych zdarzeń, w tym zdarzeń formantów hosta.

### <a name="workbook-object"></a>Obiekt skoroszytu
 Obiekt <xref:Microsoft.Office.Interop.Excel.Workbook> reprezentuje pojedynczy skoroszyt w aplikacji Excel.

 Narzędzia deweloperskie pakietu Office <xref:Microsoft.Office.Interop.Excel.Workbook> w programie <xref:Microsoft.Office.Tools.Excel.Workbook> Visual Studio rozszerzają obiekt, udostępniając ten typ. Ten typ daje dostęp do <xref:Microsoft.Office.Interop.Excel.Workbook> wszystkich funkcji obiektu. Aby uzyskać więcej informacji, zobacz [Element hosta skoroszytu](../vsto/workbook-host-item.md).

### <a name="worksheet-object"></a>obiekt arkusza
 Obiekt <xref:Microsoft.Office.Interop.Excel.Worksheet> jest członkiem <xref:Microsoft.Office.Interop.Excel.Worksheets> kolekcji. Wiele właściwości, metod i zdarzeń <xref:Microsoft.Office.Interop.Excel.Worksheet> są identyczne lub podobne do <xref:Microsoft.Office.Interop.Excel.Application> <xref:Microsoft.Office.Interop.Excel.Workbook> elementów członkowskich dostarczonych przez lub obiektów.

 Program Excel <xref:Microsoft.Office.Interop.Excel.Sheets> udostępnia kolekcję <xref:Microsoft.Office.Interop.Excel.Workbook> jako właściwość obiektu. Każdy element <xref:Microsoft.Office.Interop.Excel.Sheets> członkowski kolekcji <xref:Microsoft.Office.Interop.Excel.Worksheet> jest <xref:Microsoft.Office.Interop.Excel.Chart> obiektem lub obiektem.

 Narzędzia deweloperskie pakietu Office <xref:Microsoft.Office.Interop.Excel.Worksheet> w programie <xref:Microsoft.Office.Tools.Excel.Worksheet> Visual Studio rozszerzają obiekt, udostępniając ten typ. Ten typ zapewnia dostęp do <xref:Microsoft.Office.Interop.Excel.Worksheet> wszystkich funkcji obiektu, a także nowych funkcji, takich jak możliwość hosta zarządzanych formantów i obsługi nowych zdarzeń. Aby uzyskać więcej informacji, zobacz [Element hosta arkusza](../vsto/worksheet-host-item.md).

### <a name="range-object"></a>obiekt zakresu
 Obiekt <xref:Microsoft.Office.Interop.Excel.Range> jest obiektem, którego będzie najczęściej używany w aplikacjach programu Excel. Aby można było manipulować dowolnym regionem <xref:Microsoft.Office.Interop.Excel.Range> w programie Excel, należy wyrazić go jako obiekt i pracować z metodami i właściwościami tego zakresu. Obiekt <xref:Microsoft.Office.Interop.Excel.Range> reprezentuje komórkę, wiersz, kolumnę, zaznaczenie komórek, które zawiera jeden lub więcej bloków komórek, które mogą lub nie mogą być ciągłe, lub nawet grupę komórek na wielu arkuszach.

 Visual Studio rozszerza <xref:Microsoft.Office.Interop.Excel.Range> obiekt, <xref:Microsoft.Office.Tools.Excel.NamedRange> zapewniając <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> i typów. Te typy mają większość tych <xref:Microsoft.Office.Interop.Excel.Range> samych funkcji jako obiektu, a także nowe funkcje, takie jak możliwości wiązania danych i nowe zdarzenia. Aby uzyskać więcej informacji, zobacz [NamedRange kontroli](../vsto/namedrange-control.md) i [XmlMappedRange kontroli](../vsto/xmlmappedrange-control.md).

## <a name="use-the-excel-object-model-documentation"></a><a name="ExcelOMDocumentation"></a>Korzystanie z dokumentacji modelu obiektów programu Excel
 Aby uzyskać pełne informacje o modelu obiektów programu Excel, można zapoznać się z odwołaniem do podstawowego zestawu międzyoperacyjnego programu Excel (PIA) i odwołaniem do modelu obiektu VBA.

### <a name="primary-interop-assembly-reference"></a>Podstawowe odwołanie do złożenia międzyoperacyjnego
 Dokumentacja referencyjna pia programu Excel opisuje typy w podstawowym zestawie międzyoperacyjnym dla programu Excel. Ta dokumentacja jest dostępna z następującej lokalizacji: [Odwołanie do podstawowego zestawu interop programu Excel 2010](office-primary-interop-assemblies.md).

 Aby uzyskać więcej informacji na temat projektu pia programu Excel, takich jak różnice między klasami i interfejsami w PIA i jak zdarzenia w PIA są implementowane, zobacz [Omówienie klas i interfejsów w pakietach głównych pakietu Office](/previous-versions/office/office-12/ms247299(v=office.12)).

### <a name="vba-object-model-reference"></a>Odwołanie do modelu obiektu VBA
 Odwołanie do modelu obiektów VBA dokumentuje model obiektów programu Excel, ponieważ jest on narażony na kod języka Visual Basic for Applications (VBA). Aby uzyskać więcej informacji, zobacz [Odwołanie do modelu obiektów programu Excel 2010](/office/vba/api/overview/Excel/object-model).

 Wszystkie obiekty i elementy członkowskie w odwołaniu do modelu obiektów VBA odpowiadają typom i członkom w programie Excel PIA. Na przykład obiekt Arkusz w odwołaniu do modelu obiektu <xref:Microsoft.Office.Interop.Excel.Worksheet> VBA odpowiada obiektowi w programie Excel PIA. Chociaż odwołanie do modelu obiektu VBA zawiera przykłady kodu dla większości właściwości, metod i zdarzeń, należy przetłumaczyć kod VBA w tym odwołaniu do języka Visual Basic lub Visual C#, jeśli chcesz ich używać w projekcie programu Excel, który można utworzyć za pomocą programu Visual Studio.

### <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Rozwiązania programu Excel](../vsto/excel-solutions.md)|W tym artykule wyjaśniono, jak można tworzyć dostosowania na poziomie dokumentu i dodatki VSTO dla programu Microsoft Office Excel.|
|[Praca z zakresami](../vsto/working-with-ranges.md)|Zawiera przykłady, które pokazują, jak wykonywać typowe zadania z zakresami.|
|[Praca z arkuszami](../vsto/working-with-worksheets.md)|Zawiera przykłady, które pokazują, jak wykonywać typowe zadania za pomocą arkuszy.|
|[Praca ze skoroszytami](../vsto/working-with-workbooks.md)|Zawiera przykłady, które pokazują, jak wykonywać typowe zadania ze skoroszytami.|
