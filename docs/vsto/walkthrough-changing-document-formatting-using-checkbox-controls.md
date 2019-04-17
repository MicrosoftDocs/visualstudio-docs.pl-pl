---
title: 'Przewodnik: Zmiana formatowania dokumentu za pomocą formantów CheckBox'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word documents, changing formatting using controls
- documents [Office development in Visual Studio], formatting
- check boxes, Word documents
- documents [Office development in Visual Studio], check box controls
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f1b4137a6f024a9a4f752af7c9e19fd946a1c282
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59653895"
---
# <a name="walkthrough-change-document-formatting-using-checkbox-controls"></a>Przewodnik: Zmiana formatowania dokumentu za pomocą formantów CheckBox
  W tym instruktażu pokazano, jak użyć kontrolek formularzy Windows Forms w dostosowywania poziomie dokumentu dla programu Microsoft Office Word, aby zmienić formatowanie tekstu.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie tekstu i kontrolki do dokumentu w projekcie na poziomie dokumentu, w czasie projektowania.

- Formatowanie tekstu, gdy opcja jest zaznaczona.

  Aby wyświetlić wynik, jako przykład ukończone, zobacz przykład formanty programu Word w [Office development ― przykłady i wskazówki dotyczące](../vsto/office-development-samples-and-walkthroughs.md).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Utwórz projekt
 Pierwszym krokiem jest utworzenie projektu dokument programu Word.

### <a name="create-a-new-project"></a>Tworzenie nowego projektu

1.  Tworzenie projektu dokument programu Word z nazwą **Moje formatowania Word**. W kreatorze Wybierz **Utwórz nowy dokument**.

     Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio otwiera nowy dokument programu Word w Projektancie i dodaje **Moje formatowania Word** projekt **Eksploratora rozwiązań**.

## <a name="add-text-and-controls-to-the-word-document"></a>Dodawanie tekstu i kontrolki do dokumentu programu Word
 Na potrzeby tego przewodnika, Dodaj trzy pola wyboru i tekst w <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki do dokumentu programu Word. Pola wyboru spowoduje wyświetlenie użytkownikowi opcje formatowania tekstu.

### <a name="add-three-check-boxes"></a>Dodaj trzy pola wyboru

1.  Sprawdź, czy dokument jest otwarty w Projektancie Visual Studio.

2.  Z **wspólnych formantów** karcie **przybornika**, przeciągnij pierwszy <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> kontrolki do dokumentu.

3.  W **właściwości** okna, Zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**applyBoldFont**|
    |**Text**|**Bold**|

4.  Naciśnij klawisz **Enter** przenieść punkt wstawiania poniżej pierwsze pole wyboru.

5.  Dodawanie drugiego pola wyboru do dokumentu poniżej `ApplyBoldFont` pole wyboru, a następnie Zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**applyItalicFont**|
    |**Text**|**Kursywa**|

6.  Naciśnij klawisz **Enter** przenieść punkt wstawiania poniżej drugiego pola wyboru.

7.  Dodaj trzecie pole wyboru do dokumentu poniżej `ApplyItalicFont` pole wyboru, a następnie Zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**applyUnderlineFont**|
    |**Text**|**Underline**|

### <a name="add-text-and-a-bookmark-control"></a>Dodawanie tekstu i sterującymi zakładki

1. Przesuń punkt wstawiania poniżej formanty pól wyboru, a następnie wpisz następujący tekst:

    **Kliknij pole wyboru, aby zmienić formatowanie tekstu.**

2. Z **formanty programu Word** karcie **przybornika**, przeciągnij <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki do dokumentu.

    **Dodaj kontrolkę zakładki** pojawi się okno dialogowe.

3. Zaznacz tekst, dodać do dokumentu, a następnie kliknij przycisk **OK**.

    A <xref:Microsoft.Office.Tools.Word.Bookmark> formantu o nazwie **Bookmark1** jest dodawany do zaznaczonego tekstu w dokumencie.

4. W **właściwości** okna, zmień wartość właściwości **(nazwa)** właściwości **fontText.**

   Następnie należy napisać kod do formatowania tekstu, gdy pole wyboru jest zaznaczone lub wyczyszczone.

## <a name="format-the-text-when-a-check-box-is-checked-or-cleared"></a>Formatuj tekst, gdy pole wyboru jest zaznaczone, lub wyczyszczone
 Gdy użytkownik wybierze opcję formatowania, Zmień format tekstu w dokumencie.

### <a name="change-formatting-when-a-check-box-is-selected"></a>Zmienianie formatowania, gdy zaznaczono pole wyboru

1.  Kliknij prawym przyciskiem myszy `ThisDocument` w **Eksploratora rozwiązań**, a następnie kliknij przycisk **Wyświetl kod** w menu skrótów.

2.  Aby uzyskać C# , Dodaj następujące stałe do **ThisDocument** klasy.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#2)]

3.  Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń `applyBoldFont` pole wyboru.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#3)]

4.  Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń `applyItalicFont` pole wyboru.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#4)]

5.  Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń `applyUnderlineFont` pole wyboru.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#5)]

6.  W C#, należy dodać procedury obsługi zdarzeń dla pól tekstowych do <xref:Microsoft.Office.Tools.Word.Document.Startup> zdarzeń. Aby uzyskać informacje o sposobie tworzenia procedury obsługi zdarzeń, zobacz [jak: Tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#6)]

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz możesz przetestować dokument, aby sprawdzić, czy tekst jest poprawnie sformatowane, zaznacz lub usuń zaznaczenie pola wyboru.

### <a name="test-your-document"></a>Testowanie dokumentu

1.  Naciśnij klawisz **F5** Aby uruchomić projekt.

2.  Zaznacz lub wyczyść pole wyboru.

3.  Upewnij się, że tekst jest prawidłowo sformatowany.

## <a name="next-steps"></a>Następne kroki
 W tym instruktażu przedstawiono podstawy korzystania z pola wyboru oraz programowe Zmienianie tekstu w dokumentach programu Word. Poniżej przedstawiono niektóre zadania, które mogą pochodzić dalej:

-   Użyj przycisku, aby wypełnić pole tekstowe. Aby uzyskać więcej informacji, zobacz [instruktażu: Wyświetlanie tekstu w polu tekstowym w dokumencie za pomocą przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).

-   Za pomocą przycisków radiowych, aby wybrać styl wykresu. Aby uzyskać więcej informacji, zobacz [instruktażu: Aktualizacja wykresu w dokumencie za pomocą przycisków radiowych](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).

## <a name="see-also"></a>Zobacz także
- [Wskazówki dotyczące przy użyciu programu Word](../vsto/walkthroughs-using-word.md)
- [Office development ― przykłady i przewodniki](../vsto/office-development-samples-and-walkthroughs.md)
- [Namedrange — formant](../vsto/namedrange-control.md)
- [Ograniczenia kontrolek Windows Forms w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
