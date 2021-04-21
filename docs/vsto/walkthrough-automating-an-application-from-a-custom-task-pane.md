---
title: 'Przewodnik: automatyzowanie aplikacji z niestandardowego okienka zadań'
description: Utwórz niestandardowe okienko zadań, które automatyzuje program Microsoft PowerPoint, wstawiając daty do slajdu, gdy użytkownik kliknie kontrolkę MonthCalendar w niestandardowym okienku zadań.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio], custom task panes
- automating Office applications
- custom task panes [Office development in Visual Studio], automating applications
- custom task panes [Office development in Visual Studio], PowerPoint
- task panes [Office development in Visual Studio], automating applications
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f57ad0c858abb5f151e1b425224b5af34d464c0f
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824669"
---
# <a name="walkthrough-automate-an-application-from-a-custom-task-pane"></a>Przewodnik: automatyzowanie aplikacji z niestandardowego okienka zadań
  W tym przewodniku pokazano, jak utworzyć niestandardowe okienko zadań, które automatyzuje program PowerPoint. Niestandardowe okienko zadań wstawia daty do slajdu, gdy użytkownik kliknie kontrolkę w <xref:System.Windows.Forms.MonthCalendar> niestandardowym okienku zadań.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Mimo że w tym przewodniku jest używany program PowerPoint, koncepcje zademonstrowane w tym przewodniku mają zastosowanie do wszystkich aplikacji wymienionych powyżej.

 W instruktażu przedstawiono następujące zagadnienia:

- Projektowanie interfejsu użytkownika niestandardowego okienka zadań.

- Automatyzowanie programu PowerPoint z niestandardowego okienka zadań.

- Wyświetlanie niestandardowego okienka zadań w programie PowerPoint.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Personalizowanie środowiska IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft PowerPoint 2010 lub [!INCLUDE[PowerPoint_15_short](../vsto/includes/powerpoint-15-short-md.md)] .

