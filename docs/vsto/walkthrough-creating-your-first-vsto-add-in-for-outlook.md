---
title: 'Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Outlook'
description: Utwórz dodatek na poziomie aplikacji dla programu Microsoft Outlook. Ta funkcja jest dostępna dla samej aplikacji, niezależnie od tego, który element programu Outlook jest otwarty.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
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
ms.openlocfilehash: 7950858d3205cf910eb09e5b0a99b5f67c71c4bd
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524226"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-outlook"></a>Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Outlook
  W tym instruktażu pokazano, jak utworzyć dodatek narzędzi VSTO dla programu Microsoft Office Outlook. Funkcje, które tworzysz w tym rodzaju rozwiązanie, są dostępne dla samej aplikacji, niezależnie od tego, który element programu Outlook jest otwarty. Aby uzyskać więcej informacji, zobacz [Omówienie tworzenia rozwiązań pakietu Office &#40;narzędzi VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie projektu dodatku programu Outlook VSTO dla programu Outlook.

- Pisanie kodu, który używa modelu obiektów programu Outlook w celu dodania tekstu do tematu i treści nowej wiadomości e-mail.

- Kompilowanie i uruchamianie projektu w celu jego przetestowania.

- Czyszczenie ukończonego projektu, aby dodatek VSTO nie był już automatycznie uruchamiany na komputerze deweloperskim.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Outlook

## <a name="create-the-project"></a>Tworzenie projektu

### <a name="to-create-a-new-outlook-project-in-visual-studio"></a>Aby utworzyć nowy projekt programu Outlook w programie Visual Studio

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

3. W okienku szablony rozwiń pozycję **Visual C#** lub **Visual Basic**, a następnie rozwiń węzeł **Office/SharePoint**.

4. W rozwiniętym węźle **Office/SharePoint** wybierz węzeł **Dodatki pakietu Office** .

5. Na liście szablonów projektu wybierz projekt dodatku VSTO dla programu Outlook.

6. W polu **Nazwa** wpisz **FirstOutlookAddIn**.

7. Kliknij przycisk **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tworzy projekt **FirstOutlookAddIn** i otwiera plik kodu **ThisAddIn** w edytorze.

## <a name="write-code-that-adds-text-to-each-new-mail-message"></a>Napisz kod, który dodaje tekst do każdej nowej wiadomości e-mail
 Następnie Dodaj kod do pliku kodu ThisAddIn. Nowy kod używa modelu obiektów programu Outlook do dodawania tekstu do każdej nowej wiadomości e-mail. Domyślnie plik kodu ThisAddIn zawiera następujący wygenerowany kod:

- Częściowa definicja `ThisAddIn` klasy. Ta klasa udostępnia punkt wejścia dla kodu i zapewnia dostęp do modelu obiektów programu Outlook. Aby uzyskać więcej informacji, zobacz [dodatki narzędzi VSTO dla programu](../vsto/programming-vsto-add-ins.md). Pozostała część `ThisAddIn` klasy jest zdefiniowana w ukrytym pliku kodu, który nie powinien być modyfikowany.

- `ThisAddIn_Startup` `ThisAddIn_Shutdown` Programy obsługi zdarzeń i. Te programy obsługi zdarzeń są wywoływane, gdy program Outlook ładuje i zwalnia dodatek narzędzi VSTO. Te programy obsługi zdarzeń umożliwiają zainicjowanie dodatku VSTO podczas ładowania i oczyszczenie zasobów używanych przez dodatek VSTO po jego wyładowaniu. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

### <a name="to-add-text-to-the-subject-and-body-of-each-new-mail-message"></a>Aby dodać tekst do tematu i treści każdej nowej wiadomości e-mail

1. W pliku kodu ThisAddIn Zadeklaruj pole o nazwie `inspectors` w `ThisAddIn` klasie. `inspectors`Pole utrzymuje odwołanie do kolekcji okien inspektorów w bieżącym wystąpieniu programu Outlook. To odwołanie zapobiega zwalnianiu pamięci przez moduł wyrzucania elementów bezużytecznych, która zawiera program obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> zdarzenia.

    [!code-vb[Trin_OutlookAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#1)]
    [!code-csharp[Trin_OutlookAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#1)]

2. Zastąp metodę `ThisAddIn_Startup` następującym kodem. Ten kod dołącza procedurę obsługi zdarzeń do <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> zdarzenia.

    [!code-vb[Trin_OutlookAddInTutorial#2](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#2)]
    [!code-csharp[Trin_OutlookAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#2)]

3. W pliku kodu ThisAddIn Dodaj następujący kod do `ThisAddIn` klasy. Ten kod definiuje procedurę obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> zdarzenia.

    Gdy użytkownik tworzy nową wiadomość e-mail, ten program obsługi zdarzeń dodaje tekst do wiersza tematu i treści wiadomości.

    [!code-vb[Trin_OutlookAddInTutorial#3](../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb#3)]
    [!code-csharp[Trin_OutlookAddInTutorial#3](../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs#3)]

   Aby zmodyfikować każdą nową wiadomość e-mail, poprzednie przykłady kodu używają następujących obiektów:

- `Application`Pole `ThisAddIn` klasy. `Application`Pole zwraca <xref:Microsoft.Office.Interop.Outlook.Application> obiekt, który reprezentuje bieżące wystąpienie programu Outlook.

- `Inspector`Parametr programu obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> zdarzenia. `Inspector`Parametr jest <xref:Microsoft.Office.Interop.Outlook.Inspector> obiektem, który reprezentuje okno Inspektora nowej wiadomości e-mail. Aby uzyskać więcej informacji, zobacz [rozwiązania programu Outlook](../vsto/outlook-solutions.md).

## <a name="test-the-project"></a>Testowanie projektu
 Podczas kompilowania i uruchamiania projektu Sprawdź, czy tekst jest wyświetlany w wierszu tematu i treści nowej wiadomości e-mail.

### <a name="to-test-the-project"></a>Aby przetestować projekt

1. Naciśnij klawisz **F5** , aby skompilować i uruchomić projekt.

     Podczas kompilowania projektu, kod jest kompilowany do zestawu, który jest dołączony do folderu danych wyjściowych kompilacji dla projektu. Program Visual Studio tworzy również zestaw wpisów rejestru umożliwiających programowi Outlook odnalezienie i załadowanie dodatku VSTO oraz skonfigurowanie ustawień zabezpieczeń na komputerze deweloperskim w celu umożliwienia uruchomienia dodatku VSTO. Aby uzyskać więcej informacji, zobacz [Omówienie procesu tworzenia rozwiązań pakietu Office](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md).

2. W programie Outlook utwórz nową wiadomość e-mail.

3. Upewnij się, że następujący tekst został dodany zarówno do wiersza tematu, jak i treści wiadomości.

     **Ten tekst został dodany za pomocą kodu.**

4. Zamknij program Outlook.

## <a name="clean-up-the-project"></a>Wyczyść projekt
 Po zakończeniu opracowywania projektu, Usuń zestaw dodatków VSTO, wpisy rejestru i ustawienia zabezpieczeń z komputera deweloperskiego. W przeciwnym razie dodatek VSTO zostanie uruchomiony za każdym razem, gdy otworzysz program Outlook na komputerze deweloperskim.

### <a name="to-clean-up-your-project"></a>Aby oczyścić projekt

1. W programie Visual Studio w menu **kompilacja** kliknij pozycję **czyste rozwiązanie**.

## <a name="next-steps"></a>Następne kroki
 Po utworzeniu podstawowego dodatku narzędzi VSTO dla programu Outlook można dowiedzieć się więcej na temat opracowywania dodatków VSTO z następujących tematów:

- Ogólne zadania programistyczne, które można wykonać za pomocą dodatków narzędzi VSTO dla programu Outlook. Aby uzyskać więcej informacji, zobacz [dodatki narzędzi VSTO dla programu](../vsto/programming-vsto-add-ins.md).

- Korzystanie z modelu obiektów programu Outlook. Aby uzyskać więcej informacji, zobacz [rozwiązania programu Outlook](../vsto/outlook-solutions.md).

- Dostosowywanie interfejsu użytkownika programu Outlook, na przykład przez dodanie karty niestandardowej do wstążki lub utworzenie własnego niestandardowego okienka zadań. Aby uzyskać więcej informacji, zobacz temat [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

- Kompilowanie i debugowanie dodatków VSTO dla programu Outlook. Aby uzyskać więcej informacji, zobacz [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md).

- Wdrażanie dodatków VSTO dla programu Outlook. Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązania biurowego](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Zobacz też
- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)
- [Rozwiązania programu Outlook](../vsto/outlook-solutions.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)
- [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md)
- [Szablony projektów pakietu Office — omówienie](../vsto/office-project-templates-overview.md)
