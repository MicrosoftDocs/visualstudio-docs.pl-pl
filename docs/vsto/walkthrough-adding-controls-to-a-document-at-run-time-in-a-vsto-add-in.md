---
title: Dodawanie kontrolek do dokumentów w czasie wykonywania w dodatku narzędzi VSTO
description: Dowiedz się, jak za pomocą wstążki zezwolić użytkownikom na Dodawanie klasy przycisków lub interfejsu RichTextContentControl do dokumentu.
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
ms.openlocfilehash: 3cc88b5ee48241a15a66144c992936b55fb2acf3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838090"
---
# <a name="walkthrough-add-controls-to-a-document-at-run-time-in-a-vsto-add-in"></a>Przewodnik: Dodawanie kontrolek do dokumentu w czasie wykonywania w dodatku narzędzi VSTO
  Możesz dodać kontrolki do dowolnego otwartego dokumentu programu Microsoft Office Word przy użyciu dodatku VSTO. W tym instruktażu przedstawiono sposób użycia wstążki, aby umożliwić użytkownikom dodawanie <xref:Microsoft.Office.Tools.Word.Controls.Button> lub <xref:Microsoft.Office.Tools.Word.RichTextContentControl> do dokumentu.

 **Dotyczy:** Informacje przedstawione w tym temacie dotyczą projektów dodatku VSTO dla programu Word 2010. Aby uzyskać więcej informacji, zobacz [Dostępne funkcje uporządkowane według aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie nowego projektu dodatku VSTO programu Word.

- Udostępnienie interfejsu użytkownika (UI) do dodawania formantów do dokumentu.

- Dodawanie formantów do dokumentu w czasie wykonywania.

- Usuwanie kontrolek z dokumentu.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-a-new-word-add-in-project"></a>Utwórz nowy projekt dodatku programu Word
 Zacznij od utworzenia projektu dodatku VSTO dla programu Word.

### <a name="to-create-a-new-word-vsto-add-in-project"></a>Aby utworzyć nowy projekt dodatku VSTO programu Word

1. Utwórz projekt dodatku VSTO dla programu Word o nazwie **WordDynamicControls**. Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

2. Dodaj odwołanie do zestawu **Microsoft.Office.Tools.Word.v4.0.Utilities.dll** . Ta dokumentacja jest wymagana do programowego dodawania kontrolki Windows Forms do dokumentu w dalszej części tego przewodnika.

## <a name="provide-a-ui-to-add-controls-to-a-document"></a>Podaj interfejs użytkownika, aby dodać kontrolki do dokumentu
 Dodaj niestandardową kartę do wstążki w programie Word. Użytkownicy mogą zaznaczyć pola wyboru na karcie, aby dodać kontrolki do dokumentu.

### <a name="to-provide-a-ui-to-add-controls-to-a-document"></a>Aby zapewnić interfejs użytkownika do dodawania formantów do dokumentu

1. W menu **projekt** kliknij polecenie **Dodaj nowy element**.

2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **wstążka (projektant wizualny)**.

3. Zmień nazwę nowej wstążki **na Wstążkę, a** następnie kliknij przycisk **Dodaj**.

    Plik **MyRibbon.cs** lub **webwstążka. vb** zostanie otwarty w Projektancie wstążki i zostanie wyświetlona domyślna karta i Grupa.

4. W Projektancie wstążki kliknij grupę **grupa1** .

5. W oknie **Właściwości** , Zmień właściwość **etykieta** dla **grupa1** , aby **dodać kontrolki**.

6. Na karcie **kontrolki wstążki pakietu Office** w **przyborniku** przeciągnij kontrolkę **CheckBox** na **grupa1**.

7. Kliknij pozycję **checkBox1** , aby ją zaznaczyć.

8. W oknie **Właściwości** Zmień następujące właściwości.

   | Właściwość | Wartość |
   |-----------|-----------------------|
   | **Nazwa** | **addButtonCheckBox** |
   | **Etykieta** | **Przycisk Dodaj** |

9. Dodaj drugie pole wyboru do **grupa1**, a następnie Zmień następujące właściwości.

   | Właściwość | Wartość |
   |-----------|---------------------------|
   | **Nazwa** | **addRichTextCheckBox** |
   | **Etykieta** | **Dodaj formant tekstu sformatowanego** |

10. W Projektancie wstążki kliknij dwukrotnie przycisk **Dodaj**.

     <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click>Procedura obsługi zdarzeń pola wyboru **Dodaj przycisk** jest otwierana w edytorze kodu.

11. Wróć do projektanta wstążki, a następnie kliknij dwukrotnie przycisk **Dodaj formant tekstu sformatowanego**.

     <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click>Procedura obsługi zdarzeń okna dialogowego **Dodawanie tekstu sformatowanego** jest otwierana w edytorze kodu.

    W dalszej części tego instruktażu dodasz kod do tych programów obsługi zdarzeń w celu dodawania i usuwania kontrolek w aktywnym dokumencie.

## <a name="add-and-remove-controls-on-the-active-document"></a>Dodawanie i usuwanie formantów w aktywnym dokumencie
 Aby można było dodać kontrolkę, w kodzie dodatku narzędzi VSTO należy przekonwertować aktywny dokument na <xref:Microsoft.Office.Tools.Word.Document> *element hosta* . W rozwiązaniach pakietu Office formanty zarządzane można dodawać tylko do elementów hosta, które działają jako kontenery dla kontrolek. W projektach dodatku VSTO elementy hosta mogą być tworzone w czasie wykonywania przy użyciu `GetVstoObject` metody.

 Dodaj metody do `ThisAddIn` klasy, która może być wywoływana w celu dodania lub usunięcia <xref:Microsoft.Office.Tools.Word.Controls.Button> <xref:Microsoft.Office.Tools.Word.RichTextContentControl> aktywnego dokumentu. W dalszej części tego przewodnika te metody są wywoływane z <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> programów obsługi zdarzeń na Wstążce.

### <a name="to-add-and-remove-controls-on-the-active-document"></a>Aby dodać i usunąć kontrolki w aktywnym dokumencie

1. W **Eksplorator rozwiązań** kliknij dwukrotnie pozycję *ThisAddIn.cs* lub *ThisAddIn. vb* , aby otworzyć plik w edytorze kodu.

2. Dodaj poniższy kod do klasy `ThisAddIn`. Ten kod deklaruje <xref:Microsoft.Office.Tools.Word.Controls.Button> i <xref:Microsoft.Office.Tools.Word.RichTextContentControl> obiekty reprezentujące kontrolki, które zostaną dodane do dokumentu.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#1)]

3. Dodaj następującą metodę do `ThisAddIn` klasy. Gdy użytkownik kliknie pole wyboru **Dodaj przycisk** na Wstążce, ta metoda dodaje <xref:Microsoft.Office.Tools.Word.Controls.Button> do bieżącego zaznaczenia w dokumencie, jeśli pole wyboru jest zaznaczone, lub usuwa, <xref:Microsoft.Office.Tools.Word.Controls.Button> Jeśli pole wyboru jest wyczyszczone.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#2)]

4. Dodaj następującą metodę do `ThisAddIn` klasy. Gdy użytkownik kliknie pole wyboru **Dodaj formant tekstu sformatowanego** na Wstążce, ta metoda dodaje <xref:Microsoft.Office.Tools.Word.RichTextContentControl> do bieżącego zaznaczenia w dokumencie, jeśli pole wyboru jest zaznaczone, lub usuwa, <xref:Microsoft.Office.Tools.Word.RichTextContentControl> Jeśli pole wyboru jest wyczyszczone.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#3)]

## <a name="remove-the-button-control-when-the-document-is-saved"></a>Usuń kontrolkę przycisku, gdy dokument jest zapisywany
 Formanty Windows Forms nie są utrwalane, gdy dokument zostanie zapisany, a następnie zamknięty. Jednak otoka ActiveX dla każdej kontrolki pozostaje w dokumencie, a obramowanie tej otoki może być widoczne dla użytkowników końcowych po ponownym otwarciu dokumentu. Istnieje kilka sposobów czyszczenia dynamicznie utworzonych kontrolek Windows Forms w dodatkach narzędzi VSTO. W tym instruktażu program programowo usuwa <xref:Microsoft.Office.Tools.Word.Controls.Button> formant po zapisaniu dokumentu.

### <a name="to-remove-the-button-control-when-the-document-is-saved"></a>Aby usunąć formant przycisku, gdy dokument jest zapisywany

1. W pliku kodu *ThisAddIn.cs* lub *ThisAddIn. vb* Dodaj następującą metodę do `ThisAddIn` klasy. Ta metoda jest programem obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> zdarzenia. Jeśli zapisany dokument ma <xref:Microsoft.Office.Tools.Word.Document> skojarzony element hosta, program obsługi zdarzeń Pobiera element hosta i usuwa <xref:Microsoft.Office.Tools.Word.Controls.Button> formant, jeśli istnieje.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#4)]

2. W języku C# Dodaj następujący kod do `ThisAddIn_Startup` programu obsługi zdarzeń. Ten kod jest wymagany w języku C#, aby połączyć `Application_DocumentBeforeSave` program obsługi zdarzeń ze <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> zdarzeniem.

     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#5)]

## <a name="add-and-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Dodaj i Usuń kontrolki, gdy użytkownik kliknie pola wyboru na Wstążce
 Na koniec zmodyfikuj <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> programy obsługi zdarzeń, które zostały dodane do wstążki, aby dodać lub usunąć kontrolki dokumentu.

### <a name="to-add-or-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Aby dodać lub usunąć kontrolki, gdy użytkownik klika pola wyboru na Wstążce

1. W pliku kodu *MyRibbon.cs* lub *webwstążkę. vb* Zastąp wygenerowane `addButtonCheckBox_Click` i `addRichTextCheckBox_Click` obsługiwane procedury obsługi przy użyciu następującego kodu. Ten kod ponownie definiuje procedury obsługi zdarzeń w celu wywołania metod, `ToggleButtonOnDocument` `ToggleRichTextControlOnDocument` które zostały dodane do `ThisAddIn` klasy wcześniej w tym instruktażu.

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.vb#6)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.cs#6)]

## <a name="test-the-solution"></a>Testowanie rozwiązania
 Dodaj formanty do dokumentu, wybierając je z karty niestandardowej na Wstążce. Po zapisaniu dokumentu <xref:Microsoft.Office.Tools.Word.Controls.Button> formant zostanie usunięty.

### <a name="to-test-the-solution"></a>W celu przetestowania rozwiązania.

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

2. W aktywnym dokumencie, naciśnij klawisz **Enter** kilka razy, aby dodać nowe puste akapity do dokumentu.

3. Wybierz pierwszy akapit.

4. Kliknij kartę **Dodatki** .

5. W grupie **Dodawanie formantów** kliknij przycisk **Dodaj**.

     Przycisk pojawia się w pierwszym akapicie.

6. Zaznacz ostatni akapit.

7. W grupie **Dodawanie kontrolek** kliknij pozycję **Dodaj formant tekstu sformatowanego**.

     Do ostatniego akapitu zostanie dodany formant zawartości tekstu sformatowanego.

8. Zapisz dokument.

     Przycisk zostanie usunięty z dokumentu.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat kontrolek w dodatkach narzędzia VSTO można znaleźć w następujących tematach:

- Aby uzyskać przykład, który pokazuje, jak dodać wiele innych typów formantów do dokumentu w czasie wykonywania i ponownie utworzyć formanty po ponownym otwarciu dokumentu, zapoznaj się z artykułem {Add-In Dynamic Controls ( [przykłady i przewodniki dotyczące projektowania) w pakiecie Office](../vsto/office-development-samples-and-walkthroughs.md).

- Aby zapoznać się z przewodnikiem, który pokazuje, jak dodać kontrolki do arkusza przy użyciu dodatku VSTO dla programu Excel, zobacz [Przewodnik: Dodawanie kontrolek do arkusza w czasie wykonywania w projekcie dodatku VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md).

## <a name="see-also"></a>Zobacz też
- [Rozwiązania programu Word](../vsto/word-solutions.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Utrwalanie formantów dynamicznych w dokumentach pakietu Office](../vsto/persisting-dynamic-controls-in-office-documents.md)
- [Instrukcje: Dodawanie formantów Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Instrukcje: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Rozwiń dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
