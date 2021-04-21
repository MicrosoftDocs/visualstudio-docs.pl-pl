---
title: Dodawanie kontrolek do dokumentu w czasie rzeczywistym w dodatku VSTO
description: Dowiedz się, jak za pomocą wstążki umożliwić użytkownikom dodawanie klasy Button lub interfejsu RichTextContentControl do dokumentu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], adding controls
- application-level add-ins [Office development in Visual Studio], adding controls
- controls [Office development in Visual Studio], adding to documents at run time
- documents [Office development in Visual Studio], adding controls at run time
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c2088a4d2ca81418ca16b51b53b0af38595d75b2
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825397"
---
# <a name="walkthrough-add-controls-to-a-document-at-run-time-in-a-vsto-add-in"></a>Przewodnik: dodawanie kontrolek do dokumentu w czasie rzeczywistym w dodatku VSTO
  Kontrolki można dodawać do dowolnego otwartego Microsoft Office programu Word przy użyciu dodatku VSTO. W tym przewodniku pokazano, jak za pomocą wstążki umożliwić użytkownikom dodawanie do dokumentu plików <xref:Microsoft.Office.Tools.Word.Controls.Button> <xref:Microsoft.Office.Tools.Word.RichTextContentControl> lub .

 **Dotyczy:** Informacje zawarte w tym temacie dotyczą projektów dodatków VSTO dla programu Word 2010. Aby uzyskać więcej informacji, zobacz [Dostępne funkcje uporządkowane według aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie nowego projektu dodatku Word VSTO.

- Udostępnianie interfejsu użytkownika do dodawania kontrolek do dokumentu.

- Dodawanie kontrolek do dokumentu w czasie uruchamiania.

- Usuwanie kontrolek z dokumentu.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-a-new-word-add-in-project"></a>Tworzenie nowego projektu dodatku programu Word
 Rozpocznij od utworzenia projektu dodatku Word VSTO.

### <a name="to-create-a-new-word-vsto-add-in-project"></a>Aby utworzyć nowy projekt dodatku Word VSTO

1. Utwórz projekt dodatku VSTO dla programu Word o nazwie **WordDynamicControls**. Aby uzyskać więcej informacji, [zobacz How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Dodaj odwołanie do **zestawuMicrosoft.Office.Tools.Word.v4.0.Utilities.dll.** To odwołanie jest wymagane, aby programowo dodać kontrolkę Windows Forms do dokumentu w dalszej części tego przewodnika.

## <a name="provide-a-ui-to-add-controls-to-a-document"></a>Zapewnianie interfejsu użytkownika do dodawania kontrolek do dokumentu
 Dodaj kartę niestandardową do wstążki w programie Word. Użytkownicy mogą zaznaczyć pola wyboru na karcie, aby dodać kontrolki do dokumentu.

### <a name="to-provide-a-ui-to-add-controls-to-a-document"></a>Aby udostępnić interfejs użytkownika do dodawania kontrolek do dokumentu

1. W menu **Project (Projekt)** kliknij pozycję **Add New Item (Dodaj nowy element).**

2. W **oknie dialogowym Dodawanie nowego** elementu wybierz pozycję **Wstążka (Projektant wizualny).**

3. Zmień nazwę nowej wstążki na **MyRibbon** i kliknij przycisk **Dodaj**.

    Plik **MyRibbon.cs** lub **MyRibbon.vb** zostanie otwarty w Projektancie wstążki i zostanie wyświetlona domyślna karta i grupa.

4. W Projektancie wstążki kliknij **grupę group1.**

5. W **oknie Właściwości** zmień właściwość **Etykieta** dla **grupy group1** na **Dodaj kontrolki**.

6. Na karcie **Kontrolki wstążki pakietu Office** w **przyborniku** przeciągnij kontrolkę **CheckBox** do **grupy 1**.

7. Kliknij **pozycję CheckBox1,** aby ją zaznaczyć.

8. W **oknie** Właściwości zmień następujące właściwości.

   | Właściwość | Wartość |
   |-----------|-----------------------|
   | **Nazwa** | **addButtonCheckBox** |
   | **Etykieta** | **Dodaj przycisk** |

9. Dodaj drugie pole wyboru do **grupy group1**, a następnie zmień następujące właściwości.

   | Właściwość | Wartość |
   |-----------|---------------------------|
   | **Nazwa** | **addRichTextCheckBox** |
   | **Etykieta** | **Dodawanie kontrolki tekstu sformatowanego** |

10. W Projektancie wstążki kliknij dwukrotnie **przycisk Dodaj.**

     Procedura <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> obsługi zdarzeń pola wyboru Dodaj **przycisk** zostanie otwarta w Edytorze kodu.

11. Wróć do Projektanta wstążki i kliknij dwukrotnie pozycję **Dodaj kontrolkę tekstu sformatowanego.**

     Procedura <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> obsługi zdarzeń kontrolki Dodaj **kontrolkę tekstu** sformatowanego zostanie otwarta w Edytorze kodu.

    W dalszej części tego przewodnika dodasz kod do tych programów obsługi zdarzeń, aby dodać i usunąć kontrolki w aktywnym dokumencie.

## <a name="add-and-remove-controls-on-the-active-document"></a>Dodawanie i usuwanie kontrolek w aktywnym dokumencie
 W kodzie dodatku VSTO przed dodaniu kontrolki należy przekonwertować aktywny dokument na element <xref:Microsoft.Office.Tools.Word.Document>  hosta. W rozwiązaniach pakietu Office zarządzane kontrolki można dodawać tylko do elementów hosta, które działają jako kontenery kontrolek. W projektach dodatków VSTO elementy hosta można tworzyć w czasie działania przy użyciu `GetVstoObject` metody .

 Dodaj metody do klasy , które mogą być wywoływane w celu dodania lub usunięcia klasy `ThisAddIn` <xref:Microsoft.Office.Tools.Word.Controls.Button> lub w aktywnym <xref:Microsoft.Office.Tools.Word.RichTextContentControl> dokumencie. W dalszej części tego przewodnika wywołasz te metody z procedury obsługi zdarzeń pól wyboru <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> na wstążce.

### <a name="to-add-and-remove-controls-on-the-active-document"></a>Aby dodać i usunąć kontrolki w aktywnym dokumencie

1. W **Eksplorator rozwiązań** kliknij dwukrotnie plik *ThisAddIn.cs* lub *ThisAddIn.vb,* aby otworzyć plik w Edytorze kodu.

2. Dodaj poniższy kod do klasy `ThisAddIn`. Ten kod <xref:Microsoft.Office.Tools.Word.Controls.Button> deklaruje obiekty i <xref:Microsoft.Office.Tools.Word.RichTextContentControl> reprezentujące kontrolki, które zostaną dodane do dokumentu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs" id="Snippet1":::

3. Dodaj następującą metodę do `ThisAddIn` klasy . Gdy użytkownik kliknie  pole wyboru Dodaj przycisk na wstążce, ta metoda doda element do bieżącego zaznaczenia w dokumencie, jeśli to pole wyboru jest zaznaczone, lub usunie zaznaczenie pola <xref:Microsoft.Office.Tools.Word.Controls.Button> <xref:Microsoft.Office.Tools.Word.Controls.Button> wyboru.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs" id="Snippet2":::

4. Dodaj następującą metodę do `ThisAddIn` klasy . Gdy użytkownik kliknie  pole wyboru Dodaj kontrolkę tekstu sformatowanego na wstążce, ta metoda doda element do bieżącego zaznaczenia w dokumencie, jeśli to pole wyboru jest zaznaczone, lub usunie zaznaczenie pola <xref:Microsoft.Office.Tools.Word.RichTextContentControl> <xref:Microsoft.Office.Tools.Word.RichTextContentControl> wyboru.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs" id="Snippet3":::

## <a name="remove-the-button-control-when-the-document-is-saved"></a>Usuwanie kontrolki Przycisk po zapisaniu dokumentu
 Windows Forms formanty nie są utrwalane, gdy dokument jest zapisywany, a następnie zamykany. Jednak otoka ActiveX dla każdej kontrolki pozostaje w dokumencie, a obramowanie tej otoki jest widoczne dla użytkowników końcowych po ponownym otwarciu dokumentu. Istnieje kilka sposobów czyszczenia dynamicznie utworzonych kontrolek Windows Forms w dodatki VSTO. W tym przewodniku programowo usuniesz <xref:Microsoft.Office.Tools.Word.Controls.Button> kontrolkę po zapisaniu dokumentu.

### <a name="to-remove-the-button-control-when-the-document-is-saved"></a>Aby usunąć kontrolkę Przycisk po zapisaniu dokumentu

1. W pliku *kodu ThisAddIn.cs* lub *ThisAddIn.vb* dodaj następującą metodę do `ThisAddIn` klasy . Ta metoda jest programem obsługi zdarzeń <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> dla zdarzenia. Jeśli zapisany dokument ma skojarzony z nim element hosta, program obsługi zdarzeń pobiera element hosta i usuwa <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Tools.Word.Controls.Button> kontrolkę, jeśli istnieje.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs" id="Snippet4":::

2. W języku C# dodaj następujący kod do procedury `ThisAddIn_Startup` obsługi zdarzeń. Ten kod jest wymagany w języku C#, aby połączyć program `Application_DocumentBeforeSave` obsługi zdarzeń ze <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> zdarzeniem.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs" id="Snippet5":::

## <a name="add-and-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Dodawanie i usuwanie kontrolek, gdy użytkownik kliknie pola wyboru na wstążce
 Na koniec zmodyfikuj procedury obsługi zdarzeń pól wyboru dodanych do wstążki, aby dodać <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> lub usunąć kontrolki w dokumencie.

### <a name="to-add-or-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Aby dodać lub usunąć kontrolki, gdy użytkownik kliknie pola wyboru na wstążce

1. W pliku *kodu MyRibbon.cs* lub *MyRibbon.vb* zastąp wygenerowane procedury obsługi zdarzeń i `addButtonCheckBox_Click` następującym `addRichTextCheckBox_Click` kodem. Ten kod ponownie definiuje te programy obsługi zdarzeń w celu wywołania metod i dodanych do klasy `ToggleButtonOnDocument` `ToggleRichTextControlOnDocument` wcześniej w tym `ThisAddIn` przewodniku.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.vb" id="Snippet6":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.cs" id="Snippet6":::

## <a name="test-the-solution"></a>Testowanie rozwiązania
 Dodaj kontrolki do dokumentu, wybierając je na karcie niestandardowej na wstążce. Po zapisaniu dokumentu <xref:Microsoft.Office.Tools.Word.Controls.Button> kontrolka zostanie usunięta.

### <a name="to-test-the-solution"></a>Aby przetestować rozwiązanie.

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

2. W aktywnym dokumencie naciśnij klawisz **Enter** kilka razy, aby dodać do dokumentu nowe puste akapity.

3. Wybierz pierwszy akapit.

4. Kliknij **kartę Dodatki.**

5. W grupie **Dodaj kontrolki** kliknij przycisk **Dodaj.**

     W pierwszym akapicie zostanie wyświetlony przycisk.

6. Wybierz ostatni akapit.

7. W grupie **Dodaj kontrolki** kliknij pozycję **Dodaj kontrolkę tekstu sformatowanego.**

     Kontrolka zawartości tekstu sformatowanego jest dodawana do ostatniego akapitu.

8. Zapisz dokument.

     Przycisk zostanie usunięty z dokumentu.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat kontrolek w dodatki VSTO można znaleźć w tych tematach:

- Przykład, który demonstruje sposób dodawania wielu innych typów kontrolek do dokumentu w czasie uruchamiania i ponownego tworzenia kontrolek po ponownym otwarciu dokumentu, zobacz Przykład formantów dynamicznych programu Word Add-In na stronie Office development samples and walkthroughs (Przykład formantów dynamicznych programu Word Add-In na stronie Office development samples and walkthroughs (Przykład formantów dynamicznych programu Word Add-In na stronie Office development samples and [walkthroughs](../vsto/office-development-samples-and-walkthroughs.md)(Przykład formantów dynamicznych programu Word).

- Aby uzyskać przewodnik, który pokazuje, jak dodać kontrolki do arkusza przy użyciu dodatku VSTO dla programu Excel, zobacz Przewodnik: Dodawanie kontrolek do arkusza w czasie uruchamiania w projekcie dodatku [narzędzia VSTO.](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md)

## <a name="see-also"></a>Zobacz też
- [Rozwiązania programu Word](../vsto/word-solutions.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie rzeczywistym](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Utrwalanie kontrolek dynamicznych w dokumentach pakietu Office](../vsto/persisting-dynamic-controls-in-office-documents.md)
- [How to: Add Windows Forms controls to Office documents (2017: Dodawanie kontrolek Windows Forms do dokumentów pakietu Office)](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [2017: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w czasie uruchamiania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
