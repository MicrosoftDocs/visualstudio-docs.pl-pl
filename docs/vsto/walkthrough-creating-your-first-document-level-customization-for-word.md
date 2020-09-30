---
title: Utwórz swoje pierwsze dostosowanie na poziomie dokumentu dla programu Word
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c1f5d1d6d373a5bbcd3f10d600175a88e88823ad
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584992"
---
# <a name="walkthrough-create-your-first-document-level-customization-for-word"></a>Przewodnik: Tworzenie pierwszego dostosowania na poziomie dokumentu dla programu Word

  W tym instruktażu wprowadzającym pokazano, jak utworzyć dostosowanie na poziomie dokumentu dla programu Microsoft Office Word. Funkcje utworzone w tym rodzaju rozwiązaniu są dostępne tylko wtedy, gdy określony dokument jest otwarty. Nie można użyć dostosowania na poziomie dokumentu w celu wprowadzania zmian w całej aplikacji, na przykład wyświetlania nowej karty wstążki, gdy dowolny dokument jest otwarty.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie projektu dokumentu programu Word.

- Dodawanie tekstu do dokumentu, który jest hostowany w projektancie programu Visual Studio.

- Pisanie kodu, który używa modelu obiektów programu Word w celu dodania tekstu do niestandardowego dokumentu po jego otwarciu.

- Kompilowanie i uruchamianie projektu w celu jego przetestowania.

- Czyszczenie projektu w celu usunięcia niepotrzebnych plików kompilacji i ustawień zabezpieczeń z komputera deweloperskiego.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne

 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Tworzenie projektu

### <a name="to-create-a-new-word-document-project-in-visual-studio"></a>Aby utworzyć nowy projekt dokumentu programu Word w programie Visual Studio

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.
::: moniker range="vs-2017"
3. W okienku szablony rozwiń pozycję **Visual C#** lub **Visual Basic**, a następnie rozwiń węzeł **Office/SharePoint**.

4. W rozwiniętym węźle **Office/SharePoint** wybierz węzeł **dodatki narzędzi VSTO** .

5. Na liście szablonów projektu wybierz projekt dokumentu VSTO programu Word.

6. W polu **Nazwa** wpisz **FirstDocumentCustomization**.

7. Kliknij przycisk **OK**.

8. Wybierz pozycję **Utwórz nowy dokument** w **Kreatorze programu Visual Studio Tools dla pakietu Office**, a następnie kliknij przycisk **OK**.
::: moniker-end
::: moniker range=">=vs-2019"
3. W oknie dialogowym **Utwórz nowy projekt** wybierz projekt **dokument programu Word VSTO** .

     [!INCLUDE[new-project-dialog-search](../vsto/includes/new-project-dialog-search-md.md)]

4. Kliknij przycisk **Dalej**.

5. Wpisz **FirstWorkbookCustomization** w polu **Nazwa** w oknie dialogowym **Konfigurowanie nowego projektu** , a następnie kliknij przycisk **Utwórz**.

