---
title: 'Przewodnik: Tworzenie podstawowej aplikacji powłoki izolowanej | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, walkthroughs
- Shell [Visual Studio], walkthroughs
- walkthroughs [Visual Studio], isolated shell-based application
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 55
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b6dc84dd8d9f19012c4d09ba9bfd974ec181b9f6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74291265"
---
# <a name="walkthrough-creating-a-basic-isolated-shell-application"></a>Przewodnik: Tworzenie podstawowej aplikacji powłoki izolowanej
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak utworzyć rozwiązanie izolowanej powłoki, dostosować okno Pomoc na temat narzędzia i utworzyć program instalacyjny, który zainstaluje izolowaną powłokę.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby skorzystać z tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Aby wdrożyć powłokę izolowaną, należy również użyć pakietu redystrybucyjnego programu Visual Studio Shell (izolowany).  
  
## <a name="creating-an-isolated-shell-solution"></a>Tworzenie rozwiązania izolowanej powłoki  
 W tej sekcji pokazano, jak utworzyć rozizolowane rozwiązanie powłoki przy użyciu szablonu projektu izolowanego programu Visual Studio Shell. Rozwiązanie zawiera następujące projekty:  
  
- *Rozwiązanie*. Projekt AboutBoxPackage, który umożliwia dostosowanie wyglądu pola pomoc/informacje.  
  
- Projekt ShellExtensionsVSIX, który zawiera plik source. Extension. vsixmanifest, który definiuje różne składniki aplikacji izolowanej powłoki.  
  
- Projekt *SolutionName* , który tworzy plik wykonywalny, który wywołuje aplikację powłoki izolowanej. Ten projekt zawiera folder dostosowania powłoki, który umożliwia customiz wyglądu i zachowania aplikacji izolowanej powłoki.  
  
- Projekt interfejsu użytkownika *rozwiązania* , który tworzy zestaw satelicki, który definiuje aktywne polecenia menu i lokalizowalne ciągi.  
  
#### <a name="to-create-a-basic-isolated-shell-solution"></a>Aby utworzyć podstawowe rozwiązanie powłoki izolowanej  
  
1. Otwórz program Visual Studio i Utwórz nowy projekt.  
  
2. W oknie **Nowy projekt** rozwiń węzeł **Inne typy projektów** , a następnie wybierz opcję **rozszerzalność**. Wybierz szablon projektu **izolowany w programie Visual Studio Shell** .  
  
3. Nadaj projektowi nazwę `MyVSShellStub` i określ lokalizację. Upewnij się, że jest zaznaczone pole wyboru **Utwórz katalog dla rozwiązania** , a następnie kliknij przycisk **OK**.  
  
     Nowe rozwiązanie pojawia się w **Eksplorator rozwiązań**.  
  
4. Skompiluj rozwiązanie i Rozpocznij debugowanie aplikacji powłoki izolowanej.  
  
     Zostanie wyświetlona izolowana powłoka programu Visual Studio. Pasek tytułu odczytuje **MyVSShellStub**. Ikona paska tytułu jest generowana z \MyVSShellStub\Resource Files\ApplicationIcon.ico.  
  
## <a name="customizing-the-application-name-and-icon"></a>Dostosowywanie nazwy i ikony aplikacji  
 Możesz chcieć oznaczyć swoją aplikację za pomocą nazwy firmy i jej logo na pasku tytułu. Poniższe kroki pokazują, jak zmienić nazwę i ikonę, które są wyświetlane na pasku tytułu aplikacji niestandardowej, zmieniając plik definicji pakietu MyVSShellStub. Application. pkgdef.  
  
#### <a name="to-customize-the-application-name-and-icon"></a>Aby dostosować nazwę i ikonę aplikacji  
  
1. W projekcie MyVSShellStub Otwórz \Shell Customization\MyVSShellStub.Application.pkgdef.  
  
2. Zmień wartość `AppName` elementu na **"nazwa_aplikacji" = "Edytor muzyki firmy Fabrikam"**  
  
3. Aby zmienić ikonę aplikacji, skopiuj inną ikonę do katalogu \MyVSShellStub\MyVSShellStub\MyVSShellStub\. Zmień nazwę istniejącego pliku ApplicationIcon. ico na ApplicationIcon1. ico. Zmień nazwę nowego pliku na ApplicationIcon. ico.  
  
4. Skompiluj rozwiązanie, a następnie rozpocząć debugowanie. Zostanie wyświetlone środowisko IDE izolowanej powłoki. Pasek tytułu ma nową ikonę obok wyrazów **Edytor Muzyka firmy Fabrikam**.  
  
