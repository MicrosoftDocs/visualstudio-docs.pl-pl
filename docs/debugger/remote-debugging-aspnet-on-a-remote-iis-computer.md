---
title: Zdalne debugowanie ASP.NET Core na zdalnym komputerze IIS | Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/06/2020
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 389fe1491a92cacecd772244c2a0facd0d12c887
ms.sourcegitcommit: a778dffddb05d2f0f15969eadaf9081c9b466196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2020
ms.locfileid: "92298755"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>Zdalne debugowanie ASP.NET Core na zdalnym komputerze IIS w programie Visual Studio

Aby debugować aplikację ASP.NET Core, która została wdrożona w usługach IIS, zainstaluj i Uruchom narzędzia zdalne na komputerze, na którym została wdrożona aplikacja, a następnie Dołącz do uruchomionej aplikacji z programu Visual Studio.

![Składniki debugera zdalnego](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

W tym przewodniku wyjaśniono, jak skonfigurować i skonfigurować program Visual Studio ASP.NET Core, wdrożyć go w usługach IIS i dołączyć zdalny debuger z programu Visual Studio. Aby debugować zdalne ASP.NET 4.5.2, zobacz [Remote debug ASP.NET na komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Możesz również wdrażać i debugować usługi IIS przy użyciu platformy Azure. W przypadku Azure App Service można łatwo wdrożyć i debugować wstępnie skonfigurowane wystąpienie usług IIS i zdalny debuger przy użyciu [Snapshot Debugger](../debugger/debug-live-azure-applications.md) lub przez [dołączenie debugera z Eksplorator serwera](../debugger/remote-debugging-azure.md).

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range=">=vs-2019"
Aby wykonać kroki opisane w tym artykule, wymagany jest program Visual Studio 2019.
::: moniker-end
::: moniker range="vs-2017"
Aby wykonać kroki opisane w tym artykule, wymagany jest program Visual Studio 2017.
::: moniker-end

Te procedury zostały przetestowane na tych konfiguracjach serwera:
* Windows Server 2012 R2 i IIS 8
* Windows Server 2016 i IIS 10
* Windows Server 2019 i IIS 10

## <a name="network-requirements"></a>Wymagania dotyczące sieci

Debugowanie między dwoma komputerami połączonymi za pomocą serwera proxy nie jest obsługiwane. Debugowanie w przypadku dużych opóźnień lub połączeń o niskiej przepustowości, takich jak Internet telefoniczny lub przez Internet w różnych krajach, nie jest zalecane i może się nie powieść. Aby uzyskać pełną listę wymagań, zobacz [wymagania](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="app-already-running-in-iis"></a>Aplikacja jest już uruchomiona w usługach IIS?

Ten artykuł zawiera instrukcje dotyczące konfigurowania podstawowej konfiguracji usług IIS w systemie Windows Server i wdrażania aplikacji z programu Visual Studio. Te kroki są dołączone do programu, aby upewnić się, że na serwerze są zainstalowane wymagane składniki, że aplikacja może działać poprawnie i że wszystko jest gotowe do zdalnego debugowania.

* Jeśli aplikacja jest uruchomiona w usługach IIS i po prostu chcesz pobrać zdalny debuger i rozpocząć debugowanie, przejdź do pozycji [Pobierz i zainstaluj narzędzia zdalne w systemie Windows Server](#BKMK_msvsmon).

* Jeśli potrzebujesz pomocy, aby upewnić się, że aplikacja została prawidłowo skonfigurowana, wdrożona i uruchomiona w usługach IIS, aby umożliwić debugowanie, wykonaj wszystkie kroki opisane w tym temacie.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Tworzenie aplikacji ASP.NET Core na komputerze z Visual Studio

1. Utwórz nową aplikację sieci Web ASP.NET Core.

    ::: moniker range=">=vs-2019"
    W programie Visual Studio 2019 **naciśnij klawisze CTRL + Q** , aby otworzyć pole wyszukiwania, **wpisz ASP.NET**, wybierz pozycję **Szablony**, a następnie wybierz pozycję **Utwórz nową ASP.NET Core aplikacji sieci Web**. W wyświetlonym oknie dialogowym wpisz nazwę projektu **MyASPApp**, a następnie wybierz pozycję **Utwórz**. Następnie wybierz pozycję **aplikacja sieci Web (Model-View-Controller)**, a następnie wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    W programie Visual Studio 2017 wybierz kolejno pozycje **plik > nowy > projekt**, a następnie wybierz pozycję **Visual C# > Web > ASP.NET Core aplikacji sieci Web**. W sekcji szablony ASP.NET Core wybierz pozycję **aplikacja sieci Web (Model-View-Controller)**. Upewnij się, że wybrano ASP.NET Core 2,1, że **Obsługa platformy Docker** nie jest zaznaczona i że **uwierzytelnianie** jest ustawione na wartość **bez uwierzytelniania**. Nazwij projekt **MyASPApp**.
    ::: moniker-end

4. Otwórz plik About.cshtml.cs i ustaw punkt przerwania w `OnGet` metodzie (w starszych szablonach otwórz HomeController.cs i ustaw punkt przerwania w `About()` metodzie).

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a> Instalowanie i Konfigurowanie usług IIS w systemie Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aktualizowanie ustawień zabezpieczeń przeglądarki w systemie Windows Server

Jeśli konfiguracja zwiększonych zabezpieczeń jest włączona w programie Internet Explorer (jest włączona domyślnie), może być konieczne dodanie niektórych domen jako zaufanych lokacji, aby umożliwić pobranie niektórych składników serwera sieci Web. Dodaj Zaufane witryny, wybierając **Opcje internetowe > zabezpieczenia > zaufane lokacje > Lokacje**. Dodaj następujące domeny.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Podczas pobierania oprogramowania można uzyskać żądania udzielenia uprawnień do ładowania różnych skryptów i zasobów witryny sieci Web. Niektóre z tych zasobów nie są wymagane, ale aby uprościć proces, kliknij przycisk **Dodaj** po wyświetleniu monitu.

## <a name="install-aspnet-core-on-windows-server"></a>Zainstaluj ASP.NET Core w systemie Windows Server

1. Zainstaluj pakiet hostingu platformy .NET Core w systemie hostingu. Pakiet instaluje środowisko uruchomieniowe programu .NET Core, bibliotekę .NET Core i moduł ASP.NET Core. Aby uzyskać bardziej szczegółowe instrukcje, zobacz [Publikowanie w usługach IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    W przypadku platformy .NET Core 3 Zainstaluj [pakiet hostingu platformy .NET Core](https://dotnet.microsoft.com/permalink/dotnetcore-current-windows-runtime-bundle-installer).
    W przypadku platformy .NET Core 2 Zainstaluj [platformę .NET Core systemu Windows Server](https://aka.ms/dotnetcore-2-windowshosting).

    > [!NOTE]
    > Jeśli system nie ma połączenia z Internetem, uzyskaj i zainstaluj *[pakiet redystrybucyjny Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=53840)* przed zainstalowaniem pakietu hostingu platformy .NET Core systemu Windows Server.

3. Uruchom ponownie system (lub wykonaj polecenie **net stop was/y** , a następnie **net start W3SVC** z wiersza polecenia, aby wybrać zmianę ścieżki systemowej).

## <a name="choose-a-deployment-option"></a>Wybierz opcję wdrożenia

Jeśli potrzebujesz pomocy przy wdrażaniu aplikacji w usługach IIS, weź pod uwagę następujące opcje:

* Wdróż aplikację, tworząc plik ustawień publikowania w usługach IIS i importując ustawienia w programie Visual Studio. W niektórych scenariuszach jest to szybki sposób wdrożenia aplikacji. Podczas tworzenia pliku ustawień publikowania uprawnienia są konfigurowane automatycznie w usługach IIS.

* Wdróż program przez opublikowanie w folderze lokalnym i skopiowanie danych wyjściowych za pomocą preferowanej metody do przygotowanego folderu aplikacji w programie IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>Obowiązkowe Wdrażanie przy użyciu pliku ustawień publikowania

Tej opcji można użyć do utworzenia pliku ustawień publikowania i zaimportowania go do programu Visual Studio.

> [!NOTE]
> Ta metoda wdrażania używa Web Deploy, która musi być zainstalowana na serwerze. Jeśli chcesz skonfigurować Web Deploy ręcznie zamiast zaimportować ustawienia, możesz zainstalować Web Deploy 3,6 zamiast Web Deploy 3,6 dla serwerów hostingu. Jeśli jednak skonfigurujesz Web Deploy ręcznie, musisz upewnić się, że folder aplikacji na serwerze jest skonfigurowany z prawidłowymi wartościami i uprawnieniami (zobacz [Konfigurowanie witryny sieci Web ASP.NET](#BKMK_deploy_asp_net)).

### <a name="configure-the-aspnet-core-web-site"></a>Skonfiguruj witrynę sieci Web ASP.NET Core

1. W Menedżerze usług IIS w lewym okienku w obszarze **połączenia**wybierz pozycję **Pule aplikacji**. Otwórz przystawkę **Domyślna** i ustaw **wersję środowiska .NET CLR** na **Brak kodu zarządzanego**. Jest to wymagane w przypadku ASP.NET Core. Domyślna witryna sieci Web używa tej domyślnej.

2. Zatrzymaj i uruchom ponownie tę samą wartość.

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Instalowanie i Konfigurowanie Web Deploy serwerów hostingu w systemie Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Tworzenie pliku ustawień publikowania w usługach IIS w systemie Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importowanie ustawień publikowania w programie Visual Studio i wdrażanie

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Po pomyślnym wdrożeniu aplikacji należy uruchomić ją automatycznie. Jeśli aplikacja nie uruchamia się z programu Visual Studio, uruchom aplikację w usługach IIS, aby sprawdzić, czy działa poprawnie. W przypadku ASP.NET Core należy również upewnić się, że w polu Pula aplikacji **dla tej opcji określono wartość** **Brak kodu zarządzanego**.

1. W oknie dialogowym **Ustawienia** Włącz debugowanie, klikając przycisk **dalej**, wybierz konfigurację **debugowania** , a następnie wybierz pozycję **Usuń dodatkowe pliki w miejscu docelowym** w obszarze Opcje **publikowania plików** .

    > [!IMPORTANT]
    > W przypadku wybrania konfiguracji wydania można wyłączyć debugowanie w pliku *web.config* podczas publikowania.

1. Kliknij przycisk **Zapisz** , a następnie ponownie Opublikuj aplikację.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>Obowiązkowe Wdróż przez opublikowanie w folderze lokalnym

Za pomocą tej opcji można wdrożyć aplikację, jeśli chcesz skopiować aplikację do usług IIS przy użyciu programu PowerShell, RoboCopy lub ręcznie skopiować pliki.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a> Konfigurowanie witryny sieci Web ASP.NET Core na komputerze z systemem Windows Server

1. Otwórz Eksploratora Windows i Utwórz nowy folder **C:\Publish**, w którym później zostanie wdrożony projekt ASP.NET Core.

2. Jeśli nie jest jeszcze otwarty, Otwórz **menedżera Internet Information Services (IIS)**. (W lewym okienku Menedżer serwera wybierz pozycję **IIS**. Kliknij prawym przyciskiem myszy serwer i wybierz pozycję **menedżer Internet Information Services (IIS)**.

3. W obszarze **połączenia** w okienku po lewej stronie przejdź do **witryny**.

4. Wybierz **domyślną witrynę sieci Web**, wybierz **pozycję Ustawienia podstawowe**i ustaw **ścieżkę fizyczną** na **C:\Publish**.

4. Kliknij prawym przyciskiem myszy **domyślny węzeł witryny sieci Web** i wybierz polecenie **Dodaj aplikację**.

5. Ustaw wartość pola **alias** na **MyASPApp**, zaakceptuj domyślną pulę aplikacji (**Domyślna**konfiguracja), a następnie ustaw **ścieżkę fizyczną** na **C:\Publish**.

6. W obszarze **połączenia**wybierz pozycję **Pule aplikacji**. Otwórz przystawkę **Domyślna** i ustaw wartość pola Pula aplikacji na **Brak kodu zarządzanego**.

7. Kliknij prawym przyciskiem myszy nową witrynę w Menedżerze usług IIS, wybierz polecenie **Edytuj uprawnienia**i upewnij się, że konto IUSR, IIS_IUSRS lub użytkownik skonfigurowany do dostępu do aplikacji sieci Web jest autoryzowanym użytkownikiem z uprawnieniami do odczytu & wykonywania.

    Jeśli nie widzisz jednego z tych użytkowników z dostępem, wykonaj kroki, aby dodać IUSR jako użytkownik z uprawnieniami do odczytu & wykonywania.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Publikowanie i wdrażanie aplikacji przez publikowanie do folderu lokalnego z programu Visual Studio

Możesz również opublikować i wdrożyć aplikację za pomocą systemu plików lub innych narzędzi.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a> Pobieranie i Instalowanie narzędzi zdalnych w systemie Windows Server

Pobierz wersję narzędzi zdalnych, która pasuje do używanej wersji programu Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a> Konfigurowanie zdalnego debugera w systemie Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Jeśli musisz dodać uprawnienia dla dodatkowych użytkowników, zmienić tryb uwierzytelniania lub numer portu dla zdalnego debugera, zobacz [Konfigurowanie zdalnego debugera](../debugger/remote-debugging.md#configure_msvsmon).

Aby uzyskać informacje na temat uruchamiania zdalnego debugera jako usługi, zobacz [Uruchamianie zdalnego debugera jako usługi](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a> Dołączanie do aplikacji ASP.NET z komputera z programu Visual Studio

1. Na komputerze z Visual Studio Otwórz rozwiązanie, które próbujesz debugować (**MyASPApp** , jeśli wykonano wszystkie kroki opisane w tym artykule).
2. W programie Visual Studio kliknij pozycję **debuguj > Dołącz do procesu** (Ctrl + Alt + P).

    > [!TIP]
    > W programie Visual Studio 2017 i nowszych wersjach można ponownie dołączyć do tego samego procesu, który został wcześniej dołączony przy użyciu **debugowania > ponownie dołączyć do procesu...** (Shift + Alt + P).

3. Ustaw pole kwalifikator na **\<remote computer name>** i naciśnij klawisz **Enter**.

    Sprawdź, czy program Visual Studio dodaje wymagany port do nazwy komputera, która jest wyświetlana w formacie: ** \<remote computer name> :p** .

    ::: moniker range=">=vs-2019"
    W programie Visual Studio 2019 powinna zostać wyświetlona ** \<remote computer name> : 4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    W programie Visual Studio 2017 powinna zostać wyświetlona ** \<remote computer name> : 4022**
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

8. Otwórz witrynę sieci Web komputera zdalnego. W przeglądarce przejdź do **http:// \<remote computer name> **.

    Powinna zostać wyświetlona strona sieci Web ASP.NET.

9. W uruchomionej aplikacji ASP.NET kliknij link do strony **informacje** .

    Punkt przerwania powinien zostać trafiony w programie Visual Studio.

## <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> Rozwiązywanie problemów: otwieranie wymaganych portów w systemie Windows Server

W większości instalacji wymagane porty są otwierane przez instalację ASP.NET i zdalnego debugera. Może jednak być konieczne zweryfikowanie, czy porty są otwarte.

> [!NOTE]
> Na maszynie wirtualnej platformy Azure należy otworzyć porty za pomocą [sieciowej grupy zabezpieczeń](/azure/virtual-machines/windows/nsg-quickstart-portal).

Wymagane porty:

* 80 — wymagane dla usług IIS
::: moniker range=">=vs-2019"
* 4024 — wymagane do zdalnego debugowania z programu Visual Studio 2019 (zobacz [zdalne przydziały portu debugera](../debugger/remote-debugger-port-assignments.md) , aby uzyskać więcej informacji).
::: moniker-end
::: moniker range="vs-2017"
* 4022 — wymagane do zdalnego debugowania z programu Visual Studio 2017 (zobacz [zdalne przydziały portu debugera](../debugger/remote-debugger-port-assignments.md) , aby uzyskać więcej informacji).
::: moniker-end
* UDP 3702 — (opcjonalnie) port odnajdywania umożliwia korzystanie z przycisku **Znajdź** podczas dołączania do zdalnego debugera w programie Visual Studio.

1. Aby otworzyć port w systemie Windows Server, otwórz menu **Start** , Wyszukaj pozycję **Zapora systemu Windows z zabezpieczeniami zaawansowanymi**.

2. Następnie wybierz pozycję **reguły ruchu przychodzącego > nowej reguły > portu**, a następnie kliknij przycisk **dalej**. (W przypadku protokołu UDP 3702 wybierz zamiast nich **reguły wychodzące** ).

3. W obszarze **określone porty lokalne**wprowadź numer portu, a następnie kliknij przycisk **dalej**.

4. Kliknij pozycję **Zezwalaj na połączenie**, a następnie kliknij przycisk **dalej**.

5. Wybierz co najmniej jeden typ sieci, który ma zostać włączony dla portu, a następnie kliknij przycisk **dalej**.

    Wybrany typ musi zawierać sieć, z którą połączony jest komputer zdalny.
6. Dodaj nazwę (na przykład **IIS**, **Web Deploy**lub **msvsmon**) dla reguły ruchu przychodzącego, a następnie kliknij przycisk **Zakończ**.

    Nowa reguła powinna zostać wyświetlona na liście reguły ruchu przychodzącego lub reguły ruchu wychodzącego.

    Aby uzyskać więcej szczegółowych informacji na temat konfigurowania zapory systemu Windows, zobacz [Konfigurowanie zapory systemu Windows pod kątem zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Utwórz dodatkowe reguły dla innych wymaganych portów.
