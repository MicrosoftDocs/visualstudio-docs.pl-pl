---
title: Platforma ASP.NET debugowania zdalnego na komputerze IIS
ms.custom:
- remotedebugging
- seodec18
ms.date: 05/06/2020
ms.topic: conceptual
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: cd2b787fe546b9c53332fcdc548d3da829759755
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173918"
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>Zdalne debugowanie ASP.NET na zdalnym komputerze IIS
Aby debugować aplikację ASP.NET, która została wdrożona w usługach IIS, zainstaluj i Uruchom narzędzia zdalne na komputerze, na którym została wdrożona aplikacja, a następnie Dołącz do uruchomionej aplikacji z programu Visual Studio.

![Składniki debugera zdalnego](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

W tym przewodniku wyjaśniono, jak skonfigurować i skonfigurować aplikację Visual Studio ASP.NET MVC 4.5.2, wdrożyć ją w usługach IIS i dołączyć zdalny debuger z programu Visual Studio.

> [!NOTE]
> Aby zamiast tego ASP.NET Core debugowania zdalnego, zobacz [ASP.NET Core debugowania zdalnego na komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md). W przypadku Azure App Service można łatwo wdrażać i debugować na wstępnie skonfigurowanym wystąpieniu usług IIS przy użyciu [Snapshot Debugger](../debugger/debug-live-azure-applications.md) (wymagany jest program .NET 4.6.1) lub [dołączając debuger z Eksplorator serwera](../debugger/remote-debugging-azure.md).

## <a name="prerequisites"></a>Wymagania wstępne

::: moniker range=">=vs-2019"
Aby wykonać kroki opisane w tym artykule, wymagany jest program Visual Studio 2019.
::: moniker-end
::: moniker range="vs-2017"
Aby wykonać kroki opisane w tym artykule, wymagany jest program Visual Studio 2017.
::: moniker-end

Te procedury zostały przetestowane na tych konfiguracjach serwera:
* Systemy Windows Server 2012 R2 i IIS 8 (dla systemu Windows Server 2008 R2, kroki serwera są różne)

## <a name="network-requirements"></a>Wymagania dotyczące sieci

Zdalny debuger jest obsługiwany w systemie Windows Server, począwszy od systemu Windows Server 2008 z dodatkiem Service Pack 2. Aby uzyskać pełną listę wymagań, zobacz [wymagania](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Debugowanie między dwoma komputerami połączonymi za pomocą serwera proxy nie jest obsługiwane. Debugowanie w przypadku dużych opóźnień lub połączeń o niskiej przepustowości, takich jak Internet telefoniczny lub przez Internet w różnych krajach, nie jest zalecane i może się nie powieść.

## <a name="app-already-running-in-iis"></a>Aplikacja jest już uruchomiona w usługach IIS?

Ten artykuł zawiera instrukcje dotyczące konfigurowania podstawowej konfiguracji usług IIS w systemie Windows Server i wdrażania aplikacji z programu Visual Studio. Te kroki są dołączone do programu, aby upewnić się, że na serwerze są zainstalowane wymagane składniki, że aplikacja może działać poprawnie i że wszystko jest gotowe do zdalnego debugowania.

* Jeśli aplikacja jest uruchomiona w usługach IIS i po prostu chcesz pobrać zdalny debuger i rozpocząć debugowanie, przejdź do pozycji [Pobierz i zainstaluj narzędzia zdalne w systemie Windows Server](#BKMK_msvsmon).

* Jeśli potrzebujesz pomocy, aby upewnić się, że aplikacja została prawidłowo skonfigurowana, wdrożona i uruchomiona w usługach IIS, aby umożliwić debugowanie, wykonaj wszystkie kroki opisane w tym temacie.

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Tworzenie aplikacji ASP.NET 4.5.2 na komputerze z Visual Studio

1. Utwórz nową aplikację MVC ASP.NET.

    ::: moniker range=">=vs-2019"
    W programie Visual Studio 2019 **naciśnij klawisze CTRL + Q** , aby otworzyć pole wyszukiwania, **wpisz ASP.NET**, wybierz pozycję **Szablony**, a następnie wybierz pozycję **utwórz nową aplikację sieci Web ASP.NET (.NET Framework)**. W wyświetlonym oknie dialogowym wpisz nazwę projektu **MyASPApp**, a następnie wybierz pozycję **Utwórz**. Wybierz pozycję **MVC** i wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    W tym celu w programie Visual Studio 2017 wybierz pozycję **plik > nowy > projekt**, a następnie wybierz pozycję **Visual C# > Web > ASP.NET Web Application**. W sekcji Szablony **ASP.NET 4.5.2** wybierz pozycję **MVC**. Upewnij się, że nie wybrano opcji **Włącz obsługę platformy Docker** i że **uwierzytelnianie** jest ustawione na wartość **bez uwierzytelniania**. Nazwij projekt **MyASPApp**.)
    ::: moniker-end

2. Otwórz plik *HomeController.cs* i ustaw punkt przerwania w `About()` metodzie.

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a>Instalowanie i Konfigurowanie usług IIS w systemie Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Aktualizowanie ustawień zabezpieczeń przeglądarki w systemie Windows Server

Jeśli konfiguracja zwiększonych zabezpieczeń jest włączona w programie Internet Explorer (jest włączona domyślnie), może być konieczne dodanie niektórych domen jako zaufanych lokacji, aby umożliwić pobranie niektórych składników serwera sieci Web. Dodaj Zaufane witryny, wybierając **Opcje internetowe > zabezpieczenia > zaufane lokacje > Lokacje**. Dodaj następujące domeny.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Podczas pobierania oprogramowania można uzyskać żądania udzielenia uprawnień do ładowania różnych skryptów i zasobów witryny sieci Web. Niektóre z tych zasobów nie są wymagane, ale aby uprościć proces, kliknij przycisk **Dodaj** po wyświetleniu monitu.

## <a name="install-aspnet-45-on-windows-server"></a><a name="BKMK_deploy_asp_net"></a>Zainstaluj program ASP.NET 4,5 w systemie Windows Server

Aby uzyskać bardziej szczegółowe informacje na temat instalowania ASP.NET w usługach IIS, zobacz [iis 8,0 przy użyciu ASP.NET 3,5 i ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. W lewym okienku Menedżer serwera wybierz pozycję **IIS**. Kliknij prawym przyciskiem myszy serwer i wybierz pozycję **menedżer Internet Information Services (IIS)**.

1. Użyj Instalatora platformy sieci Web (Instalatora WebPI), aby zainstalować ASP.NET 4,5 (z węzła serwera w systemie Windows Server 2012 R2, wybierz pozycję **Pobierz nowe składniki platformy sieci Web** , a następnie wyszukaj ciąg ASP.NET).

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Jeśli używasz systemu Windows Server 2008 R2, zainstaluj ASP.NET 4 zamiast tego za pomocą tego polecenia:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\ aspnet_regiis. exe — IR**

2. Uruchom ponownie system (lub wykonaj polecenie **net stop was/y** , a następnie **net start W3SVC** z wiersza polecenia, aby wybrać zmianę ścieżki systemowej).

## <a name="choose-a-deployment-option"></a>Wybierz opcję wdrożenia

Jeśli potrzebujesz pomocy przy wdrażaniu aplikacji w usługach IIS, weź pod uwagę następujące opcje:

* Wdróż aplikację, tworząc plik ustawień publikowania w usługach IIS i importując ustawienia w programie Visual Studio. W niektórych scenariuszach jest to szybki sposób wdrożenia aplikacji. Podczas tworzenia pliku ustawień publikowania uprawnienia są konfigurowane automatycznie w usługach IIS.

* Wdróż program przez opublikowanie w folderze lokalnym i skopiowanie danych wyjściowych za pomocą preferowanej metody do przygotowanego folderu aplikacji w programie IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>Obowiązkowe Wdrażanie przy użyciu pliku ustawień publikowania

Tej opcji można użyć do utworzenia pliku ustawień publikowania i zaimportowania go do programu Visual Studio.

> [!NOTE]
> Ta metoda wdrażania używa Web Deploy, która musi być zainstalowana na serwerze. Jeśli chcesz skonfigurować Web Deploy ręcznie zamiast zaimportować ustawienia, możesz zainstalować Web Deploy 3,6 zamiast Web Deploy 3,6 dla serwerów hostingu. Jeśli jednak skonfigurujesz Web Deploy ręcznie, musisz upewnić się, że folder aplikacji na serwerze jest skonfigurowany z prawidłowymi wartościami i uprawnieniami (zobacz [Konfigurowanie witryny sieci Web ASP.NET](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Instalowanie i Konfigurowanie Web Deploy serwerów hostingu w systemie Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Tworzenie pliku ustawień publikowania w usługach IIS w systemie Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importowanie ustawień publikowania w programie Visual Studio i wdrażanie

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Po pomyślnym wdrożeniu aplikacji należy uruchomić ją automatycznie. Jeśli aplikacja nie uruchamia się z programu Visual Studio, uruchom aplikację w usługach IIS.

1. W oknie dialogowym **Ustawienia** Włącz debugowanie, klikając przycisk **dalej**, wybierz konfigurację **debugowania** , a następnie wybierz pozycję **Usuń dodatkowe pliki w miejscu docelowym** w obszarze Opcje **publikowania plików** .

    > [!IMPORTANT]
    > W przypadku wybrania konfiguracji wydania podczas publikowania należy wyłączyć debugowanie w pliku *Web. config* .

1. Kliknij przycisk **Zapisz** , a następnie ponownie Opublikuj aplikację.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>Obowiązkowe Wdróż przez opublikowanie w folderze lokalnym

Za pomocą tej opcji można wdrożyć aplikację, jeśli chcesz skopiować aplikację do usług IIS przy użyciu programu PowerShell, RoboCopy lub ręcznie skopiować pliki.

### <a name="configure-the-aspnet-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a>Konfigurowanie witryny sieci Web ASP.NET na komputerze z systemem Windows Server

1. Otwórz Eksploratora Windows i Utwórz nowy folder **C:\Publish**, w którym później zostanie wdrożony projekt ASP.NET.

2. Jeśli nie jest jeszcze otwarty, Otwórz **menedżera Internet Information Services (IIS)**. (W lewym okienku Menedżer serwera wybierz pozycję **IIS**. Kliknij prawym przyciskiem myszy serwer i wybierz pozycję **menedżer Internet Information Services (IIS)**.

3. W obszarze **połączenia** w okienku po lewej stronie przejdź do **witryny**.

4. Wybierz **domyślną witrynę sieci Web**, wybierz **pozycję Ustawienia podstawowe**i ustaw **ścieżkę fizyczną** na **C:\Publish**.

5. Kliknij prawym przyciskiem myszy **domyślny węzeł witryny sieci Web** i wybierz polecenie **Dodaj aplikację**.

6. Ustaw wartość pola **alias** na **MyASPApp**, zaakceptuj domyślną pulę aplikacji (**Domyślna**konfiguracja), a następnie ustaw **ścieżkę fizyczną** na **C:\Publish**.

7. W obszarze **połączenia**wybierz pozycję **Pule aplikacji**. Otwórz przystawkę **Domyślna** i ustaw wartość pola Pula aplikacji na **ASP.NET v 4.0** (ASP.NET 4,5 nie jest opcją dla puli aplikacji).

8. Po wybraniu lokacji w Menedżerze usług IIS wybierz pozycję **Edytuj uprawnienia**i upewnij się, że konto IUSR, IIS_IUSRS lub użytkownik skonfigurowany dla puli aplikacji jest autoryzowanym użytkownikiem z uprawnieniami do odczytu & wykonywania. Jeśli żaden z tych użytkowników nie istnieje, należy dodać IUSR jako użytkownik z uprawnieniami do odczytu & wykonania.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Publikowanie i wdrażanie aplikacji przez publikowanie do folderu lokalnego z programu Visual Studio

Możesz również opublikować i wdrożyć aplikację za pomocą systemu plików lub innych narzędzi.

1. (ASP.NET 4.5.2) Upewnij się, że w pliku Web. config znajduje się poprawna wersja programu .NET.  Na przykład jeśli docelowym jest ASP.NET 4.5.2, upewnij się, że ta wersja jest wymieniona w pliku Web. config.

    ```xml
    <system.web>
      <compilation debug="true" targetFramework="4.5.2" />
      <httpRuntime targetFramework="4.5.2" />
      <httpModules>
        <add name="ApplicationInsightsWebTracking" type="Microsoft.ApplicationInsights.Web.ApplicationInsightsHttpModule, Microsoft.AI.Web" />
      </httpModules>
    </system.web>

    ```

    Na przykład, wersja powinna być 4,0, Jeśli instalujesz ASP.NET 4 zamiast 4.5.2.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>Pobieranie i Instalowanie narzędzi zdalnych w systemie Windows Server

Pobierz wersję narzędzi zdalnych, która pasuje do używanej wersji programu Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a>Konfigurowanie zdalnego debugera w systemie Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Jeśli musisz dodać uprawnienia dla dodatkowych użytkowników, zmienić tryb uwierzytelniania lub numer portu dla zdalnego debugera, zobacz [Konfigurowanie zdalnego debugera](../debugger/remote-debugging.md#configure_msvsmon).

Aby uzyskać informacje na temat uruchamiania zdalnego debugera jako usługi, zobacz [Uruchamianie zdalnego debugera jako usługi](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>Dołączanie do aplikacji ASP.NET z komputera z programu Visual Studio

1. Na komputerze z Visual Studio Otwórz rozwiązanie, które próbujesz debugować (**MyASPApp** , jeśli wykonano kroki opisane w tym artykule).
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

5. Zaznacz opcję **Pokaż procesy wszystkich użytkowników**.

6. Wpisz pierwszą literę nazwy procesu, aby szybko znaleźć **w3wp. exe** dla ASP.NET 4,5.

    Jeśli masz wiele procesów pokazujących **w3wp. exe**, Sprawdź kolumnę **Nazwa użytkownika** . W niektórych scenariuszach kolumna **Nazwa użytkownika** zawiera nazwę puli aplikacji, na przykład **APPPOOL\DefaultAppPool IIS**. Jeśli zostanie wyświetlona Pula aplikacji, prosty sposób na zidentyfikowanie poprawnego procesu polega na utworzeniu nowej nazwanej puli aplikacji dla wystąpienia aplikacji, które ma być debugowane, a następnie można ją łatwo znaleźć w kolumnie **Nazwa użytkownika** .

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Kliknij przycisk **Dołącz**

8. Otwórz witrynę sieci Web komputera zdalnego. W przeglądarce przejdź do **http:// \<remote computer name> **.

    Powinna zostać wyświetlona strona sieci Web ASP.NET.
9. W uruchomionej aplikacji ASP.NET kliknij link do strony **informacje** .

    Punkt przerwania powinien zostać trafiony w programie Visual Studio.

## <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a>Rozwiązywanie problemów: otwieranie wymaganych portów w systemie Windows Server

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

2. Następnie wybierz pozycję **reguły ruchu przychodzącego > nową regułę > portu**. Wybierz pozycję **dalej** i w obszarze **określone porty lokalne**wprowadź numer portu, kliknij przycisk **dalej**, następnie **Zezwól na połączenie**, kliknij przycisk Dalej, a następnie Dodaj nazwę (**IIS**, **Web Deploy**lub **msvsmon**) dla reguły ruchu przychodzącego.

    Aby uzyskać więcej szczegółowych informacji na temat konfigurowania zapory systemu Windows, zobacz [Konfigurowanie zapory systemu Windows pod kątem zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Utwórz dodatkowe reguły dla innych wymaganych portów.