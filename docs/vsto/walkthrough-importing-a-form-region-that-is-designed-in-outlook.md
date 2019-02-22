---
title: 'Przewodnik: Importowanie regionów formularzy zaprojektowanych w programie Outlook'
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
ms.openlocfilehash: 646fa57ac351fab9b2527c3527ce1864c42519ce
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56631565"
---
# <a name="walkthrough-import-a-form-region-that-is-designed-in-outlook"></a>Przewodnik: Importowanie regionów formularzy zaprojektowanych w programie Outlook
  W tym instruktażu pokazano, jak projektowanie regionów formularzy w programie Microsoft Office Outlook, a następnie zaimportuj regionu formularza w projekcie dodatku narzędzi VSTO dla programu Outlook, za pomocą **nowy Region formularza** kreatora. Projektowanie regionów formularzy programu Outlook umożliwia dodanie natywne kontrolki programu Outlook do regionu formularza, który należy powiązać dane programu Outlook. Po zaimportowaniu region formularza można obsługiwać zdarzenia każdej kontrolki.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Projektowanie regionów formularzy przy użyciu projektanta regionów formularza w programie Outlook.

- Importowanie regionów formularzy w projekcie dodatku narzędzi VSTO dla programu Outlook.

- Obsługa zdarzeń formantów na region formularza.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

-   [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] lub [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)].

