---
title: 'Przewodnik: aktualizowanie wykresu w dokumencie za pomocą przycisków radiowych'
description: Dowiedz się, w jaki sposób można użyć przycisków radiowych w dostosowaniu na poziomie dokumentu dla programu Microsoft Word, aby umożliwić użytkownikom wybranie stylów wykresu w dokumencie.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: df2996d99e752fbe0f7f36bcab537ee8c19d4f06
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528392"
---
# <a name="walkthrough-update-a-chart-in-a-document-using-radio-buttons"></a>Przewodnik: aktualizowanie wykresu w dokumencie za pomocą przycisków radiowych
  W tym instruktażu pokazano, jak używać przycisków radiowych w dostosowaniu na poziomie dokumentu dla programu Microsoft Office Word, aby umożliwić użytkownikom wybranie stylów wykresu dla dokumentu.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie wykresu do dokumentu w projekcie na poziomie dokumentu w czasie projektowania.

- Grupowanie przycisków radiowych przez dodanie ich do kontrolki użytkownika.

- Zmiana stylu wykresu w przypadku wybrania opcji.

  Aby zobaczyć wynik jako ukończony przykład, zobacz przykład kontrolki słowa w podręczniku [i instruktażu opracowywania pakietu Office](../vsto/office-development-samples-and-walkthroughs.md).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Tworzenie projektu
 Pierwszym krokiem jest utworzenie projektu dokumentu programu Word.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt dokumentu programu Word z **opcjami Nazwij mój wykres**. W kreatorze wybierz pozycję **Utwórz nowy dokument**. Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Program Visual Studio otwiera nowy dokument programu Word w Projektancie i dodaje projekt **opcji my Chart** do **Eksplorator rozwiązań**.

## <a name="add-a-chart-to-the-document"></a>Dodawanie wykresu do dokumentu

### <a name="to-add-a-chart"></a>Aby dodać wykres

1. W dokumencie programu Word, który jest hostowany w projektancie programu Visual Studio, na wstążce kliknij kartę **Wstawianie** .

2. W grupie **tekst** kliknij przycisk **Wstaw obiekt** listy rozwijanej, a następnie kliknij pozycję **obiekt**.

     Zostanie otwarte okno dialogowe **obiekt** .

3. Na liście **Typ obiektu** na karcie **Utwórz nowy** wybierz pozycję **Microsoft Graph wykres** , a następnie kliknij przycisk **OK**.

     Wykres zostanie dodany do dokumentu w punkcie wstawiania i zostanie wyświetlone okno **Arkusz danych** z nieprawidłowymi danymi.

4. Zamknij okno **arkusza danych** , aby zaakceptować wartości domyślne na wykresie, a następnie kliknij wewnątrz dokumentu, aby przenieść fokus z wykresu.

5. Kliknij prawym przyciskiem myszy wykres, a następnie kliknij polecenie **Formatuj obiekt**.

6. Na karcie **Układ** okna dialogowego **Formatowanie obiektu** wybierz pozycję **kwadrat** i kliknij przycisk **OK**.

## <a name="add-a-user-control-to-the-project"></a>Dodawanie kontrolki użytkownika do projektu
 Przyciski radiowe w dokumencie nie są wzajemnie wykluczane domyślnie. Można sprawić, aby działały prawidłowo, dodając je do kontrolki użytkownika, a następnie pisząc kod, aby kontrolować wybór.

### <a name="to-add-a-user-control"></a>Aby dodać kontrolkę użytkownika

1. Wybierz projekt **Opcje mojego wykresu** w **Eksplorator rozwiązań**.

2. W menu **projekt** kliknij polecenie **Dodaj nowy element**.

3. W oknie dialogowym **Dodaj nowy element** kliknij pozycję **kontrolka użytkownika**, nazwij formant **ChartOptions,** a następnie kliknij przycisk **Dodaj**.

### <a name="to-add-windows-form-controls-to-the-user-control"></a>Aby dodać kontrolki formularza systemu Windows do kontrolki użytkownika

1. Jeśli formant użytkownika nie jest widoczny w projektancie, kliknij dwukrotnie pozycję **ChartOptions** w **Eksplorator rozwiązań**.

2. Na karcie **Formanty standardowe** **przybornika** przeciągnij pierwszy formant **przycisk radiowy** do kontrolki użytkownika i Zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**columnChart (wykres kolumnowy)**|
    |**Tekst**|**Wykres kolumnowy**|

3. Dodaj drugi **przycisk radiowy** do kontrolki użytkownika i Zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**barChart (wykres słupkowy)**|
    |**Tekst**|**Wykres słupkowy**|

4. Dodaj trzeci **przycisk radiowy** do kontrolki użytkownika i Zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**lineChart (wykres liniowy)**|
    |**Tekst**|**Wykres liniowy**|

5. Dodaj czwarty **przycisk radiowy** do kontrolki użytkownika i Zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**areaBlockChart**|
    |**Tekst**|**Wykres blokowy obszaru**|

## <a name="add-references"></a>Dodaj odwołania
 Aby uzyskać dostęp do wykresu z kontrolki użytkownika w dokumencie, musisz mieć odwołanie do `Microsoft.Office.Interop.Graph` zestawu w projekcie.

