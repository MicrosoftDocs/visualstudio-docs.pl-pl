---
title: 'Przewodnik: tworzenie pierwszego dodatku VSTO dla programu Outlook'
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a6bcc134096284579e1097edf0e958105f48cfcb
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824292"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-outlook"></a>Przewodnik: tworzenie pierwszego dodatku VSTO dla programu Outlook
  W tym przewodniku pokazano, jak utworzyć dodatek VSTO dla programu Microsoft Office Outlook. Funkcje, które tworzysz w tego typu rozwiązaniu, są dostępne dla samej aplikacji, niezależnie od tego, który element programu Outlook jest otwarty. Aby uzyskać więcej informacji, zobacz Omówienie tworzenia [rozwiązań pakietu Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie projektu dodatku VSTO programu Outlook dla programu Outlook.

- Pisanie kodu, który używa modelu obiektów programu Outlook do dodawania tekstu do tematu i treści nowej wiadomości e-mail.

- Budowania i uruchamiania projektu w celu przetestowania go.

- Czyszczenie ukończonego projektu tak, aby dodatek VSTO nie był już automatycznie uruchamiany na komputerze dewelopera.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Outlook

## <a name="create-the-project"></a>Tworzenie projektu

### <a name="to-create-a-new-outlook-project-in-visual-studio"></a>Aby utworzyć nowy projekt programu Outlook w programie Visual Studio

1. Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. W menu **File (Plik)** wskaż pozycję **New (Nowy),** a następnie kliknij pozycję **Project (Projekt).**

3. W okienku szablonów rozwiń pozycję **Visual C#** **lub Visual Basic**, a następnie rozwiń pozycję **Office/SharePoint.**

4. W rozwiniętym **węźle Office/SharePoint** wybierz węzeł **Dodatki pakietu Office.**

5. Na liście szablonów projektów wybierz projekt dodatku VSTO programu Outlook.

6. W polu **Nazwa** wpisz **FirstOutlookAddIn**.

7. Kliknij przycisk **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tworzy projekt **FirstOutlookAddIn** i otwiera plik kodu **ThisAddIn** w edytorze.

## <a name="write-code-that-adds-text-to-each-new-mail-message"></a>Pisanie kodu, który dodaje tekst do każdej nowej wiadomości e-mail
 Następnie dodaj kod do pliku kodu ThisAddIn. Nowy kod używa modelu obiektów programu Outlook do dodawania tekstu do każdej nowej wiadomości e-mail. Domyślnie plik kodu ThisAddIn zawiera następujący wygenerowany kod:

- Częściowa definicja `ThisAddIn` klasy. Ta klasa zapewnia punkt wejścia dla kodu i zapewnia dostęp do modelu obiektów programu Outlook. Aby uzyskać więcej informacji, zobacz [Program VSTO Add-ins (Dodatki programu VSTO).](../vsto/programming-vsto-add-ins.md) Pozostała część klasy `ThisAddIn` jest zdefiniowana w ukrytym pliku kodu, który nie powinien być modyfikowany.

- Programy `ThisAddIn_Startup` `ThisAddIn_Shutdown` obsługi zdarzeń i . Te procedury obsługi zdarzeń są wywoływane, gdy program Outlook ładuje i zwalnia dodatek VSTO. Użyj tych programów obsługi zdarzeń, aby zainicjować dodatek VSTO podczas ładowania i wyczyścić zasoby używane przez dodatek VSTO, gdy zostanie zwolniony. Aby uzyskać więcej informacji, zobacz [Zdarzenia w projektach pakietu Office.](../vsto/events-in-office-projects.md)

### <a name="to-add-text-to-the-subject-and-body-of-each-new-mail-message"></a>Aby dodać tekst do tematu i treści każdej nowej wiadomości e-mail

1. W pliku kodu ThisAddIn zadeklaruj pole o nazwie `inspectors` w `ThisAddIn` klasie . Pole `inspectors` zawiera odwołanie do kolekcji okien Inspector (Inspektor) w bieżącym wystąpieniu programu Outlook. To odwołanie uniemożliwia modułowi odśmiecania pamięci, która zawiera program obsługi <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> zdarzeń dla zdarzenia.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb" id="Snippet1":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs" id="Snippet1":::

2. Zastąp metodę `ThisAddIn_Startup` następującym kodem. Ten kod dołącza program obsługi zdarzeń do <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> zdarzenia.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb" id="Snippet2":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs" id="Snippet2":::

3. W pliku kodu ThisAddIn dodaj następujący kod do `ThisAddIn` klasy . Ten kod definiuje program obsługi zdarzeń <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> dla zdarzenia.

    Gdy użytkownik tworzy nową wiadomość e-mail, ta procedura obsługi zdarzeń dodaje tekst do wiersza tematu i treści wiadomości.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookAddInTutorial/ThisAddIn.vb" id="Snippet3":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookAddInTutorial/ThisAddIn.cs" id="Snippet3":::

   Aby zmodyfikować każdą nową wiadomość e-mail, w poprzednich przykładach kodu są następujące obiekty:

- Pole `Application` klasy `ThisAddIn` . Pole `Application` zwraca obiekt <xref:Microsoft.Office.Interop.Outlook.Application> reprezentujący bieżące wystąpienie programu Outlook.

- Parametr `Inspector` procedury obsługi zdarzeń <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> dla zdarzenia. Parametr `Inspector` jest <xref:Microsoft.Office.Interop.Outlook.Inspector> obiektem, który reprezentuje okno Inspector (Inspektor) nowej wiadomości e-mail. Aby uzyskać więcej informacji, zobacz [Rozwiązania programu Outlook.](../vsto/outlook-solutions.md)

## <a name="test-the-project"></a>Testowanie projektu
 Podczas kompilowania i uruchamiania projektu sprawdź, czy tekst pojawia się w wierszu tematu i w treści nowej wiadomości e-mail.

### <a name="to-test-the-project"></a>Aby przetestować projekt

1. Naciśnij **klawisz F5,** aby skompilować i uruchomić projekt.

     Podczas kompilowania projektu kod jest kompilowany w zestawie, który znajduje się w folderze danych wyjściowych kompilacji dla projektu. Visual Studio tworzy również zestaw wpisów rejestru, które umożliwiają programowi Outlook odnajdywanie i ładowanie dodatku VSTO, a także konfiguruje ustawienia zabezpieczeń na komputerze dewelopera, aby umożliwić uruchamianie dodatku VSTO. Aby uzyskać więcej informacji, zobacz [Omówienie procesu kompilacji rozwiązania pakietu Office.](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

2. W programie Outlook utwórz nową wiadomość e-mail.

3. Sprawdź, czy do wiersza tematu i treści wiadomości został dodany następujący tekst.

     **Ten tekst został dodany przy użyciu kodu.**

4. Zamknij program Outlook.

## <a name="clean-up-the-project"></a>Czyszczenie projektu
 Po zakończeniu tworzenia projektu usuń zestaw dodatku VSTO, wpisy rejestru i ustawienia zabezpieczeń z komputera dewelopera. W przeciwnym razie dodatek VSTO będzie uruchamiany przy każdym otwarciu programu Outlook na komputerze dewelopera.

### <a name="to-clean-up-your-project"></a>Aby wyczyścić projekt

1. W Visual Studio menu **Build (Kompilacja)** kliknij pozycję **Clean Solution (Wyczyść rozwiązanie).**

## <a name="next-steps"></a>Następne kroki
 Po utworzeniu podstawowego dodatku VSTO dla programu Outlook możesz dowiedzieć się więcej na temat sposobu tworzenia dodatków VSTO z tych tematów:

- Ogólne zadania programistyczne, które można wykonywać przy użyciu dodatków VSTO dla programu Outlook. Aby uzyskać więcej informacji, zobacz [Program VSTO Add-ins (Dodatki programu VSTO).](../vsto/programming-vsto-add-ins.md)

- Korzystanie z modelu obiektów programu Outlook. Aby uzyskać więcej informacji, zobacz [Rozwiązania programu Outlook](../vsto/outlook-solutions.md).

- Dostosowywanie interfejsu użytkownika programu Outlook, na przykład przez dodanie karty niestandardowej do wstążki lub utworzenie własnego niestandardowego okienka zadań. Aby uzyskać więcej informacji, zobacz [Dostosowywanie interfejsu użytkownika pakietu Office.](../vsto/office-ui-customization.md)

- Budowania i debugowania dodatków narzędzi VSTO dla programu Outlook. Aby uzyskać więcej informacji, zobacz [Build Office solutions (Tworzenie rozwiązań pakietu Office).](../vsto/building-office-solutions.md)

- Wdrażanie dodatków VSTO dla programu Outlook. Aby uzyskać więcej informacji, zobacz [Wdrażanie rozwiązania pakietu Office.](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>Zobacz też
- [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md)
- [Rozwiązania programu Outlook](../vsto/outlook-solutions.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)
- [Wdrażanie rozwiązania pakietu Office](../vsto/deploying-an-office-solution.md)
- [Omówienie szablonów projektów pakietu Office](../vsto/office-project-templates-overview.md)
