---
title: Zdalne debugowanie platformy ASP.NET Core w usługach IIS i platformą Azure | Dokumentacja firmy Microsoft
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: 91f454bec6854d4450850f970cedb197ea005f25
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57873376"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio-2017"></a>Zdalne debugowanie platformy ASP.NET Core w usługach IIS na platformie Azure w programie Visual Studio 2017

Ten przewodnik wyjaśnia, jak skonfigurować i konfigurowanie aplikacji programu Visual Studio 2017 platformy ASP.NET Core, wdrożyć ją w usługach IIS przy użyciu platformy Azure i dołączyć debuger zdalny z programu Visual Studio.

Zalecanym sposobem debugowania zdalnego na platformie Azure, zależy od danego scenariusza:

* Aby debugować platformy ASP.NET Core w usłudze Azure App Service, zobacz [debugowanie aplikacji platformy Azure przy użyciu rozszerzenia Snapshot Debugger](../debugger/debug-live-azure-applications.md). Jest to zalecana metoda.
* Debugowanie ASP.NET Core w usłudze Azure App Service przy użyciu bardziej tradycyjny funkcji debugowania, wykonaj kroki opisane w tym temacie (zobacz sekcję [zdalne debugowanie w usłudze Azure App Service](#remote_debug_azure_app_service)).

    W tym scenariuszu należy wdrożyć aplikację z poziomu programu Visual Studio na platformie Azure, ale nie trzeba ręcznie zainstalować lub skonfigurować usługi IIS lub zdalny debuger (te składniki są reprezentowane za pomocą linii kropkowanej), jak pokazano na poniższej ilustracji.

    ![Składniki zdalnego debugera](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Debugowanie usług IIS na Maszynie wirtualnej platformy Azure, wykonaj kroki opisane w tym temacie (zobacz sekcję [zdalnego debugowania na Maszynie wirtualnej platformy Azure](#remote_debug_azure_vm)). Dzięki temu można korzystać z niestandardowych konfiguracji usług IIS, ale kroki instalacji i wdrażania są bardziej skomplikowane.

    Na Maszynie wirtualnej platformy Azure należy wdrożyć aplikację z poziomu programu Visual Studio na platformie Azure i trzeba będzie również ręcznie zainstalować rolę usług IIS i zdalnym debugerem, jak pokazano na poniższej ilustracji.

    ![Składniki zdalnego debugera](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Aby debugować platformy ASP.NET Core w usłudze Azure Service Fabric, zobacz [debugowania zdalnego aplikacji usługi Service Fabric](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Pamiętaj usunąć zasoby platformy Azure, które tworzysz, po wykonaniu kroków opisanych w tym samouczku. Dzięki temu można uniknąć ponoszenia niepotrzebnych opłat.


### <a name="requirements"></a>Wymagania

Debugowanie między dwoma komputerami połączonymi za pośrednictwem serwera proxy nie jest obsługiwane. Debugowanie za pośrednictwem duże opóźnienie lub połączenia o niskiej przepustowości, takich jak Internet, połączenia telefonicznego lub przez Internet między krajów nie jest zalecane i może zakończyć się niepowodzeniem lub zbyt wolno. Aby uzyskać pełną listę wymagań, zobacz [wymagania](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Tworzenie aplikacji platformy ASP.NET Core na komputerze programu Visual Studio 2017

1. Tworzenie nowej aplikacji platformy ASP.NET Core. (Wybierz **Plik > Nowy > Projekt**, a następnie wybierz **Visual C# > sieci Web > Aplikacja sieci Web programu ASP.NET Core**).

    W **platformy ASP.NET Core** szablony zaznacz **aplikacji sieci Web**.

2. Upewnij się, że **ASP.NET Core 2.0** jest zaznaczone, który **włączyć obsługę platformy Docker** jest **nie** wybranego i **uwierzytelniania** jest równa **Bez uwierzytelniania**.

3. Nadaj projektowi nazwę **MyASPApp** i kliknij przycisk **OK** do tworzenia nowego rozwiązania.

4. Otwórz plik About.cshtml.cs i ustaw punkt przerwania `OnGet` — metoda (w szablonach starsze HomeController.cs zamiast tego otworzyć i ustaw punkt przerwania w `About()` metody).

## <a name="remote_debug_azure_app_service"></a> Zdalne debugowanie platformy ASP.NET Core w usłudze Azure App Service

Z programu Visual Studio można szybko publikowanie i debugowanie aplikacji w taki sposób, aby inicjowane w pełni wystąpienia usług IIS. Jednak jest ustawień konfiguracji usługi IIS i nie można go dostosować. Aby uzyskać szczegółowe instrukcje, zobacz [wdrażanie aplikacji sieci web platformy ASP.NET Core na platformie Azure przy użyciu programu Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Możliwość dostosowania usług IIS, należy spróbować debugowania [maszyny Wirtualnej platformy Azure](#remote_debug_azure_vm).)

#### <a name="to-deploy-the-app-and-remote-debug-using-server-explorer"></a>Aby wdrożyć aplikację i zdalne debugowanie za pomocą Eksploratora serwera

1. W programie Visual Studio, kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz **Publikuj**.

    Jeśli wcześniej skonfigurowano żadnych profilów publikowania **Publikuj** zostanie wyświetlone okienko. Kliknij przycisk **nowy profil**.

1. Wybierz **usługi Azure App Service** z **Publikuj** okno dialogowe, wybierz opcję **Utwórz nowy**i postępuj zgodnie z monitami, aby opublikować.

    Aby uzyskać szczegółowe instrukcje, zobacz [wdrażanie aplikacji sieci web platformy ASP.NET Core na platformie Azure przy użyciu programu Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Publikowanie w usłudze Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)

1. Otwórz **Eksploratora serwera** (**widoku** > **Eksploratora serwera**), kliknij prawym przyciskiem myszy w wystąpieniu usługi App Service i wybierz **dołączyć debuger**.

1. W działającej aplikacji platformy ASP.NET, kliknij link, aby **o** strony.

    W programie Visual Studio powinny trafiony punkt przerwania.

    To wszystko! Pozostałe kroki w tym temacie mają zastosowanie do zdalnego debugowania na Maszynie wirtualnej platformy Azure.

## <a name="remote_debug_azure_vm"></a> Zdalne debugowanie platformy ASP.NET Core na Maszynie wirtualnej platformy Azure

Można utworzyć maszyny Wirtualnej dla systemu Windows Server platformy i zainstaluj i skonfigurowanie usług IIS i inne składniki wymagane oprogramowanie. To jest bardziej czasochłonne niż wdrożenie usługi Azure App Service i wymaga, wykonaj pozostałe kroki w ramach tego samouczka.

Najpierw wykonaj wszystkie kroki opisane w [instalacji i uruchomienia usług IIS](/azure/virtual-machines/windows/quick-create-portal).

Po otwarciu portu 80 w sieciowej grupie zabezpieczeń należy również otworzyć port 4022 dla zdalnego debugera. Dzięki temu nie trzeba otworzyć go później.

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>Aplikacja jest już uruchomiona w usługach IIS na maszynie Wirtualnej platformy Azure?

Ten artykuł zawiera instrukcje dotyczące konfigurowania podstawowej konfiguracji programu IIS na serwerze Windows i wdrażanie aplikacji w programie Visual Studio. Te kroki są uwzględnione, aby upewnić się, że serwer ma wymagane składniki, które są zainstalowane, że aplikacja może działać poprawnie i możesz przystąpić do debugowania zdalnego.

* Jeśli Twoja aplikacja działa w usługach IIS i po prostu chcesz pobrać zdalnego debugera i rozpocząć debugowanie, przejdź do [pobrać i zainstalować narzędzia zdalnej w systemie Windows Server](#BKMK_msvsmon).

* Jeśli chcesz, aby uzyskać pomoc, aby upewnić się, że Twoja aplikacja jest skonfigurowana, wdrożeniu i poprawne działanie w usługach IIS tak, aby można było debugować, wykonaj wszystkie kroki przedstawione w tym temacie.

### <a name="update-browser-security-settings-on-windows-server"></a>Zaktualizuj ustawienia zabezpieczeń przeglądarki w systemie Windows Server

Jeśli Konfiguracja zwiększonych zabezpieczeń jest włączone w programie Internet Explorer (jest włączony domyślnie), następnie należy może być konieczne dodanie niektórych domen jako zaufane witryny, aby umożliwić pobieranie niektóre składniki serwera sieci web. Dodaj zaufanych witryn, przechodząc do **Opcje internetowe > Zabezpieczenia > Zaufane witryny > witryny**. Dodaj następujące domeny.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- Program IIS.NET

Po pobraniu oprogramowania, może zostać żądania, aby przyznać uprawnienie do ładowania różnych skrypty witryny sieci web i zasobami. Niektóre z tych zasobów nie są wymagane, ale w celu uproszczenia procesu, należy kliknąć **Dodaj** po wyświetleniu monitu.

### <a name="install-aspnet-core-on-windows-server"></a>Instalowanie platformy ASP.NET Core w systemie Windows Server

1. Zainstaluj [.NET Core systemu Windows serwer obsługujący](https://aka.ms/dotnetcore-2-windowshosting) pakietu przez system operacyjny. Pakiet zostanie zainstalowany, środowisko uruchomieniowe programu .NET Core, .NET Core bibliotek i modułu ASP.NET Core. Aby uzyskać więcej szczegółowych instrukcji, zobacz [publikowania w usługach IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Jeśli system nie ma dostępu do Internetu, należy uzyskać i zainstalować *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* przed zainstalowaniem pakietu platformy .NET Core systemu Windows serwer obsługujący.

3. Ponowne uruchomienie systemu (lub wykonania **net stop został /y** następuje **net start w3svc** z wiersza polecenia, aby wczytać zmiany w systemie ścieżki).

## <a name="choose-a-deployment-option"></a>Wybierz opcję wdrożenia

Jeśli potrzebujesz pomocy, aby wdrożyć aplikację w usługach IIS, należy wziąć pod uwagę następujące opcje:

* Wdrażanie, tworząc plik ustawień publikowania w usługach IIS i importowania ustawień w programie Visual Studio. W niektórych przypadkach jest to szybki sposób wdrożenia aplikacji. Podczas tworzenia pliku ustawień publikowania uprawnienia automatycznie są konfigurowane w usługach IIS.

* Wdrażanie, publikowanie do folderu lokalnego, a kopiowanie danych wyjściowych przez preferowaną metodą do folderu aplikacji przygotowane w usługach IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Opcjonalnie) Wdrażanie przy użyciu pliku ustawień publikowania

Można użyć tej opcji utworzyć plik ustawień publikowania i zaimportować go do programu Visual Studio.

> [!NOTE]
> Ta metoda wdrażania korzysta z narzędzia Web Deploy. Jeśli chcesz skonfigurować narzędzie Web Deploy ręcznie w programie Visual Studio zamiast importować ustawienia, można zainstalować 3.6 wdrażania sieci Web zamiast 3.6 wdrażania sieci Web dla serwerów do hostingu. Jednak jeśli skonfigurujesz narzędzia Web Deploy ręcznie, należy się upewnić, że folder aplikacji na serwerze skonfigurowano poprawne wartości i uprawnienia (zobacz [witryny sieci Web ASP.NET skonfigurować](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Instalowanie i Konfigurowanie narzędzia Web Deploy dla serwerów do hostingu w systemie Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Utwórz plik ustawień publikowania w usługach IIS w systemie Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importowanie ustawień publikowania w programie Visual Studio i wdrażanie

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Po pomyślnym wdrożeniu aplikacji powinna być uruchamiana automatycznie. Jeśli aplikacja nie zostanie uruchomiony z programu Visual Studio, należy uruchomić aplikację w usługach IIS. Dla platformy ASP.NET Core, należy się upewnić, że pula aplikacji pole **DefaultAppPool** ustawiono **bez kodu zarządzanego**.

1. W **ustawienia** okno dialogowe, Włącz debugowanie, klikając **dalej**, wybierz **debugowania** konfiguracji, a następnie wybierz **usunięcie dodatkowych plików w miejsce docelowe** w obszarze **publikowania plików** opcje.

    > [!NOTE]
    > Jeśli wybierzesz konfigurację wydania, należy wyłączyć debugowanie w *web.config* pliku podczas publikowania.

1. Kliknij przycisk **Zapisz** , a następnie ponownie opublikować aplikację.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Opcjonalnie) Wdrażanie poprzez publikowanie do folderu lokalnego

Ta opcja umożliwia wdrażanie aplikacji, jeśli chcesz skopiować ją do usług IIS przy użyciu programu Powershell, RoboCopy, lub chcesz ręcznie skopiować pliki.

### <a name="BKMK_deploy_asp_net"></a> Konfigurowanie witryny sieci Web ASP.NET na komputerze z systemem Windows Server

Jeśli importujesz ustawień publikowania, możesz pominąć tę sekcję.

1. Otwórz **Internet Information Services (IIS) Manager** i przejdź do **witryn**.

2. Kliknij prawym przyciskiem myszy **domyślna witryna sieci Web** a następnie wybierz węzeł **Add Application**.

3. Ustaw **Alias** pole **MyASPApp** i pole puli aplikacji do **bez kodu zarządzanego**. Ustaw **ścieżkę fizyczną** do **C:\Publish** (gdzie będą później wdrażania projektu programu ASP.NET).

4. Z witryną wybrane w Menedżerze usług IIS, wybierz **Edytuj uprawnienia**i upewnij się, że IUSR, IIS_IUSRS lub użytkownika skonfigurowane dla puli aplikacji jest autoryzowanym użytkownikiem z uprawnień Odczyt i wykonywanie.

    Jeśli nie widzisz jeden z tych użytkowników z dostępem, przechodzą przez kroki, aby dodać IUSR jako użytkownik z uprawnieniami Odczyt i wykonywanie.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Opcjonalnie) Publikowanie i wdrażanie aplikacji poprzez publikowanie do folderu lokalnego, w programie Visual Studio

Jeśli nie używasz, narzędzie Web Deploy, należy opublikować i wdrażanie aplikacji przy użyciu systemu plików lub innych narzędzi. Możesz rozpocząć od utworzenia pakietu przy użyciu systemu plików, a następnie ręcznie wdrożyć pakiet lub użyć innych narzędzi, takich jak program PowerShell, RoboCopy lub polecenia XCopy. W tej sekcji przyjęto założenie, że są ręczne kopiowanie pakietu, jeśli nie używasz narzędzia Web Deploy.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a> Pobierz i zainstaluj narzędzia zdalnego w systemie Windows Server

W tym samouczku używamy programu Visual Studio 2017.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="BKMK_setup"></a> Konfigurowanie zdalnego debugera w systemie Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Jeśli potrzebujesz dodać uprawnienia dla dodatkowych użytkowników do zmienić tryb uwierzytelniania lub numer portu dla zdalnego debugera, zobacz [Konfigurowanie debugera zdalnego](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="BKMK_attach"></a> Dołącz do aplikacji platformy ASP.NET z komputera z programu Visual Studio

1. Na komputerze programu Visual Studio, otwórz rozwiązanie, które chcesz debugować (**MyASPApp** Jeśli postępujesz zgodnie z instrukcjami w tym artykule).
2. W programie Visual Studio, kliknij przycisk **Debuguj > Dołącz do procesu** (Ctrl + Alt + P).

    > [!TIP]
    > W programie Visual Studio 2017 i nowszych wersjach można ponownie dołączyć do tego samego procesu wcześniej podłączany do przy użyciu **Debuguj > ponownie Dołącz do procesu...** (Shift+Alt+P).

3. Ustaw pole kwalifikator  **\<nazwy komputera zdalnego >: 4022**.
4. Kliknij przycisk **Odśwież**.
    Powinien zostać wyświetlony niektóre procesy, które są wyświetlane w **dostępne procesy** okna.

    Jeśli nie widzisz wszystkie procesy, spróbuj przy użyciu adresu IP zamiast nazwy komputera zdalnego (port jest wymagany). Możesz użyć `ipconfig` w wierszu polecenia, aby uzyskać adres IPv4.

    Jeśli chcesz używać **znaleźć** przycisku, konieczne może być [Otwórz UDP port 3702](#bkmk_openports) na serwerze.

5. Sprawdź **Pokaż procesy wszystkich użytkowników**.

6. Wpisz pierwszą literę nazwy procesu, aby szybko znaleźć *dotnet.exe* (dla platformy ASP.NET Core).

   Dla aplikacji ASP.NET Core, był poprzedniej nazwy procesu *dnx.exe*.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Kliknij przycisk **dołączyć**.

8. Otwórz witrynę sieci Web na komputerze zdalnym. W przeglądarce przejdź do **http://\<nazwy komputera zdalnego >**.

    Powinna zostać wyświetlona strona sieci web platformy ASP.NET.
9. W działającej aplikacji platformy ASP.NET, kliknij link, aby **o** strony.

    W programie Visual Studio powinny trafiony punkt przerwania.

### <a name="bkmk_openports"></a> Rozwiązywanie problemów: Otwieranie portów wymaganych w systemie Windows Server

W większości konfiguracji wymagane porty są otwarte przez instalację programu ASP.NET i zdalny debuger. Jednak jeśli rozwiązujesz problemy z wdrażaniem aplikacji znajduje się za zaporą, może być konieczne Sprawdź, czy odpowiednie porty są otwarte.

Na Maszynie wirtualnej platformy Azure, należy otworzyć porty za pośrednictwem [sieciowej grupy zabezpieczeń](/azure/virtual-machines/virtual-machines-windows-hero-role).

Wymagane porty:

- 80 - wymagane dla usług IIS
- 4022 - wymagane do zdalnego debugowania w programie Visual Studio 2017 (zobacz [zdalnego przypisania portów debugera](../debugger/remote-debugger-port-assignments.md) Aby uzyskać więcej informacji).
- UDP 3702 — port odnajdywania (opcjonalnie) umożliwia **znaleźć** przycisku związane ze zdalnym debugerem programu Visual Studio.

Ponadto te porty już powinien zostać otwarty przez instalację programu ASP.NET:
- 8172 — (opcjonalnie) wymagany dla narzędzia Web Deploy do wdrażania aplikacji w programie Visual Studio
