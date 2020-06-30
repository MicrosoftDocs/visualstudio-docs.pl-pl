---
title: 'Instrukcje: Tworzenie projektów Office w Visual Studio'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: c70668f2d4cb9597e00a7e3848b78b9f2ed49db7
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547566"
---
# <a name="how-to-create-office-projects-in-visual-studio"></a>Instrukcje: Tworzenie projektów Office w Visual Studio
  Programu można użyć [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] do utworzenia dodatku narzędzi VSTO i dostosowań na poziomie dokumentu dla aplikacji Microsoft Office. Aby uzyskać więcej informacji na temat tych typów projektów, zobacz [Omówienie tworzenia rozwiązań pakietu Office &#40;narzędzi VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-create-a-vsto-add-in-project"></a>Aby utworzyć projekt dodatku narzędzi VSTO

1. W menu **plik** wybierz pozycję **Nowy**  >  **projekt**. Jeśli zintegrowane środowisko programistyczne (IDE) jest ustawione na korzystanie z [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ustawień deweloperskich, w menu **plik** wybierz pozycję **Nowy**  >  **projekt**.

    Zostanie wyświetlone okno dialogowe **Nowy projekt**.

   > [!NOTE]
   > Projekty pakietu Office są domyślnie przeznaczone dla programu [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] . Aby uzyskać więcej informacji, zobacz [.NET Framework profilu klienta](/dotnet/framework/deployment/client-profile).

2. W okienku szablony w obszarze węzła dla języka, którego chcesz użyć, rozwiń węzeł **Office/SharePoint**.

3. Wybierz węzeł **Dodatki pakietu Office** .

4. Na liście szablonów projektu wybierz szablon projektu dodatku VSTO. Aby uzyskać listę dostępnych szablonów projektów dodatku VSTO, zobacz [Szablony projektów pakietu Office — omówienie](../vsto/office-project-templates-overview.md).

   > [!NOTE]
   > Jeśli szablony projektu nie są widoczne po wybraniu węzła **dodatków pakietu Office** , upewnij się, że w polu kombi w górnej części okna dialogowego jest zaznaczone pole wyboru **.NET Framework 4** lub nowszego. Szablony projektów pakietu Office są widoczne dla obu wersji .NET Framework.

5. W polu **Nazwa** wpisz nazwę projektu. Domyślnie nazwa projektu jest również używana jako nazwa rozwiązania.

6. W polu **Lokalizacja** wprowadź ścieżkę, w której chcesz utworzyć projekt. Można użyć ścieżek bezwzględnych i uniwersalnej konwencji nazewnictwa (UNC). Nie używaj protokołu HTTP, FTP ani innych ścieżek protokołu.

    Lokalizacje mają następujące formaty:

   * [*dysk*\]\:

   * \\\\*Serwer* \\ *Udostępnianie*

     Nie używaj tych znaków w lokalizacji:

   * Gwiazdka (*)

   * Kreska pionowa (|)

   * Dwukropek (:) (Z wyjątkiem litery dysku).

   * Podwójny cudzysłów (") (ścieżki zawierające spacje nie potrzebują cudzysłowu).

   * Mniejsze niż ( \< )

   * Większe niż (>)

   * Znak zapytania (?)

   * Znak procentu (%)

7. Wybierz przycisk **OK** .

   ::: moniker range="vs-2017"

   > [!NOTE]
   > Projekty dodatków są zawsze zapisywane podczas tworzenia. Nie można ich tworzyć jako projektów tymczasowych. Aby uzyskać więcej informacji na temat projektów tymczasowych, zobacz [tymczasowe projekty](../ide/creating-solutions-and-projects.md#create-a-temporary-project).

   ::: moniker-end

### <a name="to-create-a-document-level-customization-project"></a>Aby utworzyć projekt dostosowania na poziomie dokumentu

1. W menu **plik** wybierz pozycję **Nowy**  >  **projekt**. Jeśli środowisko IDE jest skonfigurowane do korzystania z ustawień tworzenia Visual Basic, w menu **plik** wybierz pozycję **Nowy**  >  **projekt**.

    Zostanie wyświetlone okno dialogowe **Nowy projekt**.

2. W okienku szablony w obszarze węzła dla języka, którego chcesz użyć, rozwiń węzeł **Office/SharePoint**.

3. Wybierz węzeł **Dodatki pakietu Office** .

4. Na liście szablonów projektu wybierz szablon projektu na poziomie dokumentu. Aby uzyskać listę dostępnych szablonów projektów na poziomie dokumentu, zobacz [Szablony projektów pakietu Office — omówienie](../vsto/office-project-templates-overview.md).

   > [!NOTE]
   > Jeśli szablony projektu nie są widoczne po wybraniu węzła **dodatków pakietu Office** , upewnij się, że jest zaznaczony **.NET Framework 4** lub nowszy.

5. W polu **Nazwa** wpisz nazwę projektu. Domyślnie ta nazwa jest również używana dla dokumentu. Jeśli środowisko IDE jest ustawione tak, aby korzystało z ustawień deweloperskich Visual C# lub ogólnych ustawień programistycznych, wprowadź również lokalizację i nazwę rozwiązania.

   > [!NOTE]
   > Nie można używać znaków zastępczych w ścieżce lokalizacji projektu ani w nazwie projektu. Ponadto, jeśli planujesz wdrożenie rozwiązania do użycia w trybie offline, znaki w nazwie projektu muszą pasować do specyfikacji protokołu HTTP.

6. Wybierz przycisk **OK** .

    Zostanie otwarty **kreator Visual Studio Tools dla programu Office Project** .

7. Wybierz opcję **Utwórz nowy dokument** , jeśli chcesz utworzyć nowy dokument dla rozwiązania, lub wybierz opcję **Kopiuj istniejący dokument** , jeśli chcesz dostosować istniejący dokument.

    W przypadku utworzenia nowego dokumentu należy określić nazwę w polu **Nazwa** i wybrać format dokumentu przy użyciu pola **Format** . Aby uzyskać więcej informacji na temat dostępnych formatów, zobacz [architektury dostosowań na poziomie dokumentu](../vsto/architecture-of-document-level-customizations.md).

    Jeśli używasz istniejącego dokumentu, określ lokalizację dokumentu w **pełnej ścieżce istniejącego pola dokumentu** . Można użyć ścieżek bezwzględnych i UNC. Nie używaj protokołu HTTP, FTP ani innych ścieżek protokołu do dokumentu.

    Lokalizacje mają następujące formaty:

   - [*dysk*\]\:

   - \\\\*Serwer* \\ *Udostępnianie*

     Nie używaj tych znaków w lokalizacji:

   - Gwiazdka (*)

   - Kreska pionowa (|)

   - Dwukropek (:) (Z wyjątkiem litery dysku).

   - Podwójny cudzysłów (") (ścieżki zawierające spacje nie potrzebują cudzysłowu).

   - Mniejsze niż ( \< )

   - Większe niż (>)

   - Znak zapytania (?)

   - Znak procentu (%)

   > [!NOTE]
   > Jeśli używasz istniejącego dokumentu w [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] projekcie, używaj tylko dokumentów, które zostały utworzone w lub skonwertowane do [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] . Podobnie, jeśli używasz istniejącego dokumentu w projekcie programu Word 2010, używaj tylko dokumentów utworzonych w programie lub przekonwertowanych do programu Word 2010. Niektóre funkcje zostaną wyłączone w dokumencie, jeśli używasz dokumentu, który został utworzony we wcześniejszej wersji programu Word. Jeśli spróbujesz napisać kod, który używa tych funkcji, mogą wystąpić błędy w projekcie. Aby przekonwertować dokument, otwórz go w programie [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub Word 2010 na karcie **plik** na wstążce wybierz pozycję **informacje**  >  **Konwertuj**.

8. Wybierz pozycję **Zakończ**.

9. Dodaj folder projektu i jego podfoldery do listy zaufanych lokalizacji w centrum zaufania w programie Word w następujących przypadkach:

   - Tworzysz dokument programu Word, który jest oparty na pliku *. docm* , a dokument zawiera projekt VBA lub hostuje Windows Forms formanty. Dodanie folderu projektu do listy zaufanych lokalizacji pomoże upewnić się, że dokument działa zgodnie z oczekiwaniami w czasie projektowania.

   - Tworzysz projekt szablonu programu Word, który jest oparty na pliku *. dotx* . Należy dodać folder projektu do listy zaufanych lokalizacji, aby można było uruchomić i debugować projekt.

     Aby uzyskać więcej informacji na temat dodawania dokumentu do zaufanych lokalizacji, zobacz witrynę sieci Web w Microsoft Office Online [Tworzenie, usuwanie lub zmienianie zaufanej lokalizacji plików](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).

## <a name="see-also"></a>Zobacz też
- [Szablony projektów pakietu Office — omówienie](../vsto/office-project-templates-overview.md)
- [Programowanie zespołowe rozwiązań pakietu Office](../vsto/collaborative-development-of-office-solutions.md)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
- [Wprowadzenie do programowania dodatków narzędzi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
