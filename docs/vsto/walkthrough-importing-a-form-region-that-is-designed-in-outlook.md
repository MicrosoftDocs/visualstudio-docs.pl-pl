---
title: 'Przewodnik: importowanie regionu formularza zaprojektowanego w programie Outlook'
description: Dowiedz się, jak zaprojektować region formularza w programie Microsoft Outlook, a następnie zaimportować region formularza do projektu dodatku VSTO programu Outlook przy użyciu kreatora Nowy region formularza.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4ce8c334be74f2643bfc7fa263b01a74db109eb7
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827750"
---
# <a name="walkthrough-import-a-form-region-that-is-designed-in-outlook"></a>Przewodnik: importowanie regionu formularza zaprojektowanego w programie Outlook
  W tym przewodniku pokazano, jak zaprojektować region formularza w programie Microsoft Office Outlook, a następnie zaimportować region formularza do projektu dodatku Outlook VSTO za pomocą kreatora Nowy **region formularza.** Projektowanie regionu formularza w programie Outlook umożliwia dodawanie natywnych kontrolek programu Outlook do regionu formularza, który jest wiązany z danymi programu Outlook. Po zaimportowaniu obszaru formularza można obsługiwać zdarzenia każdej kontrolki.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Projektowanie regionu formularza przy użyciu projektanta regionów formularzy w programie Outlook.

- Importowanie regionu formularza do projektu dodatku Outlook VSTO.

- Obsługa zdarzeń kontrolek w obszarze formularza.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] lub [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)].

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Personalizowanie środowiska IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="design-a-form-region-by-using-the-form-region-designer-in-outlook"></a>Projektowanie regionu formularza przy użyciu projektanta regionów formularzy w programie Outlook
 W tym kroku zaprojektujemy region formularza w programie Outlook. Następnie zapiszemy region formularza w łatwej do znalezienia lokalizacji, aby można było zaimportować go do pliku [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

 Ten przykładowy region formularza całkowicie zastępuje zwykły formularz Zadania. Umożliwia śledzenie postępu wszystkich zadań, które muszą zostać wykonane przed rozpoczęciem głównego zadania (zadań wstępnych). Region formularza zawiera listę zadań wstępnych i stan ukończenia każdego zadania na liście. Użytkownicy mogą dodawać zadania do listy i je usuwać. Mogą również odświeżyć stan ukończenia każdego zadania.

### <a name="to-design-a-form-region-by-using-the-form-region-designer-in-outlook"></a>Aby zaprojektować region formularza przy użyciu projektanta regionów formularzy w programie Outlook

1. Uruchom Microsoft Office Outlook.

2. W programie Outlook na **karcie Deweloper** kliknij pozycję **Zaprojektuj formularz**. Aby uzyskać więcej informacji, zobacz How to: Show the developer tab on the ribbon (Jak [wyświetlić kartę dewelopera na wstążce).](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)

3. W polu **Formularz projektu** kliknij pozycję **Zadanie**, a następnie kliknij przycisk **Otwórz**.

4. W programie Outlook na karcie **Deweloper** w grupie **Projekt** kliknij pozycję **Nowy region formularza.**

     Zostanie otwarty nowy region formularza. Jeśli **słynący pola** nie jest wyświetlany, kliknij pozycję S wyboru **pola** w **grupie** Narzędzia.

5. Przeciągnij pole **Temat** i pole **% Complete (Procent** ukończenia) z obszaru **Wyboru pola** do regionu formularza.

6. W grupie **Narzędzia** kliknij pozycję **Przybornik sterowania,** aby otworzyć **przybornik**.

7. Przeciągnij etykietę z **przybornika** do obszaru formularza. Umieść etykietę poniżej pól **Temat** i **% Ukończono.**

8. Kliknij prawym przyciskiem myszy etykietę, a następnie kliknij **pozycję Właściwości zaawansowane.**

9. W **oknie Właściwości** ustaw właściwość **Podpis** na wartość To **zadanie** zależy od następujących zadań, ustaw właściwość **Width** na **wartość 200,** a następnie kliknij przycisk **Zastosuj**.

10. Przeciągnij kontrolkę ListBox z **przybornika** do obszaru formularza. Położenie pola listy pod **etykietą To zadanie zależy od poniższej etykiety** zadań.

11. Wybierz właśnie dodane pole listy.

12. W **oknie Właściwości** ustaw **wartość Width (Szerokość)** **na 300**, a następnie kliknij przycisk **Apply (Zastosuj).**

13. Przeciągnij etykietę z **przybornika** do obszaru formularza. Umieść etykietę pod polem listy.

14. Wybierz właśnie dodaną etykietę.

15. W **oknie** Właściwości ustaw właściwość **Podpis** na wybierz zadanie do dodania do listy zadań zależnych, ustaw właściwość **Width** na **wartość 200,** **a** następnie kliknij przycisk **Zastosuj**.

16. Przeciągnij kontrolkę ComboBox z **przybornika** do obszaru formularza. Umieść pole kombi poniżej **etykiety Wybierz zadanie do dodania do listy zadań zależnych.**

17. Wybierz właśnie dodane pole kombi.

18. W **oknie** Właściwości ustaw właściwość **Width** na **wartość 300,** a następnie kliknij przycisk **Zastosuj.**

19. Przeciągnij kontrolkę CommandButton z **przybornika** do obszaru formularza. Umieść przycisk polecenia obok pola kombi.

20. Wybierz właśnie dodany przycisk polecenia.

21. W **oknie Właściwości** ustaw wartość **Nazwa** na **AddDependentTask,** ustaw wartość Add Dependent **Task**(Dodaj zadanie zależne), ustaw wartość **Width** (Szerokość) na **100,** a następnie kliknij przycisk **Apply (Zastosuj).** 

22. W obszarze **Wyboru pola** kliknij pozycję **Nowy.**

23. W **oknie dialogowym Nowe** pole wpisz **hiddenField w** polu **Nazwa,** a następnie kliknij przycisk **OK**.

24. Przeciągnij pole **hiddenField** z **sufiksu Wybór** pola do obszaru formularza.

25. W **oknie Właściwości** ustaw opcję **Widoczne na** **wartość 0 – Fałsz,** a następnie kliknij przycisk **Zastosuj.**

26. W programie **Outlook na** karcie Deweloper w **grupie** Projekt kliknij przycisk **Zapisz,** a następnie kliknij pozycję **Zapisz region formularza jako**.

     Nadaj regionowi **formularza nazwę TaskFormRegion** i zapisz go w katalogu lokalnym na komputerze.

     Program Outlook zapisuje region formularza jako plik magazynu formularzy programu Outlook *(ofs).* Region formularza jest zapisywany pod nazwą *TaskFormRegion.ofs.*

27. Zamknij program Outlook.

## <a name="create-a-new-outlook-add-in-project"></a>Tworzenie nowego projektu dodatku programu Outlook
 W tym kroku utworzysz projekt dodatku VSTO dla programu Outlook. W dalszej części tego przewodnika zaimportujesz region formularza do projektu.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Aby utworzyć nowy projekt dodatku VSTO programu Outlook

1. W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] programie utwórz projekt dodatku VSTO programu Outlook o nazwie **TaskAddIn**.

