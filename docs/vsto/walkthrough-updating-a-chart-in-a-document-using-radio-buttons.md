---
title: 'Przewodnik: Aktualizacja wykresu w dokumencie za pomocą przycisków radiowych'
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
ms.openlocfilehash: 88f7bb81557db813912fe4470e63b8d52c0c9371
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62981052"
---
# <a name="walkthrough-update-a-chart-in-a-document-using-radio-buttons"></a>Przewodnik: Aktualizacja wykresu w dokumencie za pomocą przycisków radiowych
  Ten przewodnik pokazuje sposób użycia przycisków radiowych w dostosowywania poziomie dokumentu dla programu Microsoft Office Word, aby zapewnić użytkownikom możliwość dokonania wyboru stylów wykresu w dokumencie.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Dodawanie wykresu do dokumentu w projekcie na poziomie dokumentu w czasie projektowania.

- Grupowanie przycisków radiowych przez dodanie ich do kontrolki użytkownika.

- Zmiana stylu wykresu, gdy opcja jest zaznaczona.

  Aby wyświetlić wynik, jako przykład ukończone, zobacz przykład formanty programu Word w [Office development ― przykłady i wskazówki dotyczące](../vsto/office-development-samples-and-walkthroughs.md).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Utwórz projekt
 Pierwszym krokiem jest utworzenie projektu dokument programu Word.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Tworzenie projektu dokument programu Word z nazwą **Moje opcje wykresu**. W kreatorze Wybierz **Utwórz nowy dokument**. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio otwiera nowy dokument programu Word w Projektancie i dodaje **Moje opcje wykresu** projekt **Eksploratora rozwiązań**.

## <a name="add-a-chart-to-the-document"></a>Dodawanie wykresu do dokumentu

### <a name="to-add-a-chart"></a>Aby dodać wykres

1. W dokumencie programu Word, który znajduje się w Projektancie Visual Studio na wstążce kliknij **Wstaw** kartę.

2. W **tekstu** grupy, kliknij przycisk **Wstawianie obiektu** przycisk listy rozwijanej, a następnie kliknij przycisk **obiektu**.

     **Obiektu** zostanie otwarte okno dialogowe.

3. W **typ obiektu** listy na **Utwórz nowy** zaznacz **wykres programu Microsoft Graph** a następnie kliknij przycisk **OK**.

     Wykres jest dodawany do dokumentu w punkcie wstawiania i **arkusz danych** zostanie wyświetlone okno z pewnymi danymi domyślne.

4. Zamknij **arkusz danych** okna, aby zaakceptować wartości domyślne na wykresie, a następnie kliknij wewnątrz dokument, aby zespół odbiegać od wykresu.

5. Kliknij prawym przyciskiem myszy wykres, a następnie kliknij przycisk **Format obiektu**.

6. Na **układ** karcie **Format obiektu** okno dialogowe, wybierz opcję **kwadrat** i kliknij przycisk **OK**.

## <a name="add-a-user-control-to-the-project"></a>Dodaj kontrolkę użytkownika do projektu
 Przyciski radiowe w dokumencie nie wykluczają się wzajemnie domyślnie. Możesz zwiększyć ich działa poprawnie przez dodanie ich do kontrolki użytkownika, a następnie pisanie kodu w celu kontrolowania zaznaczenia.

### <a name="to-add-a-user-control"></a>Aby dodać kontrolkę użytkownika

1. Wybierz **Moje opcje wykresu** projektu w **Eksploratora rozwiązań**.

2. Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.

3. W **Dodaj nowy element** okno dialogowe, kliknij przycisk **kontrolki użytkownika**, nazwij kontrolkę **ChartOptions,** i kliknij przycisk **Dodaj**.

### <a name="to-add-windows-form-controls-to-the-user-control"></a>Aby dodać formanty formularza Windows do formantu użytkownika

1. Jeśli formant użytkownika nie jest widoczny w projektancie, kliknij dwukrotnie **ChartOptions** w **Eksploratora rozwiązań**.

2. Z **wspólnych formantów** karcie **przybornika**, przeciągnij pierwszy **przycisk radiowy** sterowania do formantu użytkownika, a następnie Zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**columnChart**|
    |**Text**|**Wykres kolumnowy**|

3. Dodaj drugą **przycisk radiowy** użytkownikowi kontrolowanie, a następnie Zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**barChart**|
    |**Text**|**Wykres słupkowy**|

4. Dodać trzecią **przycisk radiowy** użytkownikowi kontrolowanie, a następnie Zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**lineChart**|
    |**Text**|**Wykres liniowy**|

5. Dodaj czwarty **przycisk radiowy** użytkownikowi kontrolowanie, a następnie Zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**areaBlockChart**|
    |**Text**|**Wykres bloku**|

## <a name="add-references"></a>Dodaj odwołania
 Dostęp do wykresu z kontrolki użytkownika do dokumentu, musi mieć odwołanie do `Microsoft.Office.Interop.Graph` zestawu w projekcie.

### <a name="to-add-a-reference-to-the-microsoftofficeinteropgraph-assembly"></a>Aby dodać odwołanie do zestawu Microsoft.Office.Interop.Graph

