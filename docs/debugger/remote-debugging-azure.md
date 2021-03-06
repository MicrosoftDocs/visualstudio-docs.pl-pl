---
title: Zdalne debugowanie ASP.NET Core w usługach IIS i na platformie Azure | Microsoft Docs
description: Dowiedz się, jak skonfigurować i skonfigurować aplikację ASP.NET Core programu Visual Studio, wdrożyć ją w usługach IIS przy użyciu platformy Azure i dołączyć zdalny debuger z programu Visual Studio.
ms.custom: remotedebugging
ms.date: 05/06/2020
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: 619f1f1cc99cbab425bc1bcb2bac181e09db8fc4
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2021
ms.locfileid: "102250071"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>Zdalne debugowanie ASP.NET Core w usługach IIS na platformie Azure w programie Visual Studio

W tym przewodniku wyjaśniono, jak skonfigurować i skonfigurować aplikację ASP.NET Core programu Visual Studio, wdrożyć ją w usługach IIS przy użyciu platformy Azure i dołączyć zdalny debuger z programu Visual Studio.

Zalecany sposób zdalnego debugowania na platformie Azure zależy od Twojego scenariusza:

* Aby debugować ASP.NET Core na Azure App Service, zobacz [debugowanie aplikacji platformy Azure przy użyciu Snapshot Debugger](../debugger/debug-live-azure-applications.md). Jest to zalecana metoda.
* Aby debugować ASP.NET Core na Azure App Service przy użyciu bardziej tradycyjnych funkcji debugowania, wykonaj kroki opisane w tym temacie (zobacz sekcję [debugowanie zdalne na Azure App Service](#remote_debug_azure_app_service)).

    W tym scenariuszu należy wdrożyć aplikację z programu Visual Studio na platformie Azure, ale nie musisz ręcznie instalować ani konfigurować usług IIS ani zdalnego debugera (te składniki są reprezentowane przez linie kropkowane), jak pokazano na poniższej ilustracji.

    ![Diagram przedstawiający relację między programem Visual Studio, Azure App Service i aplikacją ASP.NET. Usługi IIS i zdalny debuger są reprezentowane z kropkowanymi liniami.](../debugger/media/remote-debugger-azure-app-service.png)

* Aby debugować usługi IIS na maszynie wirtualnej platformy Azure, wykonaj kroki opisane w tym temacie (zobacz sekcję [debugowanie zdalne na maszynie wirtualnej platformy Azure](#remote_debug_azure_vm)). Pozwala to na użycie niestandardowej konfiguracji usług IIS, ale kroki instalacji i wdrażania są bardziej skomplikowane.

    W przypadku maszyny wirtualnej platformy Azure należy wdrożyć aplikację z programu Visual Studio na platformie Azure, a także ręcznie zainstalować rolę usług IIS i zdalny debuger, jak pokazano na poniższej ilustracji.

    ![Diagram przedstawiający relację między programem Visual Studio, maszyną wirtualną platformy Azure i aplikacją ASP.NET. Usługi IIS i zdalny debuger są reprezentowane z pełnymi wierszami.](../debugger/media/remote-debugger-azure-vm.png)

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

Debugowanie między dwoma komputerami połączonymi za pomocą serwera proxy nie jest obsługiwane. Debugowanie w przypadku dużych opóźnień lub połączeń o niskiej przepustowości, takich jak Internet telefoniczny lub przez Internet w różnych krajach, nie jest zalecane i może się nie powieść. Aby uzyskać pełną listę wymagań, zobacz [wymagania](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Tworzenie aplikacji ASP.NET Core na komputerze z Visual Studio

1. Utwórz nową aplikację sieci Web ASP.NET Core.

    ::: moniker range=">=vs-2019"
    W programie Visual Studio 2019 wybierz pozycję **Utwórz nowy projekt** w oknie uruchamiania. Jeśli okno startowe nie jest otwarte, wybierz pozycję **plik**  >  **startowy**. Wpisz **aplikacja sieci Web**, wybierz **C#** jako język, a następnie wybierz **ASP.NET Core aplikacji sieci Web (Model-View-Controller)**, a następnie wybierz **dalej**. Na następnym ekranie Nazwij projekt **MyASPApp**, a następnie wybierz przycisk **dalej**.

    Wybierz zalecaną platformę docelową (.NET Core 3,1) lub .NET 5, a następnie wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    W programie Visual Studio 2017 wybierz kolejno pozycje **plik > nowy > projekt**, a następnie wybierz pozycję **Visual C# > Web > ASP.NET Core aplikacji sieci Web**. W sekcji szablony ASP.NET Core wybierz pozycję **aplikacja sieci Web (Model-View-Controller)**. Upewnij się, że wybrano ASP.NET Core 2,1, że **Obsługa platformy Docker** nie jest zaznaczona i że **uwierzytelnianie** jest ustawione na wartość **bez uwierzytelniania**. Nazwij projekt **MyASPApp**.
    ::: moniker-end

1. Otwórz plik About.cshtml.cs i ustaw punkt przerwania w `OnGet` metodzie (w starszych szablonach otwórz HomeController.cs i ustaw punkt przerwania w `About()` metodzie).

## <a name="remote-debug-aspnet-core-on-an-azure-app-service"></a><a name="remote_debug_azure_app_service"></a> ASP.NET Core debugowania zdalnego na Azure App Service

W programie Visual Studio można szybko publikować i debugować aplikację w w pełni zainicjowanym wystąpieniu usług IIS. Jednak Konfiguracja usług IIS jest wstępnie ustawiona i nie można jej dostosować. Aby uzyskać bardziej szczegółowe instrukcje, zobacz [wdrażanie aplikacji sieci web ASP.NET Core na platformie Azure przy użyciu programu Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Jeśli potrzebujesz możliwości dostosowania usług IIS, wypróbuj debugowanie na [maszynie wirtualnej platformy Azure](#remote_debug_azure_vm)).

#### <a name="to-deploy-the-app-and-remote-debug-using-cloud-explorer"></a>Aby wdrożyć aplikację i debugowanie zdalne za pomocą programu Cloud Explorer

1. W programie Visual Studio kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz polecenie **Publikuj**.

    Jeśli wszystkie profile publikowania zostały wcześniej skonfigurowane, zostanie wyświetlone okienko **Publikowanie** . Wybierz pozycję **Nowy** lub **Nowy profil**.

1. Utwórz nowy profil publikowania.

    ::: moniker range=">=vs-2019"
    Wybierz pozycję **Azure** z okna dialogowego **Publikowanie** , a **następnie** wybierz przycisk Dalej. Następnie wybierz **Azure App Service (Windows)**, wybierz pozycję **dalej** i postępuj zgodnie z monitami, aby utworzyć profil.

    :::image type="content" source="../debugger/media/vs-2019/remotedbg-azure-app-service-profile.png" alt-text="Wdrażanie aplikacji internetowej ASP.NET Core na platformie Azure przy użyciu programu Visual Studio":::
    ::: moniker-end
    ::: moniker range="vs-2017"

    Wybierz **Azure App Service** z okna dialogowego **Publikowanie** , wybierz pozycję **Utwórz nowy** i postępuj zgodnie z monitami, aby utworzyć profil.

    ![Publikowanie w usłudze Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)
    ::: moniker-end

    Aby uzyskać bardziej szczegółowe instrukcje, zobacz [wdrażanie aplikacji sieci web ASP.NET Core na platformie Azure przy użyciu programu Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

1. W oknie publikowanie wybierz polecenie **Edytuj konfigurację** i Przełącz się do konfiguracji debugowania, a następnie wybierz pozycję **Publikuj**.

   Do debugowania aplikacji wymagana jest Konfiguracja debugowania.

1. Otwórz program **Cloud Explorer** (**Wyświetl**  >  **Eksplorator chmury**), kliknij prawym przyciskiem myszy wystąpienie App Service i wybierz **Dołącz debuger**.

   Jeśli program Cloud Explorer jest niedostępny, Otwórz Eksplorator serwera zamiast tego. Następnie kliknij prawym przyciskiem myszy wystąpienie App Service w Eksplorator serwera i wybierz polecenie **Dołącz debuger**.

1. W uruchomionej aplikacji ASP.NET kliknij link do strony **informacje** .

    Punkt przerwania powinien zostać trafiony w programie Visual Studio.

    Gotowe. Pozostałe kroki opisane w tym temacie mają zastosowanie do zdalnego debugowania na maszynie wirtualnej platformy Azure.

## <a name="remote-debug-aspnet-core-on-an-azure-vm"></a><a name="remote_debug_azure_vm"></a> ASP.NET Core debugowania zdalnego na maszynie wirtualnej platformy Azure

Można utworzyć maszynę wirtualną platformy Azure dla systemu Windows Server, a następnie zainstalować i skonfigurować usługi IIS oraz inne wymagane składniki oprogramowania. Zajmuje to więcej czasu niż wdrożenie do Azure App Service i wymaga wykonania pozostałych kroków opisanych w tym samouczku.

Te procedury zostały przetestowane na tych konfiguracjach serwera:

* Windows Server 2012 R2 i IIS 8
* Windows Server 2016 i IIS 10
* Windows Server 2019 i IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>Aplikacja jest już uruchomiona w usługach IIS na maszynie wirtualnej platformy Azure?

Ten artykuł zawiera instrukcje dotyczące konfigurowania podstawowej konfiguracji usług IIS w systemie Windows Server i wdrażania aplikacji z programu Visual Studio. Te kroki są dołączone do programu, aby upewnić się, że na serwerze są zainstalowane wymagane składniki, że aplikacja może działać poprawnie i że jest gotowy do zdalnego debugowania.

* Jeśli aplikacja jest uruchomiona w usługach IIS i po prostu chcesz pobrać zdalny debuger i rozpocząć debugowanie, przejdź do pozycji [Pobierz i zainstaluj narzędzia zdalne w systemie Windows Server](#BKMK_msvsmon).

* Jeśli potrzebujesz pomocy, aby upewnić się, że aplikacja została prawidłowo skonfigurowana, wdrożona i uruchomiona w usługach IIS, aby umożliwić debugowanie, wykonaj wszystkie kroki opisane w tym temacie.

  * Przed rozpoczęciem wykonaj wszystkie kroki opisane w temacie [Instalowanie i uruchamianie usług IIS](/azure/virtual-machines/windows/quick-create-portal).

  * Po otwarciu portu 80 w sieciowej grupie zabezpieczeń, należy również otworzyć [właściwy port](#bkmk_openports) dla zdalnego debugera (4024 lub 4022). Dzięki temu nie będzie trzeba otwierać go później. Jeśli używasz Web Deploy, Otwórz również port 8172.

### <a name="update-browser-security-settings-on-windows-server"></a>Aktualizowanie ustawień zabezpieczeń przeglądarki w systemie Windows Server

Jeśli konfiguracja zwiększonych zabezpieczeń jest włączona w programie Internet Explorer (jest włączona domyślnie), może być konieczne dodanie niektórych domen jako zaufanych lokacji, aby umożliwić pobranie niektórych składników serwera sieci Web. Dodaj Zaufane witryny, wybierając **Opcje internetowe > zabezpieczenia > zaufane lokacje > Lokacje**. Dodaj następujące domeny.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Podczas pobierania oprogramowania można uzyskać żądania udzielenia uprawnień do ładowania różnych skryptów i zasobów witryny sieci Web. Niektóre z tych zasobów nie są wymagane, ale aby uprościć proces, kliknij przycisk **Dodaj** po wyświetleniu monitu.

### <a name="install-aspnet-core-on-windows-server"></a>Zainstaluj ASP.NET Core w systemie Windows Server

1. Zainstaluj pakiet hostingu platformy .NET Core w systemie hostingu. Pakiet instaluje środowisko uruchomieniowe programu .NET Core, bibliotekę .NET Core i moduł ASP.NET Core. Aby uzyskać bardziej szczegółowe instrukcje, zobacz [Publikowanie w usługach IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    W przypadku platformy .NET Core 3 Zainstaluj [pakiet hostingu platformy .NET Core](https://dotnet.microsoft.com/permalink/dotnetcore-current-windows-runtime-bundle-installer).
    W przypadku platformy .NET Core 2 Zainstaluj [platformę .NET Core systemu Windows Server](https://aka.ms/dotnetcore-2-windowshosting).

    > [!NOTE]
    > Jeśli system nie ma połączenia z Internetem, uzyskaj i zainstaluj *[pakiet redystrybucyjny Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=53840)* przed zainstalowaniem pakietu hostingu platformy .NET Core systemu Windows Server.

2. Uruchom ponownie system (lub wykonaj polecenie **net stop was/y** , a następnie **net start W3SVC** z wiersza polecenia, aby wybrać zmianę ścieżki systemowej).

## <a name="choose-a-deployment-option"></a>Wybierz opcję wdrożenia

Jeśli potrzebujesz pomocy przy wdrażaniu aplikacji w usługach IIS, weź pod uwagę następujące opcje:

* Wdróż aplikację, tworząc plik ustawień publikowania w usługach IIS i importując ustawienia w programie Visual Studio. W niektórych scenariuszach jest to szybki sposób wdrożenia aplikacji. Podczas tworzenia pliku ustawień publikowania uprawnienia są konfigurowane automatycznie w usługach IIS.

* Wdróż program przez opublikowanie w folderze lokalnym i skopiowanie danych wyjściowych za pomocą preferowanej metody do przygotowanego folderu aplikacji w programie IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>Obowiązkowe Wdrażanie przy użyciu pliku ustawień publikowania

Tej opcji można użyć do utworzenia pliku ustawień publikowania i zaimportowania go do programu Visual Studio.

> [!NOTE]
> Ta metoda wdrażania używa Web Deploy, która musi być zainstalowana na serwerze. Jeśli chcesz skonfigurować Web Deploy ręcznie zamiast zaimportować ustawienia, możesz zainstalować Web Deploy 3,6 zamiast Web Deploy 3,6 dla serwerów hostingu. Jeśli jednak skonfigurujesz Web Deploy ręcznie, musisz upewnić się, że folder aplikacji na serwerze jest skonfigurowany z prawidłowymi wartościami i uprawnieniami (zobacz [Konfigurowanie witryny sieci Web ASP.NET](#BKMK_deploy_asp_net)).

### <a name="configure-the-aspnet-core-web-site"></a>Skonfiguruj witrynę sieci Web ASP.NET Core

1. W Menedżerze usług IIS w lewym okienku w obszarze **połączenia** wybierz pozycję **Pule aplikacji**. Otwórz przystawkę **Domyślna** i ustaw **wersję środowiska .NET CLR** na **Brak kodu zarządzanego**. Jest to wymagane w przypadku ASP.NET Core. Domyślna witryna sieci Web używa tej domyślnej.

2. Zatrzymaj i uruchom ponownie tę samą wartość.

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Instalowanie i Konfigurowanie Web Deploy serwerów hostingu w systemie Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Tworzenie pliku ustawień publikowania w usługach IIS w systemie Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importowanie ustawień publikowania w programie Visual Studio i wdrażanie

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

> [!NOTE]
> Po ponownym uruchomieniu maszyny wirtualnej platformy Azure adres IP może się zmienić.

Po pomyślnym wdrożeniu aplikacji należy uruchomić ją automatycznie. Jeśli aplikacja nie uruchamia się z programu Visual Studio, uruchom aplikację w usługach IIS, aby sprawdzić, czy działa poprawnie. W przypadku ASP.NET Core należy również upewnić się, że w polu Pula aplikacji **dla tej opcji określono wartość** **Brak kodu zarządzanego**.

1. W oknie dialogowym **Ustawienia** Włącz debugowanie, klikając przycisk **dalej**, wybierz konfigurację **debugowania** , a następnie wybierz pozycję **Usuń dodatkowe pliki w miejscu docelowym** w obszarze Opcje **publikowania plików** .

    > [!IMPORTANT]
    > W przypadku wybrania konfiguracji wydania można wyłączyć debugowanie w pliku *web.config* podczas publikowania.

1. Kliknij przycisk **Zapisz** , a następnie ponownie Opublikuj aplikację.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>Obowiązkowe Wdróż przez opublikowanie w folderze lokalnym

Za pomocą tej opcji można wdrożyć aplikację, jeśli chcesz skopiować aplikację do usług IIS przy użyciu programu PowerShell, RoboCopy lub ręcznie skopiować pliki.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a> Konfigurowanie witryny sieci Web ASP.NET Core na komputerze z systemem Windows Server

W przypadku importowania ustawień publikowania można pominąć tę sekcję.

1. Otwórz **menedżera Internet Information Services (IIS)** i przejdź do **witryny**.

2. Kliknij prawym przyciskiem myszy **domyślny węzeł witryny sieci Web** i wybierz polecenie **Dodaj aplikację**.

3. W polu **alias** ustaw wartość **MyASPApp** , a pole Pula aplikacji **nie ma kodu zarządzanego**. Ustaw **ścieżkę fizyczną** na **C:\Publish** (w którym później zostanie wdrożony projekt ASP.NET Core).

4. Po wybraniu lokacji w Menedżerze usług IIS wybierz pozycję **Edytuj uprawnienia** i upewnij się, że konto IUSR, IIS_IUSRS lub użytkownik skonfigurowany dla puli aplikacji jest autoryzowanym użytkownikiem z uprawnieniami do odczytu & wykonywania.

    Jeśli nie widzisz jednego z tych użytkowników z dostępem, wykonaj kroki, aby dodać IUSR jako użytkownik z uprawnieniami do odczytu & wykonywania.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Obowiązkowe Publikowanie i wdrażanie aplikacji przez publikowanie do folderu lokalnego z programu Visual Studio

Jeśli nie używasz Web Deploy, musisz opublikować i wdrożyć aplikację przy użyciu systemu plików lub innych narzędzi. Możesz rozpocząć od utworzenia pakietu przy użyciu systemu plików, a następnie wdrożyć pakiet ręcznie lub użyć innych narzędzi, takich jak PowerShell, Robocopy lub XCopy. W tej sekcji założono, że ręcznie skopiujesz pakiet, jeśli nie używasz Web Deploy.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a> Pobieranie i Instalowanie narzędzi zdalnych w systemie Windows Server

Pobierz wersję narzędzi zdalnych, która pasuje do używanej wersji programu Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a> Konfigurowanie zdalnego debugera w systemie Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Jeśli musisz dodać uprawnienia dla dodatkowych użytkowników, zmienić tryb uwierzytelniania lub numer portu dla zdalnego debugera, zobacz [Konfigurowanie zdalnego debugera](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a> Dołączanie do aplikacji ASP.NET z komputera z programu Visual Studio

1. Na komputerze z Visual Studio Otwórz rozwiązanie, które próbujesz debugować (**MyASPApp** , jeśli wykonano kroki opisane w tym artykule).
2. W programie Visual Studio kliknij pozycję **debuguj > Dołącz do procesu** (Ctrl + Alt + P).

    > [!TIP]
    > W programie Visual Studio 2017 i nowszych wersjach można ponownie dołączyć do tego samego procesu, który został wcześniej dołączony do programu przy użyciu **debugowania > ponownie dołączyć do procesu...** (Shift + Alt + P).

3. Ustaw pole kwalifikator na **\<remote computer name>** i naciśnij klawisz **Enter**.

    Sprawdź, czy program Visual Studio dodaje wymagany port do nazwy komputera, która jest wyświetlana w formacie: **\<remote computer name> :p** .

    ::: moniker range=">=vs-2019"
    W programie Visual Studio 2019 powinna zostać wyświetlona **\<remote computer name> : 4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    W programie Visual Studio 2017 powinna zostać wyświetlona **\<remote computer name> : 4022**
    ::: moniker-end
    Port jest wymagany. Jeśli nie widzisz numeru portu, Dodaj go ręcznie.

4. Kliknij przycisk **Odśwież**.
    Niektóre procesy powinny być widoczne w oknie **dostępne procesy** .

    Jeśli nie widzisz żadnych procesów, spróbuj użyć adresu IP zamiast nazwy komputera zdalnego (port jest wymagany). Można użyć `ipconfig` w wierszu polecenia, aby uzyskać adres IPv4.

    Jeśli chcesz użyć przycisku **Znajdź** , może być konieczne [otwarcie portu UDP 3702](#bkmk_openports) na serwerze.

5. Zaznacz opcję  **Pokaż procesy wszystkich użytkowników**.

6. Wpisz pierwszą literę nazwy procesu, aby szybko znaleźć aplikację.

    * Jeśli używasz [modelu hostingu w procesie](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1&preserve-view=true#hosting-models) na serwerze IIS, wybierz właściwy proces **w3wp.exe** . Począwszy od platformy .NET Core 3, jest to ustawienie domyślne.

    * W przeciwnym razie wybierz proces **dotnet.exe** . (Jest to model hostingu poza procesem).

    Jeśli masz wiele procesów pokazujących *w3wp.exe* lub *dotnet.exe*, Sprawdź kolumnę **Nazwa użytkownika** . W niektórych scenariuszach kolumna **Nazwa użytkownika** zawiera nazwę puli aplikacji, na przykład **APPPOOL\DefaultAppPool IIS**. Jeśli zobaczysz pulę aplikacji, ale nie jest ona unikatowa, Utwórz nową nazwę puli aplikacji dla wystąpienia aplikacji, które chcesz debugować, a następnie możesz ją łatwo znaleźć w kolumnie **Nazwa użytkownika** .

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Kliknij przycisk **Dołącz**.

8. Otwórz witrynę sieci Web komputera zdalnego. W przeglądarce przejdź do **http:// \<remote computer name>**.

    Powinna zostać wyświetlona strona sieci Web ASP.NET.
9. W uruchomionej aplikacji ASP.NET kliknij link do strony **informacje** .

    Punkt przerwania powinien zostać trafiony w programie Visual Studio.

### <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> Rozwiązywanie problemów: otwieranie wymaganych portów w systemie Windows Server

W większości instalacji wymagane porty są otwierane przez instalację ASP.NET i zdalnego debugera. Jednak w przypadku rozwiązywania problemów z wdrażaniem, gdy aplikacja znajduje się za zaporą, może być konieczne zweryfikowanie, czy są otwarte odpowiednie porty.

Na maszynie wirtualnej platformy Azure należy otworzyć porty za pomocą [sieciowej grupy zabezpieczeń](/azure/virtual-machines/windows/nsg-quickstart-portal).

Wymagane porty:

* 80 — wymagane dla usług IIS
::: moniker range=">=vs-2019"
* 4024 — wymagane do zdalnego debugowania z programu Visual Studio 2019 (zobacz [zdalne przydziały portu debugera](../debugger/remote-debugger-port-assignments.md) , aby uzyskać więcej informacji).
::: moniker-end
::: moniker range="vs-2017"
* 4022 — wymagane do zdalnego debugowania z programu Visual Studio 2017 (zobacz [zdalne przydziały portu debugera](../debugger/remote-debugger-port-assignments.md) , aby uzyskać więcej informacji).
::: moniker-end
* UDP 3702 — (opcjonalnie) port odnajdywania umożliwia korzystanie z przycisku **Znajdź** podczas dołączania do zdalnego debugera w programie Visual Studio.

Ponadto te porty powinny być już otwarte przez instalację ASP.NET:
- 8172 — (opcjonalnie) wymagane do Web Deploy wdrożenia aplikacji z programu Visual Studio
