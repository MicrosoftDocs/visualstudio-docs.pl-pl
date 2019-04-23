---
title: 'Przewodnik: Dodawanie formantów do arkusza w czasie wykonywania w projekcie dodatku narzędzi VSTO'
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
ms.openlocfilehash: 04de1e652aae1de91695029c9af66c4ad331f789
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60096780"
---
# <a name="walkthrough-add-controls-to-a-worksheet-at-runtime-in-vsto-add-in-project"></a>Przewodnik: Dodawanie formantów do arkusza w czasie wykonywania w projekcie dodatku narzędzi VSTO
  Aby dodać formanty do żadnych otwartych arkusza, przy użyciu dodatku narzędzi VSTO dla programu Excel. W tym instruktażu przedstawiono sposób użycia wstążki umożliwiające użytkownikom dodawanie <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange>, a <xref:Microsoft.Office.Tools.Excel.ListObject> do arkusza. Aby uzyskać informacje, zobacz [dodawanie formantów do dokumentów pakietu Office w środowisku uruchomieniowym](../vsto/adding-controls-to-office-documents-at-run-time.md).

 **Dotyczy:** Informacje przedstawione w tym temacie dotyczą projektów dodatku VSTO dla programu Excel. Aby uzyskać więcej informacji, zobacz [Dostępne funkcje uporządkowane według aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).

 W instruktażu przedstawiono następujące zagadnienia:

- Dostarczanie interfejsu użytkownika (UI), aby dodać formanty do arkusza.

- Dodawanie formantów do arkusza.

- Usuwanie kontrolek z arkusza.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Excel

## <a name="create-a-new-excel-vsto-add-in-project"></a>Utwórz nowy projekt dodatku narzędzi VSTO programu Excel
 Rozpocznij od utworzenia projektu dodatku narzędzi VSTO programu Excel.

### <a name="to-create-a-new-excel-vsto-add-in-project"></a>Aby utworzyć nowy projekt dodatku narzędzi VSTO programu Excel

1. W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], Utwórz projekt dodatku narzędzi VSTO programu Excel o nazwie **ExcelDynamicControls**. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w programie Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Dodaj odwołanie do **Microsoft.Office.Tools.Excel.v4.0.Utilities.dll** zestawu. To odwołanie jest wymagane, aby programowo dodać formant programu Windows Forms do arkusza w dalszej części tego przewodnika.

## <a name="provide-a-ui-to-add-controls-to-a-worksheet"></a>Udostępniają interfejs użytkownika do dodawania formantów do arkusza
 Dodaj kartę niestandardową do Wstążki programu Excel. Użytkownicy mogą wybrać pola wyboru na karcie na dodawanie formantów do arkusza.

#### <a name="to-provide-a-ui-to-add-controls-to-a-worksheet"></a>Aby zapewnić interfejsu użytkownika do dodawania formantów do arkusza

1. Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.

2. W **Dodaj nowy element** okno dialogowe, wybierz opcję **Wstążka (Projektant graficzny)**, a następnie kliknij przycisk **Dodaj**.

     Plik o nazwie **Ribbon1.cs** lub **Ribbon1.vb** zostanie otwarty w Projektancie Wstążki i wyświetla domyślną kartę i grupę.

3. Z **formanty wstążki Office** karcie **przybornika**, przeciągnij formant pola wyboru na **grupa1**.

4. Kliknij przycisk **CheckBox1** aby go zaznaczyć.

5. W **właściwości** okna, Zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**Przycisk**|
    |**Etykieta**|**Przycisk**|

6. Drugie pole wyboru, aby dodać **grupa1**, a następnie Zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**NamedRange**|
    |**Etykieta**|**NamedRange**|

7. Dodaj trzecie pole wyboru, aby **grupa1**, a następnie Zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**ListObject**|
    |**Etykieta**|**ListObject**|

## <a name="add-controls-to-the-worksheet"></a>Dodawanie formantów do arkusza
 Zarządzane formanty można dodać tylko do elementów hosta, które działają jak kontenery. Ponieważ projekty dodatków narzędzi VSTO dla programów pracować z dowolnego otwartego skoroszytu, to dodatku narzędzi VSTO konwertuje element hosta arkusza lub pobiera istniejący element hosta, przed dodaniem formantu. Dodaj kod do obsługi zdarzeń kliknięcie każdego formantu, aby wygenerować <xref:Microsoft.Office.Tools.Excel.Worksheet> element hosta, który jest oparty na otwieranie arkusza. Następnie należy dodać <xref:Microsoft.Office.Tools.Excel.Controls.Button>, <xref:Microsoft.Office.Tools.Excel.NamedRange>, a <xref:Microsoft.Office.Tools.Excel.ListObject> na bieżące zaznaczenie w arkuszu.

### <a name="to-add-controls-to-a-worksheet"></a>Aby dodać formanty do arkusza

1. W Projektancie wstążki, kliknij dwukrotnie **przycisk**.

     <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> Program obsługi zdarzeń **przycisk** pola wyboru zostanie otwarty w edytorze kodu.

