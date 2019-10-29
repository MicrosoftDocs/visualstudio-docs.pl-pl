---
title: 'Przewodnik: wdrażanie definicji Lista zadań projektu | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 854037d096ceac01969bcb0ec2e074f4cd24a2f3
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983861"
---
# <a name="walkthrough-deploy-a-project-task-list-definition"></a>Przewodnik: wdrażanie definicji listy zadań projektu

W tym instruktażu pokazano, jak za pomocą [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] tworzyć, dostosowywać, debugować i wdrażać listę programu SharePoint w celu śledzenia zadań projektu.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne

- Obsługiwane wersje systemu Microsoft Windows i programu SharePoint.

- Program Visual Studio 2017 lub Azure DevOps Services.

## <a name="create-a-sharepoint-list"></a>Utwórz listę programu SharePoint

Utwórz projekt listy programu SharePoint i skojarz definicję listy z zadaniami.

1. Otwórz okno dialogowe **Nowy projekt** , rozwiń węzeł **SharePoint** , a następnie wybierz węzeł **2010** .

2. W okienku **Szablony** wybierz szablon **projektu programu SharePoint 2010** , nazwij projekt **ProjectTaskList**, a następnie wybierz przycisk **OK** .

     Zostanie wyświetlony **Kreator dostosowania programu SharePoint** .

3. Określ lokalną witrynę programu SharePoint, która będzie używana do debugowania, wybierz przycisk opcji **Wdróż jako farmę** , a następnie wybierz przycisk **Zakończ** .

4. Otwórz menu skrótów dla projektu, a następnie wybierz **dodaj** > **nowy element**.

5. W okienku **Szablony** wybierz szablon **listy** , a następnie wybierz przycisk **Dodaj** .

     Zostanie wyświetlony **Kreator dostosowania programu SharePoint** .

6. W polu **Nazwa, która ma być wyświetlana dla listy?** wpisz **Lista zadań projektu**.

7. Wybierz opcję **Utwórz niedostosowywalną listę na podstawie istniejącego typu listy** , a następnie na liście wybierz pozycję **zadania**, a następnie wybierz przycisk **Zakończ** .

     Lista, funkcja i pakiet pojawiają się w **Eksplorator rozwiązań**.

## <a name="add-an-event-receiver"></a>Dodawanie odbiorcy zdarzeń

Na liście zadań można dodać odbiorcę zdarzeń, który automatycznie ustawia datę i opis zadania. Poniższa procedura dodaje prostą obsługę zdarzeń do wystąpienia listy jako odbiorcę zdarzeń.

1. Otwórz menu skrótów dla węzła projektu, wybierz **Dodaj**, a następnie wybierz **nowy element**.

2. Na liście szablonów programu SharePoint wybierz szablon **odbiorcy zdarzeń** , a następnie nadaj mu nazwę **ProjectTaskListEventReceiver**.

     Zostanie wyświetlony **Kreator dostosowania programu SharePoint** .

3. Na stronie **Wybierz ustawienia odbiorcy zdarzeń** wybierz pozycję **Wyświetl zdarzenia elementów** jako typ odbiorcy zdarzenia w polu Typ odbiorcy **zdarzeń, którego chcesz użyć** .

4. W polu **jaki element powinien być listą źródeł zdarzeń** wybierz pozycję **zadania**.

5. Na liście zdarzeń do obsłużenia zaznacz pole wyboru obok **elementu**, a następnie wybierz przycisk **Zakończ** .

     Do projektu zostanie dodany nowy węzeł odbiorcy zdarzeń z plikiem kodu o nazwie **ProjectTaskListEventReceiver**.

6. Dodaj kod do metody `ItemAdded` w pliku kodu **ProjectTaskListEventReceiver** . Za każdym razem, gdy nowe zadanie zostanie dodane, do zadania zostanie dodany domyślny termin ukończenia i opis. Domyślna Data ukończenia to 1 lipca 2009.

     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]
     [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]

## <a name="customize-the-project-task-list-feature"></a>Dostosowywanie funkcji listy zadań projektu

Podczas tworzenia rozwiązania programu SharePoint program Visual Studio automatycznie tworzy funkcje dla domyślnych elementów projektu. Możesz dostosować ustawienia listy zadań projektu dla witryny programu SharePoint za pomocą projektanta funkcji.

1. W **Eksplorator rozwiązań**rozwiń pozycję **funkcje**.

2. Otwórz menu skrótów dla **Feature1**, a następnie wybierz polecenie **Projektant widoków**.

3. W polu **tytuł** wprowadź wartość **Lista zadań projektu**.

4. Z listy **zakres** wybierz pozycję **Sieć Web**.

5. W oknie **Właściwości** wpisz **1.0.0.0** jako wartość właściwości **Version** .

## <a name="customize-the-project-task-list-package"></a>Dostosowywanie pakietu listy zadań projektu