2. W **oknie dialogowym Nowy** projekt wybierz pozycję **Utwórz katalog dla rozwiązania**.

3. Zapisz projekt w domyślnym katalogu projektu.

     Aby uzyskać więcej informacji, [zobacz How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="import-the-form-region"></a>Importowanie regionu formularza
 Region formularzy zaprojektowany w programie Outlook można zaimportować do projektu dodatku VSTO programu Outlook przy użyciu kreatora Nowy region **formularza programu Outlook.**

### <a name="to-import-the-form-region-into-the-outlook-vsto-add-in-project"></a>Aby zaimportować region formularza do projektu dodatku Outlook VSTO

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt **TaskAddIn,** wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Nowy element**.

2. W **okienku Szablony** wybierz pozycję Region formularza programu **Outlook,** nadaj **plikowi nazwę TaskFormRegion,** a następnie kliknij przycisk **Dodaj**.

     Zostanie **uruchomiony kreator NewOutlook Form Region (Nowy Region formularza).**

3. Na stronie **Wybierz sposób tworzenia** regionu formularza kliknij pozycję Importuj plik magazynu formularzy programu Outlook **(plik ofs),** a następnie kliknij **przycisk Przeglądaj**.

4. W **oknie dialogowym Lokalizacja** pliku istniejącego regionu formularza programu Outlook przejdź do lokalizacji pliku *TaskFormRegion.ofs,* wybierz pozycję **TaskFormRegion.ofs,** kliknij przycisk **Otwórz,** a następnie kliknij przycisk **Dalej.**

5. Na **stronie Select the type of form region you want to create** (Wybierz typ regionu formularza, który chcesz utworzyć) kliknij pozycję **Replace-all**, a następnie kliknij przycisk **Next (Dalej).**

     Obszar *formularza replace-all* zastępuje cały formularz programu Outlook. Aby uzyskać więcej informacji na temat typów regionów formularzy, zobacz [Create Outlook form regions (Tworzenie regionów formularzy programu Outlook).](../vsto/creating-outlook-form-regions.md)

6. Na stronie **Dostarczanie tekstu opisowego i wybierz preferencje wyświetlania** kliknij przycisk **Dalej.**

7. Na stronie **Identyfikowanie klas komunikatów,** które będą wyświetlać ten region formularza, w polu Które niestandardowe klasy komunikatów będą wyświetlać ten **region** formularza, wpisz **IPM. Task.TaskFormRegion**, a następnie kliknij przycisk **Zakończ.**

     Do projektu zostanie dodany plik *TaskFormRegion.cs* lub *TaskFormRegion.vb.*

## <a name="handle-the-events-of-controls-on-the-form-region"></a>Obsługa zdarzeń kontrolek w obszarze formularza
 Teraz, gdy masz już obszar formularza w projekcie, możesz dodać kod obsługujący zdarzenie przycisku dodanego do regionu formularza w `Microsoft.Office.Interop.Outlook.OlkCommandButton.Click` programie Outlook.

 Ponadto dodaj do zdarzenia <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> kod, który aktualizuje kontrolki w obszarze formularza, gdy pojawi się obszar formularza.

### <a name="to-handle-the-events-of-controls-on-the-form-region"></a>Aby obsługiwać zdarzenia kontrolek w obszarze formularza

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję *TaskFormRegion.cs* lub *TaskFormRegion.vb,* a następnie kliknij **polecenie Wyświetl kod.**

    *Plik TaskFormRegion.cs* lub *TaskFormRegion.vb* zostanie otwarty w Edytorze kodu.

2. Dodaj poniższy kod do klasy `TaskFormRegion`. Ten kod wypełnia pole kombi w obszarze formularza wierszem tematu każdego zadania z folderu Zadania programu Outlook.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs" id="Snippet1":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb" id="Snippet1":::

3. Dodaj poniższy kod do klasy `TaskFormRegion`. Ten kod wykonuje następujące zadania:

   - Lokalizuje `Microsoft.Office.Interop.Outlook.TaskItem` obiekt w folderze Tasks, wywołując metodę `FindTaskBySubjectName` pomocnika i przekazując podmiot żądanego zadania. W następnym kroku `FindTaskBySubjectName` dodasz metodę pomocnika .

   - Dodaje wartości `Microsoft.Office.Interop.Outlook.TaskItem.Subject` i do pola listy zadań `Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete` zależnych.

   - Dodaje temat zadania do ukrytego pola w obszarze formularza. Ukryte pole przechowuje te wartości jako część elementu programu Outlook.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb" id="Snippet2":::

4. Dodaj poniższy kod do klasy `TaskFormRegion`. Ten kod zawiera metodę pomocnika `FindTaskBySubjectName` opisaną w poprzednim kroku.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs" id="Snippet3":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb" id="Snippet3":::

5. Dodaj poniższy kod do klasy `TaskFormRegion`. Ten kod wykonuje następujące zadania:

   - Odświeża pole listy w obszarze formularza przy użyciu bieżącego stanu ukończenia każdego zadania zależnego.

   - Analizuje ukryte pole tekstowe, aby uzyskać temat każdego zadania zależnego. Następnie lokalizuje każdy z `Microsoft.Office.Interop.Outlook.TaskItem` nich w *folderze Tasks,* wywołując metodę `FindTaskBySubjectName` pomocnika i przekazując temat każdego zadania.

   - Dodaje wartości `Microsoft.Office.Interop.Outlook.TaskItem.Subject` i do pola listy zadań `Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete` zależnych.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb" id="Snippet4":::

6. Zastąp program `TaskFormRegion_FormRegionShowing` obsługi zdarzeń następującym kodem. Ten kod wykonuje następujące zadania:

   - Wypełnia pole kombi w obszarze formularza tematami zadań, gdy pojawi się obszar formularza.

   - Wywołuje metodę `RefreshTaskListBox` pomocnika, gdy pojawi się obszar formularza. Powoduje to wyświetlenie wszystkich zależnych zadań, które zostały dodane do pola listy, gdy element został wcześniej otwarty.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb" id="Snippet5":::

## <a name="test-the-outlook-form-region"></a>Testowanie regionu formularza programu Outlook
 Aby przetestować region formularza, dodaj zadania do listy zadań wstępnych w regionie formularza. Zaktualizuj stan ukończenia zadania wstępnego, a następnie wyświetl zaktualizowany stan ukończenia zadania na liście zadań wymagań wstępnych.

### <a name="to-test-the-form-region"></a>Aby przetestować region formularza

1. Naciśnij **klawisz F5,** aby uruchomić projekt.

     Program Outlook jest uruchamiany.

2. W programie Outlook na **karcie Narzędzia** główne kliknij pozycję **Nowe elementy,** a następnie kliknij pozycję **Zadanie.**

3. W formularzu zadania wpisz **Zadanie zależne** w **polu** Temat.

4. Na karcie **Zadanie** wstążki w grupie Akcje **kliknij** przycisk **Zapisz, & Zamknij.**

5. W programie Outlook na karcie **Narzędzia** główne kliknij pozycję **Nowe elementy,** kliknij pozycję **Więcej elementów,** a następnie kliknij pozycję **Wybierz formularz.**

6. W **oknie dialogowym Wybieranie** formularza kliknij pozycję **TaskFormRegion**, a następnie kliknij przycisk **Otwórz**.

     Zostanie **wyświetlony region formularza TaskFormRegion.** Ten formularz zastępuje cały formularz zadania. Pole **kombi Wybierz zadanie do dodania do listy** zadań zależnych jest wypełniane innymi zadaniami w folderze Zadania.

7. W formularzu zadania w polu **Temat** wpisz **Zadanie podstawowe**.

8. W Wybierz **zadanie do dodania do** listy zadań zależnych pole kombi, wybierz zadanie zależne **,** a następnie kliknij przycisk Dodaj **zadanie zależne**.

     **Ukończono 0% — zadanie** zależne pojawia się w polu **listy To zadanie** zależy od następujących zadań. Pokazuje to, że zdarzenie przycisku `Microsoft.Office.Interop.Outlook.OlkCommandButton.Click` zostało pomyślnie obsłużone.

9. Zapisz i zamknij **element Zadanie** podstawowe.

10. Otwórz ponownie element Zadanie zależne w programie Outlook.

11. W formularzu Zadanie zależne zmień pole **% Complete (Procent ukończenia)** na **50%.**

12. Na karcie **Zadanie** wstążki Zadanie zależne  w grupie Akcje kliknij przycisk **& Zamknij**.

13. Otwórz ponownie **element Zadanie podstawowe** w programie Outlook.

     **50% Ukończono — zadanie** zależne jest teraz wyświetlane w polu listy **To zadanie** zależy od następujących zadań.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat dostosowywania interfejsu użytkownika aplikacji Outlook można znaleźć w tych tematach:

- Aby dowiedzieć się więcej na temat projektowania wyglądu obszaru formularza przez przeciągnięcie kontrolek zarządzanych do projektanta wizualnego, zobacz Przewodnik: projektowanie regionu formularza [programu Outlook.](../vsto/walkthrough-designing-an-outlook-form-region.md)

- Aby dowiedzieć się, jak dostosować wstążkę elementu programu Outlook, zobacz [Dostosowywanie wstążki programu Outlook.](../vsto/customizing-a-ribbon-for-outlook.md)

- Aby dowiedzieć się więcej na temat dodawania niestandardowego okienka zadań do programu Outlook, zobacz [Niestandardowe okienka zadań.](../vsto/custom-task-panes.md)

## <a name="see-also"></a>Zobacz też
- [Uzyskiwanie dostępu do regionu formularza w czasie uruchamiania](../vsto/accessing-a-form-region-at-run-time.md)
- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
- [Wskazówki dotyczące tworzenia regionów formularzy programu Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Przewodnik: projektowanie regionu formularza programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Jak dodać region formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Kojarzenie regionu formularza z klasą komunikatów programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Akcje niestandardowe w regionach formularzy programu Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
- [How to: Prevent Outlook from displaying a form region (Jak zapobiec wyświetlaniu regionu formularza w programie Outlook)](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
