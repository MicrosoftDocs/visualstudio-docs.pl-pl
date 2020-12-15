---
title: 'Przewodnik: wstawianie tekstu do dokumentu z okienka akcji'
description: Utwórz okienko akcji w dokumencie programu Microsoft Word. Dowiedz się, że okienko akcje zawiera dwie kontrolki, które zbierają dane wejściowe, a następnie wysyłają tekst do dokumentu.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- smart documents [Office development in Visual Studio], creating in Word
- smart documents [Office development in Visual Studio], adding controls
- actions panes [Office development in Visual Studio], creating in Word
- actions panes [Office development in Visual Studio], adding controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 44fd876dfad99e1a1320a5e5d743ea8e30dfdb98
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524168"
---
# <a name="walkthrough-insert-text-into-a-document-from-an-actions-pane"></a>Przewodnik: wstawianie tekstu do dokumentu z okienka akcji
  W tym instruktażu przedstawiono sposób tworzenia okienka akcji w dokumencie programu Microsoft Office Word. Okienko akcje zawiera dwie kontrolki, które zbierają dane wejściowe, a następnie wysyłają tekst do dokumentu.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Zaprojektuj interfejs za pomocą kontrolek Windows Forms w kontrolce okienka akcji.

- Wyświetl okienko akcje, gdy aplikacja zostanie otwarta.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Tworzenie projektu
 Pierwszym krokiem jest utworzenie projektu dokumentu programu Word.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt dokumentu programu Word za pomocą **okienka nazwa moje podstawowe akcje**. W kreatorze wybierz pozycję **Utwórz nowy dokument**. Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Program Visual Studio otwiera nowy dokument programu Word w Projektancie i dodaje projekt **okienka moje podstawowe akcje** do **Eksplorator rozwiązań**.

## <a name="add-text-and-bookmarks-to-the-document"></a>Dodaj tekst i zakładki do dokumentu
 Okienko akcje wyśle tekst do zakładek w dokumencie. Aby zaprojektować dokument, wpisz tekst w celu utworzenia podstawowego formularza.

### <a name="to-add-text-to-your-document"></a>Aby dodać tekst do dokumentu

1. Wpisz następujący tekst do dokumentu programu Word:

    **21 marca 2008**

    **Nazwa**

    **Adres**

    **Jest to przykład podstawowego okienka akcji w programie Word.**

   Możesz dodać <xref:Microsoft.Office.Tools.Word.Bookmark> formant do dokumentu, przeciągając go z **przybornika** w programie Visual Studio lub za pomocą okna dialogowego **zakładka** w programie Word.

### <a name="to-add-a-bookmark-control-to-your-document"></a>Aby dodać kontrolkę zakładki do dokumentu

1. Na karcie **formanty programu Word** **przybornika** przeciągnij <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolkę do dokumentu.

     Zostanie wyświetlone okno dialogowe **Dodawanie kontrolki zakładki** .

2. Wybierz **nazwę** słowa, bez zaznaczania znacznika akapitu, i kliknij przycisk **OK**.

    > [!NOTE]
    > Znacznik akapitu powinien znajdować się poza zakładką. Jeśli znaczniki akapitu nie są widoczne w dokumencie, kliknij menu **Narzędzia** , wskaż polecenie **Microsoft Office narzędzia programu Word** , a następnie kliknij przycisk **Opcje**. Kliknij kartę **Widok** , a następnie zaznacz pole wyboru **znaczniki akapitu** w sekcji **znaczniki formatowania** okna dialogowego **Opcje** .

3. W oknie **Właściwości** Zmień właściwość **Nazwa** **Bookmark1** na **showName**.

4. Wybierz **adres** słowa, bez zaznaczania znacznika akapitu.

5. Na karcie **Wstawianie** wstążki w grupie **linki** kliknij pozycję **zakładka**.

6. W oknie dialogowym **zakładka** wpisz **ShowAddress** w polu **Nazwa zakładki** , a następnie kliknij przycisk **Dodaj**.

## <a name="add-controls-to-the-actions-pane"></a>Dodawanie kontrolek do okienka Akcje
 Aby zaprojektować interfejs okienka Akcje, Dodaj kontrolkę okienko akcji do projektu, a następnie Dodaj kontrolki Windows Forms do kontrolki okienko akcji.

### <a name="to-add-an-actions-pane-control"></a>Aby dodać kontrolkę okienka akcji

1. Wybierz projekt **okienka moje podstawowe akcje** w **Eksplorator rozwiązań**.

