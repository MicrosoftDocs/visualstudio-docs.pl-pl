---
title: 'Przewodnik: Synchronizuj niestandardowego okienka zadań z przyciskiem wstążki'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom task panes [Office development in Visual Studio], showing and hiding
- showing custom task panes
- Ribbon [Office development in Visual Studio], custom task panes
- toggle buttons [Office development in Visual Studio]
- custom task panes [Office development in Visual Studio], synchronizing with Ribbon button
- user interfaces [Office development in Visual Studio], custom task panes
- synchronization [Office development in Visual Studio], custom task panes
- task panes [Office development in Visual Studio], showing and hiding
- custom task panes [Office development in Visual Studio], creating
- hiding custom task panes
- task panes [Office development in Visual Studio], creating
- task panes [Office development in Visual Studio], synchronizing with Ribbon button
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fdbcf16139c1f0b48554b3bf14f314a73a641012
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040667"
---
# <a name="walkthrough-synchronize-a-custom-task-pane-with-a-ribbon-button"></a>Przewodnik: Synchronizuj niestandardowego okienka zadań z przyciskiem wstążki
  Ten przewodnik przedstawia sposób tworzenia niestandardowego okienka zadań, które użytkownicy mogą ukryć lub wyświetlić, klikając przycisk przełącznika na Wstążce. Należy zawsze utworzyć elementu interfejsu użytkownika, takie jak przycisk, który można kliknąć, aby wyświetlić lub ukryć niestandardowego okienka zadań, ponieważ aplikacje Microsoft Office nie umożliwiają domyślne użytkownikom wyświetlanie lub ukrywanie niestandardowych okienek zadań.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Mimo że program Excel jest wykorzystywany w tym przewodniku szczegółowo, koncepcje dowodzą Instruktaż mają zastosowanie do wszystkie aplikacje, które są wymienione powyżej.

 W instruktażu przedstawiono następujące zagadnienia:

- Projektowanie interfejsu użytkownika niestandardowego okienka zadań.

- Dodawanie przycisku przełącznika do wstążki.

- Synchronizowanie przycisk przełączania z niestandardowego okienka zadań.

> [!NOTE]
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Program Microsoft Excel lub Microsoft [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)].

## <a name="create-the-add-in-project"></a>Utwórz projekt dodatku
 W tym kroku utworzysz projekt dodatku narzędzi VSTO dla programu Excel.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt dodatku programu Excel o nazwie **SynchronizeTaskPaneAndRibbon**, przy użyciu szablonu projektu dodatku programu Excel. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwiera **ThisAddIn.cs** lub **ThisAddIn.vb** plik kodu i dodaje **SynchronizeTaskPaneAndRibbon** projekt **Eksploratora rozwiązań**.

## <a name="add-a-toggle-button-to-the-ribbon"></a>Dodaj przycisk przełączania do wstążki
 Jedną z wytycznych projektowania aplikacji pakietu Office jest, czy użytkownicy powinni zawsze mieć kontrolki interfejsu użytkownika aplikacji pakietu Office. Aby umożliwić użytkownikom określanie niestandardowego okienka zadań, można dodać przycisk przełączania wstążki, który pokazuje i ukrywa okienko zadań. Aby utworzyć przycisk przełączania, Dodaj **Wstążka (Projektant graficzny)** do projektu. Projektant pomaga dodać i ustawianie formantów, ustawianie właściwości formantu i obsługiwać zdarzenia formantu. Aby uzyskać więcej informacji, zobacz [projektanta wstążki](../vsto/ribbon-designer.md).

### <a name="to-add-a-toggle-button-to-the-ribbon"></a>Aby dodać przycisk przełączania do wstążki

1. Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.

2. W **Dodaj nowy element** okno dialogowe, wybierz opcję **Wstążka (Projektant graficzny)**.

