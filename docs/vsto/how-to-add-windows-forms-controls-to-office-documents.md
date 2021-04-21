---
title: 'How to: Add Windows forms controls to Office documents (Jak dodać kontrolki formularzy systemu Windows do dokumentów pakietu Office)'
description: Dowiedz się, jak dodawać kontrolki Windows Forms do Microsoft Office Excel i Microsoft Office dokumentów programu Word w czasie projektowania w projektach na poziomie dokumentu.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e5a196c54a513376edef5c837a429bece6dd7b16
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824838"
---
# <a name="how-to-add-windows-forms-controls-to-office-documents"></a>Jak dodać kontrolki Windows Forms do dokumentów pakietu Office
  Możesz dodawać kontrolki Windows Forms do Microsoft Office Excel i Microsoft Office dokumentów programu Word w czasie projektowania w projektach na poziomie dokumentu. W czasie uruchamiania można dodawać kontrolki w dostosowaniach na poziomie dokumentu i w dodatki VSTO. Na przykład możesz dodać kontrolkę do arkusza, aby użytkownicy <xref:Microsoft.Office.Tools.Excel.Controls.ComboBox> mogą wybierać z listy opcji.

 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

 W tym temacie opisano następujące zadania:

- [Dodawanie kontrolek w czasie projektowania](#designtime)

- [Dodawanie kontrolek w czasie uruchamiania w projektach na poziomie dokumentu](#runtimedoclevel)

- [Dodawanie kontrolek w czasie uruchamiania w dodatki VSTO](#runtimeaddin)

## <a name="add-controls-at-design-time"></a><a name="designtime"></a> Dodawanie kontrolek w czasie projektowania
 Istnieje kilka sposobów dodawania kontrolek Windows Forms do dokumentu w projekcie na poziomie dokumentu w czasie projektowania.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-drag-a-windows-forms-control-to-the-document"></a>Aby przeciągnąć kontrolkę Windows Forms do dokumentu

1. Utwórz lub otwórz projekt skoroszytu programu Excel lub projekt dokumentu programu Word Visual Studio tak, aby dokument był widoczny w projektancie. Aby uzyskać informacje na temat tworzenia projektów, [zobacz Jak tworzyć projekty pakietu Office w programie Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Na karcie **Typowe kontrolki** **przybornika** kliknij kontrolkę, którą chcesz dodać, i przeciągnij ją do dokumentu.

    > [!NOTE]
    > Po wybraniu kontrolki w programie Excel na pasku formuły zobaczysz wartość **=EMBED("WinForms.Control.Host","").**  Ten tekst jest niezbędny i nie powinien być usuwany.

### <a name="to-draw-a-windows-forms-control-on-the-document"></a>Aby narysować kontrolkę Windows Forms dokumentu

1. Utwórz lub otwórz projekt skoroszytu programu Excel lub projekt dokumentu programu Word Visual Studio tak, aby dokument był widoczny w projektancie. Aby uzyskać informacje na temat tworzenia projektów, [zobacz Jak tworzyć projekty pakietu Office w programie Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Na karcie **Typowe kontrolki** **przybornika** kliknij kontrolkę, którą chcesz dodać.

3. W dokumencie kliknij miejsce, w którym ma się znaleźć lewy górny róg kontrolki, a następnie przeciągnij do miejsca, w którym ma się znaleźć prawy dolny róg kontrolki.

     Kontrolka jest dodawana do dokumentu z określoną lokalizacją i rozmiarem.

    > [!NOTE]
    > Po wybraniu kontrolki w programie Excel na pasku formuły zobaczysz pozycję **=EMBED("WinForms.Control.Host","").**  Ten tekst jest niezbędny i nie należy go usuwać.

### <a name="to-add-a-windows-forms-control-to-the-document-by-single-clicking-the-control"></a>Aby dodać kontrolkę Windows Forms do dokumentu, klikając ją pojedynczo

1. Utwórz lub otwórz projekt skoroszytu programu Excel lub projekt dokumentu programu Word Visual Studio, aby dokument był widoczny w projektancie. Aby uzyskać informacje na temat tworzenia projektów, [zobacz Jak tworzyć projekty pakietu Office w programie Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Na karcie **Typowe kontrolki** **przybornika** kliknij kontrolkę, którą chcesz dodać

3. Na jednym z dokumentów kliknij miejsce, w którym ma zostać dodana kontrolka.

     Kontrolka jest dodawana do dokumentu z domyślnym rozmiarem.

    > [!NOTE]
    > Po wybraniu kontrolki w programie Excel na pasku formuły zobaczysz pozycję **=EMBED("WinForms.Control.Host","").**  Ten tekst jest niezbędny i nie należy go usuwać.

### <a name="to-add-a-windows-forms-control-to-the-document-by-double-clicking-the-control"></a>Aby dodać kontrolkę Windows Forms do dokumentu przez dwukrotne kliknięcie kontrolki

1. Utwórz lub otwórz projekt skoroszytu programu Excel lub projekt dokumentu programu Word Visual Studio, aby dokument był widoczny w projektancie. Aby uzyskać informacje na temat tworzenia projektów, [zobacz Jak tworzyć projekty pakietu Office w programie Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Na karcie **Typowe kontrolki** **przybornika** kliknij dwukrotnie kontrolkę, którą chcesz dodać.

     Kontrolka jest dodawana do dokumentu w środku dokumentu lub okienku aktywnym.

    > [!NOTE]
    > Po wybraniu kontrolki w programie Excel na pasku formuły zobaczysz pozycję **=EMBED("WinForms.Control.Host","").**  Ten tekst jest niezbędny i nie należy go usuwać.

### <a name="to-add-a-windows-forms-control-to-the-document-by-pressing-the-enter-key"></a>Aby dodać kontrolkę Windows Forms do dokumentu, naciskając klawisz Enter

1. Utwórz lub otwórz projekt skoroszytu programu Excel lub projekt dokumentu programu Word Visual Studio tak, aby dokument był widoczny w projektancie. Aby uzyskać informacje na temat tworzenia projektów, [zobacz How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Na karcie **Typowe kontrolki** **przybornika** kliknij kontrolkę, którą chcesz dodać, a następnie naciśnij klawisz **Enter.**

     Kontrolka jest dodawana do dokumentu w środku dokumentu lub w aktywnym okienku.

    > [!NOTE]
    > Po wybraniu kontrolki w programie Excel na pasku formuły zobaczysz wartość **=EMBED("WinForms.Control.Host","").**  Ten tekst jest niezbędny i nie powinien być usuwany.

## <a name="add-controls-at-run-time-in-document-level-projects"></a><a name="runtimedoclevel"></a> Dodawanie kontrolek w czasie uruchamiania w projektach na poziomie dokumentu
 Możesz programowo dodawać kontrolki Windows Forms do dokumentu w czasie uruchamiania. W programie Word użyj metod <xref:Microsoft.Office.Tools.Word.DocumentBase.Controls%2A> właściwości `ThisDocument` klasy . W programie Excel użyj metod <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Controls%2A> właściwości `Sheet` *klasy n.* Każda metoda ma kilka przeciążeń, które umożliwiają określenie lokalizacji kontrolki na różne sposoby.

 Gdy dodajesz kontrolkę Windows Forms do dokumentu w czasie uruchamiania, kontrolka nie jest utrwalana w dokumencie po zamknięciu dokumentu. Kontrolkę można odtworzyć przy następnym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie uruchamiania.](../vsto/adding-controls-to-office-documents-at-run-time.md)

### <a name="to-add-a-windows-forms-control-at-run-time"></a>Aby dodać kontrolkę Windows Forms w czasie uruchamiania

1. Użyj metody o nazwie Add (gdzie klasa sterowania jest nazwą klasy Windows Forms, którą chcesz \<*control class*> dodać, taką jak  <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A> ).

     Poniższy przykład kodu pokazuje, jak dodać do komórki <xref:Microsoft.Office.Tools.Excel.Controls.Button> **C5** w projekcie na poziomie dokumentu dla `Sheet1` programu Excel.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet4":::

## <a name="add-controls-at-run-time-in-vsto-add-ins"></a><a name="runtimeaddin"></a> Dodawanie kontrolek w czasie uruchamiania w dodatki VSTO
 Kontrolki Windows Forms można dodać programowo do dowolnego otwartego dokumentu w czasie uruchamiania. Najpierw wygeneruj element hosta, który jest oparty na otwartym dokumencie lub arkuszu. Następnie w programie Word użyj metod <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> właściwości nowego elementu hosta. W programie Excel użyj metod <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> właściwości nowego elementu hosta. Każda metoda ma kilka przeciążeń, które umożliwiają określenie lokalizacji kontrolki na różne sposoby.

 Po dodaniu kontrolki Windows Forms do dokumentu w czasie uruchamiania kontrolka nie jest utrwalana w dokumencie po zamknięciu dokumentu. Kontrolkę można odtworzyć przy następnym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie rzeczywistym.](../vsto/adding-controls-to-office-documents-at-run-time.md)

 Aby uzyskać więcej informacji na temat generowania elementów hosta w projektach dodatków VSTO, zobacz Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w [czasie uruchamiania.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

### <a name="to-add-a-windows-forms-control-at-run-time"></a>Aby dodać kontrolkę Windows Forms w czasie uruchamiania

1. Użyj metody o nazwie Dodaj (gdzie klasa sterowania jest nazwą klasy kontrolki Windows Forms, którą chcesz \<*control class*> dodać, na przykład  <xref:Microsoft.Office.Tools.Word.ControlExtensions.AddButton%2A> ).

    > [!NOTE]
    > W projektach dodatku VSTO, które są docelowe dla programu lub nowszych, należy dodać odwołanie do zestawuMicrosoft.Office.Tools.Excel.v4.0.Utilities.dlllubMicrosoft.Office.Tools.Word.v4.0.Utilities.dllprzed uzyskaniem dostępu do [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] metod   \<*control class*> Add.

     Poniższy przykład kodu pokazuje, jak dodać do pierwszego akapitu aktywnego dokumentu za pomocą dodatku <xref:Microsoft.Office.Tools.Word.Controls.Button> Word VSTO.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet7":::

## <a name="see-also"></a>Zobacz też
- [Windows Forms kontroli w dokumentach pakietu Office — omówienie](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie rzeczywistym](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Jak zmienić rozmiar kontrolek w komórkach arkusza](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
