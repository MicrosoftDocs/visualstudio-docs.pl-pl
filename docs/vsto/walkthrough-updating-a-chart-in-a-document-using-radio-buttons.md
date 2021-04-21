---
title: 'Przewodnik: aktualizowanie wykresu w dokumencie przy użyciu przycisków radiowych'
description: Dowiedz się, jak używać przycisków radiowych w dostosowywaniu na poziomie dokumentu dla programu Microsoft Word, aby dać użytkownikom możliwość wyboru stylów wykresu w dokumencie.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], updating using controls
- controls [Office development in Visual Studio], updating documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4d6689d82051ef5f8c887c19ec91cbb6d513b8b8
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828205"
---
# <a name="walkthrough-update-a-chart-in-a-document-using-radio-buttons"></a>Przewodnik: aktualizowanie wykresu w dokumencie przy użyciu przycisków radiowych
  W tym przewodniku pokazano, jak używać przycisków radiowych w dostosowywaniu na poziomie dokumentu dla programu Microsoft Office Word, aby dać użytkownikom możliwość wyboru stylów wykresu w dokumencie.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie wykresu do dokumentu w projekcie na poziomie dokumentu w czasie projektowania.

- Grupowanie przycisków radiowych przez dodanie ich do kontrolki użytkownika.

