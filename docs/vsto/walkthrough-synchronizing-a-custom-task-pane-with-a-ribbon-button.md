---
title: Synchronizowanie niestandardowego okienka zadań za pomocą przycisku wstążki
description: Dowiedz się, jak utworzyć niestandardowe okienko zadań, które użytkownicy mogą ukryć lub wyświetlić, klikając przycisk przełączania na wstążce.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5e7fe64d2df3298d53f567d11fe765280843e2ce
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826788"
---
# <a name="walkthrough-synchronize-a-custom-task-pane-with-a-ribbon-button"></a>Przewodnik: synchronizowanie niestandardowego okienka zadań za pomocą przycisku wstążki
  W tym przewodniku pokazano, jak utworzyć niestandardowe okienko zadań, które użytkownicy mogą ukryć lub wyświetlić, klikając przycisk przełączania na wstążce. Zawsze należy utworzyć element interfejsu użytkownika (UI), taki jak przycisk, który użytkownicy mogą kliknąć, aby wyświetlić lub ukryć niestandardowe okienko zadań, ponieważ aplikacje programu Microsoft Office nie zapewniają użytkownikom domyślnego sposobu wyświetlania lub ukrywania niestandardowych okienek zadań.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Chociaż w tym przewodniku jest używany program Excel, koncepcje zademonstrowane w tym przewodniku mają zastosowanie do wszystkich aplikacji wymienionych powyżej.

 W instruktażu przedstawiono następujące zagadnienia:

- Projektowanie interfejsu użytkownika niestandardowego okienka zadań.

- Dodawanie przycisku przełączania do wstążki.

- Synchronizowanie przycisku przełączania z niestandardowym okienkiem zadań.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Personalizowanie środowiska IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel lub Microsoft [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] .

