---
title: 'Przewodnik: Wdrażanie definicji listy zadań projektu | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3df4f161eddc5d10b77887b99d93be2204821c24
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826627"
---
# <a name="walkthrough-deploy-a-project-task-list-definition"></a>Przewodnik: Wdrażanie definicji listy zadań projektu

W tym instruktażu dowiesz się, jak używać [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] do tworzenia, dostosowywania, debugowania i wdrażania listy programu SharePoint do śledzenia zadań projektu.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne

- Obsługiwane wersje systemu Microsoft Windows i programu SharePoint.

- Program Visual Studio 2017 lub usługi Azure DevOps.

## <a name="create-a-sharepoint-list"></a>Utwórz listę programu SharePoint

Utwórz projekt z listy programu SharePoint i kojarzenie definicji listy zadań.

1. Otwórz **nowy projekt** okna dialogowego rozwiń **SharePoint** węzła, a następnie wybierz **2010** węzła.

2. W **szablony** okienku wybierz **projekt programu SharePoint 2010** szablonu, nazwę projektu **ProjectTaskList**, a następnie wybierz **OK**przycisku.

     **Kreator ustawień niestandardowych SharePoint** pojawia się.

3. Określ lokalnej witryny programu SharePoint, których używasz do debugowania, wybierz **Wdróż jako rozwiązanie farmy** przycisk opcji, a następnie wybierz **Zakończ** przycisku.

4. Otwórz menu skrótów dla projektu, a następnie wybierz **Dodaj** > **nowy element**.

5. W **szablony** okienku wybierz **listy** szablonu, a następnie wybierz **Dodaj** przycisku.

     **Kreator ustawień niestandardowych SharePoint** pojawia się.

6. W **jaką nazwę chcesz wyświetlić listy?** wprowadź **listy zadań projektu**.

7. Wybierz **tworzenie dostosowywać listy na podstawie istniejącego typu listy** przycisk opcji, a następnie na liście, wybierz **zadania**, a następnie wybierz **Zakończ** przycisku.

     Lista funkcji i pakietów są wyświetlane w **Eksploratora rozwiązań**.

## <a name="add-an-event-receiver"></a>Dodaj odbiorcę zdarzeń

Na liście zadań, można dodać odbiorcy zdarzeń, która automatycznie ustawia termin przypada daty i opis zadania. Poniższa procedura dodaje program obsługi zdarzenia prostego do wystąpienia listy jako odbiorca zdarzenia.

1. Otwórz menu skrótów dla węzła projektu, wybierz polecenie **Dodaj**, a następnie wybierz **nowy element**.

2. Na liście szablonów programu SharePoint, wybierz opcję **odbiorcy zdarzeń** szablonu, a następnie nadaj mu **ProjectTaskListEventReceiver**.

     **Kreator ustawień niestandardowych SharePoint** pojawia się.

3. Na **Wybieranie ustawień odbiorcy zdarzeń** wybierz **zdarzenia elementu listy** jako typ odbiornika zdarzeń w **jakiego typu odbiorcę zdarzeń chcesz** listy.

4. W **jaki element ma być źródła zdarzeń** wybierz **zadania**.

5. Na liście zdarzeń w celu obsługi, zaznacz pole wyboru obok pozycji **dodano element**, a następnie wybierz **Zakończ** przycisku.

     Nowy węzeł odbiornik zdarzeń jest dodawany do projektu przy użyciu pliku z kodem, który nosi nazwę **ProjectTaskListEventReceiver**.

6. Dodaj kod, aby `ItemAdded` method in Class metoda **ProjectTaskListEventReceiver** pliku kodu. Każdorazowo nowe zadanie zostanie dodany, dodawany jest domyślny termin płatności i opis zadania. Domyślnie powodu data to 1 lipca 2009.

     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]
     [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]

## <a name="customize-the-project-task-list-feature"></a>Dostosowywanie funkcji listy zadań projektu

Podczas tworzenia rozwiązania programu SharePoint, programu Visual Studio automatycznie tworzy funkcje domyślne elementów projektu. Za pomocą projektanta funkcji można dostosować ustawienia listy zadań projektu witryny programu SharePoint.

1. W **Eksploratorze rozwiązań** rozwiń węzeł **Funkcje**.

2. Otwórz menu skrótów dla **Feature1**, a następnie wybierz **Projektant widoków**.

3. W **tytuł** wprowadź **funkcji listy zadań projektu**.

4. W **zakres** wybierz **Web**.

5. W **właściwości** oknie wprowadź **1.0.0.0** jako wartość pozycji **wersji** właściwości.

## <a name="customize-the-project-task-list-package"></a>Dostosowywanie pakietu listy zadań projektu

