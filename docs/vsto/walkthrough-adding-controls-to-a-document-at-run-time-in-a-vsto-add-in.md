---
title: 'Przewodnik: Dodawanie formantów do dokumentów w czasie wykonywania w dodatku narzędzi VSTO'
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 085860294955e1049d05cf38abea636bc2eb8672
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53954899"
---
# <a name="walkthrough-add-controls-to-a-document-at-runtime-in-a-vsto-add-in"></a>Przewodnik: Dodawanie formantów do dokumentów w czasie wykonywania w dodatku narzędzi VSTO
  Aby dodać formanty dowolnego otwartego dokumentu Microsoft Word pakietu Office, za pomocą dodatku narzędzi VSTO. W tym instruktażu przedstawiono sposób użycia wstążki umożliwiające użytkownikom dodawanie <xref:Microsoft.Office.Tools.Word.Controls.Button> lub <xref:Microsoft.Office.Tools.Word.RichTextContentControl> do dokumentu.  

 **Dotyczy:** Informacje przedstawione w tym temacie dotyczą projektów dodatku VSTO dla programu Word 2010. Aby uzyskać więcej informacji, zobacz [Dostępne funkcje uporządkowane według aplikacji pakietu Office i typu projektu](../vsto/features-available-by-office-application-and-project-type.md).  

 W instruktażu przedstawiono następujące zagadnienia:  

- Tworzenie nowego projektu dodatku narzędzi VSTO programu Word.  

- Dostarczanie interfejsu użytkownika (UI), aby dodać kontrolki do dokumentu.  

- Dodawanie formantów do dokumentów w czasie wykonywania.  

- Usuwanie kontrolek z dokumentu.  

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  

## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  

-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  

## <a name="create-a-new-word-add-in-project"></a>Utwórz nowy projekt dodatku programu Word  
 Rozpocznij od utworzenia projektu dodatku narzędzi VSTO programu Word.  

### <a name="to-create-a-new-word-vsto-add-in-project"></a>Aby utworzyć nowy projekt dodatku narzędzi VSTO programu Word  

1.  Utwórz projekt dodatku narzędzi VSTO dla programu Word z nazwą **WordDynamicControls**. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  

2.  Dodaj odwołanie do **Microsoft.Office.Tools.Word.v4.0.Utilities.dll** zestawu. To odwołanie jest wymagane, aby programowo dodać formant programu Windows Forms do dokumentów w dalszej części tego przewodnika.  

## <a name="provide-a-ui-to-add-controls-to-a-document"></a>Udostępniają interfejs użytkownika, aby dodać kontrolki do dokumentu  
 Dodaj kartę niestandardową do wstążki w programie Word. Użytkownicy mogą wybrać pola wyboru na karcie, aby dodać kontrolki do dokumentu.  

### <a name="to-provide-a-ui-to-add-controls-to-a-document"></a>Aby zapewnić interfejsu użytkownika można dodać kontrolki do dokumentu  

1. Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  

2. W **Dodaj nowy element** okno dialogowe, wybierz opcję **Wstążka (Projektant graficzny)**.  

3. Zmień nazwę nowego wstążki do **MyRibbon**i kliknij przycisk **Dodaj**.  

    **MyRibbon.cs** lub **MyRibbon.vb** plik zostanie otwarty w Projektancie Wstążki i wyświetla domyślną kartę i grupę.  

4. W Projektancie Wstążki kliknij **grupa1** grupy.  

5. W **właściwości** oknie zmiany **etykiety** właściwość **grupa1** do **dodać formanty**.  

6. Z **formanty wstążki Office** karcie **przybornika**, przeciągnij **wyboru** kontrolować na **grupa1**.  

7. Kliknij przycisk **CheckBox1** aby go zaznaczyć.  

8. W **właściwości** okna, Zmień następujące właściwości.  


   | Właściwość | Wartość |
   |-----------|-----------------------|
   | **Nazwa** | **addButtonCheckBox** |
   | **Etykieta** | **Dodawanie przycisku** |


9. Drugie pole wyboru, aby dodać **grupa1**, a następnie Zmień następujące właściwości.  


   | Właściwość | Wartość |
   |-----------|---------------------------|
   | **Nazwa** | **addRichTextCheckBox** |
   | **Etykieta** | **Dodawanie kontrolki tekstu sformatowanego** |


