---
title: Zdalne debugowanie platformy ASP.NET Core na komputerze zdalnym usług IIS | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 08b58dd22e47844e62c0d312efc17e332c53f2c1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56702177"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio-2017"></a>Zdalne debugowanie platformy ASP.NET Core na komputerze zdalnym usług IIS w programie Visual Studio 2017
Do debugowania aplikacji ASP.NET, która została wdrożona w usługach IIS, zainstalować i uruchomić narzędzia zdalne na komputerze, w której została wdrożona aplikacja, a następnie dołącz do uruchomionej aplikacji w programie Visual Studio.

![Składniki zdalnego debugera](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Ten przewodnik wyjaśnia, jak skonfigurować i skonfigurować program Visual Studio 2017 platformy ASP.NET Core, wdrożyć ją w usługach IIS i dołączyć debuger zdalny z programu Visual Studio. Aby zdalne debugowanie platformy ASP.NET 4.5.2, zobacz [zdalne debugowanie platformy ASP.NET na komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Można również wdrażanie i debugowanie w programie IIS przy użyciu platformy Azure. Dla usługi Azure App Service można łatwo wdrażanie i debugowanie w ramach wstępnie skonfigurowanego wystąpienia programu IIS i zdalny debuger za pomocą [rozszerzenia Snapshot Debugger](../debugger/debug-live-azure-applications.md) lub [dołączanie debugera z poziomu Eksploratora serwera](../debugger/remote-debugging-azure.md).

Procedury te zostały przetestowane na te konfiguracje serwera:
* Windows Server 2012 R2 i IIS 8
* Windows Server 2016 i usługi IIS 10

## <a name="requirements"></a>Wymagania

Debugowanie między dwoma komputerami połączonymi za pośrednictwem serwera proxy nie jest obsługiwane. Debugowanie za pośrednictwem duże opóźnienie lub połączenie o niskiej przepustowości, takich jak Internet, połączenia telefonicznego lub przez Internet między krajów nie jest zalecane i może zakończyć się niepowodzeniem lub zbyt wolno. Aby uzyskać pełną listę wymagań, zobacz [wymagania](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="app-already-running-in-iis"></a>Aplikacja jest już uruchomiona w usługach IIS?

Ten artykuł zawiera instrukcje dotyczące konfigurowania podstawowej konfiguracji programu IIS na serwerze Windows i wdrażanie aplikacji w programie Visual Studio. Te kroki są uwzględnione, aby upewnić się, że serwer ma wymagane składniki zainstalowane prawidłowo uruchomić aplikację i można przystąpić do zdalnego debugowania.

* Jeśli Twoja aplikacja działa w usługach IIS i po prostu chcesz pobrać zdalnego debugera i rozpocząć debugowanie, przejdź do [pobrać i zainstalować narzędzia zdalnej w systemie Windows Server](#BKMK_msvsmon).

* Jeśli chcesz, aby uzyskać pomoc, aby upewnić się, że Twoja aplikacja jest skonfigurowana, wdrożeniu i poprawne działanie w usługach IIS tak, aby można było debugować, wykonaj wszystkie kroki przedstawione w tym temacie.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Tworzenie aplikacji platformy ASP.NET Core na komputerze programu Visual Studio 2017

1. Tworzenie nowej aplikacji platformy ASP.NET Core. (**Plik > Nowy > Projekt**, a następnie wybierz **Visual C# > sieci Web > Aplikacja sieci Web programu ASP.NET Core**).

    W **platformy ASP.NET Core** szablony zaznacz **aplikacji sieci Web**.

2. Upewnij się, że **ASP.NET Core 2.0** jest zaznaczone, który **włączyć obsługę platformy Docker** jest **nie** wybranego i **uwierzytelniania** jest równa **Bez uwierzytelniania**.

3. Nadaj projektowi nazwę **MyASPApp** i kliknij przycisk **OK** do tworzenia nowego rozwiązania.

4. Otwórz plik About.cshtml.cs i ustaw punkt przerwania `OnGet` — metoda (w szablonach starsze HomeController.cs zamiast tego otworzyć i ustaw punkt przerwania w `About()` metody).

## <a name="bkmk_configureIIS"></a> Instalowanie i konfigurowanie usług IIS w systemie Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Zaktualizuj ustawienia zabezpieczeń przeglądarki w systemie Windows Server

Jeśli Konfiguracja zwiększonych zabezpieczeń jest włączone w programie Internet Explorer (jest włączony domyślnie), następnie należy może być konieczne dodanie niektórych domen jako zaufane witryny, aby umożliwić pobieranie niektóre składniki serwera sieci web. Dodaj zaufanych witryn, przechodząc do **Opcje internetowe > Zabezpieczenia > Zaufane witryny > witryny**. Dodaj następujące domeny.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- Program IIS.NET

Po pobraniu oprogramowania, może zostać żądania, aby przyznać uprawnienie do ładowania różnych skrypty witryny sieci web i zasobami. Niektóre z tych zasobów nie są wymagane, ale w celu uproszczenia procesu, należy kliknąć **Dodaj** po wyświetleniu monitu.

## <a name="install-aspnet-core-on-windows-server"></a>Instalowanie platformy ASP.NET Core w systemie Windows Server

1. Zainstaluj [.NET Core systemu Windows serwer obsługujący](https://aka.ms/dotnetcore-2-windowshosting) pakietu przez system operacyjny. Pakiet instaluje środowisko uruchomieniowe programu .NET Core, .NET Core bibliotek i modułu ASP.NET Core. Aby uzyskać więcej szczegółowych instrukcji, zobacz [publikowania w usługach IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

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

1. Otwórz Eksploratora Windows i Utwórz nowy folder **C:\Publish**, gdzie będą później wdrożyć projekt ASP.NET.

2. Jeśli nie jest jeszcze otwarty, otwórz **Internet Information Services (IIS) Manager**. (W lewym okienku w Menedżerze serwera wybierz **IIS**. Kliknij prawym przyciskiem myszy serwer, a następnie wybierz pozycję **Internet Information Services (IIS) Manager**.)

3. W obszarze **połączeń** w okienku po lewej stronie przejdź do **witryn**.

4. Wybierz **domyślna witryna sieci Web**, wybierz **podstawowych ustawień**i ustaw **ścieżkę fizyczną** do **C:\Publish**.

4. Kliknij prawym przyciskiem myszy **domyślna witryna sieci Web** a następnie wybierz węzeł **Add Application**.

5. Ustaw **Alias** pole **MyASPApp**, zaakceptuj domyślne ustawienie puli aplikacji (**DefaultAppPool**) i ustaw **ścieżkę fizyczną** do  **C:\Publish**.

6. W obszarze **połączeń**, wybierz opcję **pul aplikacji**. Otwórz **DefaultAppPool** i ustawić pole puli aplikacji **bez kodu zarządzanego**.

7. Kliknij prawym przyciskiem myszy nową lokację w Menedżerze usług IIS, wybierz polecenie **Edytuj uprawnienia**i upewnij się, że IUSR, IIS_IUSRS lub użytkownika skonfigurowanego pod kątem dostępu do aplikacji sieci web jest autoryzowanym użytkownikiem z uprawnień Odczyt i wykonywanie.

    Jeśli nie widzisz jeden z tych użytkowników z dostępem, przechodzą przez kroki, aby dodać IUSR jako użytkownik z uprawnieniami Odczyt i wykonywanie.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Publikowanie i wdrażanie aplikacji poprzez publikowanie do folderu lokalnego, w programie Visual Studio

Możesz również publikować i wdrażanie aplikacji przy użyciu systemu plików lub innych narzędzi.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a> Pobierz i zainstaluj narzędzia zdalnego w systemie Windows Server

W tym samouczku używamy programu Visual Studio 2017.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="BKMK_setup"></a> Konfigurowanie zdalnego debugera w systemie Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Jeśli potrzebujesz dodać uprawnienia dla dodatkowych użytkowników do zmienić tryb uwierzytelniania lub numer portu dla zdalnego debugera, zobacz [Konfigurowanie debugera zdalnego](../debugger/remote-debugging.md#configure_msvsmon).

Aby uzyskać informacje na temat uruchamiania zdalnego debugera jako usługi, zobacz [uruchomić zdalny debuger jako usługę](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="BKMK_attach"></a> Dołącz do aplikacji platformy ASP.NET z komputera z programu Visual Studio

1. Na komputerze programu Visual Studio, otwórz rozwiązanie, które chcesz debugować (**MyASPApp** czy postępujesz zgodnie z wszystkie kroki opisane w tym artykule).
2. W programie Visual Studio, kliknij przycisk **Debuguj > Dołącz do procesu** (Ctrl + Alt + P).

    > [!TIP]
    > W programie Visual Studio 2017, możesz dołączyć do tego samego procesu wcześniej podłączany do przy użyciu **Debuguj > ponownie Dołącz do procesu...** (Shift + Alt + P).

3. Ustaw pole kwalifikator  **\<nazwy komputera zdalnego >: 4022**.
4. Kliknij przycisk **Odśwież**.
    Powinien zostać wyświetlony niektóre procesy, które są wyświetlane w **dostępne procesy** okna.

    Jeśli nie widzisz wszystkie procesy, spróbuj przy użyciu adresu IP zamiast nazwy komputera zdalnego (port jest wymagany). Możesz użyć `ipconfig` w wierszu polecenia, aby uzyskać adres IPv4.

    Jeśli chcesz używać **znaleźć** przycisku, konieczne może być [Otwórz UDP port 3702](#bkmk_openports) na serwerze.

5. Sprawdź **Pokaż procesy wszystkich użytkowników**.
6. Wpisz pierwszą literę nazwy procesu, aby szybko znaleźć **dotnet.exe** (dla platformy ASP.NET Core).

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Kliknij przycisk **dołączyć**.

8. Otwórz witrynę sieci Web na komputerze zdalnym. W przeglądarce przejdź do **http://\<nazwy komputera zdalnego >**.

    Powinna zostać wyświetlona strona sieci web platformy ASP.NET.

9. W działającej aplikacji platformy ASP.NET, kliknij link, aby **o** strony.

    W programie Visual Studio powinny trafiony punkt przerwania.

## <a name="bkmk_openports"></a> Rozwiązywanie problemów: Otwieranie portów wymaganych w systemie Windows Server

W większości konfiguracji wymagane porty są otwarte przez instalację programu ASP.NET i zdalny debuger. Jednak może być konieczne Sprawdź, czy porty zostały otwarte.

> [!NOTE]
> Na Maszynie wirtualnej platformy Azure, należy otworzyć porty za pośrednictwem [sieciowej grupy zabezpieczeń](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80-for-web-traffic).

Wymagane porty:

- 80 - wymagane dla usług IIS
- 4022 - wymagane do zdalnego debugowania w programie Visual Studio 2017 (zobacz [zdalnego przypisania portów debugera](../debugger/remote-debugger-port-assignments.md) Aby uzyskać szczegółowe informacje.
- 8172 — (opcjonalnie) wymagany dla narzędzia Web Deploy do wdrażania aplikacji w programie Visual Studio.
- UDP 3702 — port odnajdywania (opcjonalnie) umożliwia **znaleźć** przycisku związane ze zdalnym debugerem programu Visual Studio.

1. Aby otworzyć port w systemie Windows Server, należy otworzyć **Start** menu, wyszukaj **Zapora Windows z zabezpieczeniami zaawansowanymi**.

2. Następnie wybierz **reguły ruchu przychodzącego > Nowa reguła > Port**, a następnie kliknij przycisk **dalej**. (UDP 3702 wybierz **reguł dla ruchu wychodzącego** zamiast.)

3. W obszarze **określone porty lokalne**, wprowadź numer portu, kliknij przycisk **dalej**.

4. Kliknij przycisk **Zezwalaj na połączenie**, kliknij przycisk **dalej**.

5. Wybierz jeden lub więcej typów sieci można włączyć za pośrednictwem portu usługi, a następnie kliknij przycisk **dalej**.

    Wybranego typu musi zawierać sieci, do którego jest podłączony komputera zdalnego.
6. Dodaj nazwę (na przykład **IIS**, **narzędzia Web Deploy**, lub **msvsmon**) reguły ruchu przychodzącego, a następnie kliknij przycisk **Zakończ**.

    Powinieneś zobaczyć nową regułę reguły ruchu przychodzącego lub reguły ruchu wychodzącego liście.

    Jeśli chcesz, aby uzyskać więcej informacji na temat konfigurowania zapory Windows, zobacz [skonfigurować zaporę Windows do zdalnego debugowania](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Utwórz dodatkowe reguły dla wymaganych portów.