## <a name="create-the-add-in-project"></a>Tworzenie projektu dodatku
 W tym kroku utworzysz projekt dodatku VSTO dla programu Excel.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt dodatku programu Excel o nazwie **SynchronizeTaskPaneAndRibbon** przy użyciu szablonu projektu dodatku programu Excel. Aby uzyskać więcej informacji, [zobacz How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Otwiera plik kodu **ThisAddIn.cs** lub **ThisAddIn.vb** i dodaje projekt **SynchronizeTaskPaneAndRibbon** do Eksplorator rozwiązań **.**

## <a name="add-a-toggle-button-to-the-ribbon"></a>Dodawanie przycisku przełączania do wstążki
 Jedną z wytycznych dotyczących projektowania aplikacji pakietu Office jest to, że użytkownicy powinni zawsze mieć kontrolę nad interfejsem użytkownika aplikacji pakietu Office. Aby umożliwić użytkownikom kontrolowanie niestandardowego okienka zadań, można dodać przycisk przełączania Wstążki, który wyświetla i ukrywa okienko zadań. Aby utworzyć przycisk przełączania, dodaj element Wstążki **(Projektant wizualny)** do projektu. Projektant ułatwia dodawanie i ustawianie położenia kontrolek, ustawianie właściwości kontrolek i obsługę zdarzeń kontrolek. Aby uzyskać więcej informacji, zobacz [Projektant wstążki](../vsto/ribbon-designer.md).

### <a name="to-add-a-toggle-button-to-the-ribbon"></a>Aby dodać przycisk przełączania do wstążki

1. W menu **Project (Projekt)** kliknij pozycję **Add New Item (Dodaj nowy element).**

2. W **oknie dialogowym Dodawanie nowego** elementu wybierz pozycję **Wstążka (Projektant wizualny).**

3. Zmień nazwę nowej wstążki na **ManageTaskPaneRibbon** i kliknij przycisk **Dodaj**.

     Plik **ManageTaskPaneRibbon.cs** lub **ManageTaskPaneRibbon.vb** zostanie otwarty w Projektancie wstążki i zostanie wyświetlona domyślna karta i grupa.

4. W Projektancie wstążki kliknij pozycję **grupa1.**

5. W **oknie Właściwości** ustaw właściwość **Etykieta** na Menedżera **okienka zadań.**

6. Na karcie **Kontrolki wstążki pakietu Office** **przybornika** przeciągnij kontrolkę **ToggleButton** do grupy **Menedżer okienka** zadań.

7. Kliknij **pozycję toggleButton1**.

8. W **oknie Właściwości** ustaw właściwość **Etykieta** na Pokaż **okienko zadań**.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Projektowanie interfejsu użytkownika niestandardowego okienka zadań
 Nie ma projektanta wizualnego dla niestandardowych okienek zadań, ale możesz zaprojektować kontrolkę użytkownika z układem, którego potrzebujesz. W dalszej części tego przewodnika dodasz kontrolkę użytkownika do niestandardowego okienka zadań.

### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Aby zaprojektować interfejs użytkownika niestandardowego okienka zadań

1. W menu **Project (Projekt)** kliknij pozycję **Add User Control (Dodaj kontrolkę użytkownika).**

2. W **oknie dialogowym Dodawanie** nowego elementu zmień nazwę kontrolki użytkownika na **TaskPaneControl** i kliknij przycisk **Dodaj**.

     Kontrolka użytkownika zostanie otwarta w projektancie.

3. Na karcie **Typowe kontrolki** **przybornika** przeciągnij **kontrolkę TextBox** do kontrolki użytkownika.

## <a name="create-the-custom-task-pane"></a>Tworzenie niestandardowego okienka zadań
 Aby utworzyć niestandardowe okienko zadań podczas uruchamiania dodatku narzędzi VSTO, dodaj kontrolkę użytkownika do okienka zadań w programie obsługi zdarzeń <xref:Microsoft.Office.Tools.AddIn.Startup> dodatku narzędzi VSTO. Domyślnie niestandardowe okienko zadań nie będzie widoczne. W dalszej części tego przewodnika dodasz kod, który będzie wyświetlać lub ukrywać okienko zadań, gdy użytkownik kliknie przycisk przełączania dodany do wstążki.

### <a name="to-create-the-custom-task-pane"></a>Aby utworzyć niestandardowe okienko zadań

1. W **Eksplorator rozwiązań** rozwiń w **programie Excel**.

2. Kliknij prawym przyciskiem **myszy pozycję ThisAddIn.cs** lub **ThisAddIn.vb** i **kliknij polecenie Wyświetl kod.**

3. Dodaj poniższy kod do klasy `ThisAddIn`. Ten kod deklaruje wystąpienie `TaskPaneControl` klasy jako element członkowski klasy `ThisAddIn` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb" id="Snippet1":::

4. Zastąp program `ThisAddIn_Startup` obsługi zdarzeń następującym kodem. Ten kod dodaje obiekt do pola , ale nie wyświetla niestandardowego okienka zadań (domyślnie właściwość `TaskPaneControl` `CustomTaskPanes` klasy ma wartość <xref:Microsoft.Office.Tools.CustomTaskPane.Visible%2A> <xref:Microsoft.Office.Tools.CustomTaskPane> **false**). Kod Visual C# dołącza również do zdarzenia program obsługi <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> zdarzeń.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb" id="Snippet2":::

5. Dodaj następującą metodę do `ThisAddIn` klasy . Ta metoda obsługuje <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> zdarzenie. Gdy użytkownik zamknie okienko zadań,  klikając przycisk Zamknij (X), ta metoda aktualizuje stan przycisku przełączania na wstążce.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb" id="Snippet3":::

6. Dodaj następującą właściwość do `ThisAddIn` klasy . Ta właściwość uwidacznia prywatny `myCustomTaskPane1` obiekt innym klasom. W dalszej części tego przewodnika dodasz kod do `MyRibbon` klasy, która używa tej właściwości.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ThisAddIn.vb" id="Snippet4":::

## <a name="hide-and-show-the-custom-task-pane-by-using-the-toggle-button"></a>Ukrywanie i pokazywanie niestandardowego okienka zadań przy użyciu przycisku przełączania
 Ostatnim krokiem jest dodanie kodu, który wyświetla lub ukrywa niestandardowe okienko zadań, gdy użytkownik kliknie przycisk przełączania na wstążce.

### <a name="to-display-and-hide-the-custom-task-pane-by-using-the-toggle-button"></a>Aby wyświetlić i ukryć niestandardowe okienko zadań przy użyciu przycisku przełączania

1. W Projektancie wstążki kliknij dwukrotnie przycisk **przełączania Pokaż** okienko zadań.

     Visual Studio automatycznie generuje program obsługi zdarzeń o nazwie `toggleButton1_Click` , który obsługuje zdarzenie <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> przycisku przełączania. Visual Studio otwiera również plik *MyRibbon.cs* lub *MyRibbon.vb* w Edytorze kodu.

2. Zastąp program `toggleButton1_Click` obsługi zdarzeń następującym kodem. Gdy użytkownik kliknie przycisk przełączania, ten kod wyświetla lub ukrywa niestandardowe okienko zadań w zależności od tego, czy przycisk przełączania jest naciśnięty, czy nie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneRibbonSynchronize/ManageTaskPaneRibbon.cs" id="Snippet5":::

## <a name="test-the-add-in"></a>Testowanie dodatku
 Po uruchomieniu projektu program Excel zostanie otwarty bez wyświetlania niestandardowego okienka zadań. Kliknij przycisk przełączania na wstążce, aby przetestować kod.

### <a name="to-test-your-vsto-add-in"></a>Aby przetestować dodatek VSTO

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

     Upewnij się, że program Excel zostanie otwarty, a na wstążce zostanie **wyświetlona** karta Dodatki.

2. Kliknij **kartę Dodatki na** wstążce.

3. W grupie **Menedżer okienka** zadań kliknij przycisk przełączania **Pokaż** okienko zadań.

     Sprawdź, czy okienko zadań jest wyświetlane i ukryte po kliknięciu przycisku przełączania.

4. Gdy okienko zadań jest widoczne, kliknij przycisk **Zamknij** (X) w rogu okienka zadań.

     Sprawdź, czy wydaje się, że przycisk przełączania nie jest naciśnięty.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat tworzenia niestandardowych okienek zadań można znaleźć w tych tematach:

- Utwórz niestandardowe okienko zadań w dodatku narzędzi VSTO dla innej aplikacji. Aby uzyskać więcej informacji na temat aplikacji, które obsługują niestandardowe okienka zadań, zobacz [Niestandardowe okienka zadań.](../vsto/custom-task-panes.md)

- Automatyzowanie aplikacji z niestandardowego okienka zadań. Aby uzyskać więcej informacji, [zobacz Przewodnik: automatyzowanie aplikacji z niestandardowego okienka zadań.](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)

- Utwórz niestandardowe okienko zadań dla każdej wiadomości e-mail otwartej w programie Outlook. Aby uzyskać więcej informacji, zobacz Przewodnik: wyświetlanie niestandardowych okienek zadań z wiadomościami [e-mail w programie Outlook.](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)

## <a name="see-also"></a>Zobacz też
- [Niestandardowe okienka zadań](../vsto/custom-task-panes.md)
- [How to: Add a custom task pane to an application (Jak dodać niestandardowe okienko zadań do aplikacji)](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Przewodnik: automatyzowanie aplikacji z niestandardowego okienka zadań](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [Przewodnik: wyświetlanie niestandardowych okienek zadań z wiadomościami e-mail w programie Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
- [Wstążka — omówienie](../vsto/ribbon-overview.md)
