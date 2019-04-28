---
title: 'Przewodnik: Tworzenie swojej pierwszej dodatku narzędzi VSTO dla programu Outlook'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Outlook [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: aceab3fba1020c08382c31a2de32368e8ba12a05
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62981326"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-outlook"></a>Przewodnik: Tworzenie swojej pierwszej dodatku narzędzi VSTO dla programu Outlook
  W tym instruktażu przedstawiono sposób tworzenia dodatku narzędzi VSTO dla programu Microsoft Office Outlook. Funkcje, które tworzysz w tego rodzaju rozwiązania są dostępne dla aplikacji, niezależnie od tego, który jest otwarty elementu programu Outlook. Aby uzyskać więcej informacji, zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie projektu dodatku narzędzi VSTO dla programu Outlook dla programu Outlook.

- Pisanie kodu, który używa modelu obiektów programu Outlook do dodawania tekstu tematu i treści nową wiadomość e-mail.

- Tworzenie i uruchamianie projektu, aby ją przetestować.

- Czyszczenie zakończone projektu tak, aby dodatku narzędzi VSTO już nie uruchamia automatycznie na komputerze deweloperskim.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Program Microsoft Outlook

## <a name="create-the-project"></a>Utwórz projekt

### <a name="to-create-a-new-outlook-project-in-visual-studio"></a>Aby utworzyć nowy projekt programu Outlook w programie Visual Studio

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.

3. W okienku szablonów, rozwiń **Visual C#** lub **języka Visual Basic**, a następnie rozwiń węzeł **Office/SharePoint**.

4. W rozwiniętym okienku **Office/SharePoint** węzeł **dodatków pakietu Office** węzła.

5. Na liście szablonów projektu wybierz projekt dodatku narzędzi VSTO dla programu Outlook.

6. W **nazwa** wpisz **FirstOutlookAddIn**.

7. Kliknij przycisk **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tworzy **FirstOutlookAddIn** projektu i otwiera **ThisAddIn** plik kodu w edytorze.

## <a name="write-code-that-adds-text-to-each-new-mail-message"></a>Pisanie kodu, który dodaje tekst do każdej nowej wiadomości e-mail
 Następnie dodaj kod, aby plik kodu ThisAddIn. Nowy kod używa modelu obiektów programu Outlook, dodać tekst do każdej nowej wiadomości e-mail. Domyślnie plik kodu ThisAddIn zawiera następujące wygenerowanego kodu:

- Częściową definicję `ThisAddIn` klasy. Ta klasa udostępnia punkt wejścia dla kodu i zapewnia dostęp do modelu obiektów programu Outlook. Aby uzyskać więcej informacji, zobacz [dodatków narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md). W pozostałej części `ThisAddIn` klasa jest zdefiniowana w pliku ukryty kod, który nie należy modyfikować.

- `ThisAddIn_Startup` i `ThisAddIn_Shutdown` procedury obsługi zdarzeń. Te procedury obsługi zdarzeń są wywoływane, gdy program Outlook ładuje i zwalnia dodatku narzędzi VSTO dla programów. Użyj tych programów obsługi zdarzeń, można zainicjować dodatku narzędzi VSTO dla programów, podczas jego ładowania oraz aby wyczyścić zasoby używane przez dodatek narzędzi VSTO dla programu, gdy jest zwolniony. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

### <a name="to-add-text-to-the-subject-and-body-of-each-new-mail-message"></a>Aby dodać tekst na jej temat i treść każdej nowej wiadomości e-mail

1. W plik kodu ThisAddIn zadeklarować pole o nazwie `inspectors` w `ThisAddIn` klasy. `inspectors` Pola obsługuje odwołania do kolekcji Inspektor okna w bieżącym wystąpieniu programu Outlook. Zapobiega to odwołanie moduł zbierający elementy bezużyteczne zwalnianie pamięci, który zawiera program obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> zdarzeń.

    [!code-vb[Trin_OutlookAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_OutlookAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#1)]

2. Zastąp `ThisAddIn_Startup` metoda następującym kodem. Ten kod dołącza program obsługi zdarzeń do <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> zdarzeń.

    [!code-vb[Trin_OutlookAddInTutorial#2](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#2)]
    [!code-csharp[Trin_OutlookAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#2)]

3. W pliku kodu ThisAddIn, Dodaj następujący kod do `ThisAddIn` klasy. Ten kod definiuje zdarzenia obsługi dla <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> zdarzeń.

    Gdy użytkownik tworzy nową wiadomość e-mail, ta procedura obsługi zdarzeń dodaje tekst wiersza tematu i treści wiadomości.

    [!code-vb[Trin_OutlookAddInTutorial#3](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#3)]
    [!code-csharp[Trin_OutlookAddInTutorial#3](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#3)]

   Aby zmodyfikować każdej nowej wiadomości e-mail, w poprzednich przykładach kodu za pomocą następujących obiektów:

- `Application` Pole `ThisAddIn` klasy. `Application` Pole zwraca <xref:Microsoft.Office.Interop.Outlook.Application> reprezentujący bieżące wystąpienie programu Outlook.

- `Inspector` Parametrów programu obsługi zdarzeń <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> zdarzeń. `Inspector` Parametr <xref:Microsoft.Office.Interop.Outlook.Inspector> obiektu, który reprezentuje okna Inspektor nową wiadomość e-mail. Aby uzyskać więcej informacji, zobacz [rozwiązania programu Outlook](../vsto/outlook-solutions.md).

## <a name="test-the-project"></a>Projekt testowy
 Gdy skompilować i uruchomić projekt, należy sprawdzić, czy tekst jest wyświetlany w wierszu tematu i treści nową wiadomość e-mail.

### <a name="to-test-the-project"></a>Aby przetestować projekt

1. Naciśnij klawisz **F5** Aby skompilować i uruchomić projekt.

     Gdy tworzysz projekt, kod jest kompilowany do zestawu, który znajduje się w folderze wyjściowym kompilacji dla projektu. Visual Studio tworzy również zestaw wpisów rejestru dodawanych włączyć w programie Outlook wykrycie i załadowanie dodatku narzędzi VSTO dla programów i konfiguruje ustawienia zabezpieczeń na komputerze deweloperskim, aby włączyć dodatek narzędzi VSTO dla programów do uruchomienia. Aby uzyskać więcej informacji, zobacz [Przegląd procesu kompilacji rozwiązania pakietu Office](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md).

2. W programie Outlook utwórz nową wiadomość e-mail.

3. Sprawdź, czy następujący tekst został dodany do wiersza tematu i treści wiadomości.

     **Ten tekst został dodany przy użyciu kodu.**

4. Zamknij program Outlook.

## <a name="clean-up-the-project"></a>Czyszczenie projektu
 Po zakończeniu tworzenia projektu dodatku narzędzi VSTO zestaw, wpisy rejestru i ustawienia zabezpieczeń należy usunąć z komputera dewelopera. W przeciwnym razie dodatku narzędzi VSTO uruchomią każdym otwarciu programu Outlook na komputerze deweloperskim.

### <a name="to-clean-up-your-project"></a>Aby wyczyścić projektu

1. W programie Visual Studio na **kompilacji** menu, kliknij przycisk **czyste rozwiązanie**.

## <a name="next-steps"></a>Następne kroki
 Teraz, gdy utworzono podstawowe dodatku narzędzi VSTO dla programu Outlook, można dowiedzieć się więcej o tworzeniu dodatków narzędzi VSTO dla programów w tych tematach:

- Ogólne zadania programowania, które można wykonywać za pomocą dodatków narzędzi VSTO dla programu Outlook. Aby uzyskać więcej informacji, zobacz [dodatków narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md).

- Za pomocą modelu obiektów programu Outlook. Aby uzyskać więcej informacji, zobacz [rozwiązania programu Outlook](../vsto/outlook-solutions.md).

- Dostosowywanie interfejsu użytkownika programu Outlook, na przykład przez dodawanie kart niestandardowych do Wstążki lub tworzenia własnego niestandardowego okienka zadań. Aby uzyskać więcej informacji, zobacz [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

- Kompilowanie i debugowanie dodatków narzędzi VSTO dla programu Outlook. Aby uzyskać więcej informacji, zobacz [rozwiązań kompilacji pakietu Office](../vsto/building-office-solutions.md).

- Wdrażanie dodatków narzędzi VSTO dla programu Outlook. Aby uzyskać więcej informacji, zobacz [wdrożyć rozwiązanie Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Zobacz także
- [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md)
- [Rozwiązania programu Outlook](../vsto/outlook-solutions.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)
- [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)
- [Omówienie szablonów projektu pakietu Office](../vsto/office-project-templates-overview.md)
