---
title: 'Przewodnik: Wstawianie tekstu do dokumentu z okienka akcji'
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
ms.openlocfilehash: 49a570a68d2ce301ff103c3587e3246a725a1f42
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866279"
---
# <a name="walkthrough-insert-text-into-a-document-from-an-actions-pane"></a>Przewodnik: Wstawianie tekstu do dokumentu z okienka akcji
  W tym przewodniku pokazano, jak utworzyć okienka akcji w dokumencie programu Microsoft Office Word. W okienku Akcje zawiera dwie kontrolki, które gromadzenia danych wejściowych, a następnie wyślij tekstu do dokumentu.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Zaprojektuj interfejs, za pomocą kontrolek Windows Forms na kontrolki okienka akcji.  
  
-   Wyświetlany w okienku Akcje, gdy aplikacja zostanie otwarta.  
  
> [!NOTE]  
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="create-the-project"></a>Utwórz projekt  
 Pierwszym krokiem jest utworzenie projektu dokument programu Word.  
  
### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt  
  
1.  Tworzenie projektu dokument programu Word z nazwą **Moje podstawowe okienko akcji**. W kreatorze Wybierz **Utwórz nowy dokument**. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio otwiera nowy dokument programu Word w Projektancie i dodaje **Moje podstawowe okienko akcji** projekt **Eksploratora rozwiązań**.  
  
## <a name="add-text-and-bookmarks-to-the-document"></a>Dodawanie tekstu i zakładki do dokumentu  
 W okienku Akcje wyśle tekstu do zakładki w dokumencie. Do projektowania dokument, wpisz jakiś tekst, aby utworzyć formularz podstawowy.  
  
### <a name="to-add-text-to-your-document"></a>Dodawanie tekstu do dokumentu  
  
1. Wpisz następujący tekst w dokumencie programu Word:  
  
    **21 marca 2008**  
  
    **Nazwa**  
  
    **Adres**  
  
    **Jest to przykład okienko podstawowe działania w programie Word.**  
  
   Możesz dodać <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki do dokumentu, przeciągając go z **przybornika** w programie Visual Studio lub za pomocą **zakładki** okno dialogowe w programie Word.  
  
### <a name="to-add-a-bookmark-control-to-your-document"></a>Aby dodać kontrolkę zakładki w dokumencie  
  
1.  Z **formanty programu Word** karcie **przybornika**, przeciągnij <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki do dokumentu.  
  
     **Dodaj kontrolkę zakładki** pojawi się okno dialogowe.  
  
2.  Zaznacz wyraz **nazwa**, bez wybierając znak akapitu i kliknij przycisk **OK**.  
  
    > [!NOTE]  
    >  Znak powinien znajdować się poza zakładki. Znaczniki akapitu nie są widoczne w dokumencie, kliknij przycisk **narzędzia** menu wskaż **narzędzi pakietu Microsoft Office Word** a następnie kliknij przycisk **opcje**. Kliknij przycisk **widoku** , a następnie wybierz pozycję **znaczniki akapitów** pole wyboru w **znaczniki formatowania** części **opcje** okno dialogowe.  
  
3.  W **właściwości** oknie zmiany **nazwa** właściwość **Bookmark1** do **showName**.  
  
4.  Zaznacz wyraz **adres**, bez zaznaczania znak akapitu.  
  
5.  Na **Wstaw** karty wstążki w **łącza** grupy, kliknij przycisk **zakładki**.  
  
6.  W **zakładki** okno dialogowe, typ **showAddress** w **nazwy zakładki** pole, a następnie kliknij przycisk **Dodaj**.  
  
## <a name="add-controls-to-the-actions-pane"></a>Dodawanie formantów do okienka akcji  
 Projektować interfejs okienka akcji, dodać kontrolki okienka akcji do projektu, a następnie dodaj kontrolek formularzy Windows Forms do kontrolki okienka akcji.  
  
### <a name="to-add-an-actions-pane-control"></a>Aby dodać kontrolki okienka akcji  
  
1.  Wybierz **Moje podstawowe okienko akcji** projektu w **Eksploratora rozwiązań**.  
  
2.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
3.  W **Dodaj nowy element** okno dialogowe, kliknij przycisk **kontrolki okienka akcji**, nazwij kontrolkę **InsertTextControl,** i kliknij przycisk **Dodaj**.  
  
#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>Aby dodać kontrolek formularzy Windows do kontrolki okienka akcji  
  
