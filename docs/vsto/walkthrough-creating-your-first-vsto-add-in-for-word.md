---
title: 'Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Word'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- add-ins [Office development in Visual Studio], creating your first project
- Word [Office development in Visual Studio], creating your first project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ed5c5e5b03ce7ee0ffbd361b896f288f6b93a806
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64783405"
---
# <a name="walkthrough-create-your-first-vsto-add-in-for-word"></a>Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Word
  W tym instruktażu wprowadzającym pokazano, jak utworzyć dodatek narzędzi VSTO dla programu Microsoft Office Word. Funkcje, które tworzysz w tym rodzaju rozwiązanie, są dostępne dla samej aplikacji, niezależnie od tego, które dokumenty są otwarte.

 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie projektu dodatku VSTO dla programu Word.

- Pisanie kodu, który używa modelu obiektów programu Word do dodawania tekstu do dokumentu po jego zapisaniu.

- Kompilowanie i uruchamianie projektu w celu jego przetestowania.

- Czyszczenie ukończonego projektu, aby dodatek VSTO nie był już automatycznie uruchamiany na komputerze deweloperskim.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-the-project"></a>Tworzenie projektu

### <a name="to-create-a-new-word-vsto-add-in-project-in-visual-studio"></a>Aby utworzyć nowy projekt dodatku VSTO programu Word w programie Visual Studio

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

3. W okienku szablony rozwiń pozycję **Visual C#** lub **Visual Basic**, a następnie rozwiń węzeł **Office/SharePoint**.

4. W rozwiniętym węźle **Office/SharePoint** wybierz węzeł **Dodatki pakietu Office** .

5. Na liście szablonów projektu wybierz projekt dodatku VSTO programu Word.

6. W polu **Nazwa** wpisz **FirstWordAddIn**.

7. Kliknij przycisk **OK**.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tworzy projekt **FirstWordAddIn** i otwiera plik kodu ThisAddIn w edytorze.

## <a name="write-code-to-add-text-to-the-saved-document"></a>Napisz kod, aby dodać tekst do zapisanego dokumentu
 Następnie Dodaj kod do pliku kodu ThisAddIn. Nowy kod używa modelu obiektów programu Word do dodawania tekstu standardowego do każdego zapisanego dokumentu. Domyślnie plik kodu ThisAddIn zawiera następujący wygenerowany kod:

- Częściowa definicja `ThisAddIn` klasy. Ta klasa udostępnia punkt wejścia dla kodu i zapewnia dostęp do modelu obiektów programu Word. Aby uzyskać więcej informacji, zobacz [dodatki narzędzi VSTO dla programu](../vsto/programming-vsto-add-ins.md). Pozostała część `ThisAddIn` klasy jest zdefiniowana w ukrytym pliku kodu, który nie powinien być modyfikowany.

- `ThisAddIn_Startup` `ThisAddIn_Shutdown` Programy obsługi zdarzeń i. Te programy obsługi zdarzeń są wywoływane, gdy program Word ładuje i zwalnia dodatek narzędzi VSTO. Te programy obsługi zdarzeń umożliwiają zainicjowanie dodatku VSTO podczas ładowania i oczyszczenie zasobów używanych przez dodatek VSTO po jego wyładowaniu. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

### <a name="to-add-a-paragraph-of-text-to-the-saved-document"></a>Aby dodać akapit tekstu do zapisanego dokumentu

