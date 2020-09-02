---
title: 'Instrukcje: Dodawanie formantów formularzy systemu Windows do dokumentów pakietu Office'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], adding
- controls [Office development in Visual Studio], Windows Forms controls
- documents [Office development in Visual Studio], Windows Forms controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b12d51ffe3a2e647a067b95d320e8beb70cac384
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547540"
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>Instrukcje: Dodawanie formantów Windows Forms do dokumentów pakietu Office
  Możesz dodać kontrolki Windows Forms, aby Microsoft Office Excel i Microsoft Office dokumenty programu Word w czasie projektowania w projektach na poziomie dokumentu. W czasie wykonywania można dodać kontrolki w obszarze dostosowania na poziomie dokumentu i w dodatkach narzędzi VSTO. Na przykład można dodać <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> kontrolkę do arkusza, aby użytkownicy mogli wybierać z listy opcji.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 W tym temacie opisano następujące zadania:

- [Dodawanie kontrolek w czasie projektowania](#designtime)

- [Dodawanie kontrolek w czasie wykonywania w projektach na poziomie dokumentu](#runtimedoclevel)

- [Dodawanie kontrolek w czasie wykonywania w dodatkach narzędzi VSTO](#runtimeaddin)

## <a name="add-controls-at-design-time"></a><a name="designtime"></a> Dodawanie kontrolek w czasie projektowania
 Istnieje kilka sposobów dodawania formantów Windows Forms do dokumentu w projekcie na poziomie dokumentu w czasie projektowania.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-drag-a-windows-forms-control-to-the-document"></a>Aby przeciągnąć formant Windows Forms do dokumentu

1. Utwórz lub Otwórz projekt skoroszytu programu Excel lub projekt dokumentu programu Word w programie Visual Studio, aby dokument był widoczny w projektancie. Aby uzyskać informacje na temat tworzenia projektów, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Na karcie **Formanty standardowe** **przybornika**kliknij kontrolkę, którą chcesz dodać, a następnie przeciągnij ją do dokumentu.

    > [!NOTE]
    > Po wybraniu kontrolki w programie Excel zobaczysz wartość " **Osadź" (WinForms. Control. host "," ")** na **pasku formuły**. Ten tekst jest wymagany i nie należy go usuwać.

### <a name="to-draw-a-windows-forms-control-on-the-document"></a>Aby narysować kontrolkę Windows Forms w dokumencie

1. Utwórz lub Otwórz projekt skoroszytu programu Excel lub projekt dokumentu programu Word w programie Visual Studio, aby dokument był widoczny w projektancie. Aby uzyskać informacje na temat tworzenia projektów, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Na karcie **Formanty standardowe** **przybornika**kliknij kontrolkę, którą chcesz dodać.

3. W dokumencie kliknij miejsce w lewym górnym rogu kontrolki, a następnie przeciągnij się do miejsca, w którym ma się znajdować prawy dolny róg kontrolki.

     Kontrolka zostanie dodana do dokumentu z określoną lokalizacją i rozmiarem.

    > [!NOTE]
    > Po wybraniu kontrolki w programie Excel zobaczysz wartość " **Osadź" (WinForms. Control. host "," ")**  na **pasku formuły**. Ten tekst jest wymagany i nie należy go usuwać.

### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>Aby dodać kontrolkę Windows Forms do dokumentu przez pojedyncze kliknięcie kontrolki

1. Utwórz lub Otwórz projekt skoroszytu programu Excel lub projekt dokumentu programu Word w programie Visual Studio, aby dokument był widoczny w projektancie. Aby uzyskać informacje na temat tworzenia projektów, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Na karcie **Formanty standardowe** **przybornika**kliknij kontrolkę, którą chcesz dodać.

3. Jeden dokument, kliknij miejsce, do którego chcesz dodać formant.

     Kontrolka zostanie dodana do dokumentu z domyślnym rozmiarem.

    > [!NOTE]
    > Po wybraniu kontrolki w programie Excel zobaczysz wartość " **Osadź" (WinForms. Control. host "," ")** na **pasku formuły**. Ten tekst jest wymagany i nie należy go usuwać.

### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>Aby dodać kontrolkę Windows Forms do dokumentu przez dwukrotne kliknięcie kontrolki

1. Utwórz lub Otwórz projekt skoroszytu programu Excel lub projekt dokumentu programu Word w programie Visual Studio, aby dokument był widoczny w projektancie. Aby uzyskać informacje na temat tworzenia projektów, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Na karcie **Formanty standardowe** **przybornika**kliknij dwukrotnie formant, który chcesz dodać.

     Kontrolka zostanie dodana do dokumentu w centrum dokumentu lub aktywnego okienka.

    > [!NOTE]
    > Po wybraniu kontrolki w programie Excel zobaczysz wartość " **Osadź" (WinForms. Control. host "," ")** na **pasku formuły**. Ten tekst jest wymagany i nie należy go usuwać.

### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>Aby dodać kontrolkę Windows Forms do dokumentu, naciskając klawisz ENTER

1. Utwórz lub Otwórz projekt skoroszytu programu Excel lub projekt dokumentu programu Word w programie Visual Studio, aby dokument był widoczny w projektancie. Aby uzyskać informacje na temat tworzenia projektów, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Na karcie **Formanty standardowe** **przybornika**kliknij kontrolkę, którą chcesz dodać, a następnie naciśnij klawisz **Enter** .

     Kontrolka zostanie dodana do dokumentu w centrum dokumentu lub aktywnego okienka.

    > [!NOTE]
    > Po wybraniu kontrolki w programie Excel zobaczysz wartość " **Osadź" (WinForms. Control. host "," ")** na **pasku formuły**. Ten tekst jest wymagany i nie należy go usuwać.

## <a name="add-controls-at-run-time-in-document-level-projects"></a><a name="runtimedoclevel"></a> Dodawanie kontrolek w czasie wykonywania w projektach na poziomie dokumentu
 Można programowo dodać kontrolki Windows Forms do dokumentu w czasie wykonywania. W programie Word Użyj metod <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> właściwości `ThisDocument` klasy. W programie Excel Użyj metod <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> właściwości `Sheet` klasy *n* . Każda metoda ma kilka przeciążeń, które umożliwiają określenie lokalizacji kontrolki na różne sposoby.

 Po dodaniu kontrolki Windows Forms do dokumentu w czasie wykonywania formant nie jest utrwalany w dokumencie, gdy dokument zostanie zamknięty. Możesz ponownie utworzyć formant przy następnym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).

### <a name="to-add-a-windows-forms-control-at-run-time"></a>Aby dodać kontrolkę Windows Forms w czasie wykonywania

1. Użyj metody, która ma nazwę Add \<*control class*> (gdzie *Klasa sterowania* jest nazwą klasy kontrolki Windows Forms, którą chcesz dodać, na przykład <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A> ).

     Poniższy przykład kodu demonstruje, jak dodać <xref:Microsoft.Office.Tools.Excel.Controls.Button> do komórki **C5** z `Sheet1` w projekcie na poziomie dokumentu dla programu Excel.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#4)]

## <a name="add-controls-at-run-time-in-vsto-add-ins"></a><a name="runtimeaddin"></a> Dodawanie kontrolek w czasie wykonywania w dodatkach narzędzi VSTO
 Kontrolki Windows Forms można dodawać programowo do dowolnego otwartego dokumentu w czasie wykonywania. Najpierw Wygeneruj element hosta, który jest oparty na otwartym dokumencie lub arkuszu. Następnie w programie Word Użyj metod <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> właściwości nowego elementu hosta. W programie Excel Użyj metod <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> właściwości nowego elementu hosta. Każda metoda ma kilka przeciążeń, które umożliwiają określenie lokalizacji kontrolki na różne sposoby.

 Po dodaniu kontrolki Windows Forms do dokumentu w czasie wykonywania formant nie jest utrwalany w dokumencie, gdy dokument zostanie zamknięty. Możesz ponownie utworzyć formant przy następnym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).

 Aby uzyskać więcej informacji na temat generowania elementów hosta w projektach dodatku VSTO, zobacz sekcję [rozszerzając dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

### <a name="to-add-a-windows-forms-control-at-run-time"></a>Aby dodać kontrolkę Windows Forms w czasie wykonywania

1. Użyj metody, która ma nazwę Add \<*control class*> (gdzie *Klasa sterowania* jest nazwą klasy kontrolki Windows Forms, którą chcesz dodać, na przykład <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A> ).

    > [!NOTE]
    > W projektach dodatku VSTO przeznaczonych dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszych należy dodać odwołanie do zestawu *Microsoft.Office.Tools.Excel.v4.0.Utilities.dll* lub *Microsoft.Office.Tools.Word.v4.0.Utilities.dll* , zanim będzie można uzyskać dostęp do dodawania \<*control class*> metod.

     Poniższy przykład kodu ilustruje sposób dodawania <xref:Microsoft.Office.Tools.Word.Controls.Button> do pierwszego akapitu aktywnego dokumentu przy użyciu dodatku VSTO programu Word.

     [!code-vb[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#7)]
     [!code-csharp[Trin_WordAddInDynamicControls#7](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#7)]

## <a name="see-also"></a>Zobacz też
- [Kontrolki Windows Forms w dokumentach pakietu Office — omówienie](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Instrukcje: zmiana rozmiaru kontrolek w komórkach arkusza](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
