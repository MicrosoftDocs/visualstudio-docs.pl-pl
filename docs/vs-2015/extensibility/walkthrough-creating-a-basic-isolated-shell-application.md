---
title: 'Wskazówki: Tworzenie podstawowego Isolated Shell aplikacji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 55
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 901bbf12c9c1d153b84b3ed74f6ae8e97ebb2c9b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51777321"
---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>Wskazówki: Tworzenie podstawowej aplikacji Isolated Shell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak utworzyć rozwiązanie izolowanej powłoki, dostosowywanie okna Narzędzie Pomoc na temat i Utwórz program instalacyjny, który instaluje programu isolated shell.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby skorzystać z tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md). Aby wdrożyć programu isolated shell, należy również użyć pakietu redystrybucyjnego programu Visual Studio Shell (Isolated).  
  
## <a name="creating-an-isolated-shell-solution"></a>Tworzenie rozwiązań Isolated Shell  
 W tej sekcji pokazano, jak używać programu Visual Studio Shell izolowane szablonu projektu do tworzenia rozwiązania izolowanej powłoki. Rozwiązanie zawiera następujące projekty:  
  
-   *SolutionName*. Projekt AboutBoxPackage umożliwia dostosowanie wyglądu pomocy/pole informacji.  
  
-   Projekt ShellExtensionsVSIX, który zawiera plik source.extension.vsixmanifest, który definiuje różne składniki aplikacji isolated shell.  
  
-   *SolutionName* projektu, który tworzy plik wykonywalny, który wywołuje aplikacji isolated shell. Ten projekt zawiera folder dostosowania powłoki, który umożliwia dostsowywanie wygląd i zachowanie aplikacji isolated shell.  
  
-   *SolutionName* projekt interfejsu użytkownika, który tworzy definiujący aktywne menu poleceń i możliwych do zlokalizowania ciągi zestawu satelickiego.  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>Aby utworzyć rozwiązanie podstawowe izolowane powłoki  
  
1.  Otwórz program Visual Studio i Utwórz nowy projekt.  
  
2.  W **nowy projekt** okna, rozwiń węzeł **inne typy projektów** i następnie **rozszerzalności**. Wybierz **Visual Studio Shell izolowane** szablonu projektu.  
  
3.  Nadaj projektowi nazwę `MyVSShellStub` i określ lokalizację. Upewnij się, że **Utwórz katalog rozwiązania** jest zaznaczone, a następnie kliknij przycisk **OK**.  
  
     Nowe rozwiązanie jest wyświetlana w **Eksploratora rozwiązań**.  
  
4.  Skompiluj rozwiązanie, a następnie rozpocząć debugowanie aplikacji isolated shell.  
  
     Program Visual Studio, pojawi się w izolowanej powłoki. Na pasku tytułu odczytuje **MyVSShellStub**. Ikonę na pasku tytułu jest generowany na podstawie \MyVSShellStub\Resource Files\ApplicationIcon.ico.  
  
## <a name="customizing-the-application-name-and-icon"></a>Dostosowywanie nazwy aplikacji i ikony  
 Możesz chcieć oznaczyć aplikację przy użyciu nazwy firmy i jej logo na pasku tytułu. Poniższe kroki pokazują jak zmienić nazwy i ikony, które są wyświetlane na pasku tytułu aplikacji niestandardowych, zmieniając plik definicji pakietu MyVSShellStub.Application.pkgdef.  
  
#### <a name="to-customize-the-application-name-and-icon"></a>Aby dostosować nazwy aplikacji i ikony  
  
1.  W projekcie MyVSShellStub Otwórz \Shell Customization\MyVSShellStub.Application.pkgdef.  
  
2.  Zmiana `AppName` wartość elementu do **"AppName" = "Fabrikam utworów muzycznych Editor"**  
  
3.  Aby zmienić ikony aplikacji, skopiuj inną ikonę w katalogu \MyVSShellStub\MyVSShellStub\MyVSShellStub\. Zmień nazwę istniejącego pliku ApplicationIcon.ico ApplicationIcon1.ico. Zmień nazwę nowego pliku ApplicationIcon.ico.  
  
4.  Skompiluj rozwiązanie, a następnie rozpocząć debugowanie. Środowisko IDE programu isolated shell pojawia się. Na pasku tytułu ma Twoja nowa ikona obok słowa **edytora utworów muzycznych Fabrikam**.  
  
## <a name="customizing-the-default-web-browser-home-page"></a>Dostosowanie strony domowej przeglądarki sieci Web domyślne  
 W tej sekcji pokazano, jak zmienić domyślną stronę główną programu **przeglądarki sieci Web** okna, zmieniając plik definicji pakietu.  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>Aby dostosować domyślną stronę główną przeglądarki sieci Web  
  
