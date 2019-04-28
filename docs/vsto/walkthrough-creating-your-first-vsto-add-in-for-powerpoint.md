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
ms.openlocfilehash: 48b69b90c8ede6bfba4d388f547742de6d92cd7f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62981246"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-powerpoint"></a>Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu PowerPoint
  W tym instruktażu przedstawiono sposób tworzenia dodatku narzędzi VSTO dla programu Microsoft Office PowerPoint. Funkcje, które tworzysz w tego rodzaju rozwiązania są dostępne dla aplikacji, niezależnie od tego, które są otwarte prezentacji. Aby uzyskać więcej informacji, zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie projektu dodatku narzędzi VSTO dla programu PowerPoint dla programu PowerPoint.

- Pisanie kodu, który używa modelu obiektów programu PowerPoint, aby dodać pole tekstowe do każdego nowego slajdu.

- Tworzenie i uruchamianie projektu, aby ją przetestować.

- Czyszczenie projektu, tak aby dodatku narzędzi VSTO już nie uruchamia automatycznie na komputerze deweloperskim.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- PowerPoint

## <a name="create-the-project"></a>Utwórz projekt

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.

3. W okienku szablonów, rozwiń **Visual C#** lub **języka Visual Basic**, a następnie rozwiń węzeł **Office/SharePoint**.

4. W rozwiniętym okienku **Office/SharePoint** węzeł **dodatków pakietu Office** węzła.

5. Na liście szablonów projektu wybierz projekt dodatku narzędzi VSTO dla programu PowerPoint.

6. W **nazwa** wpisz **FirstPowerPointAddIn**.

7. Kliknij przycisk **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tworzy **FirstPowerPointAddIn** projektu i otwiera **ThisAddIn** plik kodu w edytorze.

## <a name="write-code-that-adds-text-to-each-new-slide"></a>Pisanie kodu, który dodaje tekst do każdego nowego slajdu
 Następnie dodaj kod, aby plik kodu ThisAddIn. Nowy kod używa modelu obiektów programu PowerPoint, aby dodać pole tekstowe do każdego nowego slajdu. Domyślnie plik kodu ThisAddIn zawiera następujące wygenerowanego kodu:

- Częściową definicję `ThisAddIn` klasy. Ta klasa udostępnia punkt wejścia dla kodu i zapewnia dostęp do modelu obiektów programu PowerPoint. Aby uzyskać więcej informacji, zobacz [dodatków narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md). W pozostałej części `ThisAddIn` klasa jest zdefiniowana w pliku ukryty kod, który nie należy modyfikować.

- `ThisAddIn_Startup` i `ThisAddIn_Shutdown` procedury obsługi zdarzeń. Te procedury obsługi zdarzeń są wywoływane, gdy program PowerPoint ładuje i zwalnia dodatku narzędzi VSTO dla programów. Użyj tych programów obsługi zdarzeń, można zainicjować dodatku narzędzi VSTO dla programów, podczas jego ładowania oraz aby wyczyścić zasoby używane przez dodatek narzędzi VSTO dla programu, gdy jest zwolniony. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

### <a name="to-add-a-text-box-to-each-new-slide"></a>Aby dodać pole tekstowe do każdego nowego slajdu

