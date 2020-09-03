---
title: Dodawanie kontrolek do arkusza w czasie wykonywania w projekcie dodatku narzędzi VSTO
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to worksheets at run time
- application-level add-ins [Office development in Visual Studio], adding controls
- worksheets, adding controls at run time
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5bf2610ca1f3f3767082bf50953f821d37d1af2a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "71253895"
---
# <a name="walkthrough-add-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project"></a>Przewodnik: Dodawanie kontrolek do arkusza w czasie wykonywania w projekcie dodatku narzędzi VSTO
  Możesz dodać kontrolki do dowolnego otwartego arkusza przy użyciu dodatku narzędzi VSTO dla programu Excel. W tym instruktażu pokazano, jak za pomocą wstążki umożliwić użytkownikom dodawanie <xref:Microsoft.Office.Tools.Excel.Controls.Button> , a <xref:Microsoft.Office.Tools.Excel.NamedRange> i <xref:Microsoft.Office.Tools.Excel.ListObject> do arkusza. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).

 **Dotyczy:** Informacje przedstawione w tym temacie dotyczą projektów dodatku VSTO dla programu Excel. Aby uzyskać więcej informacji, zobacz [Dostępne funkcje uporządkowane według aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).

 W instruktażu przedstawiono następujące zagadnienia:

- Udostępnienie interfejsu użytkownika (UI) do dodawania formantów do arkusza.

- Dodawanie formantów do arkusza.

- Usuwanie kontrolek z arkusza.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Excel

## <a name="create-a-new-excel-vsto-add-in-project"></a>Utwórz nowy projekt dodatku narzędzi VSTO dla programu Excel
 Zacznij od utworzenia projektu dodatku VSTO dla programu Excel.

### <a name="to-create-a-new-excel-vsto-add-in-project"></a>Aby utworzyć nowy projekt dodatku narzędzi VSTO dla programu Excel

1. W programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Utwórz projekt dodatku VSTO dla programu Excel o nazwie **ExcelDynamicControls**. Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Dodaj odwołanie do zestawu **Microsoft.Office.Tools.Excel.v4.0.Utilities.dll** . To odwołanie jest wymagane do programowego dodawania kontrolki Windows Forms do arkusza w dalszej części tego przewodnika.

## <a name="provide-a-ui-to-add-controls-to-a-worksheet"></a>Podaj interfejs użytkownika, aby dodać kontrolki do arkusza
 Dodaj kartę niestandardową do wstążki programu Excel. Użytkownicy mogą zaznaczyć pola wyboru na karcie, aby dodać kontrolki do arkusza.

#### <a name="to-provide-a-ui-to-add-controls-to-a-worksheet"></a>Aby zapewnić interfejs użytkownika do dodawania formantów do arkusza

1. W menu **projekt** kliknij polecenie **Dodaj nowy element**.

2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **wstążka (projektant graficzny)**, a następnie kliknij przycisk **Dodaj**.

     Plik o nazwie **Ribbon1.cs** lub **Ribbon1. vb** zostanie otwarty w Projektancie wstążki i zostanie wyświetlona domyślna karta i Grupa.

3. Na karcie **kontrolki wstążki pakietu Office** w **przyborniku**przeciągnij kontrolkę CheckBox na **grupa1**.

4. Kliknij pozycję **checkBox1** , aby ją zaznaczyć.

5. W oknie **Właściwości** Zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**Przycisk**|
    |**Etykieta**|**Przycisk**|

6. Dodaj drugie pole wyboru do **grupa1**, a następnie Zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**NamedRange**|
    |**Etykieta**|**NamedRange**|

7. Dodaj trzecie pole wyboru do **grupa1**, a następnie Zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**ListObject**|
    |**Etykieta**|**ListObject**|

## <a name="add-controls-to-the-worksheet"></a>Dodawanie formantów do arkusza
 Formanty zarządzane można dodawać tylko do elementów hosta, które działają jako kontenery. Ponieważ projekty dodatków VSTO współpracują z dowolnym otwartym skoroszytem, dodatek VSTO konwertuje arkusz na element hosta lub pobiera istniejący element hosta przed dodaniem formantu. Dodaj kod do programów obsługi zdarzeń kliknięcia dla każdej kontrolki, aby wygenerować <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta, który jest oparty na otwartym arkuszu. Następnie Dodaj a <xref:Microsoft.Office.Tools.Excel.Controls.Button> , a <xref:Microsoft.Office.Tools.Excel.NamedRange> i a <xref:Microsoft.Office.Tools.Excel.ListObject> na bieżącym zaznaczeniu w arkuszu.

### <a name="to-add-controls-to-a-worksheet"></a>Aby dodać kontrolki do arkusza

1. W Projektancie wstążki kliknij dwukrotnie **przycisk.**

     <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click>Procedura obsługi zdarzeń **przycisku** wyboru zostanie otwarta w edytorze kodu.

