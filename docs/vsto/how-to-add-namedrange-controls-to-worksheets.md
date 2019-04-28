---
title: 'Instrukcje: Dodawanie formantów NamedRange do arkuszy'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 2cc909828dc77c0f1dbe31c79255f2c93d2a95b3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62826566"
---
# <a name="how-to-add-namedrange-controls-to-worksheets"></a>Instrukcje: Dodawanie formantów NamedRange do arkuszy
  Możesz dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolek do arkusza programu Microsoft Office Excel, w czasie projektowania i w czasie wykonywania w projektach na poziomie dokumentu.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Można również dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> formantów w czasie wykonywania w projektach dodatku narzędzi VSTO.

 W tym temacie opisano następujące zadania:

- [Dodawanie formantów NamedRange w czasie projektowania](#designtime)

- [Dodawanie formantów NamedRange w czasie wykonywania w projekcie na poziomie dokumentu](#runtimedoclevel)

- [Dodawanie formantów NamedRange w czasie wykonywania w projekcie dodatku narzędzi VSTO](#runtimeaddin)

  Aby uzyskać więcej informacji na temat <xref:Microsoft.Office.Tools.Excel.NamedRange> formantów, zobacz [kontrolki NamedRange](../vsto/namedrange-control.md).

## <a name="designtime"></a> Dodawanie formantów NamedRange w czasie projektowania
 Istnieje kilka sposobów, aby dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolek do arkusza w projekcie na poziomie dokumentu, w czasie projektowania: z programu Excel, programu Visual Studio **przybornika**i z **źródeł danych** okna.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-name-box-in-excel"></a>Aby dodać kontrolkę NamedRange do arkusza przy użyciu nazwy pola w programie Excel

1. Wybierz komórkę lub komórki, które mają zostać uwzględnione w nazwanym zakresie.

2. W **pola Nazwa podmiotu**, wpisz nazwę zakresu, a następnie naciśnij klawisz **Enter**.

     **Pola Nazwa podmiotu** znajduje się obok paska formuły, tuż nad kolumny **A** arkusza.

### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-toolbox"></a>Aby dodać kontrolkę NamedRange do arkusza za pomocą przybornika

1. Otwórz **przybornika** i kliknij przycisk **kontrolki programu Excel** kartę.

2. Kliknij przycisk <xref:Microsoft.Office.Tools.Excel.NamedRange> i przeciągnij go do arkusza.

     **Dodaj zakres nazwanych** pojawi się okno dialogowe.

3. Wybierz komórkę lub komórki, które mają zostać uwzględnione w nazwanym zakresie.

4. Kliknij przycisk **OK**.

     Jeśli użytkownik nie chce nazwę domyślną, który znajduje się do kontrolki, można zmienić nazwę w **właściwości** okna.

### <a name="to-add-a-namedrange-control-to-a-worksheet-using-the-data-sources-window"></a>Aby dodać kontrolkę NamedRange do arkusza za pomocą okna źródeł danych

1. Otwórz **źródeł danych** okna i Utwórz źródło danych dla projektu. Aby uzyskać więcej informacji, zobacz [dodać nowe połączenia](../data-tools/add-new-connections.md).

2. Przeciągnij pole jednego z **źródeł danych** okna do arkusza.

     Powiązane z danymi <xref:Microsoft.Office.Tools.Excel.NamedRange> formant jest dodawany do arkusza. Aby uzyskać więcej informacji, zobacz [powiązanie danych oraz Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

## <a name="runtimedoclevel"></a> Dodawanie formantów NamedRange w czasie wykonywania w projekcie na poziomie dokumentu
 Możesz dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli programowo do arkusza w czasie wykonywania. Dzięki temu można utworzyć kontrolki hosta w odpowiedzi na zdarzenia. Utworzony dynamicznie nazwane zakresy nie są zachowywane w arkuszu zgodnie z kontrolki hosta po zamknięciu arkusza. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w środowisku uruchomieniowym](../vsto/adding-controls-to-office-documents-at-run-time.md).

### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Aby programowo dodać kontrolki NamedRange do arkusza

1. W <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> program obsługi zdarzeń `Sheet1`, Wstaw następujący kod, aby dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę komórki **A1** i ustaw jego <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> właściwości `Hello world!`

     [!code-csharp[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsExcel#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#3)]

## <a name="runtimeaddin"></a> Dodawanie formantów NamedRange w czasie wykonywania w projekcie dodatku narzędzi VSTO
 Możesz dodać <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki programowo dowolnego otwartego arkusza w projekcie dodatku narzędzi VSTO. Utworzony dynamicznie nazwane zakresy nie są zachowywane w arkuszu zgodnie z kontrolki hosta po zamknięciu arkusza. Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="to-add-a-namedrange-control-to-a-worksheet-programmatically"></a>Aby programowo dodać kontrolki NamedRange do arkusza

1. Poniższy kod generuje element hosta arkusza, która opiera się na otwieranie arkusza, a następnie dodanie <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę komórki **A1** i ustawia jego <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> właściwość `Hello world`.

     [!code-csharp[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#7)]
     [!code-vb[Trin_Excel_Dynamic_Controls#7](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#7)]

## <a name="see-also"></a>Zobacz także
- [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Namedrange — formant](../vsto/namedrange-control.md)
- [Automatyzowanie programu Excel za pomocą obiektów rozszerzonych](../vsto/automating-excel-by-using-extended-objects.md)
- [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)
- [Instrukcje: Zmiana rozmiaru formantów NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