2. W menu **projekt** kliknij polecenie **Dodaj nowy element**.

3. W oknie dialogowym **Dodaj nowy element** kliknij pozycję **kontrolka okienka akcji**, Nadaj formantowi **InsertTextControl,** a następnie kliknij przycisk **Dodaj**.

#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>Aby dodać kontrolki formularza systemu Windows do kontrolki okienka akcji

1. Jeśli formant okienka Akcje nie jest widoczny w projektancie, kliknij dwukrotnie pozycję **InsertTextControl**.

2. Na karcie **Formanty standardowe** **przybornika** przeciągnij kontrolkę **etykieta** do kontrolki okienko akcji.

3. Zmień właściwość **Text** kontrolki etykieta na **Nazwa**.

4. Dodaj kontrolkę **TextBox** do kontrolki okienka Akcje i Zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**GetName —**|
    |**Rozmiar**|**130, 20**|

5. Dodaj drugą kontrolkę **etykieta** do kontrolki okienko akcje i zmień właściwość **Text** na **Address**.

6. Dodaj drugą kontrolkę **TextBox** do kontrolki okienka Akcje i Zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**GetAddress —**|
    |**Akceptuje Return**|**True**|
    |**Multiline**|**True**|
    |**Rozmiar**|**130, 40**|

7. Dodaj kontrolkę **przycisk** do kontrolki okienko akcje i Zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**AddText**|
    |**Tekst**|**Insert**|

## <a name="add-code-to-insert-text-into-the-document"></a>Dodaj kod, aby wstawić tekst do dokumentu
 W okienku Akcje Napisz kod, który wstawia tekst z pól tekstowych do odpowiednich <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolek w dokumencie. Możesz użyć klasy, `Globals` Aby uzyskać dostęp do formantów w dokumencie z kontrolek w okienku Akcje. Aby uzyskać więcej informacji, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>Aby wstawić tekst z okienka Akcje w zakładce w dokumencie

1. Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> procedury obsługi zdarzeń przycisku **AddText** .

     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb#8)]

2. W języku C# należy dodać procedurę obsługi zdarzeń dla przycisku. Ten kod można umieścić w `InsertTextControl` konstruktorze po wywołaniu `InitializeComponent` . Aby uzyskać informacje na temat tworzenia programów obsługi zdarzeń, zobacz [How to: Create Event Handles in Office projects](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#9)]

## <a name="add-code-to-show-the-actions-pane"></a>Dodaj kod, aby wyświetlić okienko akcje
 Aby wyświetlić okienko akcje, Dodaj utworzony formant do kolekcji kontrolek.

### <a name="to-show-the-actions-pane"></a>Aby wyświetlić okienko akcje

1. Utwórz nowe wystąpienie kontrolki okienko akcji w `ThisDocument` klasie.

     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#10)]

2. Dodaj następujący kod do <xref:Microsoft.Office.Tools.Word.Document.Startup> programu obsługi zdarzeń programu `ThisDocument` .

     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#11)]

## <a name="test-the-application"></a>Testowanie aplikacji
 Przetestuj dokument, aby upewnić się, że okienko akcje otwiera się po otwarciu dokumentu, a tekst, który wpisano do pól tekstowych, zostanie wstawiony do zakładek, gdy przycisk zostanie kliknięty.

### <a name="to-test-your-document"></a>Aby przetestować dokument

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

2. Upewnij się, że okienko akcje jest widoczne.

3. Wpisz swoje imię i nazwisko oraz adres do pól tekstowych w okienku Akcje, a następnie kliknij przycisk **Wstaw**.

## <a name="next-steps"></a>Następne kroki
 Poniżej przedstawiono kilka zadań, które mogą wystąpić poniżej:

- Utwórz okienko akcji w programie Excel. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie akcji okienka do skoroszytów programu Excel](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100)).

- Powiąż dane z kontrolkami w okienku Akcje. Aby uzyskać więcej informacji, zobacz [Przewodnik: powiązywanie danych z kontrolkami w okienku Akcje programu Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).

## <a name="see-also"></a>Zobacz też
- [Przegląd okienka Akcje](../vsto/actions-pane-overview.md)
- [Instrukcje: Dodawanie okienka akcji do dokumentów programu Word lub skoroszytów programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Instrukcje: Dodawanie okienka akcji do skoroszytów programu Excel](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))
- [Instrukcje: zarządzanie układem sterowania w okienkach akcji](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Kontrolka zakładki](../vsto/bookmark-control.md)