10. W Projektancie wstążki, kliknij dwukrotnie **Dodaj przycisk**.  

     <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> Program obsługi zdarzeń **Dodaj przycisk** pola wyboru zostanie otwarty w edytorze kodu.  

11. Wróć do projektanta wstążki, a następnie kliknij dwukrotnie **Dodawanie kontrolki tekstu sformatowanego**.  

     <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> Program obsługi zdarzeń **Dodawanie kontrolki tekstu sformatowanego** pola wyboru zostanie otwarty w edytorze kodu.  

    W dalszej części tego przewodnika dodasz kod do tych programów obsługi zdarzeń, aby dodawać i usuwać kontrolek w aktywnym dokumencie.  

## <a name="add-and-remove-controls-on-the-active-document"></a>Dodawanie i usuwanie kontrolek w aktywnym dokumencie  
 W kodzie dodatku narzędzi VSTO dla programów, należy przekonwertować aktywnego dokumentu w <xref:Microsoft.Office.Tools.Word.Document> *element hosta* zanim będzie można dodać kontrolki. W rozwiązaniach pakietu Office zarządzane formanty można dodać tylko do elementów hosta, które działają jak kontenery dla kontrolek. W projektach dodatku narzędzi VSTO elementów hosta można utworzyć w czasie wykonywania za pomocą `GetVstoObject` metody.  

 Dodaj metody do `ThisAddIn` klasę, która może być wywoływana w celu dodania lub usunięcia <xref:Microsoft.Office.Tools.Word.Controls.Button> lub <xref:Microsoft.Office.Tools.Word.RichTextContentControl> w aktywnym dokumencie. W dalszej części tego przewodnika, będzie wywoływać te metody na podstawie <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> procedury obsługi zdarzeń pola wyboru na Wstążce.  

### <a name="to-add-and-remove-controls-on-the-active-document"></a>Dodawanie i usuwanie kontrolek w aktywnym dokumencie  

1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie *ThisAddIn.cs* lub *ThisAddIn.vb* do otwarcia w edytorze kodu.  

2.  Dodaj następujący kod do `ThisAddIn` klasy. Ten kod deklaruje <xref:Microsoft.Office.Tools.Word.Controls.Button> i <xref:Microsoft.Office.Tools.Word.RichTextContentControl> obiektami, które reprezentują formanty, które zostaną dodane do dokumentu.  

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#1)]  

3.  Dodaj następującą metodę do `ThisAddIn` klasy. Kiedy użytkownik kliknie **Dodaj przycisk** pole wyboru na Wstążce, Metoda ta umożliwia dodanie <xref:Microsoft.Office.Tools.Word.Controls.Button> do bieżącego zaznaczenia w dokumencie, jeśli pole wyboru jest zaznaczone, lub usuwa <xref:Microsoft.Office.Tools.Word.Controls.Button> Jeśli pole wyboru jest wyczyszczone.  

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#2)]  

4.  Dodaj następującą metodę do `ThisAddIn` klasy. Kiedy użytkownik kliknie **Dodawanie kontrolki tekstu sformatowanego** pole wyboru na Wstążce, Metoda ta umożliwia dodanie <xref:Microsoft.Office.Tools.Word.RichTextContentControl> do bieżącego zaznaczenia w dokumencie, jeśli pole wyboru jest zaznaczone, lub usuwa <xref:Microsoft.Office.Tools.Word.RichTextContentControl> Jeśli pole wyboru jest wyczyszczone.  

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#3)]  

## <a name="remove-the-button-control-when-the-document-is-saved"></a>Usuń formant przycisku, jeśli dokument zostanie zapisany  
 Nie są zachowywane kontrolek formularzy Windows Forms, gdy dokument zostanie zapisany i następnie zamknięty. Jednak otoki ActiveX dla każdego formantu pozostaje w dokumencie i obramowanie tej otoki mogą być widoczne dla użytkowników końcowych, po otwarciu dokumentu. Istnieje kilka sposobów, aby wyczyścić dynamicznie utworzoną formantów formularzy Windows w dodatkach VSTO. W tym przewodniku programowo usuniesz <xref:Microsoft.Office.Tools.Word.Controls.Button> kontroli, gdy dokument zostanie zapisany.  

### <a name="to-remove-the-button-control-when-the-document-is-saved"></a>Aby usunąć formant przycisku, gdy dokument zostanie zapisany  