Podczas tworzenia projektu programu SharePoint program Visual Studio automatycznie dodaje funkcje, które zawierają domyślne elementy projektu do pakietu. Możesz dostosować ustawienia listy zadań projektu dla witryny programu SharePoint za pomocą projektanta pakietów.

1. W **SolutionExplorer**, otwórz menu skrótów dla **pakietu**, a następnie wybierz polecenie **Projektant widoków**.

2. W polu **Nazwa** wprowadź **ProjectTaskListPackage**.

3. Zaznacz pole wyboru **Resetuj serwer sieci Web** .

## <a name="build-and-test-the-project-task-list"></a>Kompiluj i Testuj listę zadań projektu

Po uruchomieniu projektu zostanie otwarta witryna programu SharePoint. Należy jednak ręcznie przejść do lokalizacji listy zadań.

1. Wybierz klawisz **F5** , aby skompilować i wdrożyć listę zadań projektu.

     Zostanie otwarta witryna programu SharePoint.

2. Wybierz kartę **Narzędzia główne** .

3. Na lewym pasku bocznym wybierz łącze **Lista zadań projektu** .

     Zostanie wyświetlona strona Lista zadań projektu.

4. Na karcie **Narzędzia listy** wybierz kartę **elementy** .

5. W grupie **Items (elementy** ) wybierz przycisk **nowy element** .

6. W polu tekstowym **tytuł** wprowadź **Task1**.

7. Wybierz przycisk **Zapisz** .

     Po odświeżeniu lokacji zostanie wyświetlone zadanie **Task1** z datą ukończenia 7/1/2009.

8. Wybierz **Task1**.

     Zostanie wyświetlony szczegółowy widok zadania, a opis przedstawia "to zadanie krytyczne".

## <a name="deploy-the-project-task-list"></a>Wdrażanie listy zadań projektu

Po skompilowaniu i przetestowaniu listy zadań projektu można wdrożyć ją w *systemie lokalnym* lub *zdalnym*. System lokalny jest tym samym komputerze, na którym opracowano rozwiązanie, natomiast system zdalny jest innym komputerem.

### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>Aby wdrożyć listę zadań projektu w systemie lokalnym

Na pasku menu programu Visual Studio wybierz pozycję **kompilacja** > **Wdróż rozwiązanie**.

Program Visual Studio odtwarza pulę aplikacji usług IIS, wycofuje wszystkie istniejące wersje rozwiązania, kopiuje plik pakietu rozwiązań (*wsp*) do programu SharePoint, a następnie aktywuje jego funkcje. Możesz teraz używać rozwiązania w programie SharePoint. Aby uzyskać więcej informacji na temat kroków konfiguracji wdrożenia, zobacz [How to: Edit a SharePoint Deployment Configuration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>Aby wdrożyć listę zadań projektu w systemie zdalnym

1. Na pasku menu programu Visual Studio wybierz kolejno opcje **kompiluj** > **Publikuj**.

2. W oknie dialogowym **Publikowanie** wybierz przycisk opcji **Publikuj w systemie plików** .

     Można zmienić lokalizację docelową w oknie dialogowym **Publikowanie** , wybierając ![ikonę](../sharepoint/media/ellipsisicon.gif "Ikona wielokropka") wielokropka przycisku wielokropek, a następnie przechodząc do innej lokalizacji.

3. Wybierz przycisk **Publikuj** .

     Dla rozwiązania jest tworzony plik *. wsp* .

4. Skopiuj plik *. wsp* do zdalnego systemu SharePoint.

5. Użyj polecenia `Add-SPUserSolution` programu PowerShell, aby zainstalować pakiet w zdalnej instalacji programu SharePoint. (W przypadku rozwiązań farmy Użyj `Add-SPSolution` polecenie).

     Na przykład `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`.

6. Użyj polecenia `Install-SPUserSolution` programu PowerShell, aby wdrożyć rozwiązanie. (W przypadku rozwiązań farmy Użyj `Install-SPSolution` polecenie).

     Na przykład `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`.

     Aby uzyskać więcej informacji na temat wdrażania zdalnego, zobacz [Korzystanie z rozwiązań](/previous-versions/office/developer/sharepoint-2010/ee534972(v=office.14)) i [Dodawanie i wdrażanie rozwiązań za pomocą programu PowerShell w programie SharePoint 2010](http://www.dotnetmafia.com/blogs/dotnettipoftheday/archive/2009/12/02/adding-and-deploying-solutions-with-powershell-in-sharepoint-2010.aspx).

## <a name="next-steps"></a>Następne kroki

Więcej informacji na temat dostosowywania i wdrażania rozwiązań SharePoint można znaleźć w następujących tematach:

- [Przewodnik: Tworzenie kolumny witryny, typu zawartości i listy dla programu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

- [Instrukcje: Tworzenie odbiorcy zdarzeń](../sharepoint/how-to-create-an-event-receiver.md)

- [Środowisko Windows PowerShell dla programu SharePoint Server 2010](/powershell/module/sharepoint-server/&view=sharepoint-ps)

## <a name="see-also"></a>Zobacz także
[Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