- Zmiana stylu wykresu po wybraniu opcji.

  Aby zobaczyć wynik jako ukończony przykład, zobacz przykład formantów programu Word na stronie [Przykłady](../vsto/office-development-samples-and-walkthroughs.md)dla programistów pakietu Office i wskazówki .

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Tworzenie projektu
 Pierwszym krokiem jest utworzenie projektu dokumentu programu Word.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt dokumentu programu Word o nazwie **My Chart Options (Moje opcje wykresu).** W kreatorze wybierz **pozycję Utwórz nowy dokument.** Aby uzyskać więcej informacji, [zobacz How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio nowy dokument programu Word w projektancie i dodaje projekt **Moje opcje wykresu** do **Eksplorator rozwiązań**.

## <a name="add-a-chart-to-the-document"></a>Dodawanie wykresu do dokumentu

### <a name="to-add-a-chart"></a>Aby dodać wykres

1. W dokumencie programu Word hostowany w projektancie Visual Studio kliknij kartę **Wstawianie** na wstążce.

2. W grupie **Tekst** kliknij przycisk listy rozwijanej **Wstaw** obiekt, a następnie kliknij pozycję **Obiekt**.

     Obiekt **zostanie** otwarte okno dialogowe.

3. Na **liście Typ obiektu** na karcie **Tworzenie** nowego wybierz pozycję Microsoft Graph **Chart,** a następnie kliknij przycisk **OK**.

     Wykres jest dodawany do dokumentu w punkcie wstawiania, a okno **Arkusza** danych jest wyświetlane z pewnymi danymi domyślnymi.

4. Zamknij okno **Arkusz danych,** aby zaakceptować wartości domyślne na wykresie, a następnie kliknij wewnątrz dokumentu, aby przenieść fokus z wykresu.

5. Kliknij prawym przyciskiem myszy wykres, a następnie kliknij polecenie **Formatuj obiekt**.

6. Na karcie **Układ** okna dialogowego **Formatowanie obiektu** wybierz pozycję **Kwadrat i** kliknij przycisk **OK.**

## <a name="add-a-user-control-to-the-project"></a>Dodawanie kontrolki użytkownika do projektu
 Przyciski radiowe w dokumencie nie wykluczają się wzajemnie domyślnie. Można je poprawnie ustawić, dodając je do kontrolki użytkownika, a następnie pisząc kod, aby kontrolować wybór.

### <a name="to-add-a-user-control"></a>Aby dodać kontrolkę użytkownika

1. Wybierz projekt **My Chart Options (Moje** opcje wykresu) **w Eksplorator rozwiązań**.

2. W menu **Project (Projekt)** kliknij pozycję **Add New Item (Dodaj nowy element).**

3. W **oknie dialogowym Dodawanie nowego** elementu kliknij pozycję **Kontrola użytkownika,** nadaj **kontrolce nazwę ChartOptions, a** następnie kliknij przycisk **Dodaj**.

### <a name="to-add-windows-form-controls-to-the-user-control"></a>Aby dodać kontrolki Formularz systemu Windows do kontrolki użytkownika

1. Jeśli kontrolka użytkownika nie jest widoczna w projektancie, kliknij dwukrotnie pozycję **ChartOptions w** **Eksplorator rozwiązań**.

2. Na karcie **Typowe kontrolki** **przybornika** przeciągnij pierwszą kontrolkę **Przycisk** radiowy do kontrolki użytkownika i zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**columnChart (wykres kolumnowy)**|
    |**Tekst**|**Wykres kolumnowy**|

3. Dodaj drugi przycisk **radiowy** do kontrolki użytkownika i zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**barChart (wykres słupkowy)**|
    |**Tekst**|**Wykres słupkowy**|

4. Dodaj trzeci **przycisk radiowy** do kontrolki użytkownika i zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**lineChart (wykres liniowy)**|
    |**Tekst**|**Wykres liniowy**|

5. Dodaj czwarty **przycisk radiowy** do kontrolki użytkownika i zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**areaBlockChart (wykres obszarowy)**|
    |**Tekst**|**Wykres blokowy obszaru**|

## <a name="add-references"></a>Dodawanie odwołań
 Aby uzyskać dostęp do wykresu z kontrolki użytkownika w dokumencie, musisz mieć odwołanie do `Microsoft.Office.Interop.Graph` zestawu w projekcie.

### <a name="to-add-a-reference-to-the-microsoftofficeinteropgraph-assembly"></a>Aby dodać odwołanie do zestawu Microsoft.Office.Interop.Graph

1. W menu **Project (Projekt)** kliknij pozycję **Add Reference (Dodaj odwołanie).**

     Zostanie **wyświetlone okno dialogowe** Dodawanie odwołania.

2. Na karcie **.NET** wybierz pozycję **Microsoft.Office.Interop.Graph i** kliknij przycisk **OK.** Wybierz wersję zestawu 14.0.0.0.

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Zmienianie stylu wykresu po wybraniu przycisku radiowego
 Aby przyciski działały prawidłowo, utwórz zdarzenie publiczne w kontrolce użytkownika, dodaj właściwość do ustawienia typu wyboru i utwórz procedurę dla zdarzenia każdego z `CheckedChanged` przycisków radiowych.

### <a name="to-create-an-event-and-property-on-a-user-control"></a>Aby utworzyć zdarzenie i właściwość w kontrolce użytkownika

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy kontrolkę użytkownika, a następnie kliknij polecenie **Wyświetl kod.**

2. Dodaj kod, aby `SelectionChanged` utworzyć zdarzenie i właściwość do klasy `Selection` `ChartOptions` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet9":::

### <a name="to-handle-the-checkedchange-event-of-the-radio-buttons"></a>Aby obsłużyć zdarzenie CheckedChange przycisków radiowych

1. Ustaw typ wykresu w `CheckedChanged` programie obsługi zdarzeń `areaBlockChart` przycisku radiowego, a następnie podnieś zdarzenie.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet10":::

2. Ustaw typ wykresu w `CheckedChanged` programie obsługi zdarzeń `barChart` przycisku radiowego.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet11":::

3. Ustaw typ wykresu w `CheckedChanged` programie obsługi zdarzeń `columnChart` przycisku radiowego.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet12":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet12":::

4. Ustaw typ wykresu w `CheckedChanged` programie obsługi zdarzeń `lineChart` przycisku radiowego.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb" id="Snippet13":::

5. W języku C# należy dodać procedury obsługi zdarzeń dla przycisków radiowych. Możesz dodać kod do konstruktora `ChartOptions` poniżej wywołania . `InitializeComponent` Aby uzyskać informacje na temat tworzenia programów obsługi zdarzeń, zobacz [How to: Create Event Handlers in Office Projects (Jak utworzyć programy obsługi zdarzeń w projektach pakietu Office).](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs" id="Snippet14":::

## <a name="add-the-user-control-to-the-document"></a>Dodawanie kontrolki Użytkownik do dokumentu
 Podczas kompilowania rozwiązania nowa kontrolka użytkownika jest automatycznie dodawana do **przybornika**. Następnie możesz przeciągnąć kontrolkę z **przybornika** do dokumentu.

### <a name="to-add-the-user-control-your-document"></a>Aby dodać kontrolkę użytkownika do dokumentu

1. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

     Kontrolka **użytkownika ChartOptions** jest dodawana do **przybornika**.

2. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **ThisDocument.vb** lub **ThisDocument.cs,** a następnie kliknij **Projektant widoków**.

3. Przeciągnij `ChartOptions` kontrolkę z **przybornika** do dokumentu.

     W **oknie** Właściwości nadaj kontrolce nazwę, która właśnie dodano do dokumentu  `ChartOptions1` .

## <a name="change-the-chart-type"></a>Zmienianie typu wykresu
 Utwórz program obsługi zdarzeń, aby zmienić typ wykresu zgodnie z opcją wybraną w kontrolce użytkownika.

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-document"></a>Aby zmienić typ wykresu wyświetlanego w dokumencie

1. Dodaj następującą obsługę zdarzeń do `ThisDocument` klasy .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb" id="Snippet15":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet15":::

2. W języku C# należy dodać do zdarzenia program obsługi zdarzeń dla kontrolki <xref:Microsoft.Office.Tools.Word.Document.Startup> użytkownika.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs" id="Snippet16":::

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz możesz przetestować dokument, aby upewnić się, że styl wykresu został poprawnie zaktualizowany po wybraniu przycisku radiowego.

### <a name="to-test-your-document"></a>Aby przetestować dokument

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

2. Wybierz różne przyciski radiowe.

3. Upewnij się, że styl wykresu zmienia się w celu dopasowania do zaznaczenia.

## <a name="next-steps"></a>Następne kroki
 Oto kilka zadań, które mogą się pojawić w następnej części:

- Wypełnianie pola tekstowego za pomocą przycisku. Aby uzyskać więcej informacji, zobacz Przewodnik: wyświetlanie tekstu w polu [tekstowym w dokumencie przy użyciu przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).

- Zmień formatowanie, wybierając styl z pola kombi. Aby uzyskać więcej informacji, [zobacz Przewodnik: zmienianie formatowania dokumentu przy użyciu kontrolek CheckBox.](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md)

## <a name="see-also"></a>Zobacz też
- [Wskazówki dotyczące korzystania z programu Word](../vsto/walkthroughs-using-word.md)
- [Office development samples and walkthroughs (Przykłady i wskazówki dotyczące tworzenia aplikacji pakietu Office)](../vsto/office-development-samples-and-walkthroughs.md)
- [Ograniczenia kontrolek Windows Forms w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
