---
title: 'Przewodnik: Automatyzowanie aplikacji z niestandardowego okienka zadań'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f5135e96125192d7ed125287aa47c839031824fe
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871939"
---
# <a name="walkthrough-automate-an-application-from-a-custom-task-pane"></a>Przewodnik: Automatyzowanie aplikacji z niestandardowego okienka zadań
  W tym instruktażu przedstawiono sposób tworzenia niestandardowego okienka zadań, które automatyzuje program PowerPoint. Niestandardowe okienko zadań wstawia daty do slajdu, gdy użytkownik kliknie <xref:System.Windows.Forms.MonthCalendar> formant, który znajduje się w okienku zadania niestandardowego.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Chociaż w tym instruktażu jest używane program PowerPoint, koncepcje przedstawione w tym przewodniku dotyczą wszystkich aplikacji wymienionych powyżej.

 W instruktażu przedstawiono następujące zagadnienia:

- Projektowanie interfejsu użytkownika niestandardowego okienka zadań.

- Automatyzowanie programu PowerPoint z niestandardowego okienka zadań.

- Wyświetlanie niestandardowego okienka zadań w programie PowerPoint.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft PowerPoint 2010 lub [!INCLUDE[PowerPoint_15_short](../vsto/includes/powerpoint-15-short-md.md)].

## <a name="create-the-add-in-project"></a>Utwórz projekt dodatku
 Pierwszym krokiem jest utworzenie projektu dodatku VSTO dla programu PowerPoint.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt dodatku VSTO programu PowerPoint o nazwie "Moja **addin**" przy użyciu szablonu projektu dodatku dla programu PowerPoint. Aby uzyskać więcej informacji, zobacz [jak: Utwórz projekty pakietu Office w programie](../vsto/how-to-create-office-projects-in-visual-studio.md)Visual Studio.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]otwiera plik kodu **ThisAddIn.cs** lub **ThisAddIn. vb** i dodaje projekt **addin** do **Eksplorator rozwiązań**.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Projektowanie interfejsu użytkownika niestandardowego okienka zadań
 Nie istnieje projektant wizualny dla niestandardowych okienek zadań, ale można zaprojektować kontrolkę użytkownika z żądanym układem. W dalszej części tego instruktażu dodasz kontrolkę użytkownika do niestandardowego okienka zadań.

#### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Aby zaprojektować interfejs użytkownika niestandardowego okienka zadań

1. W menu **projekt** kliknij polecenie **Dodaj kontrolkę użytkownika**.

2. W oknie dialogowym **Dodaj nowy element** Zmień nazwę kontrolki użytkownika na **UserControl**, a następnie kliknij przycisk **Dodaj**.

     Formant użytkownika zostanie otwarty w projektancie.

3. Na karcie **Formanty standardowe** przybornika przeciągnijkontrolkę **MonthCalendar** do kontrolki użytkownika.

     Jeśli formant **MonthCalendar** jest większy niż powierzchnia projektowa kontrolki użytkownika, Zmień rozmiar kontrolki użytkownika tak, aby pasował do kontrolki **MonthCalendar** .

## <a name="automate-powerpoint-from-the-custom-task-pane"></a>Automatyzowanie programu PowerPoint z niestandardowego okienka zadań
 Celem dodatku VSTO jest umieszczenie wybranej daty pierwszego slajdu aktywnej prezentacji. <xref:System.Windows.Forms.MonthCalendar.DateChanged> Użyj zdarzenia kontrolki, aby dodać wybraną datę przy każdej zmianie.

### <a name="to-automate-powerpoint-from-the-custom-task-pane"></a>Aby zautomatyzować program PowerPoint z niestandardowego okienka zadań

1. W projektancie kliknij <xref:System.Windows.Forms.MonthCalendar> dwukrotnie formant.

     Zostanie otwarty plik **MyUserControl.cs** lub **UserControl. vb** oraz zostanie utworzony <xref:System.Windows.Forms.MonthCalendar.DateChanged> program obsługi zdarzeń dla zdarzenia.

