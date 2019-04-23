---
title: 'Przewodnik: Tworzenie swojej pierwszej dodatku narzędzi VSTO dla projektu'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4a84d295a47d3391f27e7101ad815dca0c910aa6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60098795"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-project"></a>Przewodnik: Tworzenie swojej pierwszej dodatku narzędzi VSTO dla projektu
  W tym instruktażu przedstawiono sposób tworzenia dodatku narzędzi VSTO dla programu Microsoft Office Project. Funkcje, które tworzysz w tego rodzaju rozwiązania są dostępne dla aplikacji, niezależnie od tego, które są otwarte projekty. Aby uzyskać więcej informacji, zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie projektu dodatku narzędzi VSTO projektu.

- Pisanie kodu, który używa modelu obiektu projektu, aby dodać zadanie do nowego projektu.

- Tworzenie i uruchamianie projektu, aby ją przetestować.

- Czyszczenie zakończone projektu tak, aby dodatku narzędzi VSTO już nie uruchamia automatycznie na komputerze deweloperskim.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] lub [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)].

## <a name="create-the-project"></a>Utwórz projekt

### <a name="to-create-a-new-project-in-visual-studio"></a>Aby utworzyć nowy projekt w programie Visual Studio

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.

3. W okienku szablonów, rozwiń **Visual C#** lub **języka Visual Basic**, a następnie rozwiń węzeł **Office/SharePoint**.

4. W rozwiniętym okienku **Office/SharePoint** węzeł **dodatków pakietu Office** węzła.

5. Na liście szablonów projektu wybierz **Project 2010 dodatków** lub **Project 2013 dodatków**.

6. W **nazwa** wpisz **FirstProjectAddIn**.

7. Kliknij przycisk **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tworzy **FirstProjectAddIn** projektu i otwiera **ThisAddIn** plik kodu w edytorze.

## <a name="write-code-that-adds-a-new-task-to-a-project"></a>Pisanie kodu, który dodaje nowe zadanie do projektu
 Następnie dodaj kod, aby plik kodu ThisAddIn. Nowy kod wykorzystuje model obiektu projektu można dodać nowe zadanie do projektu. Domyślnie plik kodu ThisAddIn zawiera następujące wygenerowanego kodu:

- Częściową definicję `ThisAddIn` klasy. Ta klasa udostępnia punkt wejścia dla kodu i zapewnia dostęp do modelu obiektu projektu. Aby uzyskać więcej informacji, zobacz [dodatków narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md). W pozostałej części `ThisAddIn` klasa jest zdefiniowana w pliku ukryty kod, który nie należy modyfikować.

- `ThisAddIn_Startup` i `ThisAddIn_Shutdown` procedury obsługi zdarzeń. Te procedury obsługi zdarzeń są wywoływane, gdy projekt ładuje i zwalnia dodatku narzędzi VSTO dla programów. Użyj tych programów obsługi zdarzeń, można zainicjować dodatku narzędzi VSTO dla programów, podczas jego ładowania oraz aby wyczyścić zasoby używane przez dodatek narzędzi VSTO dla programu, gdy jest zwolniony. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

### <a name="to-add-a-task-to-a-new-project"></a>Aby dodać zadanie do nowego projektu

1. W pliku kodu ThisAddIn, Dodaj następujący kod do `ThisAddIn` klasy. Ten kod definiuje zdarzenia obsługi dla `NewProject` zdarzenia `Microsoft.Office.Interop.MSProject.Application` klasy.

    Gdy użytkownik tworzy nowy projekt, ta procedura obsługi zdarzeń dodaje zadanie do projektu.

    [!code-vb[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_ProjectAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_ProjectAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#1)]

   Aby zmodyfikować projekt, w tym przykładzie kodu używane następujące obiekty:

- `Application` Pole `ThisAddIn` klasy. `Application` Pole zwraca `Microsoft.Office.Interop.MSProject.Application` reprezentujący bieżące wystąpienie projektu.

- `pj` Parametrów programu obsługi zdarzeń dla zdarzenia NewProject. `pj` Parametr `Microsoft.Office.Interop.MSProject.Project` obiektu, który reprezentuje projekt. Aby uzyskać więcej informacji, zobacz [projektu rozwiązania](../vsto/project-solutions.md).

1. Jeśli używasz języka C#, Dodaj następujący kod do `ThisAddIn_Startup` programu obsługi zdarzeń. Ten kod łączy `Application_Newproject` obsługi zdarzenia ze zdarzeniem NewProject.

     [!code-csharp[Trin_ProjectAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs#2)]

## <a name="test-the-project"></a>Projekt testowy
 Gdy skompilować i uruchomić projekt, należy sprawdzić, czy nowe zadanie jest wyświetlany w nowym projekcie wynikowym.

### <a name="to-test-the-project"></a>Aby przetestować projekt

1. Naciśnij klawisz **F5** Aby skompilować i uruchomić projekt. Programy Microsoft Project rozpoczyna się i automatycznie zostanie otwarty nowy pusty projekt.

     Gdy tworzysz projekt, kod jest kompilowany do zestawu, który znajduje się w folderze wyjściowym kompilacji dla projektu. Visual Studio tworzy również zestaw wpisów rejestru, umożliwiające projektu wykrycie i załadowanie dodatku narzędzi VSTO dla programów i konfiguruje ustawienia zabezpieczeń na komputerze deweloperskim, aby włączyć dodatek narzędzi VSTO dla programów do uruchomienia. Aby uzyskać więcej informacji, zobacz [Przegląd procesu kompilacji rozwiązania pakietu Office](/previous-versions/visualstudio/visual-studio-2010/h2c9cdc0(v=vs.100)).

2. Sprawdź, czy nowe zadanie zostanie dodane do pustego projektu.

3. Sprawdź, czy następujący tekst jest wyświetlany w **Nazwa zadania** pola zadania.

     **Ten tekst został dodany przy użyciu kodu.**

4. Zamknij program Microsoft Project.

## <a name="clean-up-the-project"></a>Czyszczenie projektu
 Po zakończeniu tworzenia projektu dodatku narzędzi VSTO zestaw, wpisy rejestru i ustawienia zabezpieczeń należy usunąć z komputera dewelopera. W przeciwnym razie dodatku narzędzi VSTO będzie uruchamiany za każdym razem Otwórz program Microsoft Project na komputerze deweloperskim.

### <a name="to-clean-up-your-project"></a>Aby wyczyścić projektu

1. W programie Visual Studio na **kompilacji** menu, kliknij przycisk **czyste rozwiązanie**.

## <a name="next-steps"></a>Następne kroki
 Teraz, gdy utworzono podstawowe dodatku narzędzi VSTO dla projektu, można dowiedzieć się więcej o tworzeniu dodatków narzędzi VSTO dla programów w tych tematach:

- Ogólnych zadań programowania, które można wykonywać w dodatków narzędzi VSTO dla projektu: [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md).

- Przy użyciu modelu obiektu projektu: [Projekt rozwiązania](../vsto/project-solutions.md).

- Kompilowanie i debugowanie dodatków narzędzi VSTO dla projektu: [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md).

- Wdrażanie dodatków narzędzi VSTO dla projektu: [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Zobacz także
- [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md)
- [Rozwiązania projektu](../vsto/project-solutions.md)
- [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)
- [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)
- [Omówienie szablonów projektu pakietu Office](../vsto/office-project-templates-overview.md)