## <a name="customizing-the-default-web-browser-home-page"></a>Dostosowywanie domyślnej strony głównej przeglądarki sieci Web  
 W tej sekcji pokazano, jak zmienić domyślną stronę główną okna **przeglądarki sieci Web** , zmieniając plik definicji pakietu.  
  
#### <a name="to-customize-the-default-web-browser-home-page"></a>Aby dostosować domyślną stronę główną przeglądarki sieci Web  
  
1. W pliku MyVSShellStub. Application. pkgdef Zmień wartość `DefaultHomePage` elementu na "<https://www.microsoft.com>".  
  
2. Skompiluj ponownie projekt MyVSShellStub.  
  
3. Skompiluj rozwiązanie, a następnie rozpocząć debugowanie.  
  
4. W oknie **Widok/inne okna**kliknij pozycję **przeglądarka sieci Web**. W oknie **przeglądarki sieci Web** zostanie wyświetlona strona główna Microsoft Corporation.  
  
## <a name="removing-the-print-command"></a>Usuwanie polecenia Print  
 Plik. vsct w projekcie interfejsu użytkownika powłoki izolowanej składa się z zestawu deklaracji formularza `<Define name=No_`*elementu*`>`, gdzie *element* jest jednym z standardowych poleceń i menu programu Visual Studio.  
  
 Jeśli deklaracja jest bez komentarzy, to menu lub polecenie jest wykluczone z izolowanej powłoki. Z drugiej strony, jeśli deklaracja jest komentarzem, menu lub polecenie jest zawarte w izolowanej powłoce.  
  
 W poniższych krokach utworzysz komentarz polecenia Print w pliku. vsct.  
  
#### <a name="to-remove-the-print-command"></a>Aby usunąć polecenie Print  
  
1. Sprawdź, czy polecenie **Drukuj** pojawia się w menu **plik** w aplikacji powłoki izolowanej.  
  
2. W projekcie MyVSShellStubUI Otwórz \Resource Files\MyVSShellStubUI.vsct do edycji.  
  
3. Usuń komentarz z tego wiersza:  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4. Spowoduje to usunięcie polecenia Print.  
  
5. Rozpocznij debugowanie aplikacji powłoki izolowanej. Sprawdź, czy **plik/polecenie Print** zostały utracone.  
  
## <a name="removing-features-from-the-isolated-shell"></a>Usuwanie funkcji z izolowanej powłoki  
 Niektóre pakiety, które są ładowane w programie Visual Studio, można usunąć, edytując plik. pkgundef, jeśli nie chcesz tych funkcji w niestandardowej aplikacji powłoki izolowanej. Pakiet należy określić w jednym z podkluczy klucza rejestru $RootKey $ \Packages.  
  
