---
title: 'Instrukcje: Tworzenie projektów Office w Visual Studio'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.SelectDocWizard.Page1
- VST.SelectDocWizard.Http
- VST.SelectDocWizard.Extension
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], creating projects
- Office applications [Office development in Visual Studio], creating
- Office projects [Office development in Visual Studio]
- projects [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], creating projects
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 27b0a4c93d6b8143b81b960a9b5f4a2158e7b721
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57868175"
---
# <a name="how-to-create-office-projects-in-visual-studio"></a>Instrukcje: Tworzenie projektów Office w Visual Studio
  Możesz użyć [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] do tworzenia dodatku narzędzi VSTO i na poziomie dokumentu dostosowania aplikacji pakietu Microsoft Office. Aby uzyskać więcej informacji na temat tych typów projektów, zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-create-a-vsto-add-in-project"></a>Aby utworzyć projekt dodatku narzędzi VSTO

1. Na **pliku** menu, wybierz **New** > **projektu**. Jeśli Twoje zintegrowanego środowiska programistycznego (IDE) jest skonfigurowany do używania [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ustawieniami środowiska deweloperskiego na **pliku** menu, wybierz **New** > **projektu**.

    **Nowy projekt** pojawi się okno dialogowe.

   > [!NOTE]
   >  Office Project jest docelowy [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] domyślnie. Aby uzyskać więcej informacji, zobacz [profil klienta .NET Framework](/dotnet/framework/deployment/client-profile).

2. W okienku szablonów, w obszarze węzła dla języka, którego chcesz użyć, rozwiń **Office/SharePoint**.

3. Wybierz **dodatków pakietu Office** węzła.

4. Na liście szablonów projektu wybierz szablon projektu dodatku narzędzi VSTO. Aby uzyskać listę dostępnych szablonów dodatku narzędzi VSTO dla programów project, zobacz [Przegląd szablony projektu pakietu Office](../vsto/office-project-templates-overview.md).

   > [!NOTE]
   >  Jeśli szablony projektu nie są widoczne po wybraniu **dodatków pakietu Office** węzła, upewnij się, że **.NET Framework 4** lub nowszej jest zaznaczona w polu kombi na górze okna dialogowego. Szablony projektów pakietu Office są widoczne dla obu wersji systemu .NET Framework.

5. W **nazwa** wpisz nazwę dla projektu. Domyślnie nazwa projektu jest również używany jako nazwa rozwiązania.

6. W **lokalizacji** wprowadź ścieżkę, w której chcesz utworzyć projekt. Można używać bezwzględnych i uniwersalnej naming convention (UNC) ścieżek. Nie używaj HTTP, FTP ani innych ścieżek protokołu.

    Lokalizacje mają następujące formaty:

   * [*drive*\]\:

   * \\\\*Serwer*\\*udziału*

     Nie używaj tych znaków w lokalizacji:

   * Gwiazdka (*)

   * Kreski pionowej (|)

   * Dwukropek (:) (Z wyjątkiem następujących literę dysku.)

   * Podwójny cudzysłów (") (ścieżki zawierające spacje nie potrzebują znaków cudzysłowu.)

   * Mniej niż (\<)

   * Większe niż (>)

   * Znak zapytania (?)

   * Znak procentu (%)

7. Wybierz **OK** przycisku.

   ::: moniker range="vs-2017"

   > [!NOTE]
   > Projekty dodatków są zawsze zapisywane podczas ich tworzenia. Nie można ich tworzyć jako projektów tymczasowych. Aby uzyskać więcej informacji na temat projektów tymczasowych, zobacz [projektów tymczasowych](../ide/creating-solutions-and-projects.md#create-a-temporary-project).

   ::: moniker-end

### <a name="to-create-a-document-level-customization-project"></a>Aby utworzyć projekt dostosowania na poziomie dokumentu

1. Na **pliku** menu, wybierz **New** > **projektu**. Jeśli środowisko IDE jest ustawione na korzystanie z ustawienia programowania Visual Basic, **pliku** menu, wybierz **New** > **projektu**.

    **Nowy projekt** pojawi się okno dialogowe.

2. W okienku szablonów, w obszarze węzła dla języka, którego chcesz użyć, rozwiń **Office/SharePoint**.

3. Wybierz **dodatków pakietu Office** węzła.

4. Na liście szablonów projektu wybierz szablon projektu na poziomie dokumentu. Aby uzyskać listę szablonów dostępnych projektów na poziomie dokumentu, zobacz [Przegląd szablony projektu pakietu Office](../vsto/office-project-templates-overview.md).

   > [!NOTE]
   > Jeśli szablony projektu nie są widoczne po wybraniu **dodatków pakietu Office** węzła, upewnij się, że **.NET Framework 4** lub nowszej jest zaznaczone.

5. W **nazwa** wpisz nazwę dla projektu. Domyślnie ta nazwa jest także używana dla dokumentu. Jeśli środowisko IDE jest ustawione do użycia z ustawieniami środowiska deweloperskiego Visual C# lub ogólnych ustawień programistycznych, również wprowadź lokalizację i nazwę rozwiązania.

   > [!NOTE]
   > Nie możesz używać znaków zastępczych w ścieżce lokalizacji projektu lub w nazwie projektu. Ponadto jeśli planujesz wdrożyć rozwiązanie do użytku w trybie offline, znaki w nazwie projektu muszą być zgodne specyfikacji protokołu HTTP.

6. Wybierz **OK** przycisku.

    **Visual Studio Tools dla pakietu Office, Kreator projektu** zostanie otwarty.

7. Wybierz **Utwórz nowy dokument** Jeśli chcesz utworzyć nowy dokument dla rozwiązania, lub wybierz **Kopiuj istniejący dokument** Jeśli chcesz dostosować istniejący dokument.

    Jeśli tworzysz nowy dokument, należy określić nazwę w **nazwa** pole, a następnie wybierz format dokumentu za pomocą **Format** pole. Aby uzyskać więcej informacji na temat dostępnych formatów, zobacz [Architektura dostosowywania na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md).

    Jeśli używasz istniejącego dokumentu, należy określić lokalizację dokumentu w **Pełna ścieżka istniejącego dokumentu** pole. Można użyć ścieżek bezwzględnych i UNC. Nie używaj HTTP, FTP ani innych ścieżek protokołu do dokumentu.

    Lokalizacje mają następujące formaty:

   - [*drive*\]\:

   - \\\\*Serwer*\\*udziału*

     Nie używaj tych znaków w lokalizacji:

   - Gwiazdka (*)

   - Kreski pionowej (|)

   - Dwukropek (:) (Z wyjątkiem następujących literę dysku.)

   - Podwójny cudzysłów (") (ścieżki zawierające spacje nie potrzebują znaków cudzysłowu.)

   - Mniej niż (\<)

   - Większe niż (>)

   - Znak zapytania (?)

   - Znak procentu (%)

   > [!NOTE]
   >  Jeśli używasz istniejącego dokumentu w [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] projektu, używaj tylko dokumentów, które zostały utworzone w lub przekonwertowane na [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]. Podobnie jeśli używasz istniejącego dokumentu w programie 2010 project, używaj tylko dokumentów, które zostały utworzone w lub przekonwertowane na Word 2010. Niektóre funkcje zostanie wyłączona w dokumencie, jeśli korzystasz z dokumentu, który został utworzony we wcześniejszej wersji programu Word. Jeśli próbujesz napisać kod, który używa tych funkcji, mogą wystąpić błędy w projekcie. Aby przekonwertować dokument, otwórz go w [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub Word 2010 na **pliku** karty na Wstążce, wybierz polecenie **informacje** > **przekonwertować**.

8. Wybierz **Zakończ**.

9. Dodaj folder projektu i jego podfoldery do listy zaufanych lokalizacji w Centrum zaufania w programie Word w następujących przypadkach:

   - Tworzysz dokument programu Word, który jest oparty na *docm* pliku, a dokument zawiera projekt VBA lub obsługuje formanty Windows Forms. Dodawanie folderu projektu do listy zaufanych lokalizacji może pomóc upewnić się, że dokument działa zgodnie z oczekiwaniami w czasie projektowania.

   - Tworzysz projekt szablonu programu Word, który jest oparty na *dotx* pliku. Folder projektu należy dodać do listy zaufanych lokalizacji tak, aby można uruchamiać i debugować projektu.

     Aby uzyskać więcej informacji na temat sposobu dodawania dokumentu do zaufanej lokalizacji, zobacz witryny sieci web Microsoft Office Online [Utwórz, usuń lub zmień zaufanej lokalizacji plików](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).

## <a name="see-also"></a>Zobacz także
- [Omówienie szablonów projektu pakietu Office](../vsto/office-project-templates-overview.md)
- [Programowanie zespołowe rozwiązań pakietu Office](../vsto/collaborative-development-of-office-solutions.md)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
- [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
