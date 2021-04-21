---
title: '2017: Dodawanie kontrolek ListObject do arkuszy'
description: Dowiedz się, jak dodać kontrolki ListObject do Microsoft Office programu Excel w czasie projektowania i w czasie uruchamiania w projektach na poziomie dokumentu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ListObject control, adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 077ff2e92455df283dfcaeddd7171e1f86698e6b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827893"
---
# <a name="how-to-add-listobject-controls-to-worksheets"></a>2017: Dodawanie kontrolek ListObject do arkuszy
  Kontrolki można dodawać do Microsoft Office programu Excel w czasie projektowania i w czasie <xref:Microsoft.Office.Tools.Excel.ListObject> uruchamiania w projektach na poziomie dokumentu.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Kontrolki można również <xref:Microsoft.Office.Tools.Excel.ListObject> dodawać w czasie uruchamiania w projektach dodatków VSTO.

 W tym temacie opisano następujące zadania:

- [Dodawanie kontrolek ListObject w czasie projektowania](#designtime)

- [Dodawanie kontrolek ListObject w czasie uruchamiania w projekcie na poziomie dokumentu](#runtimedoclevel)

- [Dodawanie kontrolek ListObject w czasie uruchamiania w projekcie dodatku VSTO](#runtimeaddin)

  Aby uzyskać więcej informacji na <xref:Microsoft.Office.Tools.Excel.ListObject> temat kontrolek, zobacz [ListObject, kontrolka](../vsto/listobject-control.md).

## <a name="add-listobject-controls-at-design-time"></a><a name="designtime"></a> Dodawanie kontrolek ListObject w czasie projektowania
 Istnieje kilka sposobów dodawania kontrolek do arkusza w projekcie na poziomie dokumentu w czasie projektowania: z poziomu programu Excel, z przybornika Visual Studio i z okna <xref:Microsoft.Office.Tools.Excel.ListObject> **Źródła** danych. 

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-use-the-ribbon-in-excel"></a>Aby użyć wstążki w programie Excel

1. Na karcie **Wstawianie** w grupie **Tabele** kliknij pozycję **Tabela**.

2. Zaznacz komórkę lub komórki, które chcesz uwzględnić na liście, a następnie kliknij przycisk **OK**.

#### <a name="to-use-the-toolbox"></a>Aby użyć przybornika

1. Na karcie **Kontrolki programu Excel** **przybornika** przeciągnij element <xref:Microsoft.Office.Tools.Excel.ListObject> do arkusza.

     Zostanie **wyświetlone okno dialogowe Dodawanie kontrolki ListObject.**

2. Zaznacz komórkę lub komórki, które chcesz uwzględnić na liście, a następnie kliknij przycisk **OK**.

     Jeśli nie chcesz zachować nazwy domyślnej, możesz zmienić nazwę w **oknie** Właściwości.

#### <a name="to-use-the-data-sources-window"></a>Aby użyć okna Źródła danych

1. Otwórz okno **Źródła danych** i utwórz źródło danych dla projektu. Aby uzyskać więcej informacji, zobacz [Dodawanie nowych połączeń.](../data-tools/add-new-connections.md)

2. Przeciągnij tabelę z **okna Źródła danych** do arkusza.

     Do arkusza zostanie dodana <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolka powiązana z danymi. Aby uzyskać więcej informacji, zobacz [Powiązanie danych i Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

## <a name="add-listobject-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Dodawanie kontrolek ListObject w czasie uruchamiania w projekcie na poziomie dokumentu
 Kontrolkę można <xref:Microsoft.Office.Tools.Excel.ListObject> dodać dynamicznie w czasie uruchamiania. Dzięki temu można tworzyć kontrolki hosta w odpowiedzi na zdarzenia. Dynamicznie tworzone obiekty listy nie są utrwalane w arkuszu jako kontrolki hosta po zamknięciu arkusza. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie uruchamiania.](../vsto/adding-controls-to-office-documents-at-run-time.md)

#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Aby programowo dodać kontrolkę ListObject do arkusza

1. W programie obsługi zdarzeń programu wstaw następujący kod, aby dodać kontrolkę <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> `Sheet1` do komórek od <xref:Microsoft.Office.Tools.Excel.ListObject> **A1** do **A4**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb" id="Snippet2":::

## <a name="add-listobject-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Dodawanie kontrolek ListObject w czasie uruchamiania w projekcie dodatku VSTO
 Kontrolkę można <xref:Microsoft.Office.Tools.Excel.ListObject> dodać programowo do dowolnego otwartego arkusza w projekcie dodatku VSTO. Dynamicznie tworzone obiekty listy nie są utrwalane w arkuszu jako kontrolki hosta, gdy arkusz jest zapisywany, a następnie zamykany. Aby uzyskać więcej informacji, zobacz [Extend Word documents and Excel workbooks in VSTO Add-ins at run time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)(Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w czasie uruchamiania).

#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Aby programowo dodać kontrolkę ListObject do arkusza

1. Poniższy kod generuje element hosta arkusza, który jest oparty na otwartym arkuszu, a następnie dodaje kontrolkę do <xref:Microsoft.Office.Tools.Excel.ListObject> komórek **od A1** do **A4.**

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet8":::

## <a name="see-also"></a>Zobacz też
- [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w czasie uruchamiania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Kontrolki w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [ListObject, kontrolka](../vsto/listobject-control.md)
- [Automatyzowanie programu Excel przy użyciu obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
- [How to: Resize ListObject controls (2017: Zmienianie rozmiaru kontrolek ListObject)](../vsto/how-to-resize-listobject-controls.md)
- [Wiązanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Programowe ograniczenia elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
