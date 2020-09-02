---
title: 'Instrukcje: Dodawanie formantów ListObject do arkuszy'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4c53d820170c359e568b0a7b0ab5711a632d9eba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538323"
---
# <a name="how-to-add-listobject-controls-to-worksheets"></a>Instrukcje: Dodawanie formantów ListObject do arkuszy
  Możesz dodać <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki do Microsoft Office arkusza programu Excel w czasie projektowania i w czasie wykonywania w projektach na poziomie dokumentu.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Możesz również dodawać <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolki w czasie wykonywania w projektach dodatku narzędzi VSTO.

 W tym temacie opisano następujące zadania:

- [Dodawanie formantów ListObject w czasie projektowania](#designtime)

- [Dodawanie formantów ListObject w czasie wykonywania w projekcie na poziomie dokumentu](#runtimedoclevel)

- [Dodawanie formantów ListObject w czasie wykonywania w projekcie dodatku narzędzi VSTO](#runtimeaddin)

  Aby uzyskać więcej informacji na temat <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolek, zobacz [ListObject Control](../vsto/listobject-control.md).

## <a name="add-listobject-controls-at-design-time"></a><a name="designtime"></a> Dodawanie formantów ListObject w czasie projektowania
 Istnieje kilka sposobów dodawania <xref:Microsoft.Office.Tools.Excel.ListObject> formantów do arkusza w projekcie na poziomie dokumentu w czasie projektowania: z poziomu programu Excel, z **przybornika**programu Visual Studio i z okna **źródła danych** .

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-use-the-ribbon-in-excel"></a>Aby użyć wstążki w programie Excel

1. Na karcie **Wstawianie** w grupie **tabele** kliknij pozycję **tabela**.

2. Wybierz komórkę lub komórki, które chcesz dołączyć do listy, a następnie kliknij przycisk **OK**.

#### <a name="to-use-the-toolbox"></a>Aby użyć przybornika

1. Na karcie **formanty programu Excel** **przybornika**przeciągnij element <xref:Microsoft.Office.Tools.Excel.ListObject> do arkusza.

     Zostanie wyświetlone okno dialogowe **Dodawanie kontrolki ListObject** .

2. Wybierz komórkę lub komórki, które chcesz dołączyć do listy, a następnie kliknij przycisk **OK**.

     Jeśli nie chcesz zachować nazwy domyślnej, możesz zmienić nazwę w oknie **Właściwości** .

#### <a name="to-use-the-data-sources-window"></a>Aby użyć okna źródła danych

1. Otwórz okno **źródła danych** i Utwórz źródło danych dla projektu. Aby uzyskać więcej informacji, zobacz [Dodawanie nowych połączeń](../data-tools/add-new-connections.md).

2. Przeciągnij tabelę z okna **źródła danych** do arkusza.

     <xref:Microsoft.Office.Tools.Excel.ListObject>Do arkusza zostanie dodany formant powiązany z danymi. Aby uzyskać więcej informacji, zobacz temat [powiązanie danych i Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

## <a name="add-listobject-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Dodawanie formantów ListObject w czasie wykonywania w projekcie na poziomie dokumentu
 Formant można dodać <xref:Microsoft.Office.Tools.Excel.ListObject> dynamicznie w czasie wykonywania. Dzięki temu można tworzyć kontrolki hosta w odpowiedzi na zdarzenia. Obiekty list utworzone dynamicznie nie są utrwalane w arkuszu jako kontrolki hosta, gdy arkusz jest zamknięty. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Aby programowo dodać formant ListObject do arkusza

1. W programie <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> obsługi zdarzeń w programie `Sheet1` Wstaw następujący kod, aby dodać <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolkę do komórek **a1** i **a4**.

     [!code-csharp[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsExcel#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#2)]

## <a name="add-listobject-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Dodawanie formantów ListObject w czasie wykonywania w projekcie dodatku narzędzi VSTO
 Formant można dodać <xref:Microsoft.Office.Tools.Excel.ListObject> programowo do dowolnego otwartego arkusza w projekcie dodatku VSTO. Obiekty list utworzone dynamicznie nie są utrwalane w arkuszu jako formanty hosta, gdy arkusz jest zapisywany, a następnie zamknięty. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

#### <a name="to-add-a-listobject-control-to-a-worksheet-programmatically"></a>Aby programowo dodać formant ListObject do arkusza

1. Poniższy kod generuje element hosta arkusza, który jest oparty na otwartym arkuszu, a następnie dodaje <xref:Microsoft.Office.Tools.Excel.ListObject> kontrolkę do komórek **a1** i **a4**.

     [!code-csharp[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#8)]
     [!code-vb[Trin_Excel_Dynamic_Controls#8](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#8)]

## <a name="see-also"></a>Zobacz też
- [Rozwiń dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [ListObject — formant](../vsto/listobject-control.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Instrukcje: Zmienianie rozmiaru formantów ListObject](../vsto/how-to-resize-listobject-controls.md)
- [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
