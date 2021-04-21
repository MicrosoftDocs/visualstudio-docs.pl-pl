---
title: Dodawanie kontrolek do arkusza w czasie uruchamiania w projekcie dodatku VSTO
description: Dowiedz się, jak za pomocą wstążki umożliwić użytkownikom dodawanie do arkusza elementów Button, NamedRange i ListObject.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 178180e8c698ca56b15e46bcbe65877d68c6b2a1
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824682"
---
# <a name="walkthrough-add-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project"></a>Przewodnik: Dodawanie kontrolek do arkusza w czasie uruchamiania w projekcie dodatku VSTO
  Kontrolki można dodawać do dowolnego otwartego arkusza za pomocą dodatku VSTO programu Excel. W tym przewodniku pokazano, jak za pomocą wstążki umożliwić użytkownikom dodawanie do arkusza , <xref:Microsoft.Office.Tools.Excel.Controls.Button> <xref:Microsoft.Office.Tools.Excel.NamedRange> i <xref:Microsoft.Office.Tools.Excel.ListObject> . Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie rzeczywistym.](../vsto/adding-controls-to-office-documents-at-run-time.md)

 **Dotyczy:** Informacje zawarte w tym temacie dotyczą projektów dodatków VSTO dla programu Excel. Aby uzyskać więcej informacji, zobacz [Dostępne funkcje uporządkowane według aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).

 W instruktażu przedstawiono następujące zagadnienia:

- Udostępnianie interfejsu użytkownika do dodawania kontrolek do arkusza.

- Dodawanie kontrolek do arkusza.

- Usuwanie kontrolek z arkusza.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Excel

## <a name="create-a-new-excel-vsto-add-in-project"></a>Tworzenie nowego projektu dodatku VSTO programu Excel
 Rozpocznij od utworzenia projektu dodatku VSTO dla programu Excel.

### <a name="to-create-a-new-excel-vsto-add-in-project"></a>Aby utworzyć nowy projekt dodatku VSTO programu Excel