### <a name="to-add-a-reference-to-the-microsoftofficeinteropgraph-assembly"></a>Aby dodać odwołanie do zestawu Microsoft. Office. Interop. Graph

1. W menu **projekt** kliknij polecenie **Dodaj odwołanie**.

     Zostanie wyświetlone okno dialogowe **Dodawanie odwołania** .

2. Na karcie **.NET** wybierz pozycję **Microsoft. Office. Interop. Graph** i kliknij przycisk **OK**. Wybierz wersję 14.0.0.0 zestawu.

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Zmień styl wykresu, gdy zostanie wybrany przycisk radiowy
 Aby przyciski działały prawidłowo, należy utworzyć zdarzenie publiczne na kontrolce użytkownika, dodać właściwość w celu ustawienia typu zaznaczenia i utworzyć procedurę dla `CheckedChanged` zdarzenia każdego przycisku radiowego.

### <a name="to-create-an-event-and-property-on-a-user-control"></a>Aby utworzyć zdarzenie i właściwość na kontrolce użytkownika

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy kontrolkę użytkownika, a następnie kliknij polecenie **Wyświetl kod**.

2. Dodaj kod, aby utworzyć `SelectionChanged` zdarzenie i `Selection` Właściwość do `ChartOptions` klasy.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#9)]

### <a name="to-handle-the-checkedchange-event-of-the-radio-buttons"></a>Aby obsłużyć zdarzenie CheckedChange przycisków radiowych

1. Ustaw typ wykresu w `CheckedChanged` obsłudze zdarzeń `areaBlockChart` przycisku radiowego, a następnie zgłoś zdarzenie.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#10)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#10)]

2. Ustaw typ wykresu w `CheckedChanged` obsłudze zdarzeń `barChart` przycisku radiowego.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#11)]

3. Ustaw typ wykresu w `CheckedChanged` obsłudze zdarzeń `columnChart` przycisku radiowego.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#12)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#12)]

4. Ustaw typ wykresu w `CheckedChanged` obsłudze zdarzeń `lineChart` przycisku radiowego.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#13)]

5. W języku C# należy dodać procedury obsługi zdarzeń dla przycisków radiowych. Możesz dodać kod do `ChartOptions` konstruktora, pod wywołaniem `InitializeComponent` . Aby uzyskać informacje na temat tworzenia programów obsługi zdarzeń, zobacz [How to: Create Event Handles in Office projects](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#14)]

## <a name="add-the-user-control-to-the-document"></a>Dodaj kontrolkę użytkownika do dokumentu
 Podczas kompilowania rozwiązania Nowa kontrolka użytkownika jest automatycznie dodawana do **przybornika**. Następnie możesz przeciągnąć formant z **przybornika** do dokumentu.

### <a name="to-add-the-user-control-your-document"></a>Aby dodać kontrolkę użytkownika do dokumentu

1. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

     Kontrolka użytkownika **ChartOptions** jest dodawana do **przybornika**.

2. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **ThisDocument. vb** lub **ThisDocument.cs**, a następnie kliknij pozycję **Projektant widoków**.

3. Przeciągnij `ChartOptions` formant z **przybornika** do dokumentu.

     W oknie **Właściwości** Nazwij formant, który został właśnie dodany do dokumentu  `ChartOptions1` .

## <a name="change-the-chart-type"></a>Zmień typ wykresu
 Utwórz procedurę obsługi zdarzeń, aby zmienić typ wykresu zgodnie z opcją wybraną w kontrolce użytkownika.

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-document"></a>Aby zmienić typ wykresu wyświetlanego w dokumencie

1. Dodaj do klasy następujący program obsługi zdarzeń `ThisDocument` .

     [!code-vb[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#15)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#15)]

2. W języku C# należy dodać program obsługi zdarzeń dla kontrolki użytkownika do <xref:Microsoft.Office.Tools.Word.Document.Startup> zdarzenia.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#16)]

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz można testować dokument, aby upewnić się, że styl wykresu został poprawnie zaktualizowany po wybraniu przycisku radiowego.

### <a name="to-test-your-document"></a>Aby przetestować dokument

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

2. Wybierz różne przyciski radiowe.

3. Upewnij się, że styl wykresu zmieni się, aby dopasować zaznaczenie.

## <a name="next-steps"></a>Następne kroki
 Poniżej przedstawiono kilka zadań, które mogą wystąpić poniżej:

- Wypełnienie pola tekstowego za pomocą przycisku. Aby uzyskać więcej informacji, zobacz [Przewodnik: wyświetlanie tekstu w polu tekstowym w dokumencie za pomocą przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).

- Zmień formatowanie, wybierając styl z pola kombi. Aby uzyskać więcej informacji, zobacz [Przewodnik: zmienianie formatowania dokumentu przy użyciu kontrolek CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Zobacz też
- [Wskazówki dotyczące korzystania z programu Word](../vsto/walkthroughs-using-word.md)
- [Przykłady i przewodniki dotyczące programowania pakietu Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Ograniczenia Windows Forms formantów w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
