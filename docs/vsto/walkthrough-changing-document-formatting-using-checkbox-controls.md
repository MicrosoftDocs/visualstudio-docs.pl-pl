---
title: Zmienianie formatowania dokumentu przy użyciu kontrolek CheckBox
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
ms.openlocfilehash: 24c3cb8d76551bb477f9c13cc56c313519f3b617
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67328723"
---
# <a name="walkthrough-change-document-formatting-using-checkbox-controls"></a>Przewodnik: zmienianie formatowania dokumentu przy użyciu kontrolek CheckBox
  W tym instruktażu pokazano, jak używać formantów Windows Forms w dostosowaniu na poziomie dokumentu dla Microsoft Office Word, aby zmienić formatowanie tekstu.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie tekstu i kontrolki do dokumentu w projekcie na poziomie dokumentu w czasie projektowania.

- Formatowanie tekstu w przypadku wybrania opcji.

  Aby zobaczyć wynik jako ukończony przykład, zobacz przykład kontrolki słowa w podręczniku [i instruktażu opracowywania pakietu Office](../vsto/office-development-samples-and-walkthroughs.md).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Tworzenie projektu
 Pierwszym krokiem jest utworzenie projektu dokumentu programu Word.

### <a name="create-a-new-project"></a>Tworzenie nowego projektu

1. Utwórz projekt dokumentu programu Word z nazwą **mój wyraz formatowanie**. W kreatorze wybierz pozycję **Utwórz nowy dokument**.

     Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Program Visual Studio otwiera nowy dokument programu Word w Projektancie i dodaje projekt **Moje formatowanie tekstu** do **Eksplorator rozwiązań**.

## <a name="add-text-and-controls-to-the-word-document"></a>Dodawanie tekstu i kontrolek do dokumentu programu Word
 W tym instruktażu Dodaj trzy pola wyboru i tekst w <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolce do dokumentu programu Word. Pola wyboru będą prezentowane użytkownikowi opcje formatowania tekstu.

### <a name="add-three-check-boxes"></a>Dodaj trzy pola wyboru

1. Sprawdź, czy dokument jest otwarty w projektancie programu Visual Studio.

2. Na karcie **Formanty standardowe** **przybornika**przeciągnij pierwszy <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> formant do dokumentu.

3. W oknie **Właściwości** Zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**applyBoldFont**|
    |**Tekst**|**Pogrubiona**|

4. Naciśnij klawisz **Enter** , aby przenieść punkt wstawiania poniżej pierwszego pola wyboru.

5. Dodaj drugie pole wyboru do dokumentu poniżej `ApplyBoldFont` pola wyboru i Zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**applyItalicFont**|
    |**Tekst**|**Kursywa**|

6. Naciśnij klawisz **Enter** , aby przenieść punkt wstawiania poniżej drugiego pola wyboru.

7. Dodaj trzecie pole wyboru do dokumentu poniżej `ApplyItalicFont` pola wyboru i Zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**applyUnderlineFont**|
    |**Tekst**|**Podkreślenie**|

### <a name="add-text-and-a-bookmark-control"></a>Dodawanie tekstu i kontrolki zakładki

1. Przesuń punkt wstawiania poniżej formantów pola wyboru i wpisz następujący tekst:

    **Kliknij pole wyboru, aby zmienić formatowanie tego tekstu.**

2. Na karcie **formanty programu Word** **przybornika**przeciągnij <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolkę do dokumentu.

    Zostanie wyświetlone okno dialogowe **Dodawanie kontrolki zakładki** .

3. Zaznacz tekst, który został dodany do dokumentu, a następnie kliknij przycisk **OK**.

    <xref:Microsoft.Office.Tools.Word.Bookmark>Kontrolka o nazwie **Bookmark1** jest dodawana do zaznaczonego tekstu w dokumencie.

4. W oknie **Właściwości** Zmień wartość właściwości **(Name)** na **fontText.**

   Następnie napisz kod służący do formatowania tekstu, gdy pole wyboru jest zaznaczone lub wyczyszczone.

## <a name="format-the-text-when-a-check-box-is-checked-or-cleared"></a>Sformatuj tekst, gdy pole wyboru jest zaznaczone lub wyczyszczone
 Gdy użytkownik wybierze opcję formatowania, Zmień format tekstu w dokumencie.

### <a name="change-formatting-when-a-check-box-is-selected"></a>Zmień formatowanie, gdy pole wyboru jest zaznaczone

1. Kliknij prawym przyciskiem myszy `ThisDocument` w **Eksplorator rozwiązań**, a następnie kliknij polecenie **Wyświetl kod** w menu skrótów.

2. Tylko w przypadku języka C# Dodaj następujące stałe do klasy **ThisDocument** .

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#2)]

3. Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń `applyBoldFont` pola wyboru.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#3)]

4. Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń `applyItalicFont` pola wyboru.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#4)]

5. Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń `applyUnderlineFont` pola wyboru.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#5)]

6. W języku C# należy dodać procedury obsługi zdarzeń dla pól tekstowych do <xref:Microsoft.Office.Tools.Word.Document.Startup> zdarzenia. Informacje o sposobach tworzenia programów obsługi zdarzeń znajdują się [w temacie How to: Create Event Handles in Office projects](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#6)]

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz można testować dokument, aby sprawdzić, czy tekst jest sformatowany prawidłowo po zaznaczeniu lub usunięciu zaznaczenia pola wyboru.

### <a name="test-your-document"></a>Testowanie dokumentu

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

2. Zaznacz lub wyczyść pole wyboru.

3. Upewnij się, że tekst jest poprawnie sformatowany.

## <a name="next-steps"></a>Następne kroki
 W tym instruktażu przedstawiono podstawowe informacje na temat używania pól wyboru i programistycznego zmieniania formatowania tekstu w dokumentach programu Word. Poniżej przedstawiono kilka zadań, które mogą wystąpić poniżej:

- Użyj przycisku, aby wypełnić pole tekstowe. Aby uzyskać więcej informacji, zobacz [Przewodnik: wyświetlanie tekstu w polu tekstowym w dokumencie za pomocą przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).

- Używanie przycisków radiowych do wybierania stylów wykresu. Aby uzyskać więcej informacji, zobacz [Przewodnik: aktualizowanie wykresu w dokumencie za pomocą przycisków radiowych](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).

## <a name="see-also"></a>Zobacz też
- [Wskazówki dotyczące korzystania z programu Word](../vsto/walkthroughs-using-word.md)
- [Przykłady i przewodniki dotyczące programowania pakietu Office](../vsto/office-development-samples-and-walkthroughs.md)
- [NamedRange — formant](../vsto/namedrange-control.md)
- [Ograniczenia Windows Forms formantów w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
