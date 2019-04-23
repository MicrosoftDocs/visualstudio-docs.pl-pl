---
title: 'Przewodnik: Automatyzacja aplikacji z niestandardowego okienka zadań'
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
ms.openlocfilehash: 0d2231f3e6dc6185c97a5a09e4d81db3883e8431
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60041892"
---
# <a name="walkthrough-automate-an-application-from-a-custom-task-pane"></a>Przewodnik: Automatyzacja aplikacji z niestandardowego okienka zadań
  Ten przewodnik przedstawia sposób tworzenia niestandardowego okienka zadań, która automatyzuje programu PowerPoint. Niestandardowego okienka zadań wstawia daty do slajdu, gdy użytkownik kliknie <xref:System.Windows.Forms.MonthCalendar> formant, który znajduje się na niestandardowego okienka zadań.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Chociaż w tym przewodniku szczegółowo korzysta z programu PowerPoint, pojęcia dowodzą Instruktaż mają zastosowanie do dowolnej aplikacji, które są wymienione powyżej.

 W instruktażu przedstawiono następujące zagadnienia:

- Projektowanie interfejsu użytkownika niestandardowego okienka zadań.

- Automatyzowanie programu PowerPoint z niestandardowego okienka zadań.

- Wyświetlanie niestandardowego okienka zadań w programie PowerPoint.

> [!NOTE]
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Program Microsoft PowerPoint 2010 lub [!INCLUDE[PowerPoint_15_short](../vsto/includes/powerpoint-15-short-md.md)].

## <a name="create-the-add-in-project"></a>Utwórz projekt dodatku
 Pierwszym krokiem jest utworzenie projektu dodatku narzędzi VSTO dla programu PowerPoint.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt dodatku narzędzi VSTO dla programu PowerPoint o nazwie **MyAddIn**, za pomocą szablonu projektu dodatku programu PowerPoint. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwiera **ThisAddIn.cs** lub **ThisAddIn.vb** plik kodu i dodaje **MyAddIn** projekt **Eksploratora rozwiązań**.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Projektowanie interfejsu użytkownika niestandardowego okienka zadań
 Brak wizualnego projektanta dla niestandardowych okienek zadań, ale można projektować kontrolkę użytkownika przy użyciu układu, który ma. W dalszej części tego przewodnika dodasz formant użytkownika do niestandardowego okienka zadań.

#### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Projekt interfejsu użytkownika niestandardowego okienka zadań

1. Na **projektu** menu, kliknij przycisk **Dodaj kontrolkę użytkownika**.

2. W **Dodaj nowy element** okna dialogowego pole, Zmień nazwę kontrolki użytkownika do **MyUserControl**i kliknij przycisk **Dodaj**.

     Formant użytkownika zostanie otwarty w projektancie.

3. Z **wspólnych formantów** karcie **przybornika**, przeciągnij **MonthCalendar** kontrolki do kontrolki użytkownika.

     Jeśli **MonthCalendar** kontrolki jest większa niż powierzchni projektowania formantu użytkownika, Zmień rozmiar kontrolki użytkownika, aby dopasować **MonthCalendar** kontroli.

## <a name="automate-powerpoint-from-the-custom-task-pane"></a>Automatyzowanie programu PowerPoint z niestandardowego okienka zadań
 Celem dodatku narzędzi VSTO jest umieścić wybranej daty na pierwszy slajd aktywnej prezentacji. Użyj <xref:System.Windows.Forms.MonthCalendar.DateChanged> zdarzeń formantu, aby dodać wybraną datą zawsze wtedy, gdy zmienia się.

### <a name="to-automate-powerpoint-from-the-custom-task-pane"></a>Aby zautomatyzować programu PowerPoint z niestandardowego okienka zadań

1. W projektancie, kliknij dwukrotnie <xref:System.Windows.Forms.MonthCalendar> kontroli.

     **MyUserControl.cs** lub **MyUserControl.vb** plik zostanie otwarty, a program obsługi zdarzeń dla <xref:System.Windows.Forms.MonthCalendar.DateChanged> zdarzenie jest tworzone.