1. Na **projektu** menu, kliknij przycisk **Dodaj odwołanie**.

     **Dodaj odwołanie** pojawi się okno dialogowe.

2. Na **.NET** zaznacz **Microsoft.Office.Interop.Graph** i kliknij przycisk **OK**. Wybierz 14.0.0.0 wersję zestawu.

## <a name="change-the-chart-style-when-a-radio-button-is-selected"></a>Zmiana stylu wykresu, gdy przycisk radiowy zostanie wybrany
 Aby przyciski działała prawidłowo, Utwórz zdarzenie publiczne w kontrolce użytkownika, Dodaj właściwość można ustawić typ wyboru, a następnie utwórz procedurę do `CheckedChanged` zdarzenia każdego przycisków radiowych.

### <a name="to-create-an-event-and-property-on-a-user-control"></a>Aby utworzyć zdarzenie i właściwości w kontrolce użytkownika

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy formant użytkownika, a następnie kliknij przycisk **Wyświetl kod**.

2. Dodaj kod, aby utworzyć `SelectionChanged` zdarzeń i `Selection` właściwość `ChartOptions` klasy.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#9)]

### <a name="to-handle-the-checkedchange-event-of-the-radio-buttons"></a>Aby obsłużyć zdarzenie CheckedChange przycisków radiowych

1. Ustaw typ wykresu w `CheckedChanged` program obsługi zdarzeń `areaBlockChart` przycisk radiowy, a następnie wywołaj zdarzenie.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#10)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#10)]

2. Ustaw typ wykresu w `CheckedChanged` program obsługi zdarzeń `barChart` przycisku radiowego.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#11)]

3. Ustaw typ wykresu w `CheckedChanged` program obsługi zdarzeń `columnChart` przycisku radiowego.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#12)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#12)]

4. Ustaw typ wykresu w `CheckedChanged` program obsługi zdarzeń `lineChart` przycisku radiowego.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#13)]

5. W języku C# należy dodać obsługę zdarzeń dla przycisków radiowych. Możesz dodać kod do `ChartOptions` Konstruktor poniżej wywołania `InitializeComponent`. Aby dowiedzieć się, jak tworzenie procedur obsługi zdarzeń, zobacz [jak: Tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#14)]

## <a name="add-the-user-control-to-the-document"></a>Dodaj kontrolkę użytkownika do dokumentu
 Podczas kompilowania rozwiązania nowej kontrolki użytkownika jest automatycznie dodawany do **przybornika**. Następnie można przeciągać formantu z **przybornika** do dokumentu.

### <a name="to-add-the-user-control-your-document"></a>Aby dodać dokument kontrolki użytkownika

1. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

     **ChartOptions** formant użytkownika jest dodawany do **przybornika**.

2. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ThisDocument.vb** lub **ThisDocument.cs**, a następnie kliknij przycisk **Projektant widoków**.

3. Przeciągnij `ChartOptions` z kontrolować **przybornika** do dokumentu.

     W **właściwości** okna, nazwy formant, który został właśnie dodany do dokumentu `ChartOptions1`.

## <a name="change-the-chart-type"></a>Zmień typ wykresu
 Tworzenie procedury obsługi zdarzeń, aby zmienić typ wykresu, zgodnie z opcją, który wybrano w kontrolce użytkownika.

### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-document"></a>Aby zmienić typ wykresu, który jest wyświetlany w dokumencie

1. Dodaj następującą obsługę zdarzeń w celu `ThisDocument` klasy.

     [!code-vb[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#15)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#15)]

2. W C#, należy dodać program obsługi zdarzeń dla formantu użytkownika, aby <xref:Microsoft.Office.Tools.Word.Document.Startup> zdarzeń.

     [!code-csharp[Trin_VstcoreProgrammingControlsWord#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#16)]

## <a name="test-the-application"></a>Testowanie aplikacji
 Teraz możesz przetestować dokumencie, aby upewnić się, że styl wykresu jest poprawnie aktualizowany po wybraniu przycisku radiowego.

### <a name="to-test-your-document"></a>Aby przetestować dokumentu

1. Naciśnij klawisz **F5** Aby uruchomić projekt.

2. Wybierz różne przycisków radiowych.

3. Upewnij się, że styl wykresu zmienia się zgodnie z wyborem.

## <a name="next-steps"></a>Następne kroki
 Poniżej przedstawiono niektóre zadania, które mogą pochodzić dalej:

- Za pomocą przycisku, aby wypełnić pole tekstowe. Aby uzyskać więcej informacji, zobacz [instruktażu: Wyświetlanie tekstu w polu tekstowym w dokumencie za pomocą przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).

- Zmienianie formatowania przez wybranie stylu z pola kombi. Aby uzyskać więcej informacji, zobacz [instruktażu: Dokument Zmienianie formatowania za pomocą formantów CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>Zobacz także
- [Wskazówki dotyczące przy użyciu programu Word](../vsto/walkthroughs-using-word.md)
- [Office development ― przykłady i przewodniki](../vsto/office-development-samples-and-walkthroughs.md)
- [Ograniczenia kontrolek Windows Forms w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