1. W pliku MyVSShellStub.Application.pkgdef zmienić `DefaultHomePage` wartość elementu "<http://www.microsoft.com>".  
  
2. Ponownie skompiluj projekt MyVSShellStub.  
  
3. Skompiluj rozwiązanie, a następnie rozpocząć debugowanie.  
  
4. W **widok / inne Windows**, kliknij przycisk **przeglądarki sieci Web**. **Przeglądarki sieci Web** oknie zostanie wyświetlona strona główna firmy Microsoft Corporation.  
  
## <a name="removing-the-print-command"></a>Usuwanie polecenia drukowania  
 Zawiera zestaw deklaracji w postaci pliku vsct w projekcie interfejsu użytkownika programu shell w trybie izolowanym `<Define name=No_` *elementu*`>`, gdzie *elementu* jest jednym z menu programu Visual Studio standardowe i polecenia.  
  
 W przypadku pozbawionym znaków komentarza wierszu deklaracji tego menu lub poleceń jest wykluczony z programu isolated shell. Z drugiej strony jeśli jest ujęty w deklaracji, menu lub poleceń jest uwzględniony w programu isolated shell.  
  
 W poniższych krokach Usuń komentarz polecenia drukowania w pliku vsct.  
  
#### <a name="to-remove-the-print-command"></a>Aby usunąć polecenia drukowania  
  
1.  Upewnij się, że **drukowania** polecenia pojawi się w **pliku** menu w aplikacji isolated shell.  
  
2.  W projekcie MyVSShellStubUI Otwórz \Resource Files\MyVSShellStubUI.vsct do edycji.  
  
3.  Usuń znaczniki komentarza tego wiersza:  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4.  Spowoduje to usunięcie polecenia drukowania.  
  
5.  Rozpocznij debugowanie aplikacji isolated shell. Upewnij się, że **pliku / drukowanie** polecenia został usunięty.  
  
## <a name="removing-features-from-the-isolated-shell"></a>Usuwanie funkcji z programu Isolated Shell  
 Możesz usunąć niektóre pakiety, które są ładowane z programem Visual Studio, edytując plik pkgundef, jeśli nie chcesz tych funkcji w aplikacji niestandardowej izolowane powłoki. Należy określić pakiet w jeden z podkluczy klucza rejestru \Packages $ $RootKey.  
  
> [!NOTE]
>  Aby znaleźć funkcje identyfikatorów GUID programu Visual Studio, zobacz [identyfikatorów GUID programu Visual Studio funkcje pakietu](../extensibility/package-guids-of-visual-studio-features.md).  
  
 Poniższa procedura pokazuje, jak można usunąć pliku XML edytora z programu isolated shell.  
  
#### <a name="to-remove-the-xml-editor"></a>Aby usunąć edytora XML  
  
1.  Otwórz plik MyVSShellStub.pkgundef w folderze projektu MyVSShellStub dostosowania powłoki.  
  
2.  Usuń komentarz następujący wiersz:  
  
     [$RootKey$ \Packages\\{87569308-4813-40a0-9cd0-d7a30838ca3f}]  
  
3.  Ponownie skompiluj rozwiązanie, a następnie rozpocząć debugowanie programu isolated shell. Otwórz plik XML, na przykład \MyVSShellStub\MyVSShellStub\MyVSShellStubUI\MyVSShellStubUI.vsct. Sprawdź, czy słowa kluczowe XML w pliku nie jest pokolorowany i że wpisanie "<" w wierszu nie uaktywnia etykietki narzędzi XML.  
  
## <a name="customizing-the-helpabout-box"></a>Dostosowywanie Pomoc/informacje pole  
 Można dostosować pomoc/o polu, którym zostanie utworzony jako część szablonu projektu shell w trybie izolowanym.  
  
#### <a name="to-customize-the-company-name"></a>Aby dostosować nazwę firmy  
  
1.  Nazwa firmy, informacje o prawach autorskich, wersja produktu i opis produktu znajdują się w projekcie MyVSShellStub.AboutBoxPackage w pliku \Properties\AssemblyInfo.cs. Otwórz ten plik.  
  
