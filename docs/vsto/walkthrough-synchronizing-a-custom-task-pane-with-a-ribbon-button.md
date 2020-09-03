---
title: Synchronizowanie niestandardowego okienka zadań z przyciskiem wstążki
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
ms.openlocfilehash: ad910f94c6b6a4345f6973e84e02c85d4fe1f0e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67328335"
---
# <a name="walkthrough-synchronize-a-custom-task-pane-with-a-ribbon-button"></a>Przewodnik: synchronizowanie niestandardowego okienka zadań z przyciskiem wstążki
  W tym instruktażu pokazano, jak utworzyć niestandardowe okienko zadań, które użytkownicy mogą ukryć lub wyświetlić, klikając przycisk przełączania na Wstążce. Należy zawsze utworzyć element interfejsu użytkownika (UI), taki jak przycisk, który użytkownicy mogą kliknąć, aby wyświetlić lub ukryć niestandardowe okienko zadań, ponieważ Microsoft Office aplikacje nie zapewniają użytkownikom domyślnego sposobu wyświetlania lub ukrywania niestandardowych okienek zadań.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Chociaż w tym instruktażu jest używane w programie Excel, koncepcje przedstawione w tym przewodniku dotyczą wszystkich aplikacji wymienionych powyżej.

 W instruktażu przedstawiono następujące zagadnienia:

- Projektowanie interfejsu użytkownika niestandardowego okienka zadań.

- Dodawanie przycisku przełączania do wstążki.

- Synchronizowanie przycisku przełączania z okienkiem zadania niestandardowego.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel lub Microsoft [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] .

## <a name="create-the-add-in-project"></a>Utwórz projekt dodatku
 W tym kroku utworzysz projekt dodatku VSTO dla programu Excel.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt dodatku programu Excel o nazwie **SynchronizeTaskPaneAndRibbon**przy użyciu szablonu projektu dodatku programu Excel. Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] otwiera plik kodu **ThisAddIn.cs** lub **ThisAddIn. vb** i dodaje projekt **SynchronizeTaskPaneAndRibbon** do **Eksplorator rozwiązań**.

## <a name="add-a-toggle-button-to-the-ribbon"></a>Dodaj przycisk przełączania do wstążki
 Jedną z wytycznych dotyczących projektowania aplikacji pakietu Office jest to, że użytkownicy powinni zawsze mieć kontrolę nad interfejsem użytkownika aplikacji pakietu Office. Aby umożliwić użytkownikom kontrolowanie niestandardowego okienka zadań, można dodać przycisk przełączania wstążki, który pokazuje i ukrywa okienko zadań. Aby utworzyć przycisk przełączania, Dodaj **Wstążkę (projektant graficzny)** do projektu. Projektant ułatwia dodawanie i określanie położenia kontrolek, Ustawianie właściwości kontrolki i obsługę zdarzeń kontroli. Aby uzyskać więcej informacji, zobacz [Projektant wstążki](../vsto/ribbon-designer.md).

### <a name="to-add-a-toggle-button-to-the-ribbon"></a>Aby dodać przycisk przełączania do wstążki

1. W menu **projekt** kliknij polecenie **Dodaj nowy element**.

2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **wstążka (projektant wizualny)**.

3. Zmień nazwę nowej wstążki na **ManageTaskPaneRibbon**, a następnie kliknij przycisk **Dodaj**.

     Plik **ManageTaskPaneRibbon.cs** lub **ManageTaskPaneRibbon. vb** zostanie otwarty w Projektancie wstążki i zostanie wyświetlona domyślna karta i Grupa.

4. W Projektancie wstążki kliknij pozycję **grupa1**.

5. W oknie **Właściwości** ustaw właściwość **etykieta** na **Menedżer okienka zadań**.

6. Na karcie **kontrolki wstążki pakietu Office** w **przyborniku**przeciągnij **ToggleButton** do grupy **Menedżer okienka zadań** .

7. Kliknij pozycję **toggleButton1**.

8. W oknie **Właściwości** ustaw właściwość **etykieta** na **Pokaż okienko zadań**.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Projektowanie interfejsu użytkownika niestandardowego okienka zadań
 Nie istnieje projektant wizualny dla niestandardowych okienek zadań, ale można zaprojektować kontrolkę użytkownika z żądanym układem. W dalszej części tego instruktażu dodasz kontrolkę użytkownika do niestandardowego okienka zadań.

### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Aby zaprojektować interfejs użytkownika niestandardowego okienka zadań

1. W menu **projekt** kliknij polecenie **Dodaj kontrolkę użytkownika**.

2. W oknie dialogowym **Dodaj nowy element** Zmień nazwę kontrolki użytkownika na **TaskPaneControl**, a następnie kliknij przycisk **Dodaj**.

     Formant użytkownika zostanie otwarty w projektancie.

3. Na karcie **Formanty standardowe** **przybornika**przeciągnij kontrolkę **TextBox** do kontrolki użytkownika.

## <a name="create-the-custom-task-pane"></a>Tworzenie niestandardowego okienka zadań
 Aby utworzyć niestandardowe okienko zadań po uruchomieniu dodatku VSTO, Dodaj kontrolkę użytkownika do okienka zadań w <xref:Microsoft.Office.Tools.AddIn.Startup> obsłudze zdarzeń dodatku VSTO. Domyślnie niestandardowe okienko zadań nie będzie widoczne. W dalszej części tego instruktażu dodasz kod, który będzie wyświetlany lub ukryty w okienku zadań, gdy użytkownik kliknie przycisk przełączania dodany do wstążki.

### <a name="to-create-the-custom-task-pane"></a>Aby utworzyć niestandardowe okienko zadań