6. Wybierz pozycję **Utwórz nowy dokument** w **Kreatorze programu Visual Studio Tools dla pakietu Office**, a następnie kliknij przycisk **OK**.
::: moniker-end
   - [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tworzy projekt **FirstDocumentCustomization** i dodaje dokument **FirstDocumentCustomization** i plik kodu ThisDocument do projektu. Dokument **FirstDocumentCustomization** zostanie automatycznie otwarty w projektancie.

## <a name="close-and-reopen-the-document-in-the-designer"></a>Zamknij i ponownie otwórz dokument w projektancie

 Jeśli zamierzasz celowo lub przypadkowo zamknąć dokument w Projektancie podczas tworzenia projektu, możesz go otworzyć ponownie.

### <a name="to-close-and-reopen-the-document-in-the-designer"></a>Aby zamknąć i ponownie otworzyć dokument w projektancie

1. Zamknij dokument, klikając przycisk **Zamknij** (X) dla okna projektanta.

2. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik kodu **ThisDocument** , a następnie kliknij pozycję **Projektant widoków**.

     \- oraz

     W **Eksplorator rozwiązań**kliknij dwukrotnie plik kodu **ThisDocument** .

## <a name="add-text-to-the-document-in-the-designer"></a>Dodawanie tekstu do dokumentu w projektancie

 Interfejs użytkownika można zaprojektować, modyfikując dokument, który jest otwarty w projektancie. Na przykład możesz dodać kontrolki tekstu, tabel lub wyrazów. Aby uzyskać więcej informacji o sposobach korzystania z projektanta, zobacz [projekty pakietu Office w środowisku programu Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

### <a name="to-add-text-to-your-document-by-using-the-designer"></a>Aby dodać tekst do dokumentu przy użyciu narzędzia Projektant

1. W dokumencie otwartym w projektancie wpisz następujący tekst.

     **Ten tekst został dodany za pomocą projektanta.**

## <a name="add-text-to-the-document-programmatically"></a>Programistyczne Dodawanie tekstu do dokumentu

 Następnie Dodaj kod do pliku kodu ThisDocument. Nowy kod używa modelu obiektów programu Word w celu dodania drugiego akapitu tekstu do dokumentu. Domyślnie plik kodu ThisDocument zawiera następujący wygenerowany kod:

- Częściowa definicja `ThisDocument` klasy, która reprezentuje model programowania dokumentu i zapewnia dostęp do modelu obiektów programu Word. Aby uzyskać więcej informacji, zobacz dokument dotyczący [elementów hosta](../vsto/document-host-item.md) i [modelu obiektów programu Word](../vsto/word-object-model-overview.md). Pozostała część `ThisDocument` klasy jest zdefiniowana w ukrytym pliku kodu, który nie powinien być modyfikowany.

- `ThisDocument_Startup` `ThisDocument_Shutdown` Programy obsługi zdarzeń i. Te programy obsługi zdarzeń są wywoływane, gdy dokument zostanie otwarty i zamknięty. Te programy obsługi zdarzeń umożliwiają zainicjowanie dostosowania podczas otwierania dokumentu oraz czyszczenie zasobów używanych przez dostosowanie po zamknięciu dokumentu. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

### <a name="to-add-a-second-paragraph-of-text-to-the-document-by-using-code"></a>Aby dodać drugi akapit tekstu do dokumentu przy użyciu kodu

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **ThisDocument**, a następnie kliknij pozycję **Wyświetl kod**.

     Plik kodu zostanie otwarty w programie Visual Studio.

2. Zastąp `ThisDocument_Startup` procedurę obsługi zdarzeń poniższym kodem. Gdy dokument zostanie otwarty, ten kod dodaje drugi akapit tekstu do dokumentu.

     [!code-vb[Trin_WordDocumentTutorial#1](../vsto/codesnippet/VisualBasic/FirstDocumentCustomization/ThisDocument.vb#1)]
     [!code-csharp[Trin_WordDocumentTutorial#1](../vsto/codesnippet/CSharp/FirstDocumentCustomization/ThisDocument.cs#1)]

    > [!NOTE]
    > Ten kod używa wartości indeksu 1 w celu uzyskania dostępu do pierwszego akapitu we <xref:Microsoft.Office.Tools.Word.Document.Paragraphs%2A> właściwości. Chociaż Visual Basic i Visual C# używają tablic opartych na liczbie 0, Dolna granica tablicy większości kolekcji w modelu obiektów programu Word to 1. Aby uzyskać więcej informacji, zobacz [pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md).

## <a name="test-the-project"></a>Testowanie projektu

### <a name="to-test-your-document"></a>Aby przetestować dokument

1. Naciśnij klawisz **F5** , aby skompilować i uruchomić projekt.

     Podczas kompilowania projektu, kod jest kompilowany do zestawu, który jest skojarzony z dokumentem. Program Visual Studio umieszcza kopię dokumentu i zestaw w folderze danych wyjściowych kompilacji dla projektu i konfiguruje ustawienia zabezpieczeń na komputerze deweloperskim w celu umożliwienia uruchomienia dostosowania. Aby uzyskać więcej informacji, zobacz [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md).

2. W dokumencie Sprawdź, czy widzisz następujący tekst.

     **Ten tekst został dodany za pomocą projektanta.**

     **Ten tekst został dodany za pomocą kodu.**

3. Zamknij dokument.

## <a name="clean-up-the-project"></a>Wyczyść projekt

 Po zakończeniu opracowywania projektu należy usunąć pliki z folderu danych wyjściowych kompilacji oraz ustawienia zabezpieczeń utworzone przez proces kompilacji.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Aby wyczyścić ukończony projekt na komputerze deweloperskim

1. W programie Visual Studio w menu **kompilacja** kliknij pozycję **czyste rozwiązanie**.

## <a name="next-steps"></a>Następne kroki

 Teraz, gdy utworzono podstawowe dostosowanie na poziomie dokumentu dla programu Word, możesz dowiedzieć się więcej na temat sposobu opracowywania dostosowań z tych tematów:

- Ogólne zadania programistyczne, które można wykonać w dostosowaniu na poziomie dokumentu: [dostosowania na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md).

- Zadania programistyczne, które są specyficzne dla dostosowań na poziomie dokumentu dla programu Word: [Word Solutions](../vsto/word-solutions.md).

- Za pomocą modelu obiektów programu Word: [Omówienie modelu obiektów programu](../vsto/word-object-model-overview.md)Word.

- Dostosowywanie interfejsu użytkownika programu Word, na przykład przez dodanie karty niestandardowej do wstążki lub utworzenie własnego okienka akcji: [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

- Używanie obiektów rozszerzonego programu Word dostarczonych przez rozwiązania pakietu Office w programie Visual Studio do wykonywania zadań, które nie są możliwe przy użyciu modelu obiektów programu Word (na przykład hostowanie formantów zarządzanych w dokumentach i Powiązywanie formantów Word z danymi przy użyciu modelu powiązań danych Windows Forms): [automatyzuje program Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md).

- Kompilowanie i debugowanie dostosowań na poziomie dokumentu dla programu Word: [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md).

- Wdrażanie dostosowań na poziomie dokumentu dla programu Word: [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Zobacz też

- [Omówienie programowania rozwiązań dla pakietu Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Rozwiązania programu Word](../vsto/word-solutions.md)
- [Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md)
- [Model obiektów programu Word — omówienie](../vsto/word-object-model-overview.md)
- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)
- [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md)
- [Szablony projektów pakietu Office — omówienie](../vsto/office-project-templates-overview.md)
