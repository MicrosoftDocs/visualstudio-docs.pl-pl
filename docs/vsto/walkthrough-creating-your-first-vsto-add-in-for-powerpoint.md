---
title: 'Przewodnik: tworzenie pierwszego dodatku VSTO dla programu PowerPoint'
description: Utwórz dodatek na poziomie aplikacji dla programu Microsoft PowerPoint. Ta funkcja jest dostępna dla samej aplikacji, niezależnie od tego, które prezentacje są otwarte.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a5adf37c6d55d4704ee370052646e620cbe716c3
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824253"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-powerpoint"></a>Przewodnik: tworzenie pierwszego dodatku VSTO dla programu PowerPoint
  W tym przewodniku pokazano, jak utworzyć dodatek VSTO dla Microsoft Office PowerPoint. Funkcje, które tworzysz w tego typu rozwiązaniu, są dostępne dla samej aplikacji, niezależnie od tego, które prezentacje są otwarte. Aby uzyskać więcej informacji, zobacz Omówienie tworzenia [rozwiązań pakietu Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie projektu dodatku VSTO programu PowerPoint dla programu PowerPoint.

- Pisanie kodu, który używa modelu obiektów programu PowerPoint w celu dodania pola tekstowego do każdego nowego slajdu.

- Budowania i uruchamiania projektu w celu przetestowania go.

- Czyszczenie projektu tak, aby dodatek VSTO nie był już automatycznie uruchamiany na komputerze dewelopera.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- PowerPoint

## <a name="create-the-project"></a>Tworzenie projektu

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. W menu **File (Plik)** wskaż pozycję **New (Nowy),** a następnie kliknij pozycję **Project (Projekt).**

3. W okienku szablonów rozwiń pozycję **Visual C#** **lub Visual Basic**, a następnie rozwiń pozycję **Office/SharePoint.**

4. W rozwiniętym **węźle Office/SharePoint** wybierz węzeł **Dodatki pakietu Office.**

5. Na liście szablonów projektów wybierz projekt dodatku PowerPoint VSTO.

6. W polu **Nazwa** wpisz **FirstPowerPointAddIn**.

7. Kliknij przycisk **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tworzy projekt **FirstPowerPointAddIn** i otwiera plik kodu **ThisAddIn** w edytorze.

## <a name="write-code-that-adds-text-to-each-new-slide"></a>Pisanie kodu, który dodaje tekst do każdego nowego slajdu
 Następnie dodaj kod do pliku kodu ThisAddIn. Nowy kod używa modelu obiektów programu PowerPoint, aby dodać pole tekstowe do każdego nowego slajdu. Domyślnie plik kodu ThisAddIn zawiera następujący wygenerowany kod:

- Częściowa definicja `ThisAddIn` klasy. Ta klasa zapewnia punkt wejścia dla kodu i zapewnia dostęp do modelu obiektów programu PowerPoint. Aby uzyskać więcej informacji, zobacz [Program VSTO Add-ins (Dodatki programu VSTO).](../vsto/programming-vsto-add-ins.md) Pozostała część klasy `ThisAddIn` jest zdefiniowana w ukrytym pliku kodu, który nie powinien być modyfikowany.

- Programy `ThisAddIn_Startup` `ThisAddIn_Shutdown` obsługi zdarzeń i . Te procedury obsługi zdarzeń są wywoływane, gdy program PowerPoint ładuje i zwalnia dodatek VSTO. Użyj tych programów obsługi zdarzeń, aby zainicjować dodatek VSTO podczas ładowania i wyczyścić zasoby używane przez dodatek VSTO, gdy zostanie zwolniony. Aby uzyskać więcej informacji, zobacz [Zdarzenia w projektach pakietu Office.](../vsto/events-in-office-projects.md)

### <a name="to-add-a-text-box-to-each-new-slide"></a>Aby dodać pole tekstowe do każdego nowego slajdu

1. W pliku kodu ThisAddIn dodaj następujący kod do `ThisAddIn` klasy . Ten kod definiuje program obsługi zdarzeń dla [zdarzenia Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) obiektu [Application.](/previous-versions/office/developer/office-2010/ff764034(v=office.14))

    Gdy użytkownik dodaje nowy slajd do aktywnej prezentacji, ta procedura obsługi zdarzeń dodaje pole tekstowe na początku nowego slajdu i dodaje tekst do pola tekstowego.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_PowerPointAddInTutorial/ThisAddIn.vb" id="Snippet1":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs" id="Snippet1":::

2. Jeśli używasz języka C#, dodaj następujący kod do procedury `ThisAddIn_Startup` obsługi zdarzeń. Ten kod jest wymagany do połączenia programu obsługi zdarzeń ze `Application_PresentationNewSlide` [zdarzeniem Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide.](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14))

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs" id="Snippet2":::

   Aby zmodyfikować każdy nowy slajd, poprzednie przykłady kodu używają następujących obiektów:

- Pole `Application` klasy `ThisAddIn` . Pole `Application` zwraca obiekt [Application,](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) który reprezentuje bieżące wystąpienie programu PowerPoint.

- Parametr `Sld` programu obsługi zdarzeń dla zdarzenia [Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide.](/previous-versions/office/developer/office-2010/ff762876(v%3doffice.14)) Parametr `Sld` jest [obiektem slide,](/previous-versions/office/developer/office-2010/ff763417(v=office.14)) który reprezentuje nowy slajd. Aby uzyskać więcej informacji, zobacz [Rozwiązania programu PowerPoint.](../vsto/powerpoint-solutions.md)

## <a name="test-the-project"></a>Testowanie projektu
 Podczas kompilowania i uruchamiania projektu sprawdź, czy pole tekstowe jest wyświetlane na nowych slajdach, które dodajesz do prezentacji.

### <a name="to-test-the-project"></a>Aby przetestować projekt

1. Naciśnij **klawisz F5,** aby skompilować i uruchomić projekt.

     Podczas kompilowania projektu kod jest kompilowany do zestawu, który jest umieszczany w folderze danych wyjściowych kompilacji dla projektu. Visual Studio tworzy również zestaw wpisów rejestru, które umożliwiają programowi PowerPoint odnajdywanie i ładowanie dodatku VSTO, a także konfiguruje ustawienia zabezpieczeń na komputerze dewelopera, aby umożliwić uruchamianie dodatku VSTO. Aby uzyskać więcej informacji, zobacz [Build Office solutions (Tworzenie rozwiązań pakietu Office).](../vsto/building-office-solutions.md)

2. W programie PowerPoint dodaj nowy slajd do aktywnej prezentacji.

3. Sprawdź, czy poniższy tekst został dodany do nowego pola tekstowego w górnej części slajdu.

     **Ten tekst został dodany przy użyciu kodu.**

4. Zamknij program PowerPoint.

## <a name="clean-up-the-project"></a>Czyszczenie projektu
 Po zakończeniu tworzenia projektu usuń zestaw dodatku VSTO, wpisy rejestru i ustawienia zabezpieczeń z komputera dewelopera. W przeciwnym razie dodatek VSTO będzie uruchamiany przy każdym otwarciu programu PowerPoint na komputerze dewelopera.

### <a name="to-clean-up-your-project"></a>Aby wyczyścić projekt

1. W Visual Studio menu **Build (Kompilacja)** kliknij pozycję **Clean Solution (Wyczyść rozwiązanie).**

## <a name="next-steps"></a>Następne kroki
 Po utworzeniu podstawowego dodatku VSTO dla programu PowerPoint możesz dowiedzieć się więcej na temat sposobu tworzenia dodatków VSTO z tych tematów:

- Ogólne zadania programistyczne, które można wykonywać w dodatki VSTO dla programu PowerPoint. Aby uzyskać więcej informacji, zobacz [Program VSTO Add-ins (Dodatki programu VSTO).](../vsto/programming-vsto-add-ins.md)

- Korzystanie z modelu obiektów programu PowerPoint. Aby uzyskać więcej informacji, zobacz [Rozwiązania programu PowerPoint.](../vsto/powerpoint-solutions.md)

- Dostosowywanie interfejsu użytkownika programu PowerPoint, na przykład przez dodanie karty niestandardowej do wstążki lub utworzenie własnego niestandardowego okienka zadań. Aby uzyskać więcej informacji, zobacz [Dostosowywanie interfejsu użytkownika pakietu Office.](../vsto/office-ui-customization.md)

- Budowania i debugowania dodatków narzędzi VSTO dla programu PowerPoint. Aby uzyskać więcej informacji, zobacz [Build Office solutions (Tworzenie rozwiązań pakietu Office).](../vsto/building-office-solutions.md)

- Wdrażanie dodatków VSTO dla programu PowerPoint. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozwiązania pakietu Office.](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>Zobacz też
- [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md)
- [Rozwiązania programu PowerPoint](../vsto/powerpoint-solutions.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)
- [Wdrażanie rozwiązania pakietu Office](../vsto/deploying-an-office-solution.md)
- [Omówienie szablonów projektów pakietu Office](../vsto/office-project-templates-overview.md)
