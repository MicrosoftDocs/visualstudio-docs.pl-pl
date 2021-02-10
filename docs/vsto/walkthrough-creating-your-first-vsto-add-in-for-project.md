---
title: 'Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla projektu'
description: Utwórz dodatek na poziomie aplikacji dla programu Microsoft Project. Ta funkcja jest dostępna dla samej aplikacji, niezależnie od tego, które projekty są otwarte.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- Project [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f35649db5f61cb545bb3550980b3d6b9a8742cd3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966503"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-project"></a>Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla projektu
  W tym instruktażu pokazano, jak utworzyć dodatek Narzędzia VSTO dla Microsoft Office projektu. Funkcje, które tworzysz w tym rodzaju rozwiązanie, są dostępne dla samej aplikacji, niezależnie od tego, które projekty są otwarte. Aby uzyskać więcej informacji, zobacz [Omówienie tworzenia rozwiązań pakietu Office &#40;narzędzi VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie projektu dodatku VSTO dla projektu.

- Pisanie kodu, który używa modelu obiektów projektu do dodawania zadania do nowego projektu.

- Kompilowanie i uruchamianie projektu w celu jego przetestowania.

- Czyszczenie ukończonego projektu, aby dodatek VSTO nie był już automatycznie uruchamiany na komputerze deweloperskim.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] lub [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)].

## <a name="create-the-project"></a>Tworzenie projektu

### <a name="to-create-a-new-project-in-visual-studio"></a>Aby utworzyć nowy projekt w programie Visual Studio

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

3. W okienku szablony rozwiń pozycję **Visual C#** lub **Visual Basic**, a następnie rozwiń węzeł **Office/SharePoint**.

4. W rozwiniętym węźle **Office/SharePoint** wybierz węzeł **Dodatki pakietu Office** .

5. Na liście szablonów projektu wybierz dodatek do **projektu 2010** lub dodatek **Project 2013**.

6. W polu **Nazwa** wpisz **FirstProjectAddIn**.

7. Kliknij przycisk **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tworzy projekt **FirstProjectAddIn** i otwiera plik kodu **ThisAddIn** w edytorze.

## <a name="write-code-that-adds-a-new-task-to-a-project"></a>Napisz kod, który dodaje nowe zadanie do projektu
 Następnie Dodaj kod do pliku kodu ThisAddIn. Nowy kod używa modelu obiektów projektu, aby dodać nowe zadanie do projektu. Domyślnie plik kodu ThisAddIn zawiera następujący wygenerowany kod:

- Częściowa definicja `ThisAddIn` klasy. Ta klasa udostępnia punkt wejścia dla kodu i zapewnia dostęp do modelu obiektów projektu. Aby uzyskać więcej informacji, zobacz [dodatki narzędzi VSTO dla programu](../vsto/programming-vsto-add-ins.md). Pozostała część `ThisAddIn` klasy jest zdefiniowana w ukrytym pliku kodu, który nie powinien być modyfikowany.

- `ThisAddIn_Startup` `ThisAddIn_Shutdown` Programy obsługi zdarzeń i. Te programy obsługi zdarzeń są wywoływane podczas ładowania i zwalniania dodatku VSTO przez program Project. Te programy obsługi zdarzeń umożliwiają zainicjowanie dodatku VSTO podczas ładowania i oczyszczenie zasobów używanych przez dodatek VSTO po jego wyładowaniu. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

### <a name="to-add-a-task-to-a-new-project"></a>Aby dodać zadanie do nowego projektu

