---
title: 'Przewodnik: Importowanie regionów formularzy zaprojektowanych w programie Outlook'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- importing form regions
- form regions [Office development in Visual Studio], importing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2a0de1a25a5309e99193b7be8bce2819808665b8
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584979"
---
# <a name="walkthrough-import-a-form-region-that-is-designed-in-outlook"></a>Przewodnik: Importowanie regionów formularzy zaprojektowanych w programie Outlook
  W tym instruktażu przedstawiono sposób projektowania regionu formularza w programie Microsoft Office Outlook, a następnie importowania regionu formularza do projektu dodatku VSTO programu Outlook za pomocą kreatora **nowego regionu formularza** . Projektowanie regionu formularza w programie Outlook umożliwia dodawanie natywnych kontrolek programu Outlook do regionu formularza powiązanego z danymi programu Outlook. Po zaimportowaniu regionu formularza można obsłużyć zdarzenia poszczególnych kontrolek.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Projektowanie regionu formularza przy użyciu projektanta regionów formularzy w programie Outlook.

- Importowanie regionu formularza do projektu dodatku VSTO programu Outlook.

- Obsługa zdarzeń formantów w regionie formularza.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] lub [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)].

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="design-a-form-region-by-using-the-form-region-designer-in-outlook"></a>Projektowanie regionu formularza przy użyciu projektanta regionów formularzy w programie Outlook
 W tym kroku utworzysz region formularza w programie Outlook. Następnie Zapisz region formularza w lokalizacji łatwej do znalezienia, aby można było zaimportować go do programu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 Ten przykładowy region formularza całkowicie zastępuje zwykły formularz zadania. Umożliwia śledzenie postępu wszystkich zadań, które muszą zostać wykonane, zanim będzie można wykonać zadanie główne (zadania wymagające wymagań wstępnych). W regionie formularza zostanie wyświetlona lista wstępnie wymaganych zadań i zostanie wyświetlony stan ukończenia każdego zadania na liście. Użytkownicy mogą dodawać zadania do listy i usuwać je. Mogą również odświeżać stan ukończenia każdego zadania.

### <a name="to-design-a-form-region-by-using-the-form-region-designer-in-outlook"></a>Aby zaprojektować region formularza przy użyciu projektanta regionów formularzy w programie Outlook

1. Rozpocznij Microsoft Office Outlook.