1. W **Eksplorator rozwiązań**rozwiń węzeł **Excel**.

2. Kliknij prawym przyciskiem myszy pozycję **ThisAddIn.cs** lub **ThisAddIn. vb** i kliknij polecenie **Wyświetl kod**.

3. Dodaj następujący kod do `ThisAddIn` klasy. Ten kod deklaruje wystąpienie `TaskPaneControl` jako element członkowski `ThisAddIn` .

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#1](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#1)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#1)]

4. Zastąp `ThisAddIn_Startup` procedurę obsługi zdarzeń poniższym kodem. Ten kod dodaje `TaskPaneControl` obiekt do `CustomTaskPanes` pola, ale nie wyświetla niestandardowego okienka zadań (domyślnie <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> Właściwość <xref:Microsoft.Office.Tools.CustomTaskPane> klasy ma **wartość false**). Kod Visual C# dołącza także procedurę obsługi zdarzeń do <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> zdarzenia.

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#2](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#2)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#2)]

5. Dodaj następującą metodę do `ThisAddIn` klasy. Ta metoda obsługuje <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> zdarzenie. Gdy użytkownik zamknie okienko zadań, klikając przycisk **Zamknij** (X), ta metoda aktualizuje stan przycisku przełączania na Wstążce.

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#3](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#3)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#3](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#3)]

6. Dodaj następującą właściwość do `ThisAddIn` klasy. Ta właściwość uwidacznia obiekt prywatny `myCustomTaskPane1` innym klasom. W dalszej części tego instruktażu dodasz kod do `MyRibbon` klasy, która używa tej właściwości.

     [!code-csharp[Trin_TaskPaneRibbonSynchronize#4](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs#4)]
     [!code-vb[Trin_TaskPaneRibbonSynchronize#4](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb#4)]

## <a name="hide-and-show-the-custom-task-pane-by-using-the-toggle-button"></a>Ukrywanie i pokazywanie niestandardowego okienka zadań przy użyciu przycisku przełączania
 Ostatnim krokiem jest dodanie kodu, który wyświetla lub ukrywa niestandardowe okienko zadań, gdy użytkownik kliknie przycisk przełączania na Wstążce.

### <a name="to-display-and-hide-the-custom-task-pane-by-using-the-toggle-button"></a>Aby wyświetlić i ukryć niestandardowe okienko zadań przy użyciu przycisku przełączania

1. W Projektancie wstążki kliknij dwukrotnie przycisk Przełącz **okienko zadań** .

     Program Visual Studio automatycznie generuje procedurę obsługi zdarzeń o nazwie `toggleButton1_Click` , która obsługuje <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> zdarzenie przycisku przełącznika. Visual Studio otwiera także plik *MyRibbon.cs* lub moja *wstążka. vb* w edytorze kodu.

2. Zastąp `toggleButton1_Click` procedurę obsługi zdarzeń poniższym kodem. Gdy użytkownik kliknie przycisk przełączania, ten kod wyświetla lub ukrywa niestandardowe okienko zadań, w zależności od tego, czy przycisk przełączania został naciśnięty lub nie został naciśnięty.

     [!code-vb[Trin_TaskPaneRibbonSynchronize#5](../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.vb#5)]
     [!code-csharp[Trin_TaskPaneRibbonSynchronize#5](../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.cs#5)]

## <a name="test-the-add-in"></a>Testowanie dodatku
 Gdy uruchamiasz projekt, program Excel zostanie otwarty bez wyświetlania niestandardowego okienka zadań. Kliknij przycisk przełącznika na Wstążce, aby przetestować kod.

### <a name="to-test-your-vsto-add-in"></a>Aby przetestować dodatek narzędzi VSTO

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

     Upewnij się, że program Excel zostanie otwarty, a na Wstążce pojawi się karta **Dodatki** .

2. Kliknij kartę **Dodatki** na Wstążce.

3. W grupie **Menedżer okienka zadań** kliknij przycisk Przełącz **okienko zadań** .

     Upewnij się, że okienko zadań jest wyświetlane w trybie alternatywnym i ukrywane po kliknięciu przycisku przełączania.

4. Gdy okienko zadań jest widoczne, kliknij przycisk **Zamknij** (X) w rogu okienka zadań.

     Sprawdź, czy przycisk przełączania wydaje się nie być wciśnięty.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat tworzenia niestandardowych okienek zadań można znaleźć w następujących tematach:

- Utwórz niestandardowe okienko zadań w dodatku narzędzi VSTO dla innej aplikacji. Aby uzyskać więcej informacji o aplikacjach, które obsługują niestandardowe okienka zadań, zobacz [niestandardowe okienka zadań](../vsto/custom-task-panes.md).

- Automatyzowanie aplikacji z niestandardowego okienka zadań. Aby uzyskać więcej informacji, zobacz [Przewodnik: Automatyzowanie aplikacji z niestandardowego okienka zadań](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md).

- Utwórz niestandardowe okienko zadań dla każdej wiadomości e-mail, która jest otwierana w programie Outlook. Aby uzyskać więcej informacji, zobacz [Przewodnik: Wyświetlanie niestandardowych okienek zadań z wiadomościami e-mail w programie Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).

## <a name="see-also"></a>Zobacz też
- [Niestandardowe okienka zadań](../vsto/custom-task-panes.md)
- [Instrukcje: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Przewodnik: Automatyzowanie aplikacji z niestandardowego okienka zadań](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [Przewodnik: Wyświetlanie niestandardowych okienek zadań z wiadomościami e-mail w programie Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
- [Omówienie wstążki](../vsto/ribbon-overview.md)
