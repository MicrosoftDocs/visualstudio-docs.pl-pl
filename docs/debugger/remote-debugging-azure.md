---
title: Zdalne debugowanie ASP.NET Core w usługach IIS i na platformie Azure | Microsoft Docs
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
ms.openlocfilehash: c6a41a332e16f79673b475404af27e540689938d
ms.sourcegitcommit: 3d64bfb9bf85395357effe054db9a9afaa0be5ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181137"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>Zdalne debugowanie ASP.NET Core w usługach IIS na platformie Azure w programie Visual Studio

W tym przewodniku wyjaśniono, jak skonfigurować i skonfigurować aplikację ASP.NET Core programu Visual Studio, wdrożyć ją w usługach IIS przy użyciu platformy Azure i dołączyć zdalny debuger z programu Visual Studio.

Zalecany sposób zdalnego debugowania na platformie Azure zależy od Twojego scenariusza:

* Aby debugować ASP.NET Core na Azure App Service, zobacz [debugowanie aplikacji platformy Azure przy użyciu Snapshot Debugger](../debugger/debug-live-azure-applications.md). Jest to zalecana metoda.
* Aby debugować ASP.NET Core na Azure App Service przy użyciu bardziej tradycyjnych funkcji debugowania, wykonaj kroki opisane w tym temacie (zobacz sekcję [debugowanie zdalne na Azure App Service](#remote_debug_azure_app_service)).

    W tym scenariuszu należy wdrożyć aplikację z programu Visual Studio na platformie Azure, ale nie musisz ręcznie instalować ani konfigurować usług IIS ani zdalnego debugera (te składniki są reprezentowane przez linie kropkowane), jak pokazano na poniższej ilustracji.

    ![Składniki debugera zdalnego](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Aby debugować usługi IIS na maszynie wirtualnej platformy Azure, wykonaj kroki opisane w tym temacie (zobacz sekcję [debugowanie zdalne na maszynie wirtualnej platformy Azure](#remote_debug_azure_vm)). Pozwala to na użycie niestandardowej konfiguracji usług IIS, ale kroki instalacji i wdrażania są bardziej skomplikowane.

    W przypadku maszyny wirtualnej platformy Azure należy wdrożyć aplikację z programu Visual Studio na platformie Azure, a także ręcznie zainstalować rolę usług IIS i zdalny debuger, jak pokazano na poniższej ilustracji.

    ![Składniki debugera zdalnego](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Aby debugować ASP.NET Core na platformie Azure Service Fabric, zobacz [debugowanie aplikacji zdalnej Service Fabric](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Pamiętaj o usunięciu zasobów platformy Azure utworzonych po wykonaniu kroków opisanych w tym samouczku. Dzięki temu można uniknąć niepotrzebnych opłat.

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range=">=vs-2019"
Aby wykonać kroki opisane w tym artykule, wymagany jest program Visual Studio 2019.
::: moniker-end
::: moniker range="vs-2017"
Aby wykonać kroki opisane w tym artykule, wymagany jest program Visual Studio 2017.
::: moniker-end

### <a name="network-requirements"></a>Wymagania dotyczące sieci

Debugowanie między dwoma komputerami połączonymi za pośrednictwem serwera proxy nie jest obsługiwane. Debugowanie za pośrednictwem duże opóźnienie lub połączenia o niskiej przepustowości, takich jak Internet, połączenia telefonicznego lub przez Internet między krajów nie jest zalecane i może zakończyć się niepowodzeniem lub zbyt wolno. Aby uzyskać pełną listę wymagań, zobacz [wymagania](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Tworzenie aplikacji ASP.NET Core na komputerze z Visual Studio

1. Utwórz nową aplikację ASP.NET Core.

    ::: moniker range=">=vs-2019"
    W programie Visual Studio 2019 **naciśnij klawisze CTRL + Q** , aby otworzyć pole wyszukiwania, **wpisz ASP.NET**, wybierz pozycję **Szablony**, a następnie wybierz pozycję **Utwórz nową ASP.NET Core aplikacji sieci Web**. W wyświetlonym oknie dialogowym wpisz nazwę projektu **MyASPApp**, a następnie wybierz pozycję **Utwórz**. Następnie wybierz pozycję **aplikacja sieci Web (Model-View-Controller)** , a następnie wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    W programie Visual Studio 2017 wybierz pozycję **plik > nowy > projekt**, a następnie wybierz pozycję  **C# Visual > Web > ASP.NET Core aplikacja internetowa**. W sekcji szablony ASP.NET Core wybierz pozycję **aplikacja sieci Web (Model-View-Controller)** . Upewnij się, że wybrano ASP.NET Core 2,1, że **Obsługa platformy Docker** nie jest zaznaczona i że **uwierzytelnianie** jest ustawione na wartość **bez uwierzytelniania**. Nazwij projekt **MyASPApp**.
    ::: moniker-end

1. Otwórz plik About.cshtml.cs i ustaw punkt przerwania w metodzie `OnGet` (w starszych szablonach Otwórz HomeController.cs i ustaw punkt przerwania w metodzie `About()`).

## <a name="remote_debug_azure_app_service"></a>ASP.NET Core debugowania zdalnego na Azure App Service

W programie Visual Studio można szybko publikować i debugować aplikację w w pełni zainicjowanym wystąpieniu usług IIS. Jednak Konfiguracja usług IIS jest wstępnie ustawiona i nie można jej dostosować. Aby uzyskać bardziej szczegółowe instrukcje, zobacz [wdrażanie aplikacji sieci web ASP.NET Core na platformie Azure przy użyciu programu Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Jeśli potrzebujesz możliwości dostosowania usług IIS, wypróbuj debugowanie na [maszynie wirtualnej platformy Azure](#remote_debug_azure_vm)).

#### <a name="to-deploy-the-app-and-remote-debug-using-server-explorer"></a>Aby wdrożyć aplikację i debugowanie zdalne przy użyciu Eksplorator serwera

1. W programie Visual Studio kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz polecenie **Publikuj**.

    Jeśli wszystkie profile publikowania zostały wcześniej skonfigurowane, zostanie wyświetlone okienko **Publikowanie** . Kliknij pozycję **Nowy profil**.

1. Wybierz **Azure App Service** z okna dialogowego **Publikowanie** , wybierz pozycję **Utwórz nowy**i postępuj zgodnie z monitami, aby opublikować.

    Aby uzyskać szczegółowe instrukcje, zobacz [wdrażanie aplikacji sieci web ASP.NET Core na platformie Azure przy użyciu programu Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Publikowanie w usłudze Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)

1. Otwórz **Eksplorator serwera** (**Wyświetl** > **Eksplorator serwera**), kliknij prawym przyciskiem myszy wystąpienie App Service i wybierz **Dołącz debuger**.

1. W uruchomionej aplikacji ASP.NET kliknij link do strony **informacje** .

    W programie Visual Studio powinny trafiony punkt przerwania.

    Gotowe. Pozostałe kroki opisane w tym temacie mają zastosowanie do zdalnego debugowania na maszynie wirtualnej platformy Azure.

## <a name="remote_debug_azure_vm"></a>ASP.NET Core debugowania zdalnego na maszynie wirtualnej platformy Azure

Można utworzyć maszynę wirtualną platformy Azure dla systemu Windows Server, a następnie zainstalować i skonfigurować usługi IIS oraz inne wymagane składniki oprogramowania. Zajmuje to więcej czasu niż wdrożenie do Azure App Service i wymaga wykonania pozostałych kroków opisanych w tym samouczku.

Procedury te zostały przetestowane na te konfiguracje serwera:
* Windows Server 2012 R2 i IIS 8
* Windows Server 2016 i IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>Aplikacja jest już uruchomiona w usługach IIS na maszynie wirtualnej platformy Azure?

Ten artykuł zawiera instrukcje dotyczące konfigurowania podstawowej konfiguracji programu IIS na serwerze Windows i wdrażanie aplikacji w programie Visual Studio. Te kroki są dołączone do programu, aby upewnić się, że na serwerze są zainstalowane wymagane składniki, że aplikacja może działać poprawnie i że jest gotowy do zdalnego debugowania.

* Jeśli aplikacja jest uruchomiona w usługach IIS i po prostu chcesz pobrać zdalny debuger i rozpocząć debugowanie, przejdź do pozycji [Pobierz i zainstaluj narzędzia zdalne w systemie Windows Server](#BKMK_msvsmon).

* Jeśli chcesz, aby uzyskać pomoc, aby upewnić się, że Twoja aplikacja jest skonfigurowana, wdrożeniu i poprawne działanie w usługach IIS tak, aby można było debugować, wykonaj wszystkie kroki przedstawione w tym temacie.

  * Przed rozpoczęciem wykonaj wszystkie kroki opisane w temacie [Instalowanie i uruchamianie usług IIS](/azure/virtual-machines/windows/quick-create-portal).

  * Po otwarciu portu 80 w sieciowej grupie zabezpieczeń, należy również otworzyć [właściwy port](#bkmk_openports) dla zdalnego debugera (4024 lub 4022). Dzięki temu nie będzie trzeba otwierać go później.

### <a name="update-browser-security-settings-on-windows-server"></a>Zaktualizuj ustawienia zabezpieczeń przeglądarki w systemie Windows Server

Jeśli Konfiguracja zwiększonych zabezpieczeń jest włączone w programie Internet Explorer (jest włączony domyślnie), następnie należy może być konieczne dodanie niektórych domen jako zaufane witryny, aby umożliwić pobieranie niektóre składniki serwera sieci web. Dodaj Zaufane witryny, wybierając **Opcje internetowe > zabezpieczenia > zaufane lokacje > Lokacje**. Dodaj następujące domeny.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- Program IIS.NET

Po pobraniu oprogramowania, może zostać żądania, aby przyznać uprawnienie do ładowania różnych skrypty witryny sieci web i zasobami. Niektóre z tych zasobów nie są wymagane, ale aby uprościć proces, kliknij przycisk **Dodaj** po wyświetleniu monitu.

### <a name="install-aspnet-core-on-windows-server"></a>Zainstaluj ASP.NET Core w systemie Windows Server

1. Zainstaluj pakiet [hostingu platformy .NET Core systemu Windows Server](https://aka.ms/dotnetcore-2-windowshosting) w systemie hostingu. Pakiet zainstaluje środowisko uruchomieniowe platformy .NET Core, bibliotekę .NET Core i moduł ASP.NET Core. Aby uzyskać bardziej szczegółowe instrukcje, zobacz [Publikowanie w usługach IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Jeśli system nie ma połączenia z Internetem, uzyskaj i zainstaluj pakiet *[redystrybucyjny C++ Microsoft Visual 2015](https://www.microsoft.com/download/details.aspx?id=53840)* przed zainstalowaniem pakietu hostingu platformy .NET Core systemu Windows Server.

3. Uruchom ponownie system (lub wykonaj polecenie **net stop was/y** , a następnie **net start W3SVC** z wiersza polecenia, aby wybrać zmianę ścieżki systemowej).

## <a name="choose-a-deployment-option"></a>Wybierz opcję wdrożenia

Jeśli potrzebujesz pomocy, aby wdrożyć aplikację w usługach IIS, należy wziąć pod uwagę następujące opcje:

* Wdrażanie, tworząc plik ustawień publikowania w usługach IIS i importowania ustawień w programie Visual Studio. W niektórych przypadkach jest to szybki sposób wdrożenia aplikacji. Podczas tworzenia pliku ustawień publikowania uprawnienia automatycznie są konfigurowane w usługach IIS.

* Wdrażanie, publikowanie do folderu lokalnego, a kopiowanie danych wyjściowych przez preferowaną metodą do folderu aplikacji przygotowane w usługach IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Opcjonalnie) Wdrażanie przy użyciu pliku ustawień publikowania

Można użyć tej opcji utworzyć plik ustawień publikowania i zaimportować go do programu Visual Studio.

> [!NOTE]
> Ta metoda wdrażania korzysta z narzędzia Web Deploy. Jeśli chcesz skonfigurować narzędzie Web Deploy ręcznie w programie Visual Studio zamiast importować ustawienia, można zainstalować 3.6 wdrażania sieci Web zamiast 3.6 wdrażania sieci Web dla serwerów do hostingu. Jeśli jednak skonfigurujesz Web Deploy ręcznie, musisz upewnić się, że folder aplikacji na serwerze jest skonfigurowany z prawidłowymi wartościami i uprawnieniami (zobacz [Konfigurowanie witryny sieci Web ASP.NET](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Instalowanie i Konfigurowanie narzędzia Web Deploy dla serwerów do hostingu w systemie Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Utwórz plik ustawień publikowania w usługach IIS w systemie Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importowanie ustawień publikowania w programie Visual Studio i wdrażanie

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Po pomyślnym wdrożeniu aplikacji powinna być uruchamiana automatycznie. Jeśli aplikacja nie zostanie uruchomiony z programu Visual Studio, należy uruchomić aplikację w usługach IIS. Aby uzyskać ASP.NET Core, należy upewnić się, że w polu Pula aplikacji dla **tej opcji określono** wartość **Brak kodu zarządzanego**.

1. W oknie dialogowym **Ustawienia** Włącz debugowanie, klikając przycisk **dalej**, wybierz konfigurację **debugowania** , a następnie wybierz pozycję **Usuń dodatkowe pliki w miejscu docelowym** w obszarze Opcje **publikowania plików** .

    > [!NOTE]
    > W przypadku wybrania konfiguracji wydania podczas publikowania należy wyłączyć debugowanie w pliku *Web. config* .

1. Kliknij przycisk **Zapisz** , a następnie ponownie Opublikuj aplikację.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Opcjonalnie) Wdrażanie poprzez publikowanie do folderu lokalnego

Za pomocą tej opcji można wdrożyć aplikację, jeśli chcesz skopiować aplikację do usług IIS przy użyciu programu PowerShell, RoboCopy lub ręcznie skopiować pliki.

### <a name="BKMK_deploy_asp_net"></a>Konfigurowanie witryny sieci Web ASP.NET Core na komputerze z systemem Windows Server

W przypadku importowania ustawień publikowania można pominąć tę sekcję.

1. Otwórz **menedżera Internet Information Services (IIS)** i przejdź do **witryny**.

2. Kliknij prawym przyciskiem myszy **domyślny węzeł witryny sieci Web** i wybierz polecenie **Dodaj aplikację**.

3. W polu **alias** ustaw wartość **MyASPApp** , a pole Pula aplikacji **nie ma kodu zarządzanego**. Ustaw **ścieżkę fizyczną** na **C:\Publish** (w którym później zostanie wdrożony projekt ASP.NET Core).

4. Po wybraniu lokacji w Menedżerze usług IIS wybierz pozycję **Edytuj uprawnienia**i upewnij się, że konto IUSR, IIS_IUSRS lub użytkownik skonfigurowany dla puli aplikacji jest autoryzowanym użytkownikiem z uprawnieniami do odczytu & wykonywania.

    Jeśli nie widzisz jednego z tych użytkowników z dostępem, wykonaj kroki, aby dodać IUSR jako użytkownik z uprawnieniami do odczytu & wykonywania.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Obowiązkowe Publikowanie i wdrażanie aplikacji przez publikowanie do folderu lokalnego z programu Visual Studio

Jeśli nie używasz Web Deploy, musisz opublikować i wdrożyć aplikację przy użyciu systemu plików lub innych narzędzi. Możesz rozpocząć od utworzenia pakietu przy użyciu systemu plików, a następnie wdrożyć pakiet ręcznie lub użyć innych narzędzi, takich jak PowerShell, RoboCopy lub XCopy. W tej sekcji założono, że ręcznie skopiujesz pakiet, jeśli nie używasz Web Deploy.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a>Pobieranie i Instalowanie narzędzi zdalnych w systemie Windows Server

Pobierz wersję narzędzi zdalnych, która pasuje do używanej wersji programu Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="BKMK_setup"></a>Konfigurowanie zdalnego debugera w systemie Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Jeśli musisz dodać uprawnienia dla dodatkowych użytkowników, zmienić tryb uwierzytelniania lub numer portu dla zdalnego debugera, zobacz [Konfigurowanie zdalnego debugera](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="BKMK_attach"></a>Dołączanie do aplikacji ASP.NET z komputera z programu Visual Studio

1. Na komputerze z Visual Studio Otwórz rozwiązanie, które próbujesz debugować (**MyASPApp** , jeśli wykonano kroki opisane w tym artykule).
2. W programie Visual Studio kliknij pozycję **debuguj > Dołącz do procesu** (Ctrl + Alt + P).

    > [!TIP]
    > W programie Visual Studio 2017 i nowszych wersjach można ponownie dołączyć do tego samego procesu, który został wcześniej dołączony do programu przy użyciu **debugowania > ponownie dołączyć do procesu...** (Shift + Alt + P).

3. Ustaw pole kwalifikator na **\<nazwę komputera zdalnego >** i naciśnij klawisz **Enter**.

    Sprawdź, czy program Visual Studio dodaje wymagany port do nazwy komputera, która jest wyświetlana w formacie: **\<nazwa komputera zdalnego >:p**

    ::: moniker range=">=vs-2019"
    W programie Visual Studio 2019 powinna zostać wyświetlona **nazwa\<komputera zdalnego >: 4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    W programie Visual Studio 2017 powinna zostać wyświetlona **nazwa\<komputera zdalnego >: 4022**
    ::: moniker-end
    Port jest wymagany. Jeśli nie widzisz numeru portu, Dodaj go ręcznie.

4. Kliknij przycisk **Odśwież**.
    Niektóre procesy powinny być widoczne w oknie **dostępne procesy** .

    Jeśli nie widzisz wszystkie procesy, spróbuj przy użyciu adresu IP zamiast nazwy komputera zdalnego (port jest wymagany). Aby uzyskać adres IPv4, można użyć `ipconfig` w wierszu polecenia.

    Jeśli chcesz użyć przycisku **Znajdź** , może być konieczne [otwarcie portu UDP 3702](#bkmk_openports) na serwerze.

5. Zaznacz opcję **Pokaż procesy wszystkich użytkowników**.

6. Wpisz pierwszą literę nazwy procesu, aby szybko znaleźć aplikację.

    * Wybierz polecenie **dotnet. exe** (dla platformy .NET Core)

      Jeśli masz wiele procesów, na których jest wyświetlany program **dotnet. exe**, Sprawdź kolumnę **Nazwa użytkownika** . W niektórych scenariuszach kolumna **Nazwa użytkownika** zawiera nazwę puli aplikacji, na przykład **APPPOOL\DefaultAppPool IIS**. Jeśli zostanie wyświetlona Pula aplikacji, prosty sposób na zidentyfikowanie poprawnego procesu polega na utworzeniu nowej nazwanej puli aplikacji dla wystąpienia aplikacji, które ma być debugowane, a następnie można ją łatwo znaleźć w kolumnie **Nazwa użytkownika** .

    * W niektórych scenariuszach usług IIS na liście procesów może znajdować się nazwa aplikacji, na przykład **MyASPApp. exe**. Zamiast tego możesz dołączyć do tego procesu.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Kliknij przycisk **Dołącz**.

8. Otwórz witrynę sieci Web na komputerze zdalnym. W przeglądarce przejdź do **http://\<nazwa komputera zdalnego >** .

    Powinna zostać wyświetlona strona sieci web platformy ASP.NET.
9. W uruchomionej aplikacji ASP.NET kliknij link do strony **informacje** .

    W programie Visual Studio powinny trafiony punkt przerwania.

### <a name="bkmk_openports"></a>Rozwiązywanie problemów: otwieranie wymaganych portów w systemie Windows Server

W większości konfiguracji wymagane porty są otwarte przez instalację programu ASP.NET i zdalny debuger. Jednak w przypadku rozwiązywania problemów z wdrażaniem, gdy aplikacja znajduje się za zaporą, może być konieczne zweryfikowanie, czy są otwarte odpowiednie porty.

Na maszynie wirtualnej platformy Azure należy otworzyć porty za pomocą [sieciowej grupy zabezpieczeń](/azure/virtual-machines/windows/nsg-quickstart-portal).

Wymagane porty:

* 80 - wymagane dla usług IIS
::: moniker range=">=vs-2019"
* 4024 — wymagane do zdalnego debugowania z programu Visual Studio 2019 (zobacz [zdalne przydziały portu debugera](../debugger/remote-debugger-port-assignments.md) , aby uzyskać więcej informacji).
::: moniker-end
::: moniker range="vs-2017"
* 4022 — wymagane do zdalnego debugowania z programu Visual Studio 2017 (zobacz [zdalne przydziały portu debugera](../debugger/remote-debugger-port-assignments.md) , aby uzyskać więcej informacji).
::: moniker-end
* UDP 3702 — (opcjonalnie) port odnajdywania umożliwia korzystanie z przycisku **Znajdź** podczas dołączania do zdalnego debugera w programie Visual Studio.

Ponadto te porty powinny być już otwarte przez instalację ASP.NET:
- 8172 — (opcjonalnie) wymagany dla narzędzia Web Deploy do wdrażania aplikacji w programie Visual Studio
