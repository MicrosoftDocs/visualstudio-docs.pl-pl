---
title: 'Instrukcje: Dodawanie kontrolek NamedRange do arkuszy'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, adding to worksheets
- NamedRange control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 448a44c8f4bc9380a4ef1ebfec33b264e797cac8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543523"
---
# <a name="how-to-add-namedrange-controls-to-worksheets"></a>Instrukcje: Dodawanie kontrolek NamedRange do arkuszy
  Możesz dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki do Microsoft Office arkusza programu Excel w czasie projektowania i w czasie wykonywania w projektach na poziomie dokumentu.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Możesz również dodawać <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki w czasie wykonywania w projektach dodatku narzędzi VSTO.

 W tym temacie opisano następujące zadania:

- [Dodawanie kontrolek NamedRange w czasie projektowania](#designtime)

- [Dodawanie kontrolek NamedRange w czasie wykonywania w projekcie na poziomie dokumentu](#runtimedoclevel)

- [Dodawanie kontrolek NamedRange w czasie wykonywania w projekcie dodatku narzędzi VSTO](#runtimeaddin)

  Aby uzyskać więcej informacji na temat <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolek, zobacz [NamedRange Control](../vsto/namedrange-control.md).

## <a name="add-namedrange-controls-at-design-time"></a><a name="designtime"></a> Dodawanie kontrolek NamedRange w czasie projektowania
 Istnieje kilka sposobów dodawania <xref:Microsoft.Office.Tools.Excel.NamedRange> formantów do arkusza w projekcie na poziomie dokumentu w czasie projektowania: z poziomu programu Excel, z **przybornika**programu Visual Studio i z okna **źródła danych** .

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-name-box-in-excel"></a>Aby dodać kontrolkę NamedRange do arkusza przy użyciu pola Nazwa w programie Excel

1. Wybierz komórkę lub komórki, które mają zostać uwzględnione w nazwanym zakresie.

2. W **polu Nazwa**wpisz nazwę zakresu i naciśnij klawisz **Enter**.

     **Pole Nazwa** znajduje się obok paska formuły, po prostu powyżej kolumny **A** arkusza.

### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-toolbox"></a>Aby dodać kontrolkę NamedRange do arkusza za pomocą przybornika

1. Otwórz **Przybornik** i kliknij kartę **formanty programu Excel** .

2. Kliknij <xref:Microsoft.Office.Tools.Excel.NamedRange> i przeciągnij ją do arkusza.

     Zostanie wyświetlone okno dialogowe **Dodaj nazwany zakres** .

3. Wybierz komórkę lub komórki, które mają zostać uwzględnione w nazwanym zakresie.

4. Kliknij przycisk **OK**.

     Jeśli nie chcesz, aby nazwa domyślna została nadana formantowi, możesz zmienić nazwę w oknie **Właściwości** .

### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-data-sources-window"></a>Aby dodać kontrolkę NamedRange do arkusza przy użyciu okna źródła danych

1. Otwórz okno **źródła danych** i Utwórz źródło danych dla projektu. Aby uzyskać więcej informacji, zobacz [Dodawanie nowych połączeń](../data-tools/add-new-connections.md).

2. Przeciągnij pojedyncze pole z okna **źródła danych** do arkusza.

     <xref:Microsoft.Office.Tools.Excel.NamedRange>Do arkusza zostanie dodany formant powiązany z danymi. Aby uzyskać więcej informacji, zobacz temat [powiązanie danych i Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

## <a name="add-namedrange-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Dodawanie kontrolek NamedRange w czasie wykonywania w projekcie na poziomie dokumentu
 Formant można dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> programowo do arkusza w czasie wykonywania. Dzięki temu można tworzyć kontrolki hosta w odpowiedzi na zdarzenia. Dynamicznie tworzone nazwane zakresy nie są utrwalane w arkuszu jako kontrolki hosta, gdy arkusz jest zamknięty. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).

### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Aby programowo dodać formant NamedRange do arkusza

1. W programie <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> obsługi zdarzeń programu `Sheet1` Wstaw następujący kod, aby dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> formant do komórki **a1** i ustawić jego <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> Właściwość na `Hello world!`

     [!code-csharp[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#3)]

## <a name="add-namedrange-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Dodawanie kontrolek NamedRange w czasie wykonywania w projekcie dodatku narzędzi VSTO
 Formant można dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> programowo do dowolnego otwartego arkusza w projekcie dodatku VSTO. Dynamicznie tworzone nazwane zakresy nie są utrwalane w arkuszu jako kontrolki hosta, gdy arkusz jest zamknięty. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Aby programowo dodać formant NamedRange do arkusza

1. Poniższy kod generuje element hosta arkusza, który jest oparty na otwartym arkuszu, a następnie dodaje <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę do komórki **a1** i ustawia jej <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> Właściwość na `Hello world` .

     [!code-csharp[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#7)]
     [!code-vb[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#7)]

## <a name="see-also"></a>Zobacz też
- [Rozwiń dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [NamedRange — formant](../vsto/namedrange-control.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Instrukcje: zmiana rozmiaru kontrolek NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