1.  Jeśli kontrolka okienka akcji nie jest widoczny w projektancie, kliknij dwukrotnie **InsertTextControl**.  
  
2.  Z **wspólnych formantów** karcie **przybornika**, przeciągnij **etykiety** kontrolki do kontrolki okienka akcji.  
  
3.  Zmiana **tekstu** właściwości formantu etykiety, aby **nazwa**.  
  
4.  Dodaj **Textbox** kontrolę kontrolki okienka akcji i Zmień następujące właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**getName**|  
    |**Rozmiar**|**130, 20**|  
  
5.  Dodaj drugą **etykiety** kontrolę kontrolki okienka akcji, a następnie zmień **tekstu** właściwości **adres**.  
  
6.  Dodaj drugą **Textbox** kontrolę kontrolki okienka akcji i Zmień następujące właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**getAddress**|  
    |**Akceptuje powrotu**|**True**|  
    |**Wielowierszowy**|**True**|  
    |**Rozmiar**|**130, 40**|  
  
7.  Dodaj **przycisk** kontrolę kontrolki okienka akcji i Zmień następujące właściwości.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**Nazwa**|**addText**|  
    |**Text**|**Wstaw**|  
  
## <a name="add-code-to-insert-text-into-the-document"></a>Dodaj kod, aby Wstawianie tekstu do dokumentu  
 W okienku Akcje napisać kod, który wstawia tekst z pola tekstowe w odpowiednim <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolek w dokumencie. Możesz użyć `Globals` klasy, aby uzyskać dostęp do dokumentu z kontrolek w okienku akcji. Aby uzyskać więcej informacji, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>Wstawianie tekstu w okienku Akcje w zakładki w dokumencie  
  
1.  Dodaj następujący kod do <xref:System.Windows.Forms.Control.Click> program obsługi zdarzeń **addText** przycisku.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#8)]
     [!code-vb[Trin_VstcoreActionsPaneWord#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb#8)]  
  
2.  W języku C# należy dodać moduł obsługi zdarzenia kliknięcia przycisku. Możesz umieścić ten kod w `InsertTextControl` konstruktora, po wywołaniu `InitializeComponent`. Aby dowiedzieć się, jak tworzenie procedur obsługi zdarzeń, zobacz [jak: Tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs#9)]  
  
## <a name="add-code-to-show-the-actions-pane"></a>Dodaj kod, aby pokazać okienko akcji  
 Aby pokazać okienko akcji, należy dodać formant, który został utworzony w kolekcji formant.  
  
### <a name="to-show-the-actions-pane"></a>Aby pokazać okienko akcji  
  
1.  Utwórz nowe wystąpienie kontrolki okienka akcji w `ThisDocument` klasy.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreActionsPaneWord#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#10)]  
  
2.  Dodaj następujący kod do <xref:Microsoft.Office.Tools.Word.Document.Startup> program obsługi zdarzeń `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs#11)]
     [!code-vb[Trin_VstcoreActionsPaneWord#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb#11)]  
  
## <a name="test-the-application"></a>Testowanie aplikacji  
 Przetestuj dokument, aby sprawdzić, czy po otwarciu dokumentu i czy tekst wpisany w polach tekstowych jest wstawiany do zakładek, po kliknięciu przycisku zostanie otwarte okienko akcji.  
  
### <a name="to-test-your-document"></a>Aby przetestować dokumentu  
  
1.  Naciśnij klawisz **F5** Aby uruchomić projekt.  
  
2.  Upewnij się, że widoczne jest okienko akcji.  
  
3.  Wpisz nazwę i adres w polach tekstowych w okienku akcji, a następnie kliknij przycisk **Wstaw**.  
  
## <a name="next-steps"></a>Następne kroki  
 Poniżej przedstawiono niektóre zadania, które mogą pochodzić dalej:  
  
-   Tworzenie okienek akcji w programie Excel. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie okienek akcji do skoroszytów programu Excel](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100)).  
  
-   Wiązanie danych z kontrolkami w okienku Akcje. Aby uzyskać więcej informacji, zobacz [instruktażu: Wiązanie danych z kontrolkami w okienku akcji programu Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)   
 [Instrukcje: Dodawanie okienek akcji do dokumentów programu Word lub arkuszy programu Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Instrukcje: Dodawanie okienek akcji do skoroszytów programu Excel](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))   
 [Instrukcje: Zarządzanie układem formantu w okienkach akcji](../vsto/how-to-manage-control-layout-on-actions-panes.md)   
 [BOOKMARK, kontrolka](../vsto/bookmark-control.md)  
