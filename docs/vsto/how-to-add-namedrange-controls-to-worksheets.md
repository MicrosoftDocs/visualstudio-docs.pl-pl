---
title: Jak dodać kontrolki NamedRange do arkuszy
description: Dowiedz się, jak dodawać kontrolki NamedRange do arkusza programu Excel Microsoft Office czasie projektowania i w czasie uruchamiania w projektach na poziomie dokumentu.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b7bf2f3ef91a6f572c64f94cb4b1a9a2f493e864
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827711"
---
# <a name="how-to-add-namedrange-controls-to-worksheets"></a>Jak dodać kontrolki NamedRange do arkuszy
  Kontrolki można dodawać do Microsoft Office programu Excel w czasie projektowania i w czasie <xref:Microsoft.Office.Tools.Excel.NamedRange> uruchamiania w projektach na poziomie dokumentu.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Kontrolki można również <xref:Microsoft.Office.Tools.Excel.NamedRange> dodawać w czasie uruchamiania w projektach dodatków VSTO.

 W tym temacie opisano następujące zadania:

- [Dodawanie kontrolek NamedRange w czasie projektowania](#designtime)

- [Dodawanie kontrolek NamedRange w czasie uruchamiania w projekcie na poziomie dokumentu](#runtimedoclevel)

- [Dodawanie kontrolek NamedRange w czasie uruchamiania w projekcie dodatku VSTO](#runtimeaddin)

  Aby uzyskać więcej informacji na <xref:Microsoft.Office.Tools.Excel.NamedRange> temat kontrolek, zobacz [NamedRange, kontrolka](../vsto/namedrange-control.md).

## <a name="add-namedrange-controls-at-design-time"></a><a name="designtime"></a> Dodawanie kontrolek NamedRange w czasie projektowania
 Istnieje kilka sposobów dodawania kontrolek do arkusza w projekcie na poziomie dokumentu w czasie projektowania: z poziomu programu Excel, z przybornika Visual Studio i z okna <xref:Microsoft.Office.Tools.Excel.NamedRange> **Źródła** danych. 

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-name-box-in-excel"></a>Aby dodać kontrolkę NamedRange do arkusza przy użyciu pola nazwy w programie Excel

1. Wybierz komórkę lub komórki, które chcesz uwzględnić w nazwanych zakresach.

2. W **polu Nazwa wpisz** nazwę zakresu i naciśnij klawisz **Enter**.

     Pole **nazwy znajduje** się obok paska formuły, tuż nad **kolumną A** arkusza.

### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-toolbox"></a>Aby dodać kontrolkę NamedRange do arkusza przy użyciu przybornika

1. Otwórz **przybornik i** kliknij kartę **Kontrolki programu Excel.**

2. Kliknij <xref:Microsoft.Office.Tools.Excel.NamedRange> i przeciągnij go do arkusza.

     Zostanie **wyświetlone okno dialogowe Dodawanie nazwanego** zakresu.

3. Zaznacz komórkę lub komórki, które chcesz uwzględnić w nazwanych zakresach.

4. Kliknij przycisk **OK**.

     Jeśli nie chcesz, aby kontrolka była domyślną nazwą, możesz ją zmienić w **oknie** Właściwości.

### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-data-sources-window"></a>Aby dodać kontrolkę NamedRange do arkusza przy użyciu okna Źródła danych

1. Otwórz **okno Źródła danych** i utwórz źródło danych dla projektu. Aby uzyskać więcej informacji, zobacz [Dodawanie nowych połączeń.](../data-tools/add-new-connections.md)

2. Przeciągnij jedno pole z **okna Źródła danych** do arkusza.

     Do arkusza zostanie <xref:Microsoft.Office.Tools.Excel.NamedRange> dodana kontrolka powiązana z danymi. Aby uzyskać więcej informacji, zobacz [Powiązanie danych i Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

## <a name="add-namedrange-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Dodawanie kontrolek NamedRange w czasie uruchamiania w projekcie na poziomie dokumentu
 Kontrolkę można <xref:Microsoft.Office.Tools.Excel.NamedRange> dodać programowo do arkusza w czasie uruchamiania. Dzięki temu można tworzyć kontrolki hosta w odpowiedzi na zdarzenia. Dynamicznie tworzone nazwane zakresy nie są utrwalane w arkuszu jako kontrolki hosta po zamknięciu arkusza. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie rzeczywistym.](../vsto/adding-controls-to-office-documents-at-run-time.md)

### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Aby programowo dodać kontrolkę NamedRange do arkusza

1. W programie obsługi zdarzeń wstaw następujący kod, aby dodać kontrolkę do komórki <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> `Sheet1` <xref:Microsoft.Office.Tools.Excel.NamedRange> **A1** i ustawić jej <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> właściwość na `Hello world!`

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet3":::

## <a name="add-namedrange-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Dodawanie kontrolek NamedRange w czasie uruchamiania w projekcie dodatku VSTO
 Kontrolkę można <xref:Microsoft.Office.Tools.Excel.NamedRange> dodać programowo do dowolnego otwartego arkusza w projekcie dodatku VSTO. Dynamicznie tworzone nazwane zakresy nie są utrwalane w arkuszu jako kontrolki hosta po zamknięciu arkusza. Aby uzyskać więcej informacji, zobacz [Extend Word documents and Excel workbooks in VSTO Add-ins at run time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)(Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w czasie uruchamiania).

### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Aby programowo dodać kontrolkę NamedRange do arkusza

1. Poniższy kod generuje element hosta arkusza, który jest oparty na otwartym arkuszu, a następnie dodaje kontrolkę do komórki A1 i ustawia <xref:Microsoft.Office.Tools.Excel.NamedRange> jej właściwość na  <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> `Hello world` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet7":::

## <a name="see-also"></a>Zobacz też
- [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w czasie uruchamiania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Kontrolki w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [NamedRange, kontrolka](../vsto/namedrange-control.md)
- [Automatyzowanie programu Excel przy użyciu obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
- [Jak zmienić rozmiar formantów NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
