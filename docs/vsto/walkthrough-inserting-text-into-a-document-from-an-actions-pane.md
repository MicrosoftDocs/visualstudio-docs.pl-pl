---
title: 'Przewodnik: wstawianie tekstu do dokumentu z okienka akcji'
description: Utwórz okienko akcji w dokumencie programu Microsoft Word. Dowiedz się, że okienko akcji zawiera dwie kontrolki, które zbierają dane wejściowe, a następnie wysyłają tekst do dokumentu.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1ac42954e32b30a293abbe031218213948fb103a
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824981"
---
# <a name="walkthrough-insert-text-into-a-document-from-an-actions-pane"></a>Przewodnik: wstawianie tekstu do dokumentu z okienka akcji
  W tym przewodniku pokazano, jak utworzyć okienko akcji w Microsoft Office programu Word. Okienko akcji zawiera dwie kontrolki, które zbierają dane wejściowe, a następnie wysyłają tekst do dokumentu.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Projektowanie interfejsu przy użyciu Windows Forms kontrolek w kontrolce okienka akcji.

- Wyświetla okienko akcji po otworze aplikacji.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Personalizowanie środowiska IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].

## <a name="create-the-project"></a>Tworzenie projektu
 Pierwszym krokiem jest utworzenie projektu dokumentu programu Word.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt dokumentu programu Word o nazwie My Basic Actions Pane (Moje **podstawowe akcje).** W kreatorze wybierz **pozycję Utwórz nowy dokument.** Aby uzyskać więcej informacji, [zobacz How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio nowy dokument programu Word w projektancie i dodaje projekt Okienko Moje podstawowe **akcje** do **Eksplorator rozwiązań**.

## <a name="add-text-and-bookmarks-to-the-document"></a>Dodawanie tekstu i zakładek do dokumentu
 Okienko akcji spowoduje wysłanie tekstu do zakładek w dokumencie. Aby zaprojektować dokument, wpisz jakiś tekst, aby utworzyć formularz podstawowy.

### <a name="to-add-text-to-your-document"></a>Aby dodać tekst do dokumentu

1. Wpisz następujący tekst w dokumencie programu Word:

    **21 marca 2008 r.**

    **Nazwa**

    **Adres**

    **Jest to przykład podstawowego okienka akcji w programie Word.**

   Kontrolkę można dodać do dokumentu, przeciągając ją z przybornika w Visual Studio lub przy użyciu okna <xref:Microsoft.Office.Tools.Word.Bookmark> **dialogowego** Zakładka w programie Word. 

### <a name="to-add-a-bookmark-control-to-your-document"></a>Aby dodać kontrolkę Zakładka do dokumentu

1. Na karcie **Kontrolki programu Word** **przybornika** przeciągnij <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolkę do dokumentu.

     Zostanie **wyświetlone okno dialogowe Dodawanie kontrolki** zakładki.

2. Wybierz wyraz **Name (Nazwa)** bez zaznaczania znacznika akapitu, a następnie kliknij przycisk **OK.**

    > [!NOTE]
    > Znacznik akapitu powinien być poza zakładką. Jeśli znaki akapitu nie są widoczne w dokumencie, kliknij **menu** Narzędzia, wskaż polecenie narzędzia Microsoft Office **Word,** a następnie kliknij pozycję **Opcje**. Kliknij **kartę Widok** i zaznacz pole wyboru **Znaczniki akapitu** w sekcji **Znaczniki** formatowania okna **dialogowego** Opcje.

3. W **oknie** Właściwości zmień właściwość **Name zakładki** **Bookmark1** na **showName**.

4. Wybierz wyraz **Address (Adres)** bez zaznaczania znacznika akapitu.

5. Na karcie **Wstawianie** wstążki w grupie **Linki** kliknij pozycję **Zakładka.**

6. W **oknie dialogowym** Zakładka wpisz **showAddress** w polu **Nazwa zakładki** i kliknij przycisk **Dodaj**.

## <a name="add-controls-to-the-actions-pane"></a>Dodawanie kontrolek do okienka akcji
 Aby zaprojektować interfejs okienka akcji, dodaj do projektu kontrolkę okienka akcji, a następnie dodaj kontrolki Windows Forms do kontrolki okienka akcji.

### <a name="to-add-an-actions-pane-control"></a>Aby dodać kontrolkę okienka akcji

1. Wybierz projekt **My Basic Actions Pane (Okienko moje** podstawowe akcje) w **Eksplorator rozwiązań**.

2. W menu **Project (Projekt)** kliknij **pozycję Add New Item (Dodaj nowy element).**

3. W **oknie dialogowym Dodawanie nowego elementu** kliknij pozycję **Kontrolka okienka akcje,** nadaj **kontrolce nazwę InsertTextControl,** a następnie kliknij przycisk **Dodaj**.

#### <a name="to-add-windows-form-controls-to-the-actions-pane-control"></a>Aby dodać kontrolki Formularz systemu Windows do kontrolki okienka akcji

1. Jeśli kontrolka okienka akcji nie jest widoczna w projektancie, kliknij dwukrotnie **pozycję InsertTextControl**.

2. Na karcie **Typowe kontrolki** **przybornika** przeciągnij kontrolkę **Etykieta** do kontrolki okienka akcji.

3. Zmień właściwość **Text** kontrolki Etykieta na **Nazwa**.

4. Dodaj **kontrolkę Pole tekstowe** do kontrolki okienka akcji i zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**Getname**|
    |**Rozmiar**|**130, 20**|

5. Dodaj drugą **kontrolkę Etykieta** do kontrolki okienka akcji i zmień **właściwość Text** na **Adres**.

6. Dodaj drugą **kontrolkę Pole tekstowe** do kontrolki okienka akcji i zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**getAddress**|
    |**Akceptuje zwrot**|**True**|
    |**Multiline**|**True**|
    |**Rozmiar**|**130, 40**|

7. Dodaj **kontrolkę Przycisk** do kontrolki okienka akcji i zmień następujące właściwości.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**Nazwa**|**addText**|
    |**Tekst**|**Insert**|

## <a name="add-code-to-insert-text-into-the-document"></a>Dodawanie kodu w celu wstawiania tekstu do dokumentu
 W okienku akcji napisz kod, który wstawia tekst z pól tekstowych do odpowiednich <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolek w dokumencie. Możesz użyć klasy `Globals` , aby uzyskać dostęp do kontrolek w dokumencie z kontrolek w okienku akcji. Aby uzyskać więcej informacji, zobacz [Globalny dostęp do obiektów w projektach pakietu Office.](../vsto/global-access-to-objects-in-office-projects.md)

### <a name="to-insert-text-from-the-actions-pane-in-a-bookmark-in-the-document"></a>Aby wstawić tekst z okienka akcji w zakładce w dokumencie

1. Dodaj następujący kod do procedury <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń **przycisku addText.**

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/InsertTextControl.vb" id="Snippet8":::

2. W języku C# musisz dodać program obsługi zdarzeń dla kliknięcia przycisku. Ten kod można umieścić w `InsertTextControl` konstruktorze po wywołaniu . `InitializeComponent` Aby uzyskać informacje na temat tworzenia programów obsługi zdarzeń, zobacz [Jak tworzyć procedury obsługi zdarzeń w projektach pakietu Office.](../vsto/how-to-create-event-handlers-in-office-projects.md)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/InsertTextControl.cs" id="Snippet9":::

## <a name="add-code-to-show-the-actions-pane"></a>Dodawanie kodu w celu pokazania okienka akcji
 Aby wyświetlić okienko akcji, dodaj utworzoną kontrolkę do kolekcji kontrolek.

### <a name="to-show-the-actions-pane"></a>Aby wyświetlić okienko akcji

1. Utwórz nowe wystąpienie kontrolki okienka akcji w `ThisDocument` klasie .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet10":::

2. Dodaj następujący kod do procedury <xref:Microsoft.Office.Tools.Word.Document.Startup> obsługi zdarzeń `ThisDocument` programu .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreActionsPaneWordCS/ThisDocument.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreActionsPaneWordVB/ThisDocument.vb" id="Snippet11":::

## <a name="test-the-application"></a>Testowanie aplikacji
 Przetestuj dokument, aby sprawdzić, czy okienko akcji jest otwierane po otwarciu dokumentu i czy tekst wpisany w polach tekstowych jest wstawiany do zakładek po kliknięciu przycisku.

### <a name="to-test-your-document"></a>Aby przetestować dokument

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

2. Upewnij się, że okienko akcji jest widoczne.

3. Wpisz swoją nazwę i adres w polach tekstowych w okienku akcji, a następnie kliknij pozycję **Wstaw**.

## <a name="next-steps"></a>Następne kroki
 Oto kilka zadań, które mogą się pojawić w następnej części:

- Tworzenie okienka akcji w programie Excel. Aby uzyskać więcej informacji, [zobacz Jak dodać okienko akcji do skoroszytów programu Excel.](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))

- Powiąż dane z kontrolkami w okienku akcji. Aby uzyskać więcej informacji, [zobacz Przewodnik: wiązanie danych z kontrolkami w okienku akcji programu Word.](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md)

## <a name="see-also"></a>Zobacz też
- [Omówienie okienka Akcje](../vsto/actions-pane-overview.md)
- [How to: Add an actions pane to Word documents or Excel workbooks (Jak dodać okienko akcji do dokumentów programu Word lub skoroszytów programu Excel)](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [How to: Add an actions pane to Excel workbooks (Jak dodać okienko akcji do skoroszytów programu Excel)](/previous-versions/visualstudio/visual-studio-2010/e3zbk0hz(v=vs.100))
- [Samodzielnie: zarządzanie układem kontrolek w okienkach akcji](../vsto/how-to-manage-control-layout-on-actions-panes.md)
- [Kontrolka zakładki](../vsto/bookmark-control.md)