2. Dodaj następujący kod na początku pliku. Ten kod tworzy aliasy dla <xref:Microsoft.Office.Core> przestrzeni nazw i [programu PowerPoint](/previous-versions/office/developer/office-2010/ff763170%28v%3doffice.14%29) .

     [!code-csharp[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#1)]
     [!code-vb[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#1)]

3. Dodaj następujący kod do `MyUserControl` klasy. Ten kod deklaruje obiekt [Shape](/previous-versions/office/developer/office-2010/ff760244(v=office.14)) jako element członkowski `MyUserControl`. W poniższym kroku użyjesz tego [kształtu](/previous-versions/office/developer/office-2010/ff760244(v=office.14)) , aby dodać pole tekstowe do slajdu w aktywnej prezentacji.

     [!code-csharp[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#2)]
     [!code-vb[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#2)]

4. Zastąp procedurę obsługi zdarzeń poniższym kodem. `monthCalendar1_DateChanged` Ten kod dodaje pole tekstowe do pierwszego slajdu w aktywnej prezentacji, a następnie dodaje aktualnie wybraną datę do pola tekstowego. Ten kod używa `Globals.ThisAddIn` obiektu do uzyskiwania dostępu do modelu obiektów programu PowerPoint.

     [!code-csharp[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#3)]
     [!code-vb[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#3)]

5. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **addin** , a następnie kliknij polecenie **Kompiluj**. Upewnij się, że projekt kompiluje się bez błędów.

## <a name="display-the-custom-task-pane"></a>Wyświetlanie niestandardowego okienka zadań
 Aby wyświetlić niestandardowe okienko zadań po uruchomieniu dodatku VSTO, Dodaj kontrolkę użytkownika do okienka zadań w <xref:Microsoft.Office.Tools.AddIn.Startup> obsłudze zdarzeń dodatku VSTO.

### <a name="to-display-the-custom-task-pane"></a>Aby wyświetlić niestandardowe okienko zadań

1. W **Eksplorator rozwiązań**rozwiń węzeł **PowerPoint**.

2. Kliknij prawym przyciskiem myszy pozycję **ThisAddIn.cs** lub **ThisAddIn. vb** i kliknij polecenie **Wyświetl kod**.

3. Dodaj następujący kod do `ThisAddIn` klasy. Ten kod deklaruje wystąpienia `MyUserControl` elementów <xref:Microsoft.Office.Tools.CustomTaskPane> i jako elementy członkowskie `ThisAddIn` klasy.

     [!code-vb[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#4)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#4)]

4. Zastąp procedurę obsługi zdarzeń poniższym kodem. `ThisAddIn_Startup` Ten kod tworzy nowe <xref:Microsoft.Office.Tools.CustomTaskPane> przez `MyUserControl` dodanie obiektu do `CustomTaskPanes` kolekcji. Kod wyświetla również okienko zadań.

     [!code-vb[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#5)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#5)]

## <a name="test-the-add-in"></a>Testowanie dodatku
 Po uruchomieniu projektu zostanie otwarty program PowerPoint, a dodatek VSTO wyświetli niestandardowe okienko zadań. Kliknij kontrolkę, <xref:System.Windows.Forms.MonthCalendar> aby przetestować kod.

### <a name="to-test-your-vsto-add-in"></a>Aby przetestować dodatek narzędzi VSTO

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

2. Upewnij się, że niestandardowe okienko zadań jest widoczne.

3. Kliknij datę w <xref:System.Windows.Forms.MonthCalendar> kontrolce w okienku zadań.

     Data jest wstawiana do pierwszego slajdu w aktywnej prezentacji.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat tworzenia niestandardowych okienek zadań można znaleźć w następujących tematach:

- Utwórz niestandardowe okienko zadań w dodatku narzędzi VSTO dla innej aplikacji. Aby uzyskać więcej informacji o aplikacjach, które obsługują niestandardowe okienka zadań, zobacz [niestandardowe okienka zadań](../vsto/custom-task-panes.md).

- Utwórz przycisk wstążki, którego można użyć do ukrycia lub wyświetlenia niestandardowego okienka zadań. Aby uzyskać więcej informacji, [zobacz Przewodnik: Synchronizowanie niestandardowego okienka zadań z przyciskiem](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)wstążki.

- Utwórz niestandardowe okienko zadań dla każdej wiadomości e-mail, która jest otwierana w programie Outlook. Aby uzyskać więcej informacji, [zobacz Przewodnik: Wyświetlanie niestandardowych okienek zadań z wiadomościami e-mail](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)w programie Outlook.

## <a name="see-also"></a>Zobacz także
- [Niestandardowe okienka zadań](../vsto/custom-task-panes.md)
- [Instrukcje: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Przewodnik: Synchronizowanie niestandardowego okienka zadań z przyciskiem wstążki](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [Przewodnik: Wyświetlanie niestandardowych okienek zadań z wiadomościami e-mail w programie Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