2. W programie Outlook na karcie **deweloper** kliknij pozycję **Projektuj formularz**. Aby uzyskać więcej informacji, zobacz [jak: wyświetlić kartę Deweloper na Wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

3. W **formularzu projekt** kliknij **zadanie**, a następnie kliknij przycisk **Otwórz**.

4. W programie Outlook na karcie **deweloper** w grupie **projekt** kliknij pozycję **Nowy region formularza**.

     Zostanie otwarty nowy region formularza. Jeśli **Wybór pola** nie jest wyświetlany, kliknij przycisk selektor **pól** w grupie **Narzędzia** .

5. Przeciągnij pole **subject** i pole **ukończono (%)** z selektora **pól** do regionu formularza.

6. W grupie **Narzędzia** kliknij pozycję **Przybornik formantów** , aby otworzyć **Przybornik**.

7. Przeciągnij etykietę z **przybornika** do regionu formularza. Umieść etykietę poniżej pól **temat** i **% Complete** .

8. Kliknij prawym przyciskiem myszy etykietę, a następnie kliknij przycisk **Właściwości zaawansowane**.

9. W oknie **Właściwości** ustaw właściwość **Caption** na **to zadanie zależnie od następujących zadań**, ustaw właściwość **Width** na **200**, a następnie kliknij przycisk **Zastosuj**.

10. Przeciągnij formant ListBox z **przybornika** do regionu formularza. Umieść pole listy poniżej **tego zadania zależy od następującej etykiety zadań** .

11. Zaznacz dodane pole listy.

12. W oknie **Właściwości** Ustaw **Szerokość** na **300**, a następnie kliknij przycisk **Zastosuj**.

13. Przeciągnij etykietę z **przybornika** do regionu formularza. Umieść etykietę pod polem listy.

14. Wybierz etykietę, która właśnie została dodana.

15. W oknie **Właściwości** , ustaw właściwość **Caption** , aby **wybrać zadanie do dodania do listy zadań zależnych**, ustaw właściwość **Width** na **200**, a następnie kliknij przycisk **Zastosuj**.

16. Przeciągnij kontrolkę ComboBox z **przybornika** do regionu formularza. Umieść pole kombi poniżej **opcji wybierz zadanie do dodania do listy zależnych zadań** .

17. Zaznacz dodane pole kombi.

18. W oknie **Właściwości** ustaw właściwość **Szerokość** na **300**, a następnie kliknij przycisk **Zastosuj**.

19. Przeciągnij formant CommandButton z **przybornika** do regionu formularza. Umieść przycisk polecenia obok pola kombi.

20. Wybierz właśnie dodany przycisk polecenia.

21. W oknie **Właściwości** , ustaw **nazwę** na **AddDependentTask**, ustaw **podpis** , aby **dodać zadanie zależne**, ustaw **Szerokość** na **100**, a następnie kliknij przycisk **Zastosuj**.

22. W oknie **wybór pól**kliknij pozycję **Nowy**.

23. W oknie dialogowym **Nowy pole** wpisz **HiddenField** w polu **Nazwa** , a następnie kliknij przycisk **OK**.

24. Przeciągnij pole **hiddenField** z selektora **pola** do regionu formularza.

25. W oknie **Właściwości** ustaw wartość **widoczny** na **0-false**, a następnie kliknij przycisk **Zastosuj**.

26. W programie Outlook na karcie **deweloper** w grupie **projekt** kliknij przycisk **Zapisz** , a następnie kliknij pozycję **Zapisz region formularza jako**.

     Nadaj nazwę regionowi **TaskFormRegion** i Zapisz ją w katalogu lokalnym na komputerze.

     Program Outlook zapisuje region formularza jako plik magazynu formularzy programu Outlook (*OFS*). Region formularza jest zapisywany z nazwą *TaskFormRegion. ofs*.

27. Zamknij program Outlook.

## <a name="create-a-new-outlook-add-in-project"></a>Utwórz nowy projekt dodatku programu Outlook
 W tym kroku utworzysz projekt dodatku VSTO dla programu Outlook. W dalszej części tego instruktażu zostanie zaimportowany region formularza do projektu.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Aby utworzyć nowy projekt dodatku VSTO dla programu Outlook

1. W programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Utwórz projekt dodatku VSTO programu Outlook o nazwie **TaskAddIn**.

2. W oknie dialogowym **Nowy projekt** wybierz pozycję **Utwórz katalog dla rozwiązania**.

3. Zapisz projekt w domyślnym katalogu projektu.

     Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="import-the-form-region"></a>Importowanie regionu formularza
 Możesz zaimportować region formularza zaprojektowany w programie Outlook do projektu dodatku VSTO programu Outlook przy użyciu **nowego kreatora regionu formularza programu Outlook** .

### <a name="to-import-the-form-region-into-the-outlook-vsto-add-in-project"></a>Aby zaimportować region formularza do projektu dodatku VSTO programu Outlook

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **TaskAddIn** , wskaż polecenie **Dodaj**, a następnie kliknij pozycję **nowy element**.

2. W okienku **Szablony** wybierz pozycję **region formularza programu Outlook**, Nazwij plik **TaskFormRegion**, a następnie kliknij przycisk **Dodaj**.

     Zostanie uruchomiony Kreator **regionu formularza NewOutlook** .

3. Na stronie **Wybierz, jak chcesz utworzyć region formularza** kliknij pozycję **Importuj plik magazynu formularzy programu Outlook (ofs)**, a następnie kliknij przycisk **Przeglądaj**.

4. W oknie dialogowym **istniejąca lokalizacja pliku regionu formularza programu Outlook** przejdź do lokalizacji *TaskFormRegion. ofs*, wybierz pozycję **TaskFormRegion. ofs**, kliknij przycisk **Otwórz**, a następnie kliknij przycisk **dalej**.

5. Na stronie **Wybierz typ regionu formularza, który chcesz utworzyć** kliknij przycisk **Zamień wszystkie**, a następnie kliknij przycisk **dalej**.

     Region *Zamień wszystko* zastępuje cały formularz programu Outlook. Aby uzyskać więcej informacji na temat typów regionów formularzy, zobacz [Tworzenie regionów formularzy w programie Outlook](../vsto/creating-outlook-form-regions.md).

6. Na stronie **podaj tekst opisowy i wybierz Preferencje wyświetlania** kliknij przycisk **dalej**.

7. Na stronie **Zidentyfikuj klasy komunikatów, które będą wyświetlać ten region formularza** , w oknie, w **których niestandardowych klasach wiadomości będzie wyświetlany ten region formularza** , wpisz **IPM. Task. TaskFormRegion**, a następnie kliknij przycisk **Zakończ**.

     Do projektu zostanie dodany plik *TaskFormRegion.cs* lub *TaskFormRegion. vb* .

## <a name="handle-the-events-of-controls-on-the-form-region"></a>Obsługa zdarzeń formantów w regionie formularza
 Teraz, gdy masz region formularza w projekcie, możesz dodać kod, który obsługuje `Microsoft.Office.Interop.Outlook.OlkCommandButton.Click` zdarzenie przycisku dodanego do regionu formularza w programie Outlook.

 Ponadto Dodaj kod do <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> zdarzenia, które aktualizuje kontrolki w regionie formularza, gdy zostanie wyświetlony region formularza.

### <a name="to-handle-the-events-of-controls-on-the-form-region"></a>Aby obsłużyć zdarzenia formantów w regionie formularza

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję *TaskFormRegion.cs* lub *TaskFormRegion. vb*, a następnie kliknij polecenie **Wyświetl kod**.

    *TaskFormRegion.cs* lub *TaskFormRegion. vb* zostanie otwarty w edytorze kodu.

2. Dodaj poniższy kod do klasy `TaskFormRegion`. Ten kod wypełnia pole kombi w regionie formularza z wierszem tematu każdego zadania z folderu zadania programu Outlook.

    [!code-csharp[Trin_Outlook_FR_Import#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#1)]
    [!code-vb[Trin_Outlook_FR_Import#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#1)]

3. Dodaj poniższy kod do klasy `TaskFormRegion`. Ten kod wykonuje następujące zadania:

   - Lokalizuje `Microsoft.Office.Interop.Outlook.TaskItem` w folderze zadania przez wywołanie `FindTaskBySubjectName` metody pomocnika i przekazanie tematu żądanego zadania. `FindTaskBySubjectName`W następnym kroku dodasz metodę pomocnika.

   - Dodaje `Microsoft.Office.Interop.Outlook.TaskItem.Subject` wartości i `Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete` do pola listy zadań zależnych.

   - Dodaje temat zadania do pola ukrytego w regionie formularza. Pole ukryte przechowuje te wartości jako część elementu programu Outlook.

     [!code-csharp[Trin_Outlook_FR_Import#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#2)]
     [!code-vb[Trin_Outlook_FR_Import#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#2)]

4. Dodaj poniższy kod do klasy `TaskFormRegion`. Ten kod zawiera metodę pomocnika `FindTaskBySubjectName` , która została opisana w poprzednim kroku.

    [!code-csharp[Trin_Outlook_FR_Import#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#3)]
    [!code-vb[Trin_Outlook_FR_Import#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#3)]

5. Dodaj poniższy kod do klasy `TaskFormRegion`. Ten kod wykonuje następujące zadania:

   - Odświeża pole listy w regionie formularza z bieżącym stanem ukończenia poszczególnych zadań zależnych.

   - Analizuje ukryte pole tekstowe, aby uzyskać temat poszczególnych zadań zależnych. Następnie lokalizuje każdy `Microsoft.Office.Interop.Outlook.TaskItem` w folderze *zadania* przez wywołanie `FindTaskBySubjectName` metody pomocnika i przekazanie tematu każdego zadania.

   - Dodaje `Microsoft.Office.Interop.Outlook.TaskItem.Subject` wartości i `Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete` do pola listy zadań zależnych.

     [!code-csharp[Trin_Outlook_FR_Import#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#4)]
     [!code-vb[Trin_Outlook_FR_Import#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#4)]

6. Zastąp `TaskFormRegion_FormRegionShowing` procedurę obsługi zdarzeń poniższym kodem. Ten kod wykonuje następujące zadania:

   - Wypełnia pole kombi w regionie formularza przy użyciu tematów zadania, gdy zostanie wyświetlony region formularza.

   - Wywołuje `RefreshTaskListBox` metodę pomocnika, gdy zostanie wyświetlony region formularza. Spowoduje to wyświetlenie wszystkich zadań zależnych, które zostały dodane do pola listy, gdy element został wcześniej otwarty.

     [!code-csharp[Trin_Outlook_FR_Import#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#5)]
     [!code-vb[Trin_Outlook_FR_Import#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#5)]

## <a name="test-the-outlook-form-region"></a>Testowanie regionu formularza programu Outlook
 Aby przetestować region formularza, Dodaj zadania do listy zadań wymaganych wstępnie w regionie formularza. Zaktualizuj stan ukończenia zadania wymagań wstępnych, a następnie Wyświetl zaktualizowany stan ukończenia zadania na liście zadań wymaganych wstępnie.

### <a name="to-test-the-form-region"></a>Aby przetestować region formularza

1. Naciśnij klawisz **F5** , aby uruchomić projekt.

     Program Outlook zostanie uruchomiony.

2. W programie Outlook na karcie **Narzędzia główne** kliknij pozycję **nowe elementy**, a następnie kliknij pozycję **zadanie**.

3. W formularzu zadania wpisz **zależne zadanie** w polu **podmiot** .

4. Na karcie **zadanie** wstążki w grupie **Akcje** kliknij przycisk **Zapisz & Zamknij**.

5. W programie Outlook na karcie **Narzędzia główne** kliknij pozycję **nowe elementy**, kliknij pozycję **więcej elementów**, a następnie kliknij pozycję **Wybierz formularz**.

6. W oknie dialogowym **Wybieranie formularza** kliknij pozycję **TaskFormRegion**, a następnie kliknij pozycję **Otwórz**.

     Zostanie wyświetlony region formularza **TaskFormRegion** . Ten formularz zastępuje cały formularz zadania. Pole kombi **Wybierz zadanie do dodania do listy zadań zależnych** jest wypełniane innymi zadaniami w folderze zadania.

7. W formularzu zadania w polu **podmiot** wpisz **podstawowe zadanie**.

8. W polu kombi **Wybierz zadanie do dodania do listy zadań zależnych** wybierz pozycję **zadanie zależne**, a następnie kliknij pozycję **Dodaj zadanie zależne**.

     **0% wykonania zadania zależnego** w **tym zadaniu jest zależne od poniższego** pola listy zadań. Pokazuje to, że można pomyślnie obsłużyć `Microsoft.Office.Interop.Outlook.OlkCommandButton.Click` zdarzenie przycisku.

9. Zapisz i Zamknij **podstawowy element zadania** .

10. Otwórz ponownie zależny element zadania w programie Outlook.

11. W formularzu zadanie zależne Zmień wartość pola **ukończono** na **50%**.

12. Na karcie **zadanie** na Wstążce zadań zależnych w grupie **Akcje** kliknij przycisk **Zapisz & Zamknij**.

13. Otwórz ponownie **podstawowy element zadania** w programie Outlook.

     **50% zadanie zależne od ukończenia** teraz pojawia się w **tym zadaniu, zależnie od poniższego** pola listy zadań.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat sposobu dostosowywania interfejsu użytkownika aplikacji Outlook można znaleźć w następujących tematach:

- Aby dowiedzieć się więcej na temat projektowania wyglądu regionu formularza przez przeciąganie formantów zarządzanych do projektanta wizualnego, zobacz [Przewodnik: Projektowanie regionu formularza programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).

- Aby dowiedzieć się, jak dostosować Wstążkę elementu programu Outlook, zobacz [Dostosowywanie wstążki dla programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

- Aby dowiedzieć się więcej na temat dodawania niestandardowego okienka zadań do programu Outlook, zobacz [niestandardowe okienka zadań](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Zobacz też
- [Dostęp do regionu formularza w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md)
- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
- [Wytyczne dotyczące tworzenia regionów formularzy programu Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Przewodnik: Projektowanie regionu formularza programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Instrukcje: Dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Niestandardowe akcje w regionach formularzy programu Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
- [Instrukcje: zapobieganie wyświetlaniu regionu formularza przez program Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