1. W pliku kodu ThisAddIn Dodaj następujący kod do `ThisAddIn` klasy. Nowy kod definiuje procedurę obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> zdarzenia, które jest zgłaszane po zapisaniu dokumentu.

    Gdy użytkownik zapisuje dokument, program obsługi zdarzeń dodaje nowy tekst na początku dokumentu.

    [!code-vb[Trin_WordAddInTutorial#1](../vsto/codesnippet/VisualBasic/FirstWordAddIn/ThisAddIn.vb#1)]
    [!code-csharp[Trin_WordAddInTutorial#1](../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs#1)]

   > [!NOTE]
   > Ten kod używa wartości indeksu 1 w celu uzyskania dostępu do pierwszego akapitu w <xref:Microsoft.Office.Interop.Word._Document.Paragraphs%2A> kolekcji. Chociaż Visual Basic i Visual C# używają tablic opartych na liczbie 0, Dolna granica tablicy większości kolekcji w modelu obiektów programu Word to 1. Aby uzyskać więcej informacji, zobacz [pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md).

2. Jeśli używasz języka C#, Dodaj następujący kod wymagany do `ThisAddIn_Startup` programu obsługi zdarzeń. Ten kod służy do łączenia programu `Application_DocumentBeforeSave` obsługi zdarzeń ze <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> zdarzeniem.

    [!code-csharp[Trin_WordAddInTutorial#2](../vsto/codesnippet/CSharp/FirstWordAddIn/ThisAddIn.cs#2)]

   Aby zmodyfikować dokument po jego zapisaniu, poprzednie przykłady kodu używają następujących obiektów:

- `Application`Pole `ThisAddIn` klasy. `Application`Pole zwraca <xref:Microsoft.Office.Interop.Word.Application> obiekt, który reprezentuje bieżące wystąpienie wyrazu.

- `Doc`Parametr programu obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> zdarzenia. `Doc`Parametr jest <xref:Microsoft.Office.Interop.Word.Document> obiektem, który reprezentuje zapisany dokument. Aby uzyskać więcej informacji, zobacz temat [Omówienie modelu obiektów programu Word](../vsto/word-object-model-overview.md).

## <a name="test-the-project"></a>Testowanie projektu

### <a name="to-test-the-project"></a>Aby przetestować projekt

1. Naciśnij klawisz **F5** , aby skompilować i uruchomić projekt.

     Podczas kompilowania projektu, kod jest kompilowany do zestawu, który jest dołączony do folderu danych wyjściowych kompilacji dla projektu. Program Visual Studio tworzy również zestaw wpisów rejestru, które umożliwiają programowi Word odnalezienie i załadowanie dodatku VSTO oraz skonfigurowanie ustawień zabezpieczeń na komputerze deweloperskim w celu umożliwienia uruchomienia dodatku VSTO. Aby uzyskać więcej informacji, zobacz [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md).

2. W programie Word Zapisz aktywny dokument.

3. Sprawdź, czy do dokumentu został dodany następujący tekst.

     **Ten tekst został dodany za pomocą kodu.**

4. Zamknij program Word.

## <a name="clean-up-the-project"></a>Wyczyść projekt
 Po zakończeniu opracowywania projektu, Usuń zestaw dodatków VSTO, wpisy rejestru i ustawienia zabezpieczeń z komputera deweloperskiego. W przeciwnym razie dodatek narzędzi VSTO będzie nadal uruchamiany za każdym razem, gdy otworzysz program Word na komputerze deweloperskim.

### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Aby wyczyścić ukończony projekt na komputerze deweloperskim

1. W programie Visual Studio w menu **kompilacja** kliknij pozycję **czyste rozwiązanie**.

## <a name="next-steps"></a>Następne kroki
 Po utworzeniu podstawowego dodatku narzędzi VSTO dla programu Word można dowiedzieć się więcej o sposobach opracowywania dodatków VSTO z następujących tematów:

- Ogólne zadania programistyczne, które można wykonywać w dodatkach narzędzi VSTO: [programowe dodatki narzędzi VSTO](../vsto/programming-vsto-add-ins.md).

- Zadania programistyczne, które są specyficzne dla dodatków programu Word VSTO: [rozwiązania programu Word](../vsto/word-solutions.md).

- Za pomocą modelu obiektów programu Word: [Omówienie modelu obiektów programu](../vsto/word-object-model-overview.md)Word.

- Dostosowywanie interfejsu użytkownika programu Word, na przykład przez dodanie karty niestandardowej do wstążki lub utworzenie własnego niestandardowego okienka zadań: [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

- Kompilowanie i debugowanie dodatków narzędzi VSTO dla programu Word: [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md).

- Wdrażanie dodatków narzędzi VSTO dla programu Word: [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md).

## <a name="see-also"></a>Zobacz też
- [Omówienie programowania rozwiązań dla pakietu Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Rozwiązania programu Word](../vsto/word-solutions.md)
- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)
- [Model obiektów programu Word — omówienie](../vsto/word-object-model-overview.md)
- [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)
- [Tworzenie rozwiązań pakietu Office](../vsto/building-office-solutions.md)
- [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md)
- [Szablony projektów pakietu Office — omówienie](../vsto/office-project-templates-overview.md)