3. Zmień nazwę nowego wstążki do **ManageTaskPaneRibbon**i kliknij przycisk **Dodaj**.

     **ManageTaskPaneRibbon.cs** lub **ManageTaskPaneRibbon.vb** plik zostanie otwarty w Projektancie Wstążki i wyświetla domyślną kartę i grupę.

4. W Projektancie Wstążki kliknij **grupa1**.

5. W **właściwości** oknie **etykiety** właściwości **Menedżera okienka zadań**.

6. Z **formanty wstążki Office** karcie **przybornika**, przeciągnij **ToggleButton** na **Menedżera okienka zadań** grupy.

7. Click **toggleButton1**.

8. W **właściwości** oknie **etykiety** właściwości **Pokaż okienko zadań**.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Projektowanie interfejsu użytkownika niestandardowego okienka zadań
 Brak wizualnego projektanta dla niestandardowych okienek zadań, ale można projektować kontrolkę użytkownika przy użyciu układu, który ma. W dalszej części tego przewodnika dodasz formant użytkownika do niestandardowego okienka zadań.

### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Projekt interfejsu użytkownika niestandardowego okienka zadań

1. Na **projektu** menu, kliknij przycisk **Dodaj kontrolkę użytkownika**.

2. W **Dodaj nowy element** okna dialogowego pole, Zmień nazwę kontrolki użytkownika do **TaskPaneControl**i kliknij przycisk **Dodaj**.

     Formant użytkownika zostanie otwarty w projektancie.

3. Z **wspólnych formantów** karcie **przybornika**, przeciągnij **TextBox** kontrolki do kontrolki użytkownika.

## <a name="create-the-custom-task-pane"></a>Tworzenie niestandardowego okienka zadań
 Do uruchomienia dodatku narzędzi VSTO dla programów, należy utworzyć niestandardowego okienka zadań, Dodaj formant użytkownika do okienka zadań w <xref:Microsoft.Office.Tools.AddIn.Startup> programu obsługi zdarzeń w dodatku VSTO. Domyślnie niestandardowego okienka zadań nie będą widoczne. W dalszej części tego przewodnika należy dodać kod, który spowoduje wyświetlanie lub ukrywanie okienka zadań, gdy użytkownik kliknie przycisk przełącznika, który dodano do wstążki.

### <a name="to-create-the-custom-task-pane"></a>Aby utworzyć niestandardowego okienka zadań

1. W **Eksploratora rozwiązań**, rozwiń węzeł **Excel**.

2. Kliknij prawym przyciskiem myszy **ThisAddIn.cs** lub **ThisAddIn.vb** i kliknij przycisk **Wyświetl kod**.

3. Dodaj następujący kod do `ThisAddIn` klasy. Ten kod deklaruje wystąpienie `TaskPaneControl` jako członek `ThisAddIn`.

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#1](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#1)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#1)]

4. Zastąp `ThisAddIn_Startup` programu obsługi zdarzeń z następującym kodem. Ten kod dodaje `TaskPaneControl` obiekt `CustomTaskPanes` pole, ale nie wyświetla niestandardowego okienka zadań (domyślnie <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> właściwość <xref:Microsoft.Office.Tools.CustomTaskPane> klasa jest **false**). Kod Visual C# dołącza również program obsługi zdarzeń do <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> zdarzeń.

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#2](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#2)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#2)]

5. Dodaj następującą metodę do `ThisAddIn` klasy. Ta metoda obsługuje <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> zdarzeń. Gdy użytkownik zamknie okienka zadań, klikając **Zamknij** przycisku (X), te aktualizacje metoda stan przełącznik znajdujący się na Wstążce.

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#3](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#3)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#3](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#3)]

6. Dodaj następującą właściwość do `ThisAddIn` klasy. Ta właściwość udostępnia prywatna `myCustomTaskPane1` obiektu dla innych klas. W dalszej części tego przewodnika, można dodać kod `MyRibbon` klasy, która używa tej właściwości.

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#4](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#4)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#4](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#4)]