2. Zastąp `Button_Click` procedurę obsługi zdarzeń poniższym kodem.

     Ten kod używa `GetVstoObject` metody, aby uzyskać element hosta, który reprezentuje pierwszy arkusz w skoroszycie, a następnie dodaje <xref:Microsoft.Office.Tools.Excel.Controls.Button> formant do aktualnie zaznaczonej komórki.

     [!code-csharp[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#2)]
     [!code-vb[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#2)]

3. W **Eksplorator rozwiązań**wybierz pozycję *Ribbon1.cs* lub *Ribbon1. vb*.

4. W menu **Widok** kliknij pozycję **Projektant**.

5. W Projektancie wstążki kliknij dwukrotnie pozycję **NamedRange**.

6. Zastąp `NamedRange_Click` procedurę obsługi zdarzeń poniższym kodem.

     Ten kod używa `GetVstoObject` metody, aby uzyskać element hosta, który reprezentuje pierwszy arkusz w skoroszycie, a następnie definiuje <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolkę dla aktualnie zaznaczonej komórki lub komórek.

     [!code-csharp[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#3)]
     [!code-vb[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#3)]

7. W Projektancie wstążki kliknij dwukrotnie pozycję **listaobject**.

8. Zastąp `ListObject_Click` procedurę obsługi zdarzeń poniższym kodem.

     Ten kod używa `GetVstoObject` metody, aby uzyskać element hosta, który reprezentuje pierwszy arkusz w skoroszycie, a następnie definiuje <xref:Microsoft.Office.Tools.Excel.ListObject> dla aktualnie zaznaczonej komórki lub komórek.

     [!code-csharp[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#4)]
     [!code-vb[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#4)]

9. Dodaj następujące instrukcje na górze pliku kodu wstążki.

     [!code-csharp[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#1)]
     [!code-vb[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#1)]

## <a name="remove-controls-from-the-worksheet"></a>Usuń kontrolki z arkusza
 Kontrolki nie są utrwalane, gdy arkusz jest zapisywany i zamykany. Należy programowo usunąć wszystkie wygenerowane Windows Forms kontrolki przed zapisaniem arkusza lub po ponownym otwarciu skoroszytu zostanie wyświetlony tylko kontur formantu. Dodaj kod do <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> zdarzenia, które usuwa Windows Forms kontrolki z kolekcji Controls wygenerowanego elementu hosta. Aby uzyskać więcej informacji, zobacz [Utrwalanie formantów dynamicznych w dokumentach pakietu Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

### <a name="to-remove-controls-from-the-worksheet"></a>Aby usunąć kontrolki z arkusza

1. W **Eksplorator rozwiązań**wybierz pozycję *ThisAddIn.cs* lub *ThisAddIn. vb*.

2. W menu **Widok** kliknij polecenie **kod**.

3. Dodaj następującą metodę do `ThisAddIn` klasy. Ten kod pobiera pierwszy arkusz w skoroszycie, a następnie używa `HasVstoObject` metody do sprawdzenia, czy arkusz zawiera wygenerowany obiekt arkusza. Jeśli wygenerowany obiekt arkusza ma kontrolki, kod pobiera ten obiekt arkusza i wykonuje iterację w kolekcji formantów, usuwając kontrolki.

     [!code-csharp[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#6)]
     [!code-vb[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#6)]

4. W języku C# należy utworzyć procedurę obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> zdarzenia. Możesz umieścić ten kod w `ThisAddIn_Startup` metodzie. Aby uzyskać więcej informacji na temat tworzenia programów obsługi zdarzeń, zobacz [How to: Create Event Handles in Office projects](../vsto/how-to-create-event-handlers-in-office-projects.md). Zastąp metodę `ThisAddIn_Startup` następującym kodem.

     [!code-csharp[Trin_Excel_Dynamic_Controls#5](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#5)]

## <a name="test-the-solution"></a>Testowanie rozwiązania
 Dodaj formanty do arkusza, wybierając je z karty niestandardowej na Wstążce. Po zapisaniu arkusza te kontrolki są usuwane.

### <a name="to-test-the-solution"></a>W celu przetestowania rozwiązania.

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

2. Zaznacz dowolną komórkę w arkuszu Arkusz1.

3. Kliknij kartę **Dodatki** .

4. W grupie **grupa1** kliknij **przycisk**.

     Zostanie wyświetlony przycisk w zaznaczonej komórce.

5. Wybierz inną komórkę w arkuszu Arkusz1.

6. W grupie **grupa1** kliknij pozycję **NamedRange**.

     Nazwany zakres jest zdefiniowany dla zaznaczonej komórki.

7. Wybierz serię komórek w arkuszu Arkusz1.

8. W grupie **grupa1** kliknij pozycję **ListObject**.

     Dodano obiekt listy dla zaznaczonych komórek.

9. Zapisz arkusz.

     Kontrolki dodane do Arkusz1 nie są już wyświetlane.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat kontrolek w projektach dodatku narzędzi VSTO programu Excel można znaleźć w tym temacie:

- Aby dowiedzieć się więcej o sposobach zapisywania formantów w arkuszu, zobacz przykład formantów dynamicznych dodatku VSTO programu Excel w temacie [przykłady i Instruktaże dotyczące programowania w pakiecie Office](../vsto/office-development-samples-and-walkthroughs.md).

## <a name="see-also"></a>Zobacz też
- [Rozwiązania programu Excel](../vsto/excel-solutions.md)
- [Kontrolki formularzy Windows Forms w dokumentach pakietu Office — omówienie](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [NamedRange — formant](../vsto/namedrange-control.md)
- [ListObject — formant](../vsto/listobject-control.md)