1.  W *ThisAddIn.cs* lub *ThisAddIn.vb* plik kodu, dodaj następującą metodę do `ThisAddIn` klasy. Ta metoda jest program obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> zdarzeń. Jeśli został zapisany dokument <xref:Microsoft.Office.Tools.Word.Document> element hosta, który jest skojarzony z nim program obsługi zdarzeń pobiera element hosta i usuwa <xref:Microsoft.Office.Tools.Word.Controls.Button> kontrolować, jeśli taki istnieje.  

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#4)]  

2.  W języku C#, Dodaj następujący kod do `ThisAddIn_Startup` programu obsługi zdarzeń. Ten kod w języku C# połączenie wymaga `Application_DocumentBeforeSave` programu obsługi zdarzeń z <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> zdarzeń.  

     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/ThisAddIn.cs#5)]  

## <a name="add-and-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Dodawanie i usuwanie kontrolki, gdy użytkownik kliknie pole wyboru na Wstążce  
 Na koniec zmodyfikuj <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> procedury obsługi zdarzeń pola wyboru dodane do wstążki, aby dodać lub usunąć kontrolki do dokumentu.  

### <a name="to-add-or-remove-controls-when-the-user-clicks-the-check-boxes-on-the-ribbon"></a>Aby dodać lub usunąć kontrolki, gdy użytkownik kliknie przycisk pola wyboru na Wstążce  

1.  W *MyRibbon.cs* lub *MyRibbon.vb* plik kodu, Zastąp wygenerowany `addButtonCheckBox_Click` i `addRichTextCheckBox_Click` procedury obsługi zdarzeń z następującym kodem. Ten kod redefiniuje tych programów obsługi zdarzeń, aby wywołać `ToggleButtonOnDocument` i `ToggleRichTextControlOnDocument` metod, które zostały dodane do `ThisAddIn` klasa we wcześniejszej części tego przewodnika.  

     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/VisualBasic/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.vb#6)]
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControlsWalkthrough/MyRibbon.cs#6)]  

## <a name="test-the-solution"></a>Testowanie rozwiązania  
 Dodawanie kontrolki do dokumentu, wybierając je z niestandardowej karty na Wstążce. Podczas zapisywania dokumentu, <xref:Microsoft.Office.Tools.Word.Controls.Button> formant jest usuwany.  

### <a name="to-test-the-solution"></a>Do przetestowania rozwiązania.  

1.  Naciśnij klawisz **F5** Aby uruchomić projekt.  

2.  W aktywnym dokumencie naciśnij **Enter** kilka razy, aby dodać nowy pusty akapitów do dokumentu.  

3.  Wybierz opcję pierwszym akapicie.  

4.  Kliknij przycisk **Add-Ins** kartę.  

5.  W **dodać formanty** grupy, kliknij przycisk **Dodaj przycisk**.  

     Przycisk pojawia się w pierwszym akapicie.  

6.  Wybierz ostatni akapitu.  

7.  W **dodać formanty** grupy, kliknij przycisk **Dodawanie kontrolki tekstu sformatowanego**.  

     Kontrolki zawartości tekstu sformatowanego jest dodawany do ostatniego akapitu.  

8.  Zapisz dokument.  

     Przycisk zostanie usunięty z dokumentu.  

## <a name="next-steps"></a>Następne kroki  
 Możesz dowiedzieć się więcej informacji na temat formantów w dodatkach VSTO w tych tematach:  

-   Przykład demonstrujący, jak dodać wiele innych typów formantów do dokumentów w czasie wykonywania i ponowne utworzenie formanty, po otwarciu dokumentu, można znaleźć w artykule Word dodatek dynamicznej formantów próbki w [Office development ― przykłady i wskazówki dotyczące](../vsto/office-development-samples-and-walkthroughs.md).  

-   Aby uzyskać wskazówki, który demonstruje sposób dodawania formantów do arkusza za pomocą dodatku narzędzi VSTO dla programu Excel, zobacz [instruktażu: Dodawanie formantów do arkusza w czasie wykonywania w projekcie dodatku narzędzi VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md).  

## <a name="see-also"></a>Zobacz także  
 [Rozwiązania programu Word](../vsto/word-solutions.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Utrwalanie kontrolek dynamicznych w dokumentach pakietu Office](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [Instrukcje: Dodawanie kontrolek formularzy Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Instrukcje: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
