---
title: 'Przewodnik: tworzenie pierwszego dodatku VSTO dla projektu'
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
ms.openlocfilehash: 48d7baf9605947818ffd79eb7312c0dbefe581ac
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824266"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-project"></a>Przewodnik: tworzenie pierwszego dodatku VSTO dla projektu
  W tym przewodniku pokazano, jak utworzyć dodatek VSTO dla Microsoft Office Project. Funkcje, które tworzysz w tego rodzaju rozwiązaniu, są dostępne dla samej aplikacji, niezależnie od tego, które projekty są otwarte. Aby uzyskać więcej informacji, zobacz [Omówienie tworzenia rozwiązań pakietu Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie projektu dodatku VSTO projektu.

- Pisanie kodu, który używa modelu obiektów project w celu dodania zadania do nowego projektu.

- Budowania i uruchamiania projektu w celu przetestowania go.

- Czyszczenie ukończonego projektu tak, aby dodatek VSTO nie był już automatycznie uruchamiany na komputerze dewelopera.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] lub [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)].

## <a name="create-the-project"></a>Tworzenie projektu

### <a name="to-create-a-new-project-in-visual-studio"></a>Aby utworzyć nowy projekt w programie Visual Studio

1. Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. W menu **File (Plik)** wskaż pozycję **New (Nowy),** a następnie kliknij pozycję **Project (Projekt).**

3. W okienku szablonów rozwiń pozycję **Visual C#** **lub Visual Basic**, a następnie rozwiń pozycję **Office/SharePoint.**

4. W rozwiniętym **węźle Office/SharePoint** wybierz węzeł Dodatki **pakietu Office.**

5. Na liście szablonów projektów wybierz pozycję **Project 2010 Add-in** lub **Project 2013 Add-in**.

6. W polu **Nazwa** wpisz **FirstProjectAddIn**.

7. Kliknij przycisk **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tworzy projekt **FirstProjectAddIn** i otwiera plik kodu **ThisAddIn** w edytorze.

## <a name="write-code-that-adds-a-new-task-to-a-project"></a>Pisanie kodu, który dodaje nowe zadanie do projektu
 Następnie dodaj kod do pliku kodu ThisAddIn. Nowy kod używa modelu obiektu Project, aby dodać nowe zadanie do projektu. Domyślnie plik kodu ThisAddIn zawiera następujący wygenerowany kod:

- Częściowa definicja `ThisAddIn` klasy. Ta klasa zapewnia punkt wejścia dla kodu i zapewnia dostęp do modelu obiektów project. Aby uzyskać więcej informacji, zobacz [Program VSTO Add-ins (Dodatki programu VSTO).](../vsto/programming-vsto-add-ins.md) Pozostała część klasy `ThisAddIn` jest zdefiniowana w ukrytym pliku kodu, który nie powinien być modyfikowany.

- Programy `ThisAddIn_Startup` obsługi zdarzeń i `ThisAddIn_Shutdown` . Te procedury obsługi zdarzeń są wywoływane, gdy projekt ładuje i zwalnia dodatek VSTO. Użyj tych programów obsługi zdarzeń, aby zainicjować dodatek VSTO podczas ładowania i wyczyścić zasoby używane przez dodatek VSTO, gdy jest zwalniany. Aby uzyskać więcej informacji, zobacz [Zdarzenia w projektach pakietu Office.](../vsto/events-in-office-projects.md)

### <a name="to-add-a-task-to-a-new-project"></a>Aby dodać zadanie do nowego projektu

1. W pliku kodu ThisAddIn dodaj następujący kod do `ThisAddIn` klasy . Ten kod definiuje program obsługi zdarzeń dla `NewProject` zdarzenia `Microsoft.Office.Interop.MSProject.Application` klasy .

    Gdy użytkownik tworzy nowy projekt, ta procedura obsługi zdarzeń dodaje zadanie do projektu.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ProjectAddInTutorial/ThisAddIn.vb" id="Snippet1":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs" id="Snippet1":::

   Aby zmodyfikować projekt, w tym przykładzie kodu używane są następujące obiekty:

- Pole `Application` klasy `ThisAddIn` . Pole `Application` zwraca `Microsoft.Office.Interop.MSProject.Application` obiekt reprezentujący bieżące wystąpienie obiektu Project.

- Parametr `pj` procedury obsługi zdarzeń dla zdarzenia NewProject. Parametr `pj` jest `Microsoft.Office.Interop.MSProject.Project` obiektem, który reprezentuje projekt. Aby uzyskać więcej informacji, zobacz [Project solutions (Rozwiązania projektu).](../vsto/project-solutions.md)

1. Jeśli używasz języka C#, dodaj następujący kod do procedury `ThisAddIn_Startup` obsługi zdarzeń. Ten kod łączy program `Application_Newproject` obsługi zdarzeń ze zdarzeniem NewProject.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ProjectAddInTutorial/ThisAddIn.cs" id="Snippet2":::

## <a name="test-the-project"></a>Testowanie projektu
 Podczas kompilowania i uruchamiania projektu sprawdź, czy nowe zadanie pojawia się w wynikowy nowy projekt.

### <a name="to-test-the-project"></a>Aby przetestować projekt

1. Naciśnij **klawisz F5,** aby skompilować i uruchomić projekt. Program Microsoft Project uruchamia i automatycznie otwiera nowy pusty projekt.

     Podczas kompilowania projektu kod jest kompilowany w zestawie, który znajduje się w folderze wyjściowym kompilacji dla projektu. Visual Studio tworzy również zestaw wpisów rejestru, które umożliwiają projektowi odnajdywanie i ładowanie dodatku VSTO, a także konfiguruje ustawienia zabezpieczeń na komputerze dewelopera, aby umożliwić uruchamianie dodatku VSTO. Aby uzyskać więcej informacji, zobacz [Office solution build process overview (Omówienie procesu kompilacji rozwiązania pakietu Office).](/previous-versions/visualstudio/visual-studio-2010/h2c9cdc0(v=vs.100))

2. Sprawdź, czy nowe zadanie zostało dodane do pustego projektu.

3. Sprawdź, czy w polu **Nazwa** zadania zadania znajduje się następujący tekst.

     **Ten tekst został dodany przy użyciu kodu.**

4. Zamknij program Microsoft Project.

## <a name="clean-up-the-project"></a>Czyszczenie projektu
 Po zakończeniu tworzenia projektu usuń zestaw dodatku VSTO, wpisy rejestru i ustawienia zabezpieczeń z komputera dewelopera. W przeciwnym razie dodatek VSTO będzie uruchamiany przy każdym otwarciu programu Microsoft Project na komputerze dewelopera.

### <a name="to-clean-up-your-project"></a>Aby wyczyścić projekt

1. W Visual Studio menu Build  (Kompilacja) kliknij pozycję **Clean Solution (Wyczyść rozwiązanie).**

## <a name="next-steps"></a>Następne kroki
 Teraz, po utworzeniu podstawowego dodatku VSTO dla projektu, możesz dowiedzieć się więcej na temat tworzenia dodatków VSTO z tych tematów:

- Ogólne zadania programistyczne, które można wykonywać w dodatki VSTO dla projektu: [Dodatki programu VSTO.](../vsto/programming-vsto-add-ins.md)

- Przy użyciu modelu obiektów Project: [Project solutions](../vsto/project-solutions.md).

- Kompilowanie i debugowanie dodatków narzędzi VSTO dla projektu: [tworzenie rozwiązań pakietu Office.](../vsto/building-office-solutions.md)

- Wdrażanie dodatków VSTO dla projektu: [wdrażanie rozwiązania pakietu Office.](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>Zobacz też
- [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md)
- [Rozwiązania projektu](../vsto/project-solutions.md)
- [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)
- [Wdrażanie rozwiązania pakietu Office](../vsto/deploying-an-office-solution.md)
- [Omówienie szablonów projektów pakietu Office](../vsto/office-project-templates-overview.md)