1. W pliku kodu ThisAddIn Dodaj następujący kod do `ThisAddIn` klasy. Ten kod definiuje procedurę obsługi zdarzeń dla `NewProject` zdarzenia `Microsoft.Office.Interop.MSProject.Application` klasy.

    Gdy użytkownik tworzy nowy projekt, ten program obsługi zdarzeń dodaje zadanie do projektu.

    [!code-vb[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ProjectAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#1)]

   Aby zmodyfikować projekt, w tym przykładzie kodu są stosowane następujące obiekty:

- `Application`Pole `ThisAddIn` klasy. `Application`Pole zwraca `Microsoft.Office.Interop.MSProject.Application` obiekt, który reprezentuje bieżące wystąpienie projektu.

- `pj`Parametr programu obsługi zdarzeń dla zdarzenia NewProject. `pj`Parametr jest `Microsoft.Office.Interop.MSProject.Project` obiektem, który reprezentuje projekt. Aby uzyskać więcej informacji, zobacz [Project Solutions](../vsto/project-solutions.md).

1. Jeśli używasz języka C#, Dodaj następujący kod do `ThisAddIn_Startup` programu obsługi zdarzeń. Ten kod nawiązuje połączenie `Application_Newproject` z programem obsługi zdarzeń przy użyciu zdarzenia NewProject.

     [!code-csharp[Trin_ProjectAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#2)]

## <a name="test-the-project"></a>Testowanie projektu
 Podczas kompilowania i uruchamiania projektu, upewnij się, że nowe zadanie pojawia się w powstającym nowym projekcie.

### <a name="to-test-the-project"></a>Aby przetestować projekt

1. Naciśnij klawisz **F5** , aby skompilować i uruchomić projekt. Program Microsoft Project zostanie uruchomiony i automatycznie otworzy nowy pusty projekt.

     Podczas kompilowania projektu, kod jest kompilowany do zestawu, który jest dołączony do folderu danych wyjściowych kompilacji dla projektu. Program Visual Studio tworzy również zestaw wpisów rejestru, które umożliwiają programowi Project odnalezienie i załadowanie dodatku VSTO oraz skonfigurowanie ustawień zabezpieczeń na komputerze deweloperskim w celu umożliwienia uruchomienia dodatku VSTO. Aby uzyskać więcej informacji, zobacz [Omówienie procesu tworzenia rozwiązań pakietu Office](/previous-versions/visualstudio/visual-studio-2010/h2c9cdc0(v=vs.100)).

2. Sprawdź, czy nowe zadanie zostało dodane do pustego projektu.

3. Sprawdź, czy w polu **Nazwa zadania** zadania zostanie wyświetlony następujący tekst.

     **Ten tekst został dodany za pomocą kodu.**

4. Zamknij program Microsoft Project.

## <a name="clean-up-the-project"></a>Wyczyść projekt
 Po zakończeniu opracowywania projektu, Usuń zestaw dodatków VSTO, wpisy rejestru i ustawienia zabezpieczeń z komputera deweloperskiego. W przeciwnym razie dodatek VSTO zostanie uruchomiony za każdym razem, gdy otworzysz program Microsoft Project na komputerze deweloperskim.

### <a name="to-clean-up-your-project"></a>Aby oczyścić projekt

1. W programie Visual Studio w menu **kompilacja** kliknij pozycję **czyste rozwiązanie**.

## <a name="next-steps"></a>Następne kroki
 Po utworzeniu podstawowego dodatku narzędzi VSTO dla programu Project można dowiedzieć się więcej o sposobach opracowywania dodatków VSTO z następujących tematów:

- Ogólne zadania programistyczne, które można wykonać w dodatkach narzędzi VSTO dla projektu: [programowe dodatki narzędzi VSTO](../vsto/programming-vsto-add-ins.md).

- Korzystanie z modelu obiektów projektu: [rozwiązania projektu](../vsto/project-solutions.md).

- Kompilowanie i debugowanie dodatków VSTO dla projektu: [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md).

- Wdrażanie dodatków VSTO dla projektu: [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Zobacz też
- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)
- [Rozwiązania projektu](../vsto/project-solutions.md)
- [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)
- [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md)
- [Szablony projektów pakietu Office — omówienie](../vsto/office-project-templates-overview.md)