1. W pliku kodu ThisAddIn, Dodaj następujący kod do `ThisAddIn` klasy. Ten kod definiuje zdarzenia obsługi dla [Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) zdarzenia <xref:Microsoft.Office.Interop.PowerPoint.Application> obiektu.

    Gdy użytkownik dodaje nowy slajd do aktywnej prezentacji, ta procedura obsługi zdarzeń dodaje pole tekstowe na początku nowego slajdu, a następnie dodaje tekst w polu tekstowym.

    [!code-vb[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_PowerPointAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#1)]

2. Jeśli używasz języka C#, Dodaj następujący kod do `ThisAddIn_Startup` programu obsługi zdarzeń. Ten kod jest wymagane do połączenia z `Application_PresentationNewSlide` programu obsługi zdarzeń z [Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) zdarzeń.

    [!code-csharp[Trin_PowerPointAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#2)]

   Aby zmodyfikować każdego nowego slajdu, w poprzednich przykładach kodu za pomocą następujących obiektów:

- `Application` Pole `ThisAddIn` klasy. `Application` Pole zwraca <xref:Microsoft.Office.Interop.PowerPoint.Application> reprezentujący bieżące wystąpienie programu PowerPoint.

- `Sld` Parametrów programu obsługi zdarzeń [Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) zdarzeń. `Sld` Parametr <xref:Microsoft.Office.Interop.PowerPoint.Slide> obiektu, który reprezentuje nowy slajd. Aby uzyskać więcej informacji, zobacz [PowerPoint — rozwiązania](../vsto/powerpoint-solutions.md).

## <a name="test-the-project"></a>Projekt testowy
 Gdy skompilować i uruchomić projekt, należy sprawdzić, czy w polu tekstowym jest wyświetlana w nowych slajdów, które dodajesz do prezentacji.

### <a name="to-test-the-project"></a>Aby przetestować projekt

1. Naciśnij klawisz **F5** Aby skompilować i uruchomić projekt.

     Gdy tworzysz projekt, kod jest kompilowany do zestawu, który jest umieszczany w folderze wyjściowym kompilacji dla projektu. Visual Studio tworzy również zestaw wpisów rejestru, umożliwiające wykrycie i załadowanie dodatku narzędzi VSTO dla programu PowerPoint i konfiguruje ustawienia zabezpieczeń na komputerze deweloperskim, aby włączyć dodatek narzędzi VSTO dla programów do uruchomienia. Aby uzyskać więcej informacji, zobacz [rozwiązań kompilacji pakietu Office](../vsto/building-office-solutions.md).

2. W programie PowerPoint należy dodać nowy slajd do aktywnej prezentacji.

3. Sprawdź, czy następujący tekst została dodana do nowego pola tekstowego u góry slajdu.

     **Ten tekst został dodany przy użyciu kodu.**

4. Zamknij program PowerPoint.

## <a name="clean-up-the-project"></a>Czyszczenie projektu
 Po zakończeniu tworzenia projektu dodatku narzędzi VSTO zestaw, wpisy rejestru i ustawienia zabezpieczeń należy usunąć z komputera dewelopera. W przeciwnym razie dodatku narzędzi VSTO będzie uruchamiany za każdym razem otworzysz PowerPoint na komputerze deweloperskim.

### <a name="to-clean-up-your-project"></a>Aby wyczyścić projektu

1. W programie Visual Studio na **kompilacji** menu, kliknij przycisk **czyste rozwiązanie**.

## <a name="next-steps"></a>Następne kroki
 Teraz, gdy utworzono podstawowe dodatku narzędzi VSTO dla programu PowerPoint, można dowiedzieć się więcej o tworzeniu dodatków narzędzi VSTO dla programów w tych tematach:

- Ogólne zadania programowania, które można wykonywać w dodatków narzędzi VSTO dla programu PowerPoint. Aby uzyskać więcej informacji, zobacz [dodatków narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md).

- Za pomocą modelu obiektów programu PowerPoint. Aby uzyskać więcej informacji, zobacz [PowerPoint — rozwiązania](../vsto/powerpoint-solutions.md).

- Dostosowywanie interfejsu użytkownika programu PowerPoint, na przykład przez dodawanie kart niestandardowych do Wstążki lub tworzenia własnego niestandardowego okienka zadań. Aby uzyskać więcej informacji, zobacz [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

- Kompilowanie i debugowanie dodatków narzędzi VSTO dla programu PowerPoint. Aby uzyskać więcej informacji, zobacz [rozwiązań kompilacji pakietu Office](../vsto/building-office-solutions.md).

- Wdrażanie dodatków narzędzi VSTO dla programu PowerPoint. Aby uzyskać więcej informacji, zobacz [wdrożyć rozwiązanie Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Zobacz także
- [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md)
- [PowerPoint — rozwiązania](../vsto/powerpoint-solutions.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)
- [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)
- [Omówienie szablonów projektu pakietu Office](../vsto/office-project-templates-overview.md)
