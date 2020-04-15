---
title: Zdalne debugowanie ASP.NET rdzenia na komputerze zdalnych usług IIS | Dokumenty firmy Microsoft
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: b33ead969456935dab54c042ba4fbaf1f5ff44f4
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385475"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>Zdalne debugowanie ASP.NET rdzenia na zdalnym komputerze usług IIS w programie Visual Studio

Aby debugować aplikację ASP.NET Core, która została wdrożona w serwisach IIS, zainstaluj i uruchom narzędzia zdalne na komputerze, na którym wdrożono aplikację, a następnie dołącz do uruchomionej aplikacji z programu Visual Studio.

![Składniki zdalnego debugera](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

W tym przewodniku wyjaśniono, jak skonfigurować i skonfigurować program Visual Studio ASP.NET Core, wdrożyć go w usługach IIS i dołączyć zdalny debuger z programu Visual Studio. Aby zdalnie debugować ASP.NET 4.5.2, zobacz [Zdalne debugowanie ASP.NET na komputerze usług IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Można również wdrożyć i debugować na usługach IIS przy użyciu platformy Azure. W usłudze Azure App Service można łatwo wdrożyć i debugować wstępnie skonfigurowane wystąpienie usług IIS i debuger zdalny przy użyciu [debugera migawki](../debugger/debug-live-azure-applications.md) lub [dołączając debuger z Eksploratora serwera](../debugger/remote-debugging-azure.md).

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range=">=vs-2019"
Visual Studio 2019 jest wymagane, aby wykonać kroki pokazane w tym artykule.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 jest wymagane, aby wykonać kroki pokazane w tym artykule.
::: moniker-end

Te procedury zostały przetestowane na następujących konfiguracjach serwera:
* Systemy Windows Server 2012 R2 i USŁUGI IIS 8
* Systemy Windows Server 2016 i USŁUGI IIS 10

## <a name="network-requirements"></a>Wymagania dotyczące sieci

Debugowanie między dwoma komputerami podłączonymi za pośrednictwem serwera proxy nie jest obsługiwane. Debugowanie za pośrednictwem połączenia o dużej masie lub niskiej przepustowości, takiego jak dialup Internet lub przez Internet w różnych krajach, nie jest zalecane i może zakończyć się niepowodzeniem lub być niedopuszczalnie powolne. Aby uzyskać pełną listę wymagań, zobacz [Wymagania](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="app-already-running-in-iis"></a>Aplikacja już uruchomiona w iis?

Ten artykuł zawiera kroki dotyczące konfigurowania podstawowej konfiguracji usług IIS na serwerze Windows i wdrażania aplikacji w programie Visual Studio. Te kroki są uwzględniane, aby upewnić się, że serwer ma zainstalowane wymagane składniki, że aplikacja może działać poprawnie i że można przystąpić do zdalnego debugowania.

* Jeśli aplikacja działa w serwisach IIS i chcesz po prostu pobrać debuger zdalny i rozpocząć debugowanie, przejdź do [pozycji Pobierz i zainstaluj narzędzia zdalne w systemie Windows Server](#BKMK_msvsmon).

* Jeśli chcesz pomóc, aby upewnić się, że aplikacja jest skonfigurowana, wdrożona i działa poprawnie w usługach IIS, dzięki czemu można debugować, wykonaj wszystkie kroki opisane w tym temacie.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Tworzenie aplikacji ASP.NET Core na komputerze z programem Visual Studio

1. Utwórz nową aplikację sieci web ASP.NET Core. 

    ::: moniker range=">=vs-2019"
    W programie Visual Studio 2019 wpisz **klawisze Ctrl + Q,** aby otworzyć pole wyszukiwania, wpisz **asp.net**, wybierz pozycję **Szablony**, a następnie wybierz pozycję **Utwórz nową ASP.NET podstawową aplikację sieci Web**. W wyświetlonym oknie dialogowym nazwij projekt **MyASPApp**, a następnie wybierz pozycję **Utwórz**. Następnie wybierz pozycję **Aplikacja sieci Web (Model-View-Controller),** a następnie wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    W programie Visual Studio 2017 wybierz pozycję **Plik > nowy projekt >**, a następnie wybierz pozycję Visual **C# > Web > ASP.NET Core Web Application**. W sekcji szablony ASP.NET Core wybierz pozycję **Aplikacja sieci Web (Administrator widoku modelu)**. Upewnij się, że wybrano ASP.NET Core 2.1, że **opcja Włącz obsługę platformy Docker** nie jest zaznaczona i że **uwierzytelnianie** jest ustawione na **Brak uwierzytelniania**. Nazwij projekt **MyASPApp**.
    ::: moniker-end

4. Otwórz plik About.cshtml.cs i ustaw punkt przerwania `OnGet` w metodzie (w starszych szablonach otwórz HomeController.cs zamiast `About()` tego i ustaw punkt przerwania w metodzie).

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a>Instalowanie i konfigurowanie usług IIS w systemie Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aktualizowanie ustawień zabezpieczeń przeglądarki w systemie Windows Server

Jeśli konfiguracja zwiększonych zabezpieczeń jest włączona w programie Internet Explorer (jest domyślnie włączona), może być konieczne dodanie niektórych domen jako zaufanych witryn, aby umożliwić pobranie niektórych składników serwera sieci Web. Dodaj zaufane witryny, przechodząc do **opcji internetowych > zabezpieczenia > zaufanych witryn > witryn .** Dodaj następujące domeny.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Podczas pobierania oprogramowania można otrzymywać prośby o udzielenie uprawnień do ładowania różnych skryptów i zasobów witryny sieci Web. Niektóre z tych zasobów nie są wymagane, ale aby uprościć proces, kliknij przycisk **Dodaj** po wyświetleniu monitu.

## <a name="install-aspnet-core-on-windows-server"></a>Instalowanie ASP.NET Core w systemie Windows Server

1. Zainstaluj pakiet [hostingu systemu .NET Core Windows Server w](https://aka.ms/dotnetcore-2-windowshosting) systemie hostingowym. Pakiet instaluje środowisko uruchomieniowe .NET Core, bibliotekę .NET Core i moduł ASP.NET Core. Aby uzyskać bardziej szczegółowe instrukcje, zobacz [Publikowanie w usługach IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

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

1. Otwórz Eksploratora Windows i utwórz nowy folder **C:\Publish**, w którym później wdrożysz projekt ASP.NET Core.

2. Jeśli nie jest jeszcze otwarty, otwórz **Menedżera internetowych usług informacyjnych (IIS).** (W lewym okienku Menedżera serwera wybierz pozycję **IIS**. Kliknij prawym przyciskiem myszy serwer i wybierz **menedżera internetowych usług informacyjnych (IIS).**

3. W obszarze **Połączenia** w lewym okienku przejdź do **strony Witryny**.

4. Wybierz **domyślną witrynę sieci Web**, wybierz pozycję **Ustawienia podstawowe**i ustaw **ścieżkę fizyczną** na **C:\Publikuj**.

4. Kliknij prawym przyciskiem myszy domyślny węzeł **Witryna sieci Web** i wybierz polecenie Dodaj **aplikację**.

5. Ustaw pole **Alias** na **MyASPApp**, zaakceptuj domyślną pulę aplikacji **(DefaultAppPool)** i ustaw **ścieżkę fizyczną** na **C:\Publish**.

6. W obszarze **Połączenia**wybierz pozycję **Pule aplikacji**. Otwórz **domyślną usługę Adpool** i ustaw pole Puli aplikacji na **Brak kodu zarządzanego**.

7. Kliknij prawym przyciskiem myszy nową witrynę w Menedżerze usług IIS, wybierz polecenie **Edytuj uprawnienia**i upewnij się, że funkcja IUSR, IIS_IUSRS lub użytkownik skonfigurowany do uzyskiwania dostępu do aplikacji sieci web jest autoryzowanym użytkownikiem z uprawnieniami do odczytu & wykonywania.

    Jeśli nie widzisz jednego z tych użytkowników z dostępem, wykonaj kroki, aby dodać IUSR jako użytkownika z prawami do odczytu & wykonywania.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Publikowanie i wdrażanie aplikacji przez publikowanie w folderze lokalnym z programu Visual Studio

Aplikację można również publikować i wdrażać za pomocą systemu plików lub innych narzędzi.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>Pobieranie i instalowanie narzędzi zdalnych w systemie Windows Server

Pobierz wersję narzędzi zdalnych, która pasuje do twojej wersji programu Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a>Konfigurowanie zdalnego debugera w systemie Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Jeśli chcesz dodać uprawnienia dla dodatkowych użytkowników, zmień tryb uwierzytelniania lub numer portu dla zdalnego debugera, zobacz [Konfigurowanie debugera zdalnego](../debugger/remote-debugging.md#configure_msvsmon).

Aby uzyskać informacje dotyczące uruchamiania zdalnego debugera jako usługi, zobacz [Uruchamianie debugera zdalnego jako usługi](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>Dołącz do aplikacji ASP.NET z komputera programu Visual Studio

1. Na komputerze z programu Visual Studio otwórz rozwiązanie, które próbujesz debugować (**MyASPApp,** jeśli wykonując wszystkie kroki opisane w tym artykule).
2. W programie Visual Studio kliknij polecenie **Debugowanie > dołącz do procesu** (Ctrl + Alt + P).

    > [!TIP]
    > W programie Visual Studio 2017 i nowszych wersjach można ponownie dołączyć do tego samego procesu, do którego wcześniej dołączono przy użyciu **debugowania > Ponowne dołączanie do procesu...** (Shift + Alt + P).

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

    * Jeśli korzystasz z [modelu hostingu w aplikacji](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1#hosting-models) w serwisie IIS, wybierz poprawny proces **w3wp.exe.** Począwszy od .NET Core 3, jest to wartość domyślna.

    * W przeciwnym razie wybierz proces **dotnet.exe.** (Jest to model hostingu poza procesem).

    Jeśli masz wiele procesów *pokazujących w3wp.exe* lub *dotnet.exe,* zaznacz **kolumnę Nazwa użytkownika.** W niektórych scenariuszach **kolumna Nazwa użytkownika** zawiera nazwę puli aplikacji, na przykład **IIS APPPOOL\DefaultAppPool**. Jeśli widzisz pulę aplikacji, ale nie jest unikatowa, utwórz nową pulę aplikacji o nazwie dla wystąpienia aplikacji, które chcesz debugować, a następnie możesz ją łatwo znaleźć w kolumnie **Nazwa użytkownika.**

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

## <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a>Rozwiązywanie problemów: otwieranie wymaganych portów w systemie Windows Server

W większości konfiguracji wymagane porty są otwierane przez instalację ASP.NET i debugera zdalnego. Jednak może być konieczne sprawdzenie, czy porty są otwarte.

> [!NOTE]
> Na maszynie Wirtualnej platformy Azure należy otworzyć porty za pośrednictwem [sieciowej grupy zabezpieczeń](/azure/virtual-machines/windows/nsg-quickstart-portal).

Wymagane porty:

* 80 - Wymagane dla iis
::: moniker range=">=vs-2019"
* 4024 — wymagane do zdalnego debugowania z programu Visual Studio 2019 (zobacz [przypisania portów debugera zdalnego, aby](../debugger/remote-debugger-port-assignments.md) uzyskać więcej informacji).
::: moniker-end
::: moniker range="vs-2017"
* 4022 — wymagane do zdalnego debugowania z programu Visual Studio 2017 (zobacz [przypisania portów debugera zdalnego, aby](../debugger/remote-debugger-port-assignments.md) uzyskać więcej informacji).
::: moniker-end
* UDP 3702 - (Opcjonalnie) Odnajdowanie port umożliwia **przycisk Znajdź** podczas podłączania do debugera zdalnego w programie Visual Studio.

1. Aby otworzyć port w systemie Windows Server, otwórz menu **Start,** wyszukaj **Zaporę systemu Windows z zabezpieczeniami zaawansowanymi**.

2. Następnie wybierz polecenie **Reguły przychodzące > Nowa reguła > port**, a następnie kliknij przycisk **Dalej**. (W przypadku protokołu UDP 3702 wybierz pozycję **Reguły wychodzące).**

3. W obszarze **Określone porty lokalne**wprowadź numer portu, kliknij przycisk **Dalej**.

4. Kliknij **pozycję Zezwól na połączenie**, kliknij przycisk **Dalej**.

5. Wybierz jeden lub więcej typów sieci, aby włączyć port, a następnie kliknij przycisk **Dalej**.

    Wybrany typ musi obejmować sieć, do której jest podłączony komputer zdalny.
6. Dodaj nazwę (na przykład **IIS**, **Web Deploy**lub **msvsmon)** dla reguły przychodzącej i kliknij przycisk **Zakończ**.

    Nowa reguła powinna zostać wyświetlona na liście Reguły przychodzące lub Reguły wychodzące.

    Aby uzyskać więcej informacji na temat konfigurowania Zapory systemu Windows, zobacz [Konfigurowanie Zapory systemu Windows do zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Utwórz dodatkowe reguły dla innych wymaganych portów.