> [!NOTE]
>  Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

 ![Link do wideo](../vsto/media/playvideo.gif "link do wideo") powiązane demonstracyjne wideo – zobacz [jak: Tworzenie regionów formularzy programu Outlook przy użyciu programu Visual Studio 2008? ](http://go.microsoft.com/fwlink/?LinkID=130305).
## <a name="design-a-form-region-by-using-the-form-region-designer-in-outlook"></a>Projektowanie regionów formularzy przy użyciu projektanta regionów formularza w programie Outlook
 W tym kroku zostanie projektowanie regionów formularzy w programie Outlook. Następnie wykonasz zapisywania regionu formularza z lokalizacją łatwe do znalezienia tak, aby zaimportować je do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

 Ten region formularza przykład całkowicie zastępuje zwykle formularza zadania. Zapewnia ona sposób śledzenia postępu wszystkich zadań, które należy wykonać, aby można było głównego zadania wykonywane (zadań wstępne). Region formularza jest wyświetlana lista zadań wstępnych i pokazuje stan ukończenia każdego zadania na liście. Użytkownicy mogą dodawać zadania do listy i usuń je. Można również odświeżyć stan ukończenia każdego zadania.

### <a name="to-design-a-form-region-by-using-the-form-region-designer-in-outlook"></a>Aby zaprojektować regionu formularza za pomocą projektanta regionów formularza programu Outlook

1.  Uruchom program Microsoft Office Outlook.

2.  W programie Outlook na **Developer** kliknij pozycję **projektowania formularza**. Aby uzyskać więcej informacji, zobacz [jak: Pokazywanie karty dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

3.  W **projektowania formularza** kliknij **zadań**, a następnie kliknij przycisk **Otwórz**.

4.  W programie Outlook na **Developer** na karcie **projektowania** grupy, kliknij przycisk **nowy Region formularza**.

     Zostanie otwarty nowy region formularza. Jeśli **wybór pola** nie jest wyświetlana, kliknij przycisk **wybór pola** w **narzędzia** grupy.

5.  Przeciągnij **podmiotu** pola i **% Complete** pola z **wybór pola** do regionu formularza.

6.  W **narzędzia** grupy, kliknij przycisk **przybornik** otworzyć **przybornika**.

7.  Przeciągnij etykietę z **przybornika** do regionu formularza. Umieść etykietę pod **podmiotu** i **% Complete** pola.

8.  Kliknij etykietę prawym przyciskiem myszy, a następnie kliknij przycisk **zaawansowane właściwości**.

9. W **właściwości** oknie **podpis** właściwości **to zadanie jest zależna od następujących zadań**ustaw **szerokość** właściwości **200**, a następnie kliknij przycisk **Zastosuj**.

10. Przeciągnięcie formantu ListBox z **przybornika** do regionu formularza. Położenie pola listy poniżej **to zadanie jest zależna od następujących zadań** etykiety.

11. Wybierz pole listy, który właśnie został dodany.

12. W **właściwości** oknie **szerokość** do **300**, a następnie kliknij przycisk **Zastosuj**.

13. Przeciągnij etykietę z **przybornika** do regionu formularza. Pozycja etykiety poniżej pola listy.

14. Wybierz etykietę, który właśnie został dodany.

15. W **właściwości** oknie **podpis** właściwości **wybierz zadanie do dodania do listy zadań zależnych**ustaw **szerokość** Właściwość **200**, a następnie kliknij przycisk **Zastosuj**.

16. Przeciągnij formant pola kombi z **przybornika** do regionu formularza. Położenie pola kombi pod **wybierz zadanie do dodania do listy zadań zależnych** etykiety.

17. Zaznacz pole kombi, który właśnie został dodany.

18. W **właściwości** oknie **szerokość** właściwości **300**, a następnie kliknij przycisk **Zastosuj**.

19. Przeciągnięcie formantu CommandButton z **przybornika** do regionu formularza. Położenie przycisku polecenia, obok pola kombi.

20. Wybieranie przycisku polecenia, który właśnie został dodany.

21. W **właściwości** oknie **nazwa** do **AddDependentTask**ustaw **podpis** do **Dodaj zadanie zależne**ustaw **szerokość** do **100**, a następnie kliknij przycisk **Zastosuj**.

22. W **wybór pola**, kliknij przycisk **New**.

23. W **nowe pole** okno dialogowe, typ **formant hiddenField** w **nazwa** pola, a następnie kliknij przycisk **OK**.

24. Przeciągnij **formant hiddenField** pola z **wybór pola** do regionu formularza.

25. W **właściwości** oknie **Visible** do **0 - FAŁSZ**, a następnie kliknij przycisk **Zastosuj**.

26. W programie Outlook na **Developer** na karcie **projektu** grupy, kliknij przycisk **Zapisz** przycisk, a następnie kliknij przycisk **Zapisz regionu formularza jako**.

     Nazwa regionu formularza **TaskFormRegion** i zapisz go w lokalnym katalogu na komputerze.

     Outlook zapisuje regionu formularza jako magazynu formularzy programu Outlook (*OFS*) pliku. Region formularza zostaje zapisana wraz z nazwą *TaskFormRegion.ofs*.

27. Zamknij program Outlook.

## <a name="create-a-new-outlook-add-in-project"></a>Utwórz nowy projekt dodatku programu Outlook
 W tym kroku utworzysz projekt dodatku narzędzi VSTO dla programu Outlook. W dalszej części tego przewodnika zostaną zaimportowane regionu formularza do projektu.

### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>Aby utworzyć nowy projekt dodatku narzędzi VSTO dla programu Outlook

1.  W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], Utwórz projekt dodatku narzędzi VSTO dla programu Outlook o nazwie **TaskAddIn**.

2.  W **nowy projekt** okno dialogowe, wybierz opcję **Utwórz katalog rozwiązania**.

3.  Zapisz projekt do domyślnego katalogu projektu.

     Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="import-the-form-region"></a>Importowanie regionów formularzy
 Możesz zaimportować regionu formularza zaprojektowanego w programie Outlook w projekcie dodatku narzędzi VSTO dla programu Outlook przy użyciu **nowy Region formularza programu Outlook** kreatora.

### <a name="to-import-the-form-region-into-the-outlook-vsto-add-in-project"></a>Aby zaimportować regionu formularza do projektu dodatku narzędzi VSTO dla programu Outlook

1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **TaskAddIn** projekt, wskaż opcję **Dodaj**, a następnie kliknij przycisk **nowy element**.

2.  W **szablony** okienku wybierz **Region formularza programu Outlook**, nadaj plikowi nazwę **TaskFormRegion**, a następnie kliknij przycisk **Dodaj**.

     **Regionu formularza NewOutlook** uruchamiany jest Kreator.

3.  Na **wybierz sposób tworzenia regionu formularza** kliknij **importowanie magazynu formularzy programu Outlook (ofs) pliku**, a następnie kliknij przycisk **Przeglądaj**.

4.  W **istniejącej lokalizacji pliku regionu formularza programu Outlook** okno dialogowe, przejdź do lokalizacji *TaskFormRegion.ofs*, wybierz opcję **TaskFormRegion.ofs**, kliknij przycisk **Otwórz**, a następnie kliknij przycisk **dalej**.

5.  Na **wybierz typ regionu formularza chcesz utworzyć** kliknij **Zastąp wszystkie**, a następnie kliknij przycisk **dalej**.

     A *Zastąp wszystkie* regionu formularza zastępuje cały formularz programu Outlook. Aby uzyskać więcej informacji na temat typów regionu formularza, zobacz [regionach formularzy programu Outlook z tworzenia](../vsto/creating-outlook-form-regions.md).

6.  Na **tekst opisu i wybierz preferencje wyświetlania** kliknij **dalej**.

7.  Na **Określ klasy wiadomości, które będzie wyświetlany ten region formularza** stronie **których niestandardowych klasach wiadomości będzie wyświetlany ten region formularza** wpisz **IPM. Task.TaskFormRegion**, a następnie kliknij przycisk **Zakończ**.

     A *TaskFormRegion.cs* lub *TaskFormRegion.vb* plik zostanie dodany do projektu.

## <a name="handle-the-events-of-controls-on-the-form-region"></a>Obsługa zdarzeń formantów na region formularza
 Teraz, gdy region formularza w projekcie, możesz dodać kod, który obsługuje `Microsoft.Office.Interop.Outlook.OlkCommandButton.Click` zdarzenia przycisku, który został dodany do regionu formularza programu Outlook.

 Ponadto Dodaj kod, aby <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> zdarzenia, które aktualizuje formantów na region formularza, podczas wyświetlania regionu formularza.

### <a name="to-handle-the-events-of-controls-on-the-form-region"></a>Do obsługi zdarzeń formantów na region formularza

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy *TaskFormRegion.cs* lub *TaskFormRegion.vb*, a następnie kliknij przycisk **Wyświetl kod**.

    *TaskFormRegion.cs* lub *TaskFormRegion.vb* zostanie otwarty w edytorze kodu.

2. Dodaj następujący kod do `TaskFormRegion` klasy. Ten kod powoduje wypełnienie pola kombi na region formularza wiersza tematu każdego zadania w folderze zadania programu Outlook.

    [!code-csharp[Trin_Outlook_FR_Import#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#1)]
    [!code-vb[Trin_Outlook_FR_Import#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#1)]

3. Dodaj następujący kod do `TaskFormRegion` klasy. Kod będzie wykonywał następujące zadania:

   - Lokalizuje `Microsoft.Office.Interop.Outlook.TaskItem` w folderze zadań, wywołując `FindTaskBySubjectName` metody pomocnika i przekazanie przedmiotem odpowiednie zadanie. Należy dodać `FindTaskBySubjectName` metody pomocnika w następnym kroku.

   - Dodaje `Microsoft.Office.Interop.Outlook.TaskItem.Subject` i `Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete` wartości do pola listy zadanie zależne.

   - Dodaje temat zadania ukryte pole na region formularza. Ukryte pole te wartości są przechowywane jako część elementu programu Outlook.

     [!code-csharp[Trin_Outlook_FR_Import#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#2)]
     [!code-vb[Trin_Outlook_FR_Import#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#2)]

4. Dodaj następujący kod do `TaskFormRegion` klasy. Ten kod zawiera metody pomocnika `FindTaskBySubjectName` który został opisany w poprzednim kroku.

    [!code-csharp[Trin_Outlook_FR_Import#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#3)]
    [!code-vb[Trin_Outlook_FR_Import#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#3)]

5. Dodaj następujący kod do `TaskFormRegion` klasy. Kod będzie wykonywał następujące zadania:

   - Odświeża pola listy na region formularza o bieżący stan ukończenia każdego zadania zależne.

   - Analizuje tekstu ukrytego pola uzyskać podmiotu każdego zadania zależne. Następnie klient zlokalizuje każdego `Microsoft.Office.Interop.Outlook.TaskItem` w *zadania* folderu przez wywołanie metody `FindTaskBySubjectName` metody pomocnika i przekazanie podmiotu każdego zadania.

   - Dodaje `Microsoft.Office.Interop.Outlook.TaskItem.Subject` i `Microsoft.Office.Interop.Outlook.TaskItem.PercentComplete` wartości do pola listy zadanie zależne.

     [!code-csharp[Trin_Outlook_FR_Import#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#4)]
     [!code-vb[Trin_Outlook_FR_Import#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#4)]

6. Zastąp `TaskFormRegion_FormRegionShowing` programu obsługi zdarzeń z następującym kodem. Kod będzie wykonywał następujące zadania:

   - Wypełnia pola kombi na region formularza za pomocą zadań przedmioty, podczas wyświetlania regionu formularza.

   - Wywołania `RefreshTaskListBox` metody pomocnika, podczas wyświetlania regionu formularza. Spowoduje to wyświetlenie zależne zadania, które zostały dodane do pola listy, jeśli element został wcześniej otwarty.

     [!code-csharp[Trin_Outlook_FR_Import#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Import/TaskFormRegion.cs#5)]
     [!code-vb[Trin_Outlook_FR_Import#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Import_O12/TaskFormRegion.vb#5)]

## <a name="test-the-outlook-form-region"></a>Testowanie region formularza programu Outlook
 Aby przetestować regionu formularza, Dodaj zadania do listy wymagań wstępnych zadań na region formularza. Zaktualizuj stan ukończenia zadań wstępne, a następnie Wyświetl stan ukończenia zaktualizowane zadanie na liście zadań wstępne.

### <a name="to-test-the-form-region"></a>Aby przetestować region formularza

1.  Naciśnij klawisz **F5** Aby uruchomić projekt.

     Uruchamia program Outlook.

2.  W programie Outlook na **Home** kliknij pozycję **nowe elementy**, a następnie kliknij przycisk **zadań**.

3.  W formularzu zadania wpisz **zadanie zależne** w **podmiotu** pola.

4.  Na **zadań** karty wstążki w **akcje** grupy, kliknij przycisk **Zapisz i Zamknij**.

5.  W programie Outlook na **Home** kliknij pozycję **nowe elementy**, kliknij przycisk **więcej elementów**, a następnie kliknij przycisk **wybierz formularz**.

6.  W **wybierz formularz** okno dialogowe, kliknij przycisk **TaskFormRegion**, a następnie kliknij przycisk **Otwórz**.

     **TaskFormRegion** wyświetlania regionu formularza. Ten formularz, zastępuje formularza całego zadania. **Wybierz zadanie do dodania do listy zadań zależnych** pola kombi jest wypełniana przy użyciu innych zadań w folderze zadania.

7.  W formularzu zadania w **podmiotu** wpisz **głównym zadaniem**.

8.  W **wybierz zadanie do dodania do listy zadań zależnych** pola kombi, wybierz **zadanie zależne**, a następnie kliknij przycisk **Dodaj zadanie zależne**.

     **0% Complete — zadanie zależne** pojawia się w **to zadanie jest zależna od następujących zadań** pola listy. Oznacza to, że możesz pomyślnie obsłużony `Microsoft.Office.Interop.Outlook.OlkCommandButton.Click` zdarzenia przycisku.

9. Zapisz i Zamknij **głównym zadaniem** elementu.

10. Otwórz element zależnego zadania w programie Outlook.

11. Zmień na formularzu zadania zależne **% Complete** pole **50%**.

12. Na **zadań** karty wstążki zadania zależne w **akcje** grupy, kliknij przycisk **Zapisz i Zamknij**.

13. Otwórz ponownie **głównym zadaniem** element w programie Outlook.

     **50% Complete — zadanie zależne** pojawi się w **to zadanie jest zależna od następujących zadań** pola listy.

## <a name="next-steps"></a>Następne kroki
 Możesz dowiedzieć się więcej na temat sposobu dostosowywania interfejsu użytkownika aplikacji Outlook w tych tematach:

-   Aby dowiedzieć się więcej na temat Zaprojektuj wygląd regionu formularza przeciągania zarządzanych kontrolki do wizualnego projektanta, zobacz [instruktażu: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).

-   Aby dowiedzieć się więcej na temat dostosowywania na Wstążce elementu programu Outlook, zobacz [Dostosuj Wstążkę dla programu Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

-   Aby dowiedzieć się więcej na temat sposobu dodawania niestandardowego okienka zadań do programu Outlook, zobacz [niestandardowych okienek zadań](../vsto/custom-task-panes.md).

## <a name="see-also"></a>Zobacz także
- [Dostęp do regionów formularzy w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md)
- [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)
- [Wytyczne dotyczące tworzenia regionów formularzy programu Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Przewodnik: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Instrukcje: Dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Niestandardowe akcje w regionach formularzy programu Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
- [Instrukcje: Ochrona programu Outlook przed wyświetlaniem regionów formularzy](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