2. Zastąp `Button_Click` programu obsługi zdarzeń z następującym kodem.

     Ten kod używa `GetVstoObject` metodę, aby uzyskać element hosta, który reprezentuje pierwszy arkusz w skoroszycie, a następnie dodaje <xref:Microsoft.Office.Tools.Excel.Controls.Button> kontrolki aktualnie zaznaczonej komórki.

     [!code-csharp[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#2)]
     [!code-vb[Trin_Excel_Dynamic_Controls#2](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#2)]

3. W **Eksploratora rozwiązań**, wybierz opcję *Ribbon1.cs* lub *Ribbon1.vb*.

4. Na **widoku** menu, kliknij przycisk **projektanta**.

5. W Projektancie wstążki, kliknij dwukrotnie **NamedRange**.

6. Zastąp `NamedRange_Click` programu obsługi zdarzeń z następującym kodem.

     Ten kod używa `GetVstoObject` metodę, aby uzyskać element hosta, który reprezentuje pierwszy arkusz w skoroszycie, a następnie definiuje <xref:Microsoft.Office.Tools.Excel.NamedRange> kontroli dla aktualnie wybranego komórkę lub komórki.

     [!code-csharp[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#3)]
     [!code-vb[Trin_Excel_Dynamic_Controls#3](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#3)]

7. W Projektancie wstążki, kliknij dwukrotnie **ListObject**.

8. Zastąp `ListObject_Click` programu obsługi zdarzeń z następującym kodem.

     Ten kod używa `GetVstoObject` metodę, aby uzyskać element hosta, który reprezentuje pierwszy arkusz w skoroszycie, a następnie definiuje <xref:Microsoft.Office.Tools.Excel.ListObject> dla aktualnie wybranego komórkę lub komórki.

     [!code-csharp[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#4)]
     [!code-vb[Trin_Excel_Dynamic_Controls#4](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#4)]

9. Dodaj następujące instrukcje na górze pliku kodu wstążki.

     [!code-csharp[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs#1)]
     [!code-vb[Trin_Excel_Dynamic_Controls#1](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb#1)]

## <a name="remove-controls-from-the-worksheet"></a>Usuń kontrolki z arkusza
 Formanty nie są zachowywane, jeśli arkusz zostanie zapisany i zamknięte. Wszystkie kontrolki Windows Forms wygenerowanym należy usunąć programowe, zanim arkusz jest zapisywany lub tylko konspektu kontrolki będą wyświetlane, gdy ponownie otworzyć skoroszytu. Dodaj kod, aby <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> zdarzenia, które usuwa kontrolek formularzy Windows Forms z kolekcji kontrolek hosta wygenerowanego elementu. Aby uzyskać więcej informacji, zobacz [kontrolek dynamicznych w dokumentach pakietu Office utrwalenia](../vsto/persisting-dynamic-controls-in-office-documents.md).

### <a name="to-remove-controls-from-the-worksheet"></a>Aby usunąć kontrolki arkusza

1. W **Eksploratora rozwiązań**, wybierz opcję *ThisAddIn.cs* lub *ThisAddIn.vb*.

2. Na **widoku** menu, kliknij przycisk **kodu**.

3. Dodaj następującą metodę do `ThisAddIn` klasy. Ten kod pobiera pierwszego arkusza w skoroszycie, a następnie używa `HasVstoObject` metodę, aby sprawdzić, czy arkusz ma obiekt arkusza wygenerowany. Jeśli obiekt arkusza wygenerowanego zawiera formanty, kod pobiera obiekt tego arkusza i iteruje po kolekcji kontroli, usuwanie kontrolki.

     [!code-csharp[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#6)]
     [!code-vb[Trin_Excel_Dynamic_Controls#6](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#6)]

4. W C#, należy utworzyć program obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> zdarzeń. Możesz umieścić ten kod w `ThisAddIn_Startup` metody. Aby uzyskać więcej informacji na temat tworzenia procedury obsługi zdarzeń, zobacz [jak: Tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md). Zastąp `ThisAddIn_Startup` metoda następującym kodem.

     [!code-csharp[Trin_Excel_Dynamic_Controls#5](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#5)]

## <a name="test-the-solution"></a>Testowanie rozwiązania
 Dodawanie formantów do arkusza, wybierając je z niestandardowej karty na Wstążce. Po zapisaniu arkusza te kontrolki są usuwane.

### <a name="to-test-the-solution"></a>Do przetestowania rozwiązania.

1. Naciśnij klawisz **F5** Aby uruchomić projekt.

2. Wybierz dowolną komórkę w arkuszu 1.

3. Kliknij przycisk **Add-Ins** kartę.

4. W **grupa1** grupy, kliknij przycisk **przycisk**.

     Przycisk pojawia się w zaznaczonej komórki.

5. Wybierz inną komórkę w arkuszu 1.

6. W **grupa1** grupy, kliknij przycisk **NamedRange**.

     Nazwany zakres jest zdefiniowana dla zaznaczonej komórki.

7. Wybierz serię komórek w arkuszu 1.

8. W **grupa1** grupy, kliknij przycisk **ListObject**.

     Obiekt listy jest dodawany dla zaznaczonych komórek.

9. Zapisz arkusz.

     Formanty, które zostały dodane do Arkusz1 nie jest już wyświetlane.

## <a name="next-steps"></a>Następne kroki
 Możesz dowiedzieć się więcej informacji na temat formantów w projektach dodatku narzędzi VSTO programu Excel z tego tematu:

- Aby dowiedzieć się więcej na temat zapisywania kontrolek do arkusza, zobacz VSTO programu Excel dodatek dynamicznej formantów próbki w [Office development ― przykłady i wskazówki dotyczące](../vsto/office-development-samples-and-walkthroughs.md).

## <a name="see-also"></a>Zobacz także
- [Rozwiązania programu Excel](../vsto/excel-solutions.md)
- [Windows forms, formanty na przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Namedrange — formant](../vsto/namedrange-control.md)
- [ListObject — formant](../vsto/listobject-control.md)