2.  Zmiany `AssemblyCompany` wartość, która **Fabrikam**, `AssemblyProduct` i `AssemblyTitle` wartości **edytora utworów muzycznych Fabrikam**i `AssemblyCopyright` wartość, która **Copyright © Firma Fabrikam 2015**:  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")]  
    [assembly: AssemblyDescription("")]  
    [assembly: AssemblyConfiguration("")]  
    [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")]  
    [assembly: AssemblyProduct("Fabrikam Music Editor ")]  
    [assembly: AssemblyCopyright("Copyright © Fabrikam 2015”)]  
    ```  
  
3.  Aby dodać opis produktu, należy zmienić `AssemblyDescription` wartość **opis edytora muzyka firmy Fabrikam.**:  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4.  Rozpocznij debugowanie i Otwórz w aplikacji isolated shell **Pomoc / informacje** pole. Zmieniono parametry powinny być widoczne. Tytuł Pomoc/informacje pola jest taka sama jak `AssemblyTitle` wartość AssemblyInfo.cs.  
  
5.  Właściwości **Pomoc/informacje** pola znajdują się w pliku MyVSShellStub.AboutBoxPackage\AboutBox.xaml. Aby zmienić szerokość pomocy/pole informacji, przejdź do `AboutDialogStyle` blokowania i ustaw `Width` właściwości do 200:  
  
    ```  
    <Style x:Key="AboutDialogStyle" TargetType="Window">  
        <Setter Property="Height" Value="Auto" />  
        <Setter Property="Width" Value="200" />  
        <Setter Property="ShowInTaskbar" Value="False" />  
        <Setter Property="ResizeMode" Value="NoResize" />  
        <Setter Property="WindowStyle" Value="SingleBorderWindow" />  
        <Setter Property="SizeToContent" Value="Height" />  
    </Style>  
    ```  
  
6.  Ponownie skompiluj rozwiązanie, a następnie rozpocząć debugowanie programu isolated shell. Pomoc/pole informacji powinny być mniej więcej w kształcie kwadratu.  
  
## <a name="before-you-deploy-the-isolated-shell-application"></a>Przed wdrożeniem aplikacji Isolated Shell  
 Usługi aplikacji isolated shell można zainstalować na dowolnym komputerze, który zawiera pakiet redystrybucyjny programu Visual Studio Shell (Isolated). Aby uzyskać więcej informacji na temat pakietu redystrybucyjnego, zobacz [pobieranie Visual Studio Extensibility](http://go.microsoft.com/fwlink/?LinkID=119298) witryny sieci Web.  
  
## <a name="deploying-the-isolated-shell-application"></a>Wdrażanie aplikacji Isolated Shell  
 Możesz wdrożyć Twojej aplikacji isolated shell na komputerze docelowym, tworząc projekt Instalatora. Należy określić te rzeczy:  
  
- Układ foldery i pliki na komputerze docelowym.  
  
- Warunki uruchamiania, które gwarantuje, że .NET Framework i Visual Studio powłoki środowiska uruchomieniowego są instalowane na komputerze docelowym.  
  
  W poniższej procedurze należy zainstalować InstallShield Limited Edition na komputerze.  
  
#### <a name="to-create-the-setup-project"></a>Aby utworzyć projekt instalacji  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł rozwiązania, a następnie kliknij przycisk **Dodaj nowy projekt**.  
  
2. W **nowy projekt** okna dialogowego rozwiń **inne typy projektów** , a następnie wybierz **instalacja i wdrożenie**. Wybierz szablon InstallShield. Nazwa nowego projektu `MySetup` a następnie kliknij przycisk **OK**.  
  
3. Jeśli InstallShield Limited Edition jest już zainstalowany, przejdź do następnego kroku.  
  
    Jeśli nie zainstalowano jeszcze programu InstallShield Limited Edition, zostanie wyświetlona strona pobierania programu InstallShield. Postępuj zgodnie z instrukcjami, aby pobrać i zainstalować produkt, wybierając wersję InstallShield, który jest zgodny z wersją programu Visual Studio. Należy określić, czy można zarejestrować instalacji programu InstallShield lub użyć go w wersji ewaluacyjnej. Po zakończeniu instalacji należy ponownie uruchomić program Visual Studio.  
  
   > [!IMPORTANT]
   >  Przed utworzeniem projektu InstallShield, należy uruchomić program Visual Studio jako administrator. Jeśli nie zrobisz, zostanie wyświetlony błąd, podczas kompilowania projektu.  
  
   Następne kroki pokazują, jak skonfigurować projekt Instalatora.  
  
> [!IMPORTANT]
>  Upewnij się, czy został wcześniej utworzony konfiguracji wydania projektu izolowanej powłoki co najmniej raz przed rozpoczęciem konfigurowania projektu Instalatora.  
  
#### <a name="to-configure-the-setup-project"></a>Aby skonfigurować Projekt instalacji  
  
1.  W **Eksploratora rozwiązań**w obszarze **MySetup** projektu, wybierz **Asystent projektu**. W dolnym wierszu **Asystent projektu** oknie Wybierz **informacje o aplikacji**. Wprowadź **Fabrikam** jako nazwę swojej firmy i **edytora utworów muzycznych Fabrikam** jako nazwę swojej aplikacji. Wybierz do przodu strzałkę w prawym dolnym rogu **Asystent projektu**.  
  
2.  Wybierz **tak** w obszarze **aplikacji wymaga oprogramowania do zainstalowania na maszynie?** , a następnie wybierz **programu Microsoft .NET Framework 4.5 pełny pakiet**.  
  
3.  Wybierz **pliki aplikacji** znajdujący się w dolnej części okna i upewnij się, że **edytora utworów muzycznych Fabrikam** jest wybrany folder.  
  
4.  Wybierz **Dodaj pliki** przycisku. W **Dodaj pliki** okna dialogowego Dodaj następujące pliki z **MyVSShellStub\Release** folderu:  
  
    1.  MyVSShellStub.exe.config  
  
    2.  DebuggerProxy.dll  
  
    3.  DebuggerProxy.dll.manifest  
  
    4.  MyVSShellStub.pkgdef  
  
    5.  MyVSShellStub.pkgundef  
  
    6.  MyVSShellStub.winprf  
  
    7.  Splash.bmp  
  
5.  Kliknij przycisk **Dodaj dane wyjściowe projektu** przycisku i Dodaj **MyVSShellStub/podstawowe wyjście**. Kliknij przycisk **OK**.  
  
6.  W okienku po lewej stronie w obszarze **komputera docelowego**, kliknij prawym przyciskiem myszy **Fabrikam utworów muzycznych edytora [INSTALLDIR]** węzeł i Dodaj **nowy Folder** o nazwie **rozszerzenia** .  
  
7.  Kliknij prawym przyciskiem myszy **rozszerzenia** węzła w okienku po lewej stronie i Dodaj nowy folder o nazwie **aplikacji**.  
  
8.  Wybierz **aplikacji** folder i kliknij przycisk **Dodaj dane wyjściowe projektu** przycisk, a następnie wybierz główny wynik projektu MyVSShellStub.AboutBoxPackage.  
  
9. Kliknij przycisk **Dodaj pliki** znajdujący się i w folderze \MyVSShellStub\Release\Extensions\Application\ należy dodać następujące pliki:  
  
    -   MyVSShellStub.AboutBoxPackage.pkgdef  
  
    -   MyVSShellStub.Application.pkgdef  
  
10. Kliknij prawym przyciskiem myszy **Fabrikam utworów muzycznych edytora [INSTALLDIR]** węzła w okienku po lewej stronie i Dodaj nowy folder o nazwie **1033**.  
  
11. Wybierz 1033 folder, a następnie kliknij przycisk **Dodaj dane wyjściowe projektu** przycisk, a następnie zaznacz główny wynik projektu MyVSShellStubUI.  
  
12. Przenieś do **skróty aplikacji** okna.  
  
13. Kliknij przycisk **New** do tworzenia skrótów i wybierz **\Fabrikam\Fabrikam Music Editor\MyVSShellStub.Primary Output [Folderprogramfiles]**.  
  
14. Przenieś do **wywiad instalacji** okienka.  
  
15. Ustaw wszystkie elementy **nie**.  
  
16. W **Eksploratora rozwiązań**, w projekcie MySetup Otwórz **zdefiniować wymagania dotyczące konfiguracji i akcji \ wymagania**. **Wymagania** zostanie otwarte okno.  
  
17. Kliknij prawym przyciskiem myszy **wymagania dotyczące oprogramowania System** i wybierz **Utwórz nowy warunek uruchomienia**. **Kreatora wyszukiwania systemu** pojawia się.  
  
18. W **co chcesz znaleźć?** okienku wybierz **wpis rejestru** listy rozwijanej i kliknij przycisk **dalej**.  
  
19. W **jak chcesz jej szukać?** okienku wybierz **HKEY_LOCAL_MACHINE** jako katalogu głównego rejestru. Wprowadź **SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** w 64-bitowych systemach lub **SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** dla systemów 32-bitowych, a następnie wprowadź  **Zainstaluj** jako wartości rejestru. Kliknij przycisk **Dalej**.  
  
20. W **co chcesz zrobić z wartością?** okienku, wprowadź **ten produkt wymaga programu Visual Studio 2015 izolowane powłoki pakiet redystrybucyjny programu do zainstalowania.** jako wyświetlany tekst i kliknij przycisk **Zakończ**.  
  
21. Ponownie skompiluj rozwiązanie izolowanej powłoki, aby utworzyć projekt Instalatora.  
  
     Plik setup.exe można znaleźć w następującym folderze:  
  
     \MyVSShellStub\MySetup\MySetup\Express\SingleImage\DiskImages\DISK1  
  
## <a name="testing-the-installation-program"></a>Testowanie Program instalacyjny  
 Aby przetestować instalację, skopiuj plik setup.exe na inny komputer i uruchomić plik wykonywalny Instalatora. Można uruchomić aplikacji isolated shell.