## <a name="create-the-add-in-project"></a>Tworzenie projektu dodatku
 Pierwszym krokiem jest utworzenie projektu dodatku VSTO dla programu PowerPoint.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt dodatku PowerPoint VSTO o nazwie **MyAddIn** przy użyciu szablonu projektu dodatku programu PowerPoint. Aby uzyskać więcej informacji, [zobacz How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwiera plik **kodu ThisAddIn.cs** lub **ThisAddIn.vb** i dodaje projekt **MyAddIn** do **Eksplorator rozwiązań**.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Projektowanie interfejsu użytkownika niestandardowego okienka zadań
 Nie ma projektanta wizualnego dla niestandardowych okienek zadań, ale możesz zaprojektować kontrolkę użytkownika z układem, którego potrzebujesz. W dalszej części tego przewodnika dodasz kontrolkę użytkownika do niestandardowego okienka zadań.

#### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Aby zaprojektować interfejs użytkownika niestandardowego okienka zadań

1. W menu **Project (Projekt)** kliknij pozycję **Add User Control (Dodaj kontrolkę użytkownika).**

2. W **oknie dialogowym Dodawanie** nowego elementu zmień nazwę kontrolki użytkownika na **MyUserControl** i kliknij przycisk **Dodaj**.

     Kontrolka użytkownika zostanie otwarta w projektancie.

3. Na karcie **Typowe kontrolki** **przybornika przeciągnij** kontrolkę **MonthCalendar** do kontrolki użytkownika.

     Jeśli **kontrolka MonthCalendar jest** większa niż powierzchnia projektowa kontrolki użytkownika, zmień rozmiar kontrolki użytkownika, aby pasowała do **kontrolki MonthCalendar.**

## <a name="automate-powerpoint-from-the-custom-task-pane"></a>Automatyzowanie programu PowerPoint z niestandardowego okienka zadań
 Celem dodatku VSTO jest umieścić wybraną datę w pierwszym slajdzie aktywnej prezentacji. Użyj zdarzenia <xref:System.Windows.Forms.MonthCalendar.DateChanged> kontrolki, aby dodać wybraną datę przy każdej zmianie.

### <a name="to-automate-powerpoint-from-the-custom-task-pane"></a>Aby zautomatyzować program PowerPoint z niestandardowego okienka zadań

1. W projektancie kliknij dwukrotnie <xref:System.Windows.Forms.MonthCalendar> kontrolkę.

     Zostanie **otwarty plik MyUserControl.cs** lub **MyUserControl.vb** i zostanie utworzony program obsługi <xref:System.Windows.Forms.MonthCalendar.DateChanged> zdarzeń dla zdarzenia.

2. Dodaj następujący kod na górze pliku. Ten kod tworzy aliasy dla przestrzeni <xref:Microsoft.Office.Core> nazw i [programu PowerPoint.](/previous-versions/office/developer/office-2010/ff763170%28v%3doffice.14%29)

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb" id="Snippet1":::

3. Dodaj poniższy kod do klasy `MyUserControl`. Ten kod deklaruje [obiekt Shape](/previous-versions/office/developer/office-2010/ff760244(v=office.14)) jako członka `MyUserControl` . W następnym kroku użyjemy [](/previous-versions/office/developer/office-2010/ff760244(v=office.14)) tego kształtu, aby dodać pole tekstowe do slajdu w aktywnej prezentacji.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb" id="Snippet2":::

4. Zastąp program `monthCalendar1_DateChanged` obsługi zdarzeń następującym kodem. Ten kod dodaje pole tekstowe do pierwszego slajdu w aktywnej prezentacji, a następnie dodaje aktualnie wybraną datę do pola tekstowego. Ten kod używa `Globals.ThisAddIn` obiektu w celu uzyskania dostępu do modelu obiektów programu PowerPoint.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb" id="Snippet3":::

5. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt **MyAddIn,** a następnie kliknij polecenie **Build (Kompilacja).** Sprawdź, czy projekt jest kompilowany bez błędów.

## <a name="display-the-custom-task-pane"></a>Wyświetlanie niestandardowego okienka zadań
 Aby wyświetlić niestandardowe okienko zadań podczas uruchamiania dodatku narzędzi VSTO, dodaj kontrolkę użytkownika do okienka zadań w programie obsługi zdarzeń <xref:Microsoft.Office.Tools.AddIn.Startup> dodatku narzędzi VSTO.

### <a name="to-display-the-custom-task-pane"></a>Aby wyświetlić niestandardowe okienko zadań

1. W **Eksplorator rozwiązań** rozwiń program **PowerPoint.**

2. Kliknij prawym przyciskiem **myszy pozycję ThisAddIn.cs** lub **ThisAddIn.vb** i **kliknij polecenie Wyświetl kod.**

3. Dodaj poniższy kod do klasy `ThisAddIn`. Ten kod deklaruje wystąpienia klas `MyUserControl` i <xref:Microsoft.Office.Tools.CustomTaskPane> jako składowe klasy `ThisAddIn` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb" id="Snippet4":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs" id="Snippet4":::

4. Zastąp program `ThisAddIn_Startup` obsługi zdarzeń następującym kodem. Ten kod tworzy nowy <xref:Microsoft.Office.Tools.CustomTaskPane> przez dodanie obiektu do `MyUserControl` `CustomTaskPanes` kolekcji. Kod wyświetla również okienko zadań.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs" id="Snippet5":::

## <a name="test-the-add-in"></a>Testowanie dodatku
 Po uruchomieniu projektu zostanie otwarty program PowerPoint, a dodatek VSTO wyświetli niestandardowe okienko zadań. Kliknij <xref:System.Windows.Forms.MonthCalendar> kontrolkę, aby przetestować kod.

### <a name="to-test-your-vsto-add-in"></a>Aby przetestować dodatek VSTO

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

2. Upewnij się, że niestandardowe okienko zadań jest widoczne.

3. Kliknij datę w <xref:System.Windows.Forms.MonthCalendar> kontrolce w okienku zadań.

     Data zostanie wstawiona do pierwszego slajdu w aktywnej prezentacji.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat tworzenia niestandardowych okienek zadań można znaleźć w tych tematach:

- Utwórz niestandardowe okienko zadań w dodatku narzędzi VSTO dla innej aplikacji. Aby uzyskać więcej informacji na temat aplikacji, które obsługują niestandardowe okienka zadań, zobacz [Niestandardowe okienka zadań.](../vsto/custom-task-panes.md)

- Utwórz przycisk wstążki, który może służyć do ukrywania lub wyświetlania niestandardowego okienka zadań. Aby uzyskać więcej informacji, [zobacz Przewodnik: synchronizowanie niestandardowego](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)okienka zadań za pomocą przycisku wstążki .

- Utwórz niestandardowe okienko zadań dla każdej wiadomości e-mail otwartej w programie Outlook. Aby uzyskać więcej informacji, zobacz Przewodnik: wyświetlanie niestandardowych okienek zadań z wiadomościami [e-mail w programie Outlook.](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)

## <a name="see-also"></a>Zobacz też
- [Niestandardowe okienka zadań](../vsto/custom-task-panes.md)
- [How to: Add a custom task pane to an application (Jak dodać niestandardowe okienko zadań do aplikacji)](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Przewodnik: synchronizowanie niestandardowego okienka zadań za pomocą przycisku wstążki](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [Przewodnik: wyświetlanie niestandardowych okienek zadań z wiadomościami e-mail w programie Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