## <a name="hide-and-show-the-custom-task-pane-by-using-the-toggle-button"></a>Ukryć i pokazać niestandardowego okienka zadań za pomocą przycisku przełączania
 Ostatnim krokiem jest, aby dodać kod, który wyświetla lub ukrywa niestandardowego okienka zadań, gdy użytkownik kliknie przycisk przełączania na Wstążce.

### <a name="to-display-and-hide-the-custom-task-pane-by-using-the-toggle-button"></a>Aby wyświetlić i ukryć niestandardowego okienka zadań za pomocą przycisku przełączania

1. W Projektancie wstążki, kliknij dwukrotnie **Pokaż okienko zadań** przycisku przełączania.

     Program Visual Studio automatycznie generuje moduł obsługi zdarzeń o nazwie `toggleButton1_Click`, która obsługuje <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> zdarzenia przycisku przełącznika. Program Visual Studio otwiera również *MyRibbon.cs* lub *MyRibbon.vb* plik w edytorze kodu.

2. Zastąp `toggleButton1_Click` programu obsługi zdarzeń z następującym kodem. Gdy użytkownik kliknie przycisk przełączania, ten kod wyświetla lub ukrywa niestandardowego okienka zadań, w zależności od tego, czy przycisk przełączania jest wciśnięty lub nie.

     [!code-vb[Trin_TaskPaneRibbonSynchronize#5](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.vb#5)]
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#5](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.cs#5)]

## <a name="test-the-add-in"></a>Testowanie dodatku programu
 Kiedy uruchamiasz projekt, zostanie otwarty bez wyświetlania niestandardowego okienka zadań. Kliknij przycisk przełączania na Wstążce Aby przetestować kod.

### <a name="to-test-your-vsto-add-in"></a>Aby przetestować dodatku narzędzi VSTO

1. Naciśnij klawisz **F5** Aby uruchomić projekt.

     Upewnij się, że, zostanie otwarty i **Add-Ins** na Wstążce zostanie wyświetlona karta.

2. Kliknij przycisk **Add-Ins** karty na Wstążce.

3. W **Menedżera okienka zadań** grupy, kliknij przycisk **Pokaż okienko zadań** przycisku przełączania.

     Sprawdź okienko zadań jest też wyświetlana i ukryty, gdy klikniesz przycisk przełącznika.

4. Gdy okienko zadań jest widoczna, kliknij przycisk **Zamknij** przycisku (X) w rogu okienka zadań.

     Sprawdź, czy przycisk przełączania wydaje się być nienaciśnięty.

## <a name="next-steps"></a>Następne kroki
 Możesz dowiedzieć się więcej na temat sposobu tworzenia niestandardowych okienek zadań z tych tematów:

- Tworzenie niestandardowego okienka zadań w dodatku narzędzi VSTO dla różnych aplikacji. Aby uzyskać więcej informacji na temat aplikacji, które obsługują niestandardowe okienka zadań, zobacz [niestandardowych okienek zadań](../vsto/custom-task-panes.md).

- Automatyzacja aplikacji z niestandardowego okienka zadań. Aby uzyskać więcej informacji, zobacz [instruktażu: Automatyzacja aplikacji z niestandardowego okienka zadań](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md).

- Tworzenie niestandardowego okienka zadań dla każdej wiadomości e-mail, który jest otwierany w programie Outlook. Aby uzyskać więcej informacji, zobacz [instruktażu: Wyświetlanie niestandardowych okienek zadań z wiadomościami e-mail w programie Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).

## <a name="see-also"></a>Zobacz także
- [Niestandardowe okienka zadań](../vsto/custom-task-panes.md)
- [Instrukcje: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Przewodnik: Automatyzacja aplikacji z niestandardowego okienka zadań](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [Przewodnik: Wyświetlanie niestandardowych okienek zadań z wiadomościami e-mail w programie Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
- [Wstążka — omówienie](../vsto/ribbon-overview.md)