Podczas tworzenia projektu programu SharePoint, programu Visual Studio automatycznie dodaje funkcje, które zawierają domyślne elementy projektu do pakietu. Ustawienia listy zadań projektu witryny programu SharePoint można dostosować za pomocą projektanta pakietu.

1. W **SolutionExplorer**, otwórz menu skrótów dla **pakietu**, a następnie wybierz **Projektant widoków**.

2. W **nazwa** wprowadź **ProjectTaskListPackage**.

3. Wybierz **Resetuj serwer sieci Web** pole wyboru.

## <a name="build-and-test-the-project-task-list"></a>Tworzenie i testowanie listy zadań projektu

Kiedy uruchamiasz projekt, otwiera się witryna SharePoint. Jednak należy ręcznie przejdź do lokalizacji na liście zadań.

1. Wybierz **F5** klawisz, aby tworzyć i wdrażać listy zadań projektu.

     Otwiera się witryna SharePoint.

2. Wybierz **Home** kartę.

3. Na lewym pasku bocznym wybierz opcję **listy zadań projektu** łącza.

     Zostanie wyświetlona strona listy zadań projektu.

4. W **narzędzia do obsługi List** kartę, wybrać **elementów** kartę.

5. W **elementów** grupy, wybierz **nowy element** przycisku.

6. W **tytuł** tekstu wprowadź **Task1**.

7. Wybierz **Zapisz** przycisku.

     Po odświeżeniu lokacji **Task1** zostanie wyświetlone zadanie z terminem 7/1/2009.

8. Wybierz **Task1**.

     Szczegółowy widok tego zadania zostanie wyświetlone, a opis pokazuje "To jest zadanie krytyczne".

## <a name="deploy-the-project-task-list"></a>Wdrażanie z listy zadań projektu

Po utworzeniu i przetestowaniu listy zadań projektu, można wdrożyć do *systemu lokalnego* lub *systemu zdalnego*. System lokalny jest tym samym komputerze, na którym opracowała rozwiązanie, natomiast system zdalny jest inny komputer.

### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>Aby wdrożyć projekt listy zadań do systemu lokalnego

Na pasku menu programu Visual Studio, wybierz **kompilacji** > **wdrożyć rozwiązanie**.

Program Visual Studio odtwarzania puli aplikacji usług IIS, wycofuje wszystkie wersje istniejącego rozwiązania, kopiuje pakietu rozwiązania (*WSP*) pliku do programu SharePoint, a następnie aktywuje jego funkcji. Można teraz używać rozwiązania w programie SharePoint. Aby uzyskać więcej informacji na temat wdrażania, czynności konfiguracyjne, zobacz [jak: Edytowanie konfiguracji wdrażania SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>Aby wdrożyć projekt listy zadań do systemu zdalnego

1. Na pasku menu programu Visual Studio, wybierz **kompilacji** > **Publikuj**.

2. W **Publikuj** okna dialogowego wybierz **opublikowanie w systemie plików** przycisku opcji.

     Można zmienić lokalizacji docelowej w **Publikuj** okno dialogowe, wybierając przycisk wielokropka ![ikonę wielokropka](../sharepoint/media/ellipsisicon.gif "ikonę wielokropka") oraz kierując się do innej lokalizacji.

3. Wybierz **Publikuj** przycisku.

     A *.wsp* plik jest tworzony dla rozwiązania.

4. Kopiuj *.wsp* plików do systemu zdalnego programu SharePoint.

5. Za pomocą programu PowerShell `Add-SPUserSolution` polecenie, aby zainstalować pakiet w zdalnej instalacji programu SharePoint. (W przypadku rozwiązań farmy, użyj `Add-SPSolution` polecenia.)

     Na przykład `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.

6. Za pomocą programu PowerShell `Install-SPUserSolution` polecenie, aby wdrożyć rozwiązanie. (W przypadku rozwiązań farmy, użyj `Install-SPSolution` polecenia.)

     Na przykład `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`.

     Aby uzyskać więcej informacji dotyczących zdalnego wdrażania, zobacz [przy użyciu rozwiązania](http://go.microsoft.com/fwlink/?LinkId=217680) i [Dodawanie i wdrażanie rozwiązań przy użyciu programu PowerShell w programie SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=217682).

## <a name="next-steps"></a>Następne kroki

Możesz dowiedzieć się więcej na temat sposobu dostosowywania i wdrażania rozwiązań programu SharePoint z następujących tematów:

- [Przewodnik: Tworzenie kolumny witryny, typu zawartości oraz list dla SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

- [Instrukcje: Tworzenie obsługiwanego odbiornika](../sharepoint/how-to-create-an-event-receiver.md)

- [Program Windows PowerShell dla programu SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=217684)

## <a name="see-also"></a>Zobacz także
[Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
