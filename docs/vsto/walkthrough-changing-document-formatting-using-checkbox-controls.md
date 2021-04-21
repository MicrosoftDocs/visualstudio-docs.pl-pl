---
title: Zmienianie formatowania dokumentu przy użyciu kontrolek CheckBox
description: Dowiedz się, jak Windows Forms formantów w dostosowywaniu na poziomie dokumentu dla programu Microsoft Word w celu zmiany formatowania tekstu.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3f6fbb91c37fd8956860eed8e4d39f8b0a8c1a0e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824422"
---
# <a name="walkthrough-change-document-formatting-using-checkbox-controls"></a>Przewodnik: zmienianie formatowania dokumentu przy użyciu kontrolek CheckBox
  W tym przewodniku pokazano, jak używać kontrolek Windows Forms w dostosowywaniu na poziomie dokumentu dla Microsoft Office Word w celu zmiany formatowania tekstu.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie tekstu i kontrolki do dokumentu w projekcie na poziomie dokumentu w czasie projektowania.

- Formatowanie tekstu po wybraniu opcji.

  Aby zobaczyć wynik jako ukończony przykład, zobacz Word Controls Sample (Przykład kontrolek programu Word) na stronie [Office development samples and walkthroughs](../vsto/office-development-samples-and-walkthroughs.md)(Przykłady dla programistów i przewodników dla pakietu Office).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Tworzenie projektu
 Pierwszym krokiem jest utworzenie projektu dokumentu programu Word.

### <a name="create-a-new-project"></a>Tworzenie nowego projektu

1. Utwórz projekt dokumentu programu Word o nazwie **My Word Formatting (Formatowanie wyrazów).** W kreatorze wybierz **pozycję Utwórz nowy dokument.**

     Aby uzyskać więcej informacji, [zobacz How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio nowy dokument programu Word w projektancie i dodaje projekt **Formatowanie wyrazów** do Eksplorator rozwiązań **.**

## <a name="add-text-and-controls-to-the-word-document"></a>Dodawanie tekstu i kontrolek do dokumentu programu Word
 W tym przewodniku dodaj trzy pola wyboru i tekst w kontrolce <xref:Microsoft.Office.Tools.Word.Bookmark> do dokumentu programu Word. Pola wyboru będą przedstawiać użytkownikowi opcje formatowania tekstu.

### <a name="add-three-check-boxes"></a>Dodawanie trzech pól wyboru

1. Sprawdź, czy dokument jest otwarty w projektancie Visual Studio aplikacji.

2. Na karcie **Typowe kontrolki** **przybornika** przeciągnij pierwszą <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> kontrolkę do dokumentu.

3. W **oknie** Właściwości zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**applyBoldFont**|
    |**Tekst**|**Pogrubiona**|

4. Naciśnij **klawisz Enter,** aby przenieść punkt wstawiania poniżej pierwszego pola wyboru.

5. Dodaj drugie pole wyboru do dokumentu poniżej pola wyboru `ApplyBoldFont` i zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**applyItalicFont**|
    |**Tekst**|**Kursywa**|

6. Naciśnij **klawisz Enter,** aby przenieść punkt wstawiania poniżej drugiego pola wyboru.

7. Dodaj trzecie pole wyboru do dokumentu poniżej pola wyboru `ApplyItalicFont` i zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**applyUnderlineFont**|
    |**Tekst**|**Podkreślenie**|

### <a name="add-text-and-a-bookmark-control"></a>Dodawanie tekstu i kontrolki Zakładka

1. Przenieś punkt wstawiania poniżej kontrolek pola wyboru i wpisz następujący tekst:

    **Kliknij pole wyboru, aby zmienić formatowanie tego tekstu.**

2. Przeciągnij **kontrolkę** do dokumentu z karty Kontrolki **wyrazów** w <xref:Microsoft.Office.Tools.Word.Bookmark> przyborniku.

    Zostanie **wyświetlone okno dialogowe Dodawanie kontrolki** zakładki.

3. Wybierz tekst dodany do dokumentu, a następnie kliknij przycisk **OK.**

    <xref:Microsoft.Office.Tools.Word.Bookmark>Kontrolka **o nazwie Bookmark1** jest dodawana do zaznaczonego tekstu w dokumencie.

4. W **oknie** Właściwości zmień wartość właściwości **(Name)** na **fontText.**

   Następnie napisz kod, aby sformatować tekst, gdy pole wyboru jest zaznaczone lub wyczyszone.

## <a name="format-the-text-when-a-check-box-is-checked-or-cleared"></a>Formatowanie tekstu, gdy pole wyboru jest zaznaczone lub wyczyszone
 Gdy użytkownik wybierze opcję formatowania, zmień format tekstu w dokumencie.

### <a name="change-formatting-when-a-check-box-is-selected"></a>Zmienianie formatowania, gdy pole wyboru jest zaznaczone

1. Kliknij prawym przyciskiem `ThisDocument` myszy pozycję Eksplorator rozwiązań , **a** następnie kliknij polecenie **Wyświetl** kod w menu skrótów.

2. Tylko w przypadku języka C# dodaj następujące stałe do **klasy ThisDocument.**

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet2":::

3. Dodaj następujący kod do procedury <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń tego pola `applyBoldFont` wyboru.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet3":::

4. Dodaj następujący kod do procedury <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń tego pola `applyItalicFont` wyboru.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet4":::

5. Dodaj następujący kod do procedury <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń tego pola `applyUnderlineFont` wyboru.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet5":::

6. W języku C# należy dodać procedury obsługi zdarzeń dla pól tekstowych do <xref:Microsoft.Office.Tools.Word.Document.Startup> zdarzenia. Aby uzyskać informacje na temat tworzenia programów obsługi zdarzeń, zobacz Jak tworzyć procedury obsługi [zdarzeń w projektach pakietu Office.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet6":::

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz możesz przetestować dokument, aby sprawdzić, czy tekst jest poprawnie sformatowany po zaznaczeniu lub wyczyszczeniu pola wyboru.

### <a name="test-your-document"></a>Testowanie dokumentu

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

2. Zaznacz lub wyczyść pole wyboru.

3. Upewnij się, że tekst jest poprawnie sformatowany.

## <a name="next-steps"></a>Następne kroki
 W tym przewodniku przedstawiono podstawy używania pól wyboru i programowego zmieniania formatowania tekstu w dokumentach programu Word. Oto kilka zadań, które mogą się pojawić w następnej części:

- Użyj przycisku, aby wypełnić pole tekstowe. Aby uzyskać więcej informacji, zobacz Przewodnik: wyświetlanie tekstu w polu [tekstowym w dokumencie przy użyciu przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).

- Wybieranie stylów wykresu za pomocą przycisków radiowych. Aby uzyskać więcej informacji, [zobacz Przewodnik: aktualizowanie wykresu w dokumencie za pomocą przycisków radiowych](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).

## <a name="see-also"></a>Zobacz też
- [Wskazówki dotyczące korzystania z programu Word](../vsto/walkthroughs-using-word.md)
- [Office development samples and walkthroughs (Przykłady i wskazówki dotyczące tworzenia aplikacji pakietu Office)](../vsto/office-development-samples-and-walkthroughs.md)
- [NamedRange, kontrolka](../vsto/namedrange-control.md)
- [Ograniczenia kontrolek Windows Forms dokumentów pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
