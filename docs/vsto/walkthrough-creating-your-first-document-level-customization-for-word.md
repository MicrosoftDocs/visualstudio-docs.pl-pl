---
title: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Word
description: Utwórz dostosowanie na poziomie dokumentu dla programu Microsoft Word. Funkcje, które tworzysz w tego typu rozwiązaniu, są dostępne tylko wtedy, gdy konkretny dokument jest otwarty.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, creating your first project
- Word [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 71051c6255f9035079a7888fb3a4c7df2f5eab59
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827555"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-word"></a>Przewodnik: tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Word

  W tym przewodniku wprowadzającym pokazano, jak utworzyć dostosowanie na poziomie dokumentu dla Microsoft Office Word. Funkcje, które tworzysz w tego typu rozwiązaniu, są dostępne tylko wtedy, gdy konkretny dokument jest otwarty. Nie można użyć dostosowania na poziomie dokumentu, aby wprowadzić zmiany w całej aplikacji, na przykład wyświetlając nową kartę Wstążki, gdy dowolny dokument jest otwarty.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie projektu dokumentu programu Word.

- Dodawanie tekstu do dokumentu, który jest hostowany w Visual Studio projektanta.

- Pisanie kodu, który używa modelu obiektu programu Word do dodawania tekstu do dostosowanego dokumentu po jego otwarciu.

- Budowania i uruchamiania projektu w celu przetestowania go.

- Czyszczenie projektu w celu usunięcia niepotrzebnych plików kompilacji i ustawień zabezpieczeń z komputera dewelopera.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne

 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Tworzenie projektu

### <a name="to-create-a-new-word-document-project-in-visual-studio"></a>Aby utworzyć nowy projekt dokumentu programu Word w programie Visual Studio

1. Uruchom [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. W menu **File (Plik)** wskaż pozycję **New (Nowy),** a następnie kliknij pozycję **Project (Projekt).**
::: moniker range="vs-2017"
3. W okienku szablonów rozwiń pozycję **Visual C#** **lub Visual Basic**, a następnie rozwiń pozycję **Office/SharePoint.**

4. W rozwiniętym **węźle Office/SharePoint** wybierz węzeł Dodatki **VSTO.**

5. Na liście szablonów projektów wybierz projekt dokumentu Word VSTO.

6. W polu **Nazwa** wpisz **FirstDocumentCustomization**.

7. Kliknij przycisk **OK**.

8. Wybierz **pozycję Utwórz nowy dokument w** **kreatorze Visual Studio Tools projektu pakietu Office,** a następnie kliknij przycisk **OK.**
::: moniker-end
::: moniker range=">=vs-2019"
3. W **oknie dialogowym Create a New Project (Tworzenie** nowego projektu) wybierz **projekt Word VSTO Document (Projekt dokumentu Word VSTO).**

     [!INCLUDE[new-project-dialog-search](../vsto/includes/new-project-dialog-search-md.md)]

4. Kliknij przycisk **Dalej**.

5. Wpisz **FirstWorkbookCustomization w** **polu Nazwa** w **oknie dialogowym Konfigurowanie nowego projektu** i kliknij pozycję **Utwórz**.

6. Wybierz **pozycję Utwórz nowy dokument w** **kreatorze Visual Studio Tools projektu pakietu Office,** a następnie kliknij przycisk **OK.**
::: moniker-end
   - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Tworzy projekt **FirstDocumentCustomization** i dodaje do projektu dokument **FirstDocumentCustomization** oraz plik kodu ThisDocument. Dokument **FirstDocumentCustomization** jest otwierany automatycznie w projektancie.

## <a name="close-and-reopen-the-document-in-the-designer"></a>Zamykanie i ponowne otwieranie dokumentu w projektancie

 Jeśli dokument w projektancie został celowo lub przypadkowo zamknięty podczas tworzenia projektu, możesz otworzyć go ponownie.

### <a name="to-close-and-reopen-the-document-in-the-designer"></a>Aby zamknąć i ponownie otworzyć dokument w projektancie

1. Zamknij dokument, klikając przycisk **Zamknij** (X) w oknie projektanta.

2. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy plik **kodu ThisDocument,** a następnie kliknij **Projektant widoków**.

     \- lub —

     W **Eksplorator rozwiązań** kliknij dwukrotnie **plik kodu ThisDocument.**

## <a name="add-text-to-the-document-in-the-designer"></a>Dodawanie tekstu do dokumentu w projektancie

 Interfejs użytkownika (UI) dostosowania można zaprojektować, modyfikując dokument otwarty w projektancie. Możesz na przykład dodać tekst, tabele lub kontrolki programu Word. Aby uzyskać więcej informacji na temat korzystania z projektanta, zobacz Office projects in the Visual Studio environment (Projekty pakietu [Office w środowisku Visual Studio office).](../vsto/office-projects-in-the-visual-studio-environment.md)

### <a name="to-add-text-to-your-document-by-using-the-designer"></a>Aby dodać tekst do dokumentu przy użyciu projektanta

1. W dokumencie otwartym w projektancie wpisz następujący tekst.

     **Ten tekst został dodany przy użyciu projektanta.**

## <a name="add-text-to-the-document-programmatically"></a>Programowe dodawanie tekstu do dokumentu

 Następnie dodaj kod do pliku kodu ThisDocument. Nowy kod używa modelu obiektów programu Word, aby dodać drugi akapit tekstu do dokumentu. Domyślnie plik kodu ThisDocument zawiera następujący wygenerowany kod:

- Częściowa definicja klasy, która reprezentuje model programowania dokumentu i zapewnia dostęp do `ThisDocument` modelu obiektów programu Word. Aby uzyskać więcej informacji, zobacz [Document host item (Element hosta dokumentu)](../vsto/document-host-item.md) i [Word object model overview (Omówienie modelu obiektu programu Word).](../vsto/word-object-model-overview.md) Pozostała część klasy `ThisDocument` jest zdefiniowana w ukrytym pliku kodu, który nie powinien być modyfikowany.

- Programy `ThisDocument_Startup` obsługi zdarzeń i `ThisDocument_Shutdown` . Te procedury obsługi zdarzeń są wywoływane po otwarciu i zamknięciu dokumentu. Użyj tych programów obsługi zdarzeń, aby zainicjować dostosowanie po otwarciu dokumentu i wyczyścić zasoby używane przez dostosowanie po zamknięciu dokumentu. Aby uzyskać więcej informacji, zobacz [Zdarzenia w projektach pakietu Office.](../vsto/events-in-office-projects.md)

### <a name="to-add-a-second-paragraph-of-text-to-the-document-by-using-code"></a>Aby dodać drugi akapit tekstu do dokumentu przy użyciu kodu

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **ThisDocument**, a następnie kliknij polecenie **Wyświetl kod.**

     Plik kodu zostanie otwarty w Visual Studio.

2. Zastąp program `ThisDocument_Startup` obsługi zdarzeń następującym kodem. Po otwarciu dokumentu ten kod dodaje do dokumentu drugi akapit tekstu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/FirstDocumentCustomization/ThisDocument.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/FirstDocumentCustomization/ThisDocument.cs" id="Snippet1":::

    > [!NOTE]
    > Ten kod używa wartości indeksu 1, aby uzyskać dostęp do pierwszego akapitu we właściwości <xref:Microsoft.Office.Tools.Word.Document.Paragraphs%2A> . Chociaż Visual Basic i Visual C# używają tablic opartych na 0, dolna granica tablicy większości kolekcji w modelu obiektów programu Word wynosi 1. Aby uzyskać więcej informacji, zobacz [Pisanie kodu w rozwiązaniach pakietu Office.](../vsto/writing-code-in-office-solutions.md)

## <a name="test-the-project"></a>Testowanie projektu

### <a name="to-test-your-document"></a>Aby przetestować dokument

1. Naciśnij **klawisz F5,** aby skompilować i uruchomić projekt.

     Podczas kompilowania projektu kod jest kompilowany do zestawu skojarzonego z dokumentem. Visual Studio umieszcza kopię dokumentu i zestawu w folderze danych wyjściowych kompilacji dla projektu i konfiguruje ustawienia zabezpieczeń na komputerze dewelopera, aby umożliwić uruchomienie dostosowania. Aby uzyskać więcej informacji, zobacz [Build Office solutions (Tworzenie rozwiązań pakietu Office).](../vsto/building-office-solutions.md)

2. W dokumencie sprawdź, czy widzisz następujący tekst.

     **Ten tekst został dodany przy użyciu projektanta.**

     **Ten tekst został dodany przy użyciu kodu.**

3. Zamknij dokument.

## <a name="clean-up-the-project"></a>Czyszczenie projektu

 Po zakończeniu tworzenia projektu należy usunąć pliki z folderu wyjściowego kompilacji oraz ustawienia zabezpieczeń utworzone w procesie kompilacji.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Aby wyczyścić ukończony projekt na komputerze dewelopera

1. W Visual Studio menu Build  (Kompilacja) kliknij pozycję **Clean Solution (Wyczyść rozwiązanie).**

## <a name="next-steps"></a>Następne kroki

 Teraz, po utworzeniu podstawowego dostosowania na poziomie dokumentu dla programu Word, możesz dowiedzieć się więcej na temat tworzenia dostosowań z tych tematów:

- Ogólne zadania programistyczne, które można wykonywać w dostosowaniach na poziomie dokumentu: [Programowanie dostosowań na poziomie dokumentu.](../vsto/programming-document-level-customizations.md)

- Zadania programistyczne specyficzne dla dostosowań na poziomie dokumentu dla rozwiązań word: [Word.](../vsto/word-solutions.md)

- Korzystanie z modelu obiektów programu Word: [Omówienie modelu obiektów programu Word](../vsto/word-object-model-overview.md).

- Dostosowywanie interfejsu użytkownika programu Word, na przykład przez dodanie karty niestandardowej do wstążki lub utworzenie własnego okienka akcji: Dostosowywanie interfejsu [użytkownika pakietu Office](../vsto/office-ui-customization.md).

- Używanie rozszerzonych obiektów word dostarczanych przez rozwiązania pakietu Office w programie Visual Studio do wykonywania zadań, które nie są możliwe przy użyciu modelu obiektów programu Word (na przykład hostowanie kontrolek zarządzanych w dokumentach i powiązanie kontrolek programu Word z danymi przy użyciu modelu powiązania danych programu Windows Forms): [automatyzowanie](../vsto/automating-word-by-using-extended-objects.md)programu Word przy użyciu obiektów rozszerzonych.

- Kompilowanie i debugowanie dostosowań na poziomie dokumentu dla programu Word: [Tworzenie rozwiązań pakietu Office.](../vsto/building-office-solutions.md)

- Wdrażanie dostosowań na poziomie dokumentu dla programu Word: [wdrażanie rozwiązania pakietu Office.](../vsto/deploying-an-office-solution.md)

## <a name="see-also"></a>Zobacz też

- [Omówienie tworzenia rozwiązań pakietu Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Rozwiązania programu Word](../vsto/word-solutions.md)
- [Zaprogramowanie dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)
- [Omówienie modelu obiektów programu Word](../vsto/word-object-model-overview.md)
- [Automatyzowanie programu Word przy użyciu obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)
- [Wdrażanie rozwiązania pakietu Office](../vsto/deploying-an-office-solution.md)
- [Omówienie szablonów projektów pakietu Office](../vsto/office-project-templates-overview.md)