> [!NOTE]
> Aby znaleźć identyfikatory GUID funkcji programu Visual Studio, zobacz [identyfikatory GUID pakietu funkcji programu Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
 Poniższa procedura pokazuje, jak usunąć Edytor XML z izolowanej powłoki.  
  
#### <a name="to-remove-the-xml-editor"></a>Aby usunąć Edytor XML  
  
1. Otwórz plik MyVSShellStub. pkgundef w folderze dostosowania powłoki projektu MyVSShellStub.  
  
2. Usuń komentarz z następującego wiersza:  
  
     [$RootKey $ \Packages\\{87569308-4813-40a0-9cd0-d7a30838ca3f}]  
  
3. Skompiluj ponownie rozwiązanie i Rozpocznij debugowanie izolowanej powłoki. Otwórz plik XML, na przykład \MyVSShellStub\MyVSShellStub\MyVSShellStubUI\MyVSShellStubUI.vsct. Sprawdź, czy słowa kluczowe XML w pliku nie są kolorowe i że wpisanie "<" w wierszu nie powoduje Wywołaj etykietek XML.  
  
## <a name="customizing-the-helpabout-box"></a>Dostosowywanie okna Pomoc/informacje  
 Można dostosować okno Pomoc/informacje, które jest tworzone w ramach szablonu projektu izolowanej powłoki.  
  
#### <a name="to-customize-the-company-name"></a>Aby dostosować nazwę firmy  
  
1. Nazwa firmy, informacje o prawach autorskich, wersja produktu i opis produktu znajdują się w projekcie MyVSShellStub. AboutBoxPackage w pliku \Properties\AssemblyInfo.cs. Otwórz ten plik.  
  
2. Zmień wartość `AssemblyCompany` na **Fabrikam**, wartości `AssemblyProduct` i `AssemblyTitle` na program **Fabrikam Music Editor**, a `AssemblyCopyright` wartość **Copyright © Fabrikam 2015**:  
  
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
  
3. Aby dodać opis produktu, Zmień wartość `AssemblyDescription` na **Opis edytora Music firmy Fabrikam.** :  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4. Rozpocznij debugowanie i w aplikacji izolowanej powłoki Otwórz okno **Pomoc/informacje** . Powinny być widoczne zmienione ciągi. Tytuł pola pomoc/informacje jest taki sam jak wartość `AssemblyTitle` w AssemblyInfo.cs.  
  
5. Właściwości samego pola **Pomoc/informacje** znajdują się w pliku MyVSShellStub. AboutBoxPackage\AboutBox.XAML. Aby zmienić szerokość pola pomoc/informacje, przejdź do bloku `AboutDialogStyle` i ustaw właściwość `Width` na 200:  
  
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
  
6. Skompiluj ponownie rozwiązanie i Rozpocznij debugowanie izolowanej powłoki. Pole pomoc/informacje powinno mieć wartość około kwadratu.  
  
## <a name="before-you-deploy-the-isolated-shell-application"></a>Przed wdrożeniem aplikacji izolowanej powłoki  
 Izolowaną aplikację powłoki można zainstalować na dowolnym komputerze, na którym znajduje się pakiet redystrybucyjny programu Visual Studio Shell (izolowany). Aby uzyskać więcej informacji na temat pakietu redystrybucyjnego, zobacz witrynę sieci Web [do pobrania rozszerzalności programu Visual Studio](https://go.microsoft.com/fwlink/?LinkID=119298) .  
  
## <a name="deploying-the-isolated-shell-application"></a>Wdrażanie aplikacji izolowanej powłoki  
 Aplikację powłoki izolowanej należy wdrożyć na komputerze docelowym przez utworzenie projektu Instalatora. Należy określić następujące elementy:  
  
- Układ folderów i plików na komputerze docelowym.  
  
- Warunki uruchamiania, które gwarantują, że .NET Framework i środowisko uruchomieniowe powłoki programu Visual Studio są zainstalowane na komputerze docelowym.  
  
  W poniższej procedurze należy zainstalować program InstallShield Limited Edition na komputerze.  
  
#### <a name="to-create-the-setup-project"></a>Aby utworzyć projekt instalacyjny  
  
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł rozwiązanie, a następnie kliknij polecenie **Dodaj nowy projekt**.  
  
2. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Inne typy projektów** , a następnie wybierz pozycję **Instalacja i wdrożenie**. Wybierz szablon InstallShield. Nazwij nowy projekt `MySetup` a następnie kliknij przycisk **OK**.  
  
3. Jeśli program InstallShield Limited Edition jest już zainstalowany, przejdź do następnego kroku.  
  
    Jeśli program InstallShield Limited Edition nie został jeszcze zainstalowany, zostanie wyświetlona strona pobierania InstallShield. Postępuj zgodnie z instrukcjami, aby pobrać i zainstalować produkt, wybierając wersję programu InstallShield zgodną z wersją programu Visual Studio. Należy zdecydować, czy należy zarejestrować instalację programu InstallShield, czy użyć jej jako ewaluacyjnej. Po zakończeniu instalacji należy ponownie uruchomić program Visual Studio.  
  
   > [!IMPORTANT]
   > Przed utworzeniem projektu InstallShield należy uruchomić program Visual Studio jako administrator. Jeśli tego nie zrobisz, wystąpi błąd podczas kompilowania projektu.  
  
   W następnych krokach pokazano, jak skonfigurować projekt Instalatora.  
  
> [!IMPORTANT]
> Upewnij się, że została skompilowana konfiguracja wydania odizolowanego projektu powłoki co najmniej raz przed skonfigurowaniem projektu Instalatora.  
  
#### <a name="to-configure-the-setup-project"></a>Aby skonfigurować projekt instalacyjny  
  
1. W **Eksplorator rozwiązań**w obszarze Projekt **konfiguracji** wybierz pozycję **Asystent projektu**. W dolnym wierszu okna **Asystenta projektu** wybierz pozycję **Informacje o aplikacji**. Wpisz **Fabrikam** jako nazwę swojej firmy i **Edytor muzyki Fabrikam** jako nazwę swojej aplikacji. Wybierz strzałkę do przodu w prawym dolnym rogu **Asystenta projektu**.  
  
2. Wybierz pozycję **tak** w obszarze **czy aplikacja wymaga zainstalowania oprogramowania na komputerze?** , a następnie wybierz pozycję **Microsoft .NET Framework 4,5 pełen pakiet**.  
  
3. Wybierz przycisk **pliki aplikacji** w dolnej części okna i upewnij się, że wybrano folder **Edytor muzyki firmy Fabrikam** .  
  
4. Wybierz przycisk **Dodaj pliki** . W oknie dialogowym **Dodaj pliki** Dodaj następujące pliki z folderu **MyVSShellStub\Release** :  
  
    1. MyVSShellStub.exe.config  
  
    2. DebuggerProxy.dll  
  
    3. DebuggerProxy.dll.manifest  
  
    4. MyVSShellStub.pkgdef  
  
    5. MyVSShellStub.pkgundef  
  
    6. MyVSShellStub.winprf  
  
    7. Splash.bmp  
  
5. Kliknij przycisk **Dodaj dane wyjściowe projektu** i Dodaj **MyVSShellStub/podstawowy wynik**. Kliknij przycisk **OK**.  
  
6. W lewym okienku w obszarze **komputer docelowy**kliknij prawym przyciskiem myszy węzeł **Fabrikam Music Editor [INSTALLDIR]** i Dodaj **Nowy folder** o nazwie **Extensions**.  
  
7. Kliknij prawym przyciskiem myszy węzeł **rozszerzenia** w lewym okienku i Dodaj nowy folder o nazwie **aplikacja**.  
  
8. Wybierz folder **aplikacji** , a następnie kliknij przycisk **Dodaj dane wyjściowe projektu** , a następnie wybierz podstawowe wyjście z projektu MyVSShellStub. AboutBoxPackage.  
  
9. Kliknij przycisk **Dodaj pliki** i w folderze \MyVSShellStub\Release\Extensions\Application\ Dodaj następujące pliki:  
  
    - MyVSShellStub.AboutBoxPackage.pkgdef  
  
    - MyVSShellStub.Application.pkgdef  
  
10. W lewym okienku kliknij prawym przyciskiem myszy węzeł **Edytor muzyki firmy Fabrikam [INSTALLDIR]** , a następnie Dodaj nowy folder o nazwie **1033**.  
  
11. Wybierz folder 1033, a następnie kliknij przycisk **Dodaj dane wyjściowe projektu** i wybierz podstawowe wyjście z projektu MyVSShellStubUI.  
  
12. Przejdź do okna **Skróty aplikacji** .  
  
13. Kliknij pozycję **Nowy** , aby utworzyć skrót, a następnie wybierz pozycję **[Folderprogramfiles] \Fabrikam\Fabrikam Music Editor\MyVSShellStub.Primary Output**.  
  
14. Przejdź do okienka **Wywiad instalacji** .  
  
15. Ustaw wartość **nie**dla wszystkich elementów.  
  
16. W **Eksplorator rozwiązań**w projekcie websetup Otwórz pozycję **Zdefiniuj wymagania instalacji i akcje \ wymagania**. Zostanie otwarte okno **wymagania** .  
  
17. Kliknij prawym przyciskiem myszy **system wymagania systemowe** i wybierz polecenie **Utwórz nowy warunek uruchomienia**. Zostanie wyświetlony **Kreator wyszukiwania systemu** .  
  
18. W okienku **co chcesz znaleźć?** wybierz **pozycję wpis rejestru** na liście rozwijanej, a następnie kliknij przycisk **dalej**.  
  
19. W okienku **jak chcesz go wyszukać?** wybierz **HKEY_LOCAL_MACHINE** jako katalog główny rejestru. Wprowadź **SOFTWARE\Wow6432Node\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** dla systemów 64-bitowych lub **SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell** dla systemów 32-bitowych, a następnie wprowadź **Zainstaluj** jako wartość rejestru. Kliknij przycisk **Dalej**.  
  
20. W okienku **co chcesz zrobić z wartością?** wprowadź **ten produkt, aby zainstalować pakiet redystrybucyjny powłoki programu Visual Studio 2015.** jako tekst wyświetlany i kliknij przycisk **Zakończ**.  
  
21. Odbuduj rozwiązanie izolowanej powłoki, aby utworzyć projekt Instalatora.  
  
     Plik Setup. exe można znaleźć w następującym folderze:  
  
     \MyVSShellStub\MySetup\MySetup\Express\SingleImage\DiskImages\DISK1  
  
## <a name="testing-the-installation-program"></a>Testowanie programu instalacyjnego  
 Aby przetestować instalację, skopiuj plik Setup. exe na inny komputer i uruchom plik wykonywalny Instalatora. Powinno być możliwe uruchomienie aplikacji izolowanej powłoki.