2. Dodaj następujący kod na początku pliku. Ten kod tworzy aliasy dla <xref:Microsoft.Office.Core> i <xref:Microsoft.Office.Interop.PowerPoint> przestrzeni nazw.

     [!code-csharp[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#1)]
     [!code-vb[Trin_TaskPaneMonthCalendar#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#1)]

3. Dodaj następujący kod do `MyUserControl` klasy. Ten kod deklaruje <xref:Microsoft.Office.Interop.PowerPoint.Shape> obiektu jako członek `MyUserControl`. W następnym kroku zostanie ona użyta <xref:Microsoft.Office.Interop.PowerPoint.Shape> można dodać pole tekstowe do slajdu aktywnej prezentacji.

     [!code-csharp[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#2)]
     [!code-vb[Trin_TaskPaneMonthCalendar#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#2)]

4. Zastąp `monthCalendar1_DateChanged` programu obsługi zdarzeń z następującym kodem. Ten kod dodaje pole tekstowe do pierwszy slajd aktywnej prezentacji, a następnie dodaje aktualnie wybranej daty do pola tekstowego. Ten kod używa `Globals.ThisAddIn` obiekt dostępu do modelu obiektu programu PowerPoint.

     [!code-csharp[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/MyUserControl.cs#3)]
     [!code-vb[Trin_TaskPaneMonthCalendar#3](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/MyUserControl.vb#3)]

5. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **MyAddIn** projektu, a następnie kliknij przycisk **kompilacji**. Upewnij się, że projekt zostanie skompilowany bez błędów.

## <a name="display-the-custom-task-pane"></a>Wyświetlanie niestandardowego okienka zadań
 Aby wyświetlić niestandardowego okienka zadań, rozpoczęciu dodatku narzędzi VSTO dla programów, należy dodać kontrolkę użytkownika do okienka zadań w <xref:Microsoft.Office.Tools.AddIn.Startup> programu obsługi zdarzeń w dodatku VSTO.

### <a name="to-display-the-custom-task-pane"></a>Aby wyświetlić niestandardowego okienka zadań

1. W **Eksploratora rozwiązań**, rozwiń węzeł **PowerPoint**.

2. Kliknij prawym przyciskiem myszy **ThisAddIn.cs** lub **ThisAddIn.vb** i kliknij przycisk **Wyświetl kod**.

3. Dodaj następujący kod do `ThisAddIn` klasy. Ten kod deklaruje wystąpień `MyUserControl` i <xref:Microsoft.Office.Tools.CustomTaskPane> jako elementy członkowskie `ThisAddIn` klasy.

     [!code-vb[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#4)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#4](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#4)]

4. Zastąp `ThisAddIn_Startup` programu obsługi zdarzeń z następującym kodem. Ten kod tworzy nową <xref:Microsoft.Office.Tools.CustomTaskPane> , dodając `MyUserControl` obiekt `CustomTaskPanes` kolekcji. Kod jest również wyświetlane w okienku zadań.

     [!code-vb[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/VisualBasic/Trin_TaskPaneMonthCalendar/ThisAddIn.vb#5)]
     [!code-csharp[Trin_TaskPaneMonthCalendar#5](../vsto/codesnippet/CSharp/Trin_TaskPaneMonthCalendar/ThisAddIn.cs#5)]

## <a name="test-the-add-in"></a>Testowanie dodatku programu
 Kiedy uruchamiasz projekt, otwiera programu PowerPoint, i dodatku narzędzi VSTO Wyświetla niestandardowego okienka zadań. Kliknij przycisk <xref:System.Windows.Forms.MonthCalendar> formantu, aby przetestować kod.

### <a name="to-test-your-vsto-add-in"></a>Aby przetestować dodatku narzędzi VSTO

1. Naciśnij klawisz **F5** Aby uruchomić projekt.

2. Upewnij się, że niestandardowego okienka zadań jest widoczna.

3. Kliknij datę w <xref:System.Windows.Forms.MonthCalendar> formantu w okienku zadań.

     Daty są wstawiane do pierwszy slajd aktywnej prezentacji.

## <a name="next-steps"></a>Następne kroki
 Możesz dowiedzieć się więcej na temat sposobu tworzenia niestandardowych okienek zadań z tych tematów:

- Tworzenie niestandardowego okienka zadań w dodatku narzędzi VSTO dla różnych aplikacji. Aby uzyskać więcej informacji na temat aplikacji, które obsługują niestandardowe okienka zadań, zobacz [niestandardowych okienek zadań](../vsto/custom-task-panes.md).

- Utwórz przycisk wstążki, który może służyć do ukryć lub wyświetlić niestandardowego okienka zadań. Aby uzyskać więcej informacji, zobacz [instruktażu: Synchronizuj niestandardowego okienka zadań z przyciskiem wstążki](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).

- Tworzenie niestandardowego okienka zadań dla każdej wiadomości e-mail, który jest otwierany w programie Outlook. Aby uzyskać więcej informacji, zobacz [instruktażu: Wyświetlanie niestandardowych okienek zadań z wiadomościami e-mail w programie Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md).

## <a name="see-also"></a>Zobacz także
- [Niestandardowe okienka zadań](../vsto/custom-task-panes.md)
- [Instrukcje: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Przewodnik: Synchronizuj niestandardowego okienka zadań z przyciskiem wstążki](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [Przewodnik: Wyświetlanie niestandardowych okienek zadań z wiadomościami e-mail w programie Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md)