1. W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pliku utwórz projekt dodatku Excel VSTO o nazwie **ExcelDynamicControls**. Aby uzyskać więcej informacji, [zobacz How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Dodaj odwołanie do **zestawuMicrosoft.Office.Tools.Excel.v4.0.Utilities.dll.** To odwołanie jest wymagane, aby programowo dodać kontrolkę Windows Forms do arkusza w dalszej części tego przewodnika.

## <a name="provide-a-ui-to-add-controls-to-a-worksheet"></a>Zapewnienie interfejsu użytkownika w celu dodania kontrolek do arkusza
 Dodaj kartę niestandardową do wstążki programu Excel. Użytkownicy mogą zaznaczać pola wyboru na karcie, aby dodać kontrolki do arkusza.

#### <a name="to-provide-a-ui-to-add-controls-to-a-worksheet"></a>Aby udostępnić interfejs użytkownika do dodawania kontrolek do arkusza

1. W menu **Project (Projekt)** kliknij **pozycję Add New Item (Dodaj nowy element).**

2. W **oknie dialogowym Dodawanie nowego** elementu wybierz pozycję **Wstążka (Projektant wizualny),** a następnie kliknij przycisk **Dodaj**.

     Plik o nazwie **Ribbon1.cs** lub **Ribbon1.vb** zostanie otwarty w Projektancie wstążki i wyświetli domyślną kartę i grupę.

3. Na karcie **Kontrolki wstążki pakietu Office** **przybornika** przeciągnij kontrolkę CheckBox do **grupy 1.**

4. Kliknij **pozycję CheckBox1,** aby ją zaznaczyć.

5. W **oknie** Właściwości zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**Przycisk**|
    |**Etykieta**|**Przycisk**|

6. Dodaj drugie pole wyboru do **grupy group1**, a następnie zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**Namedrange**|
    |**Etykieta**|**Namedrange**|

7. Dodaj trzecie pole wyboru do **grupy group1**, a następnie zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**Listobject**|
    |**Etykieta**|**Listobject**|

## <a name="add-controls-to-the-worksheet"></a>Dodawanie kontrolek do arkusza
 Zarządzane kontrolki można dodawać tylko do elementów hosta, które działają jako kontenery. Ponieważ projekty dodatków VSTO działają z dowolnym otwartym skoroszytem, dodatek VSTO konwertuje arkusz na element hosta lub pobiera istniejący element hosta przed dodaniem kontrolki. Dodaj kod do obsługi zdarzeń kliknięcia każdej kontrolki, aby wygenerować element hosta, który jest <xref:Microsoft.Office.Tools.Excel.Worksheet> oparty na otwartym arkuszu. Następnie dodaj , <xref:Microsoft.Office.Tools.Excel.Controls.Button> a i przy bieżącym <xref:Microsoft.Office.Tools.Excel.NamedRange> <xref:Microsoft.Office.Tools.Excel.ListObject> zaznaczeniu w arkuszu.

### <a name="to-add-controls-to-a-worksheet"></a>Aby dodać kontrolki do arkusza

1. W Projektancie wstążki kliknij **dwukrotnie** przycisk .

     Procedura <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> obsługi zdarzeń **przycisku** jest otwierana w Edytorze kodu.

2. Zastąp program `Button_Click` obsługi zdarzeń następującym kodem.

     Ten kod używa metody w celu uzyskania elementu hosta reprezentującego pierwszy arkusz w skoroszycie, a następnie dodaje kontrolkę `GetVstoObject` <xref:Microsoft.Office.Tools.Excel.Controls.Button> do aktualnie wybranej komórki.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb" id="Snippet2":::

3. W **Eksplorator rozwiązań** wybierz pozycję *Ribbon1.cs* lub *Ribbon1.vb.*

4. W menu **Widok** kliknij pozycję **Projektant.**

5. W Projektancie wstążki kliknij dwukrotnie pozycję **NamedRange**.

6. Zastąp program `NamedRange_Click` obsługi zdarzeń następującym kodem.

     Ten kod używa metody w celu uzyskania elementu hosta reprezentującego pierwszy arkusz w skoroszycie, a następnie definiuje kontrolkę dla aktualnie `GetVstoObject` <xref:Microsoft.Office.Tools.Excel.NamedRange> wybranej komórki lub komórek.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb" id="Snippet3":::

7. W Projektancie wstążki kliknij dwukrotnie **pozycję ListObject.**

8. Zastąp program `ListObject_Click` obsługi zdarzeń następującym kodem.

     Ten kod używa metody w celu uzyskania elementu hosta reprezentującego pierwszy arkusz w skoroszycie, a następnie definiuje element dla aktualnie `GetVstoObject` <xref:Microsoft.Office.Tools.Excel.ListObject> wybranej komórki lub komórek.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb" id="Snippet4":::

9. Dodaj następujące instrukcje na początku pliku kodu wstążki.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/Ribbon1.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/Ribbon1.vb" id="Snippet1":::

## <a name="remove-controls-from-the-worksheet"></a>Usuwanie kontrolek z arkusza
 Kontrolki nie są utrwalane po zapisaniu i zamknięciu arkusza. Należy programowo usunąć wszystkie wygenerowane kontrolki Windows Forms przed zapisaniem arkusza lub gdy skoroszyt zostanie ponownie otwarty, zostanie wyświetlony tylko kontur kontrolki. Dodaj do zdarzenia kod, który Windows Forms kontrolki z kolekcji <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> kontrolek wygenerowanego elementu hosta. Aby uzyskać więcej informacji, zobacz [Utrwalanie kontrolek dynamicznych w dokumentach pakietu Office.](../vsto/persisting-dynamic-controls-in-office-documents.md)

### <a name="to-remove-controls-from-the-worksheet"></a>Aby usunąć kontrolki z arkusza

1. W **Eksplorator rozwiązań** wybierz pozycję *ThisAddIn.cs lub* *ThisAddIn.vb.*

2. W menu **Widok** kliknij pozycję **Kod**.

3. Dodaj następującą metodę do `ThisAddIn` klasy . Ten kod pobiera pierwszy arkusz w skoroszycie, a następnie używa metody , aby sprawdzić, czy arkusz ma `HasVstoObject` wygenerowany obiekt arkusza. Jeśli wygenerowany obiekt arkusza zawiera kontrolki, kod pobiera ten obiekt arkusza i iteruje po kolekcji kontrolek, usuwając kontrolki.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb" id="Snippet6":::

4. W języku C# należy utworzyć program obsługi zdarzeń <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookBeforeSave> dla zdarzenia. Ten kod można umieścić w `ThisAddIn_Startup` metodzie . Aby uzyskać więcej informacji na temat tworzenia programów obsługi zdarzeń, zobacz [Jak tworzyć procedury obsługi zdarzeń w projektach pakietu Office.](../vsto/how-to-create-event-handlers-in-office-projects.md) Zastąp metodę `ThisAddIn_Startup` następującym kodem.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs" id="Snippet5":::

## <a name="test-the-solution"></a>Testowanie rozwiązania
 Dodaj kontrolki do arkusza, zaznaczając je na karcie niestandardowej na wstążce. Po zapisaniu arkusza te kontrolki zostaną usunięte.

### <a name="to-test-the-solution"></a>Aby przetestować rozwiązanie.

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

2. Zaznacz dowolną komórkę w arkuszu Sheet1.

3. Kliknij **kartę Dodatki.**

4. W grupie **group1** kliknij **przycisk**.

     W wybranej komórce zostanie wyświetlony przycisk.

5. Wybierz inną komórkę w arkuszu Sheet1.

6. W grupie **group1** kliknij pozycję **NamedRange**.

     Nazwany zakres jest definiowany dla wybranej komórki.

7. Wybierz serię komórek w arkuszu Sheet1.

8. W grupie **group1** kliknij pozycję **ListObject**.

     Obiekt listy jest dodawany dla wybranych komórek.

9. Zapisz arkusz.

     Kontrolki dodane do arkusza Sheet1 nie są już wyświetlane.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat kontrolek w projektach dodatków VSTO programu Excel można znaleźć w tym temacie:

- Aby dowiedzieć się więcej na temat zapisywania kontrolek w arkuszu, zobacz przykładowe kontrolki dynamiczne dodatku VSTO programu Excel w przykładach dla developmentowych aplikacji [pakietu Office i przewodnikach.](../vsto/office-development-samples-and-walkthroughs.md)

## <a name="see-also"></a>Zobacz też
- [Rozwiązania programu Excel](../vsto/excel-solutions.md)
- [Kontrolki formularzy systemu Windows w dokumentach pakietu Office — omówienie](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Kontrolki w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [NamedRange, kontrolka](../vsto/namedrange-control.md)
- [ListObject, kontrolka](../vsto/listobject-control.md)
