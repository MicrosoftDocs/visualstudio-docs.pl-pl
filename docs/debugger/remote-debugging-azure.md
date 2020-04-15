---
title: Zdalne debugowanie ASP.NET Core na usługach IIS i na platformie Azure | Dokumenty firmy Microsoft
ms.custom: remotedebugging
ms.date: 04/14/2020
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: 079e324f2304118c9041118c13e8ebc0cce2015c
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385505"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>Zdalne debugowanie ASP.NET core na usługach IIS na platformie Azure w programie Visual Studio

W tym przewodniku wyjaśniono, jak skonfigurować i skonfigurować aplikację programu Visual Studio ASP.NET Core, wdrożyć ją w usługach IIS przy użyciu platformy Azure i dołączyć debuger zdalny z programu Visual Studio.

Zalecany sposób zdalnego debugowania na platformie Azure zależy od scenariusza:

* Aby debugować ASP.NET Core w usłudze Azure App Service, zobacz [Debugowanie aplikacji platformy Azure przy użyciu debugera migawek](../debugger/debug-live-azure-applications.md). Jest to zalecana metoda.
* Aby debugować ASP.NET Core w usłudze Azure App Service przy użyciu bardziej tradycyjnych funkcji debugowania, wykonaj kroki opisane w tym temacie (zobacz sekcję [Debugowanie zdalne w usłudze Azure App Service).](#remote_debug_azure_app_service)

    W tym scenariuszu należy wdrożyć aplikację z programu Visual Studio na platformie Azure, ale nie trzeba ręcznie zainstalować lub skonfigurować usługi IIS lub debuger zdalny (te składniki są reprezentowane z liniami kropkowanymi), jak pokazano na poniższej ilustracji.

    ![Składniki zdalnego debugera](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Aby debugować usługi IIS na maszynie Wirtualnej platformy Azure, wykonaj kroki opisane w tym temacie (zobacz [sekcję Zdalne debugowanie na maszynie Wirtualnej platformy Azure).](#remote_debug_azure_vm) Dzięki temu można użyć dostosowanej konfiguracji usług IIS, ale kroki konfiguracji i wdrażania są bardziej skomplikowane.

    W przypadku maszyny Wirtualnej platformy Azure należy wdrożyć aplikację z programu Visual Studio na platformie Azure, a także ręcznie zainstalować rolę usług IIS i debuger zdalny, jak pokazano na poniższej ilustracji.

    ![Składniki zdalnego debugera](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Aby debugować ASP.NET Core w sieci szkieletowej usług Azure, zobacz [Debugowanie aplikacji zdalnej sieci szkieletowej usług](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Pamiętaj, aby usunąć zasoby platformy Azure, które można utworzyć po wykonaniu kroków w tym samouczku. W ten sposób można uniknąć ponoszenia niepotrzebnych opłat.

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range=">=vs-2019"
Visual Studio 2019 jest wymagane, aby wykonać kroki pokazane w tym artykule.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 jest wymagane, aby wykonać kroki pokazane w tym artykule.
::: moniker-end

### <a name="network-requirements"></a>Wymagania dotyczące sieci

Debugowanie między dwoma komputerami podłączonymi za pośrednictwem serwera proxy nie jest obsługiwane. Debugowanie za pośrednictwem połączenia o dużej masie lub niskiej przepustowości, takiego jak dialup Internet lub przez Internet w różnych krajach, nie jest zalecane i może zakończyć się niepowodzeniem lub być niedopuszczalnie powolne. Aby uzyskać pełną listę wymagań, zobacz [Wymagania](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Tworzenie aplikacji ASP.NET Core na komputerze z programem Visual Studio

1. Utwórz nową aplikację ASP.NET Core.

    ::: moniker range=">=vs-2019"
    W programie Visual Studio 2019 wpisz **klawisze Ctrl + Q,** aby otworzyć pole wyszukiwania, wpisz **asp.net**, wybierz pozycję **Szablony**, a następnie wybierz pozycję **Utwórz nową ASP.NET podstawową aplikację sieci Web**. W wyświetlonym oknie dialogowym nazwij projekt **MyASPApp**, a następnie wybierz pozycję **Utwórz**. Następnie wybierz pozycję **Aplikacja sieci Web (Model-View-Controller),** a następnie wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    W programie Visual Studio 2017 wybierz pozycję **Plik > nowy projekt >**, a następnie wybierz pozycję Visual **C# > Web > ASP.NET Core Web Application**. W sekcji szablony ASP.NET Core wybierz pozycję **Aplikacja sieci Web (Administrator widoku modelu)**. Upewnij się, że wybrano ASP.NET Core 2.1, że **opcja Włącz obsługę platformy Docker** nie jest zaznaczona i że **uwierzytelnianie** jest ustawione na **Brak uwierzytelniania**. Nazwij projekt **MyASPApp**.
    ::: moniker-end

1. Otwórz plik About.cshtml.cs i ustaw punkt przerwania `OnGet` w metodzie (w starszych szablonach otwórz HomeController.cs zamiast `About()` tego i ustaw punkt przerwania w metodzie).

## <a name="remote-debug-aspnet-core-on-an-azure-app-service"></a><a name="remote_debug_azure_app_service"></a>Zdalne debugowanie ASP.NET rdzenia w usłudze azure app service

W programie Visual Studio można szybko opublikować i debugować aplikację do w pełni aprowizowanego wystąpienia usług IIS. Jednak konfiguracja usług IIS jest wstępnie ustawiona i nie można jej dostosować. Aby uzyskać bardziej szczegółowe instrukcje, zobacz [Wdrażanie aplikacji sieci Web ASP.NET Core na platformie Azure przy użyciu programu Visual Studio.](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs) (Jeśli potrzebujesz możliwości dostosowania usług IIS, spróbuj debugować na [maszynie wirtualnej platformy Azure](#remote_debug_azure_vm).)

#### <a name="to-deploy-the-app-and-remote-debug-using-cloud-explorer"></a>Aby wdrożyć aplikację i zdalne debugowanie przy użyciu Cloud Explorer

1. W programie Visual Studio kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Publikuj**.

    Jeśli wcześniej skonfigurowano profile publikowania, zostanie wyświetlone okienko **Publikowania.** Kliknij **pozycję Nowy profil**.

1. Wybierz pozycję **Usługa Azure App Service** w oknie dialogowym **Publikowanie,** wybierz pozycję **Utwórz nowy**i postępuj zgodnie z instrukcjami, aby utworzyć profil.

    Aby uzyskać szczegółowe instrukcje, zobacz [Wdrażanie aplikacji sieci Web ASP.NET Core na platformie Azure przy użyciu programu Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Publikowanie w usłudze Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)

1. W oknie Publikowanie wybierz pozycję **Edytuj konfigurację** i przełącz się do konfiguracji debugowania, a następnie wybierz pozycję **Publikuj**.

   Konfiguracja debugowania jest wymagana do debugowania aplikacji.

1. Otwórz **Eksploratora chmury** **(Wyświetl** > **Eksploratora chmury),** kliknij prawym przyciskiem myszy wystąpienie usługi App Service i wybierz polecenie **Dołącz debuger**.

   Jeśli Eksplorator w chmurze nie jest dostępny, otwórz Eksploratora serwera. Następnie kliknij prawym przyciskiem myszy wystąpienie usługi App Service w Eksploratorze serwera i wybierz polecenie **Dołącz debuger**.

1. W uruchomionej aplikacji ASP.NET kliknij łącze do strony **Informacje.**

    Punkt przerwania powinien zostać trafiony w programie Visual Studio.

    Gotowe. Pozostałe kroki w tym temacie dotyczą zdalnego debugowania na maszynie Wirtualnej platformy Azure.

## <a name="remote-debug-aspnet-core-on-an-azure-vm"></a><a name="remote_debug_azure_vm"></a>Zdalne debugowanie ASP.NET rdzenia na maszynie Wirtualnej platformy Azure

Można utworzyć maszynę wirtualną platformy Azure dla systemu Windows Server, a następnie zainstalować i skonfigurować usługi IIS i inne wymagane składniki oprogramowania. Zajmuje to więcej czasu niż wdrażanie w usłudze Azure App Service i wymaga wykonania pozostałych kroków w tym samouczku.

Te procedury zostały przetestowane na następujących konfiguracjach serwera:
* Systemy Windows Server 2012 R2 i USŁUGI IIS 8
* Systemy Windows Server 2016 i USŁUGI IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>Aplikacja już uruchomiona w usługach IIS na maszynie Wirtualnej platformy Azure?

Ten artykuł zawiera kroki dotyczące konfigurowania podstawowej konfiguracji usług IIS na serwerze Windows i wdrażania aplikacji w programie Visual Studio. Te kroki są uwzględniane, aby upewnić się, że serwer ma zainstalowane wymagane składniki, że aplikacja może działać poprawnie i że można przystąpić do zdalnego debugowania.

* Jeśli aplikacja działa w serwisach IIS i chcesz po prostu pobrać debuger zdalny i rozpocząć debugowanie, przejdź do [pozycji Pobierz i zainstaluj narzędzia zdalne w systemie Windows Server](#BKMK_msvsmon).

* Jeśli chcesz pomóc, aby upewnić się, że aplikacja jest skonfigurowana, wdrożona i działa poprawnie w usługach IIS, dzięki czemu można debugować, wykonaj wszystkie kroki opisane w tym temacie.

  * Przed rozpoczęciem wykonaj wszystkie kroki opisane w aplikacji [Zainstaluj i uruchom usługi IIS](/azure/virtual-machines/windows/quick-create-portal).

  * Po otwarciu portu 80 w grupie zabezpieczeń Sieć otwórz również [odpowiedni port](#bkmk_openports) dla zdalnego debugera (4024 lub 4022). W ten sposób nie będziesz musiał go później otwierać.

### <a name="update-browser-security-settings-on-windows-server"></a>Aktualizowanie ustawień zabezpieczeń przeglądarki w systemie Windows Server

Jeśli konfiguracja zwiększonych zabezpieczeń jest włączona w programie Internet Explorer (jest domyślnie włączona), może być konieczne dodanie niektórych domen jako zaufanych witryn, aby umożliwić pobranie niektórych składników serwera sieci Web. Dodaj zaufane witryny, przechodząc do **opcji internetowych > zabezpieczenia > zaufanych witryn > witryn .** Dodaj następujące domeny.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Podczas pobierania oprogramowania można otrzymywać prośby o udzielenie uprawnień do ładowania różnych skryptów i zasobów witryny sieci Web. Niektóre z tych zasobów nie są wymagane, ale aby uprościć proces, kliknij przycisk **Dodaj** po wyświetleniu monitu.

### <a name="install-aspnet-core-on-windows-server"></a>Instalowanie ASP.NET Core w systemie Windows Server

1. Zainstaluj pakiet [hostingu systemu .NET Core Windows Server w](https://aka.ms/dotnetcore-2-windowshosting) systemie hostingowym. Pakiet zainstaluje środowisko uruchomieniowe .NET Core, bibliotekę .NET Core i moduł ASP.NET Core. Aby uzyskać bardziej szczegółowe instrukcje, zobacz [Publikowanie w usługach IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Jeśli system nie ma połączenia z Internetem, przed zainstalowaniem pakietu hostingowego systemu .NET Core Windows Server Hosting można uzyskać i zainstalować program *[Microsoft Visual C++ 2015.](https://www.microsoft.com/download/details.aspx?id=53840)*

3. Uruchom ponownie system (lub wykonać **net stop został /y** następnie **net start w3svc** z wiersza polecenia, aby odebrać zmianę w ścieżce systemu).

## <a name="choose-a-deployment-option"></a>Wybierz opcję wdrażania

Jeśli potrzebujesz pomocy w celu wdrożenia aplikacji w uiświadamianych programach IIS, rozważ następujące opcje:

* Wdrażanie przez utworzenie pliku ustawień publikowania w ujm i zaimportowanie ustawień w programie Visual Studio. W niektórych scenariuszach jest to szybki sposób wdrażania aplikacji. Podczas tworzenia pliku ustawień publikowania uprawnienia są automatycznie konfigurowanie w uzywanych programach IIS.

* Wdrażanie przez publikowanie w folderze lokalnym i kopiowanie danych wyjściowych za pomocą preferowanej metody do przygotowanego folderu aplikacji w serwisach IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Opcjonalnie) Wdrażanie przy użyciu pliku ustawień publikowania

Tej opcji można utworzyć plik ustawień publikowania i zaimportować go do programu Visual Studio.

> [!NOTE]
> Ta metoda wdrażania używa wdrożenia w sieci Web. Jeśli chcesz ręcznie skonfigurować wdrażanie w sieci Web w programie Visual Studio zamiast importować te ustawienia, możesz zainstalować program Web Deploy 3.6 zamiast wdrożenia w sieci Web 3.6 dla serwerów hostingowych. Jeśli jednak program Wdrażania sieci Web zostanie skonfigurowany ręcznie, należy upewnić się, że folder aplikacji na serwerze jest skonfigurowany z poprawnymi wartościami i uprawnieniami (zobacz [Konfigurowanie ASP.NET witryny sieci Web](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Instalowanie i konfigurowanie wdrażania sieci Web dla serwerów hostingowych w systemie Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Tworzenie pliku ustawień publikowania w serwisach IIS w systemie Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importowanie ustawień publikowania w programie Visual Studio i wdrażanie

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Po pomyślnym wdrożeniu aplikacji należy uruchomić automatycznie. Jeśli aplikacja nie uruchamia się z programu Visual Studio, uruchom aplikację w iis. W przypadku ASP.NET Core należy upewnić się, że pole Puli aplikacji dla **puli DefaultAppPool** jest ustawione na **Brak kodu zarządzanego**.

1. W oknie dialogowym **Ustawienia** włącz debugowanie, klikając przycisk **Dalej**, wybierz konfigurację **debugowania,** a następnie wybierz pozycję **Usuń dodatkowe pliki w miejscu docelowym** w obszarze Opcje **publikowania plików.**

    > [!NOTE]
    > Jeśli wybierzesz konfigurację wersji, podczas publikowania należy wyłączyć debugowanie w pliku *web.config.*

1. Kliknij **pozycję Zapisz,** a następnie ponownie opublikuj aplikację.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Opcjonalnie) Wdrażanie przez publikowanie w folderze lokalnym

Za pomocą tej opcji można wdrożyć aplikację, jeśli chcesz skopiować aplikację do iIS przy użyciu programu PowerShell, RoboCopy lub chcesz ręcznie skopiować pliki.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a>Konfigurowanie witryny sieci Web ASP.NET Core na komputerze z systemem Windows Server

Jeśli importujesz ustawienia publikowania, możesz pominąć tę sekcję.

1. Otwórz **Menedżera internetowych usług informacyjnych (IIS)** i przejdź do **witryn**.

2. Kliknij prawym przyciskiem myszy domyślny węzeł **Witryna sieci Web** i wybierz polecenie Dodaj **aplikację**.

3. Ustaw pole **Alias** na **MyASPApp,** a pole Puli aplikacji na **Brak kodu zarządzanego**. Ustaw **ścieżkę fizyczną** na **C:\Publish** (gdzie później wdrożysz projekt ASP.NET Core).

4. Po wybraniu witryny w Menedżerze usług IIS wybierz pozycję Edytuj uprawnienia i upewnij się, że usługa IUSR, IIS_IUSRS lub użytkownik skonfigurowany dla puli aplikacji jest autoryzowanym użytkownikiem z **uprawnieniami**do odczytu & wykonywania.

    Jeśli nie widzisz jednego z tych użytkowników z dostępem, wykonaj kroki, aby dodać IUSR jako użytkownika z prawami do odczytu & wykonywania.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Opcjonalnie) Publikowanie i wdrażanie aplikacji przez publikowanie w folderze lokalnym z programu Visual Studio

Jeśli nie używasz narzędzia Web Deploy, musisz opublikować i wdrożyć aplikację przy użyciu systemu plików lub innych narzędzi. Można rozpocząć od utworzenia pakietu przy użyciu systemu plików, a następnie ręcznie wdrożyć pakiet lub użyć innych narzędzi, takich jak PowerShell, RoboCopy lub XCopy. W tej sekcji zakładamy, że ręcznie kopiujesz pakiet, jeśli nie używasz wdrażania w sieci Web.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>Pobieranie i instalowanie narzędzi zdalnych w systemie Windows Server

Pobierz wersję narzędzi zdalnych, która pasuje do twojej wersji programu Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a>Konfigurowanie zdalnego debugera w systemie Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Jeśli chcesz dodać uprawnienia dla dodatkowych użytkowników, zmień tryb uwierzytelniania lub numer portu dla zdalnego debugera, zobacz [Konfigurowanie debugera zdalnego](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>Dołącz do aplikacji ASP.NET z komputera programu Visual Studio

1. Na komputerze z programu Visual Studio otwórz rozwiązanie, które próbujesz debugować (**MyASPApp,** jeśli wykonując kroki opisane w tym artykule).
2. W programie Visual Studio kliknij polecenie **Debugowanie > dołącz do procesu** (Ctrl + Alt + P).

    > [!TIP]
    > W programie Visual Studio 2017 i nowszych wersjach można ponownie dołączyć do tego samego procesu, do którego wcześniej dołączono przy użyciu **debugowania > Ponowne dołączanie do procesu...** (Shift+Alt+P).

3. Ustaw pole Kwalifikator na ** \<>nazwa komputera zdalnego** i naciśnij klawisz **Enter**.

    Sprawdź, czy program Visual Studio dodaje wymagany port do nazwy komputera, który jest wyświetlany w formacie: ** \<nazwa komputera zdalnego>:port**

    ::: moniker range=">=vs-2019"
    W programie Visual Studio 2019 powinna być widoczna ** \<nazwa komputera zdalnego>:4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    W programie Visual Studio 2017 powinna być widoczna ** \<nazwa komputera zdalnego>:4022**
    ::: moniker-end
    Port jest wymagany. Jeśli nie widzisz numeru portu, dodaj go ręcznie.

4. Kliknij przycisk **Odśwież**.
    Niektóre procesy powinny być wyświetlane w oknie **Dostępne procesy.**

    Jeśli nie widzisz żadnych procesów, spróbuj użyć adresu IP zamiast nazwy komputera zdalnego (port jest wymagany). Można użyć `ipconfig` w wierszu polecenia, aby uzyskać adres IPv4.

    Jeśli chcesz użyć przycisku **Znajdź,** może być konieczne [otwarcie portu UDP 3702](#bkmk_openports) na serwerze.

5. Zaznacz **pole pokaż procesy od wszystkich użytkowników**.

6. Wpisz pierwszą literę nazwy procesu, aby szybko znaleźć aplikację.

    * Wybierz **program dotnet.exe** (dla platformy .NET Core)

      Jeśli masz wiele procesów pokazujących **program dotnet.exe,** zaznacz **kolumnę Nazwa użytkownika.** W niektórych scenariuszach **kolumna Nazwa użytkownika** zawiera nazwę puli aplikacji, na przykład **IIS APPPOOL\DefaultAppPool**. Jeśli widzisz pulę aplikacji, łatwym sposobem zidentyfikowania poprawnego procesu jest utworzenie nowej puli aplikacji o nazwie dla wystąpienia aplikacji, które chcesz debugować, a następnie można ją łatwo znaleźć w kolumnie **Nazwa użytkownika.**

    * W niektórych scenariuszach usługi IIS możesz znaleźć nazwę aplikacji na liście procesów, na przykład **MyASPApp.exe**. Zamiast tego można dołączyć do tego procesu.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Kliknij **pozycję Dołącz**.

8. Otwórz witrynę sieci Web komputera zdalnego. W przeglądarce przejdź do **http://\<nazwa komputera zdalnego>**.

    Powinna zostać wyświetlona strona internetowa ASP.NET.
9. W uruchomionej aplikacji ASP.NET kliknij łącze do strony **Informacje.**

    Punkt przerwania powinien zostać trafiony w programie Visual Studio.

### <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a>Rozwiązywanie problemów: otwieranie wymaganych portów w systemie Windows Server

W większości konfiguracji wymagane porty są otwierane przez instalację ASP.NET i debugera zdalnego. Jednak jeśli rozwiązujesz problemy z wdrażaniem, a aplikacja jest hostowana za zaporą, może być konieczne sprawdzenie, czy prawidłowe porty są otwarte.

Na maszynie Wirtualnej platformy Azure należy otworzyć porty za pośrednictwem [sieciowej grupy zabezpieczeń](/azure/virtual-machines/windows/nsg-quickstart-portal).

Wymagane porty:

* 80 - Wymagane dla iis
::: moniker range=">=vs-2019"
* 4024 — wymagane do zdalnego debugowania z programu Visual Studio 2019 (zobacz [przypisania portów debugera zdalnego, aby](../debugger/remote-debugger-port-assignments.md) uzyskać więcej informacji).
::: moniker-end
::: moniker range="vs-2017"
* 4022 — wymagane do zdalnego debugowania z programu Visual Studio 2017 (zobacz [przypisania portów debugera zdalnego, aby](../debugger/remote-debugger-port-assignments.md) uzyskać więcej informacji).
::: moniker-end
* UDP 3702 - (Opcjonalnie) Odnajdowanie port umożliwia **przycisk Znajdź** podczas podłączania do debugera zdalnego w programie Visual Studio.

Ponadto porty te powinny być już otwarte przez instalację ASP.NET:
- 8172 - (opcjonalnie) wymagane do wdrożenia w sieci Web do wdrożenia aplikacji z programu Visual Studio
