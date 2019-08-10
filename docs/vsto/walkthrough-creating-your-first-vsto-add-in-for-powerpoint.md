---
title: 'Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu PowerPoint'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- PowerPoint [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9bba8095c1e79b8ab8addfd69afc1e89a50e3fce
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871953"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-powerpoint"></a>Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu PowerPoint
  W tym instruktażu pokazano, jak utworzyć dodatek narzędzi VSTO dla programu Microsoft Office PowerPoint. Funkcje, które tworzysz w tym rodzaju rozwiązanie, są dostępne dla samej aplikacji, niezależnie od tego, które prezentacje są otwarte. Aby uzyskać więcej informacji, zobacz temat [Tworzenie rozwiązań &#40;pakietu&#41;Office — Omówienie programu VSTO](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie projektu dodatku VSTO dla programu PowerPoint dla programu PowerPoint.

- Pisanie kodu, który używa modelu obiektów programu PowerPoint do dodawania pola tekstowego do każdego nowego slajdu.

- Kompilowanie i uruchamianie projektu w celu jego przetestowania.

- Czyszczenie projektu, aby dodatek VSTO nie był już automatycznie uruchamiany na komputerze deweloperskim.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- PowerPoint

## <a name="create-the-project"></a>Utwórz projekt

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

3. W okienku szablony rozwiń pozycję **Wizualizacja C#**  lub **Visual Basic**, a następnie rozwiń węzeł **Office/SharePoint**.

4. W rozwiniętym węźle **Office/SharePoint** wybierz węzeł **Dodatki pakietu Office** .

5. Na liście szablonów projektu wybierz projekt dodatku VSTO dla programu PowerPoint.

6. W polu **Nazwa** wpisz **FirstPowerPointAddIn**.

7. Kliknij przycisk **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]tworzy projekt **FirstPowerPointAddIn** i otwiera plik kodu **ThisAddIn** w edytorze.

## <a name="write-code-that-adds-text-to-each-new-slide"></a>Napisz kod, który dodaje tekst do każdego nowego slajdu
 Następnie Dodaj kod do pliku kodu ThisAddIn. Nowy kod używa modelu obiektów programu PowerPoint do dodawania pola tekstowego do każdego nowego slajdu. Domyślnie plik kodu ThisAddIn zawiera następujący wygenerowany kod:

- Częściowa definicja `ThisAddIn` klasy. Ta klasa udostępnia punkt wejścia dla kodu i zapewnia dostęp do modelu obiektów programu PowerPoint. Aby uzyskać więcej informacji, zobacz [dodatki narzędzi VSTO dla programu](../vsto/programming-vsto-add-ins.md). Pozostała część `ThisAddIn` klasy jest zdefiniowana w ukrytym pliku kodu, który nie powinien być modyfikowany.

- Programy obsługi `ThisAddIn_Shutdown` zdarzeń i.`ThisAddIn_Startup` Te programy obsługi zdarzeń są wywoływane, gdy program PowerPoint ładuje i zwalnia dodatek narzędzi VSTO. Te programy obsługi zdarzeń umożliwiają zainicjowanie dodatku VSTO podczas ładowania i oczyszczenie zasobów używanych przez dodatek VSTO po jego wyładowaniu. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

### <a name="to-add-a-text-box-to-each-new-slide"></a>Aby dodać pole tekstowe do każdego nowego slajdu

1. W pliku kodu ThisAddIn Dodaj następujący kod do `ThisAddIn` klasy. Ten kod definiuje procedurę obsługi zdarzeń dla zdarzenia [Microsoft. Office. Interop. PowerPoint. EApplication_Event. PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) obiektu [Application](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) .

    Gdy użytkownik doda nowy slajd do aktywnej prezentacji, ten program obsługi zdarzeń dodaje pole tekstowe na początku nowego slajdu i dodaje jakiś tekst do pola tekstowego.

    [!code-vb[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_PowerPointAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#1)]

2. Jeśli używasz programu C#, Dodaj następujący kod do `ThisAddIn_Startup` programu obsługi zdarzeń. Ten kod jest wymagany do nawiązania `Application_PresentationNewSlide` połączenia z programem obsługi zdarzeń przy użyciu zdarzenia [Microsoft. Office. Interop. PowerPoint. EApplication_Event. PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) .

    [!code-csharp[Trin_PowerPointAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#2)]

   Aby zmodyfikować poszczególne nowe slajdy, poprzednie przykłady kodu używają następujących obiektów:

- `Application` Pole`ThisAddIn` klasy. Pole zwraca obiekt aplikacji, który reprezentuje bieżące wystąpienie programu PowerPoint. [](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) `Application`

- Parametr programu obsługi zdarzeń dla zdarzenia [Microsoft. Office. Interop. PowerPoint. EApplication_Event. PresentationNewSlide.](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) `Sld` Parametr jest obiektem slajdu, który reprezentuje nowy slajd. [](/previous-versions/office/developer/office-2010/ff763417(v=office.14)) `Sld` Aby uzyskać więcej informacji, zobacz [rozwiązania programu PowerPoint](../vsto/powerpoint-solutions.md).

## <a name="test-the-project"></a>Testowanie projektu
 Podczas kompilowania i uruchamiania projektu, sprawdź, czy pole tekstowe pojawia się w nowych slajdach dodawanych do prezentacji.

### <a name="to-test-the-project"></a>Aby przetestować projekt

1. Naciśnij klawisz **F5** , aby skompilować i uruchomić projekt.

     Podczas kompilowania projektu, kod jest kompilowany do zestawu, który jest umieszczony w folderze danych wyjściowych kompilacji dla projektu. Program Visual Studio tworzy również zestaw wpisów rejestru, które umożliwiają programowi PowerPoint odnajdywanie i ładowanie dodatku VSTO oraz Konfigurowanie ustawień zabezpieczeń na komputerze deweloperskim, aby umożliwić uruchomienie dodatku VSTO. Aby uzyskać więcej informacji, zobacz [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md).

2. W programie PowerPoint Dodaj nowy slajd do aktywnej prezentacji.

3. Sprawdź, czy do nowego pola tekstowego w górnej części slajdu zostanie dodany następujący tekst.

     **Ten tekst został dodany za pomocą kodu.**

4. Zamknij program PowerPoint.

## <a name="clean-up-the-project"></a>Wyczyść projekt
 Po zakończeniu opracowywania projektu, Usuń zestaw dodatków VSTO, wpisy rejestru i ustawienia zabezpieczeń z komputera deweloperskiego. W przeciwnym razie dodatek VSTO zostanie uruchomiony za każdym razem, gdy otworzysz program PowerPoint na komputerze deweloperskim.

### <a name="to-clean-up-your-project"></a>Aby oczyścić projekt

1. W programie Visual Studio w menu **kompilacja** kliknij pozycję **czyste rozwiązanie**.

## <a name="next-steps"></a>Następne kroki
 Po utworzeniu podstawowego dodatku narzędzi VSTO dla programu PowerPoint można dowiedzieć się więcej na temat opracowywania dodatków VSTO z następujących tematów:

- Ogólne zadania programistyczne, które można wykonywać w dodatkach narzędzi VSTO dla programu PowerPoint. Aby uzyskać więcej informacji, zobacz [dodatki narzędzi VSTO dla programu](../vsto/programming-vsto-add-ins.md).

- Korzystanie z modelu obiektów programu PowerPoint. Aby uzyskać więcej informacji, zobacz [rozwiązania programu PowerPoint](../vsto/powerpoint-solutions.md).

- Dostosowywanie interfejsu użytkownika programu PowerPoint, na przykład przez dodanie karty niestandardowej do wstążki lub utworzenie własnego niestandardowego okienka zadań. Aby uzyskać więcej informacji, zobacz temat [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

- Kompilowanie i debugowanie dodatków VSTO dla programu PowerPoint. Aby uzyskać więcej informacji, zobacz [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md).

- Wdrażanie dodatków VSTO dla programu PowerPoint. Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązania biurowego](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Zobacz także
- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)
- [Rozwiązania programu PowerPoint](../vsto/powerpoint-solutions.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)
- [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md)
- [Szablony projektów pakietu Office — omówienie](../vsto/office-project-templates-overview.md)
