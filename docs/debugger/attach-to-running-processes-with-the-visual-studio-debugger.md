---
title: Dołączanie do uruchomionych procesów za pomocą debugera
description: Dowiedz się, jak dołączyć Visual Studio do uruchomionego procesu na komputerze lokalnym lub zdalnym.
ms.custom: SEO-VS-2020
ms.date: 06/12/2020
ms.topic: conceptual
f1_keywords:
- vs.debug.processes.attach
- vs.debug.process
- vs.debug.programs
- vs.debug.detaching
- vs.debug.processes
- vs.debug.error.attach
- vs.debug.remotemachine
dev_langs:
- CSharp
- FSharp
- C++
- VB
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e3836403af80d06a2ecaa7f77cb7f49f0c6f0e8
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389790"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Dołączanie do uruchomionego procesu za pomocą debugera programu Visual Studio

Możesz dołączyć Visual Studio do uruchomionego procesu na komputerze lokalnym lub zdalnym. Po uruchomieniu procesu wybierz pozycję Debuguj dołączanie do procesu lub naciśnij klawisze  >   **Ctrl** Alt p w Visual Studio i użyj okna dialogowego Dołączanie do procesu, aby dołączyć +  +  debuger do procesu. 

Możesz użyć  dołączania do procesu, aby debugować uruchomione aplikacje na komputerach lokalnych lub zdalnych, jednocześnie debugować wiele procesów, debugować aplikacje, które nie zostały utworzone w programie Visual Studio, lub debugować dowolną aplikację, która nie została uruchomiona od Visual Studio z dołączonym debugerem. Jeśli na przykład uruchamiasz aplikację bez debugera i występuje wyjątek, możesz dołączyć debuger do procesu uruchamiania aplikacji i rozpocząć debugowanie.

> [!TIP]
> Nie masz pewności, czy użyć **funkcji Dołącz do procesu** w scenariuszu debugowania? Zobacz [typowe scenariusze debugowania.](#BKMK_Scenarios)

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> Dołączanie do uruchomionego procesu na komputerze lokalnym

Aby szybko ponownie dołączyć do procesu, który został wcześniej dołączony, zobacz [Ponowne dołączanie do procesu](#BKMK_reattach).

**Aby dołączyć do procesu na komputerze lokalnym:**

1. W Visual Studio wybierz pozycję  >  **Debuguj dołączanie do procesu** (lub naciśnij klawisze **Ctrl** Alt P ), aby +  + otworzyć okno **dialogowe Dołączanie do** procesu.

1. Sprawdź **typ połączenia**.

   W większości scenariuszy można użyć **domyślnego .** Niektóre scenariusze mogą wymagać innego typu połączenia. Aby uzyskać więcej informacji, zobacz inne sekcje w tym artykule lub [Typowe scenariusze debugowania.](#BKMK_Scenarios)

1. Ustaw wartość **pola Połączenie docelowe** na nazwę komputera lokalnego.

   ![Zrzut ekranu przedstawiający okno dialogowe Dołączanie do procesu z docelową wartością połączenia ustawioną na nazwę komputera lokalnego.](../debugger/media/DBG_Basics_Attach_To_Process.png)

1. Na liście **Dostępne procesy** znajdź i wybierz proces lub procesy, do których chcesz dołączyć.

   - Aby szybko wybrać proces, wpisz jego nazwę lub pierwszą literę w **polu Filtruj procesy.**

   - Jeśli nie znasz nazwy procesu, przejrzyj listę lub [](#BKMK_Scenarios) zobacz Typowe scenariusze debugowania dla niektórych typowych nazw procesów.

   >[!TIP]
   >Procesy można uruchamiać i zatrzymywać w tle, gdy okno dialogowe Dołączanie do procesu jest otwarte, więc lista uruchomionych procesów może nie zawsze być aktualna.  Możesz wybrać pozycję **Odśwież** w dowolnym momencie, aby wyświetlić bieżącą listę.

1. W polu **Dołącz do** upewnij się, że na liście znajduje się typ kodu, który chcesz debugować. Domyślne ustawienie **Automatyczne** działa w przypadku większości typów aplikacji.

   Jeśli używasz **domyślnego** typu połączenia, możesz ręcznie wybrać typ kodu, do którego chcesz dołączyć. W przeciwnym razie **opcja Wybierz** może być wyłączona.

   Aby ręcznie wybrać typy kodu:
   1. Kliknij pozycję **Wybierz**.
   1. W **oknie dialogowym Wybieranie typu** kodu wybierz pozycję **Debuguj te typy kodu.**
      Jeśli podczas próby dołączenia do procesu na liście wystąpi błąd, możesz użyć okna dialogowego Wybierz typ [kodu,](../debugger/select-code-type-dialog-box.md) aby [rozwiązać](#BKMK_Troubleshoot_attach_errors) problem.
   1. Wybierz typy kodu, które chcesz debugować.
   1. Wybierz przycisk **OK**.

1. Wybierz pozycję **Dołącz**.

>[!NOTE]
>Można dołączyć do wielu aplikacji na potrzeby debugowania, ale tylko jedna aplikacja jest aktywna w debugerze jednocześnie. Aktywną aplikację można ustawić na pasku narzędzi Visual Studio **debugowania** lub **w oknie Procesy.**

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Dołączanie do procesu na komputerze zdalnym

Możesz również wybrać komputer zdalny  w oknie dialogowym Dołączanie do procesu, wyświetlić listę dostępnych procesów uruchomionych na tym komputerze i dołączyć do co najmniej jednego procesu debugowania. Debuger zdalny *(msvsmon.exe*) musi być uruchomiony na komputerze zdalnym. Aby uzyskać więcej informacji, zobacz [Zdalne debugowanie](../debugger/remote-debugging.md).

Aby uzyskać bardziej szczegółowe instrukcje dotyczące debugowania ASP.NET aplikacji wdrożonych w usługach IIS, zobacz Zdalne debugowanie ASP.NET [na zdalnym komputerze usług IIS.](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)

**Aby dołączyć do uruchomionego procesu na komputerze zdalnym:**

1. W Visual Studio wybierz pozycję  >  **Debuguj dołączanie do procesu** (lub naciśnij klawisze **Ctrl** Alt P ), aby +  + otworzyć okno **dialogowe Dołączanie do** procesu.

1. Sprawdź **typ połączenia**.

   W większości scenariuszy można użyć **domyślnego .** Niektóre scenariusze, takie jak debugowanie systemu Linux lub konteneryzowana aplikacja, wymagają innego typu połączenia. Aby uzyskać więcej informacji, zobacz inne sekcje w tym artykule lub [Typowe scenariusze debugowania.](#BKMK_Scenarios)

1. W **polu Miejsce docelowe** połączenia wybierz komputer zdalny, korzystając z jednej z następujących metod:

   - Wybierz strzałkę listy rozwijanej obok pozycji **Element docelowy** połączenia i wybierz nazwę komputera z listy rozwijanej.
   - Wpisz nazwę komputera w polu **Miejsce docelowe połączenia** i naciśnij klawisz **Enter**.

     Sprawdź, Visual Studio dodaje wymagany port do nazwy komputera, która jest wyświetlana w **\<remote computer name> formacie: :p ort**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Jeśli nie możesz nawiązać połączenia przy użyciu nazwy komputera zdalnego, spróbuj użyć adresu IP i portu (na przykład `123.45.678.9:4022` ). Port 4024 jest domyślnym portem zdalnego debugera Visual Studio 2019 x64. Aby uzyskać informacje na temat innych przypisań portów debugera zdalnego, zobacz [Remote debugger port assignments](remote-debugger-port-assignments.md)(Przypisania portów debugera zdalnego).

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Jeśli nie możesz nawiązać połączenia przy użyciu nazwy komputera zdalnego, spróbuj użyć adresu IP i portu (na przykład `123.45.678.9:4022` ). Port 4022 jest domyślnym portem zdalnego debugera Visual Studio 2017 x64. Aby uzyskać informacje na temat innych przypisań portów debugera zdalnego, zobacz [Remote debugger port assignments](remote-debugger-port-assignments.md)(Przypisania portów debugera zdalnego).

     ::: moniker-end

   - Wybierz przycisk **Znajdź** obok pola **Element docelowy połączenia,** aby otworzyć **okno dialogowe** Połączenia zdalne. W **oknie dialogowym** Połączenia zdalne są wyświetlane wszystkie urządzenia, które znajdują się w podsieci lokalnej lub są bezpośrednio podłączone do komputera. Może być konieczne [otwarcie portu UDP 3702](../debugger/remote-debugger-port-assignments.md) na serwerze w celu odnajdywania urządzeń zdalnych. Wybierz komputer lub urządzenie, a następnie kliknij pozycję **Wybierz.**

   > [!NOTE]
   > Ustawienie **Typ połączenia jest** zachowywane między sesjami debugowania. Ustawienie **Miejsce docelowe połączenia** jest utrwalane między sesjami debugowania tylko wtedy, gdy pomyślnie nawiązaniu połączenia debugowania z tym elementem docelowym.

3. Kliknij **przycisk Odśwież,** aby wypełnić **listę Dostępne procesy.**

    >[!TIP]
    >Procesy można uruchamiać i zatrzymywać w tle, gdy okno dialogowe Dołączanie do procesu jest otwarte, więc lista uruchomionych procesów może nie zawsze być aktualna.  Możesz wybrać pozycję **Odśwież** w dowolnym momencie, aby wyświetlić bieżącą listę.

4. Na liście **Dostępne procesy** znajdź i wybierz proces lub procesy, do których chcesz dołączyć.

   - Aby szybko wybrać proces, wpisz jego nazwę lub pierwszą literę w **polu Filtruj procesy.**

   - Jeśli nie znasz nazwy procesu, przejrzyj listę lub [](#BKMK_Scenarios) zobacz Typowe scenariusze debugowania dla niektórych typowych nazw procesów.

   - Aby znaleźć procesy uruchomione na wszystkich kontach użytkowników, zaznacz **pole wyboru Pokaż procesy ze wszystkich** użytkowników.

     >[!NOTE]
     >Jeśli spróbujesz dołączyć do procesu należącego do niezaufanego konta użytkownika, zostanie wyświetlone okno dialogowe z ostrzeżeniem o zabezpieczeniach. Aby uzyskać więcej informacji, zobacz Ostrzeżenie o zabezpieczeniach: Dołączanie do procesu należącego do niezaufanego użytkownika może [być niebezpieczne. Jeśli poniższe informacje wyglądają podejrzanie lub nie masz pewności, nie dołączaj do tego procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).

5. W polu **Dołącz do** upewnij się, że na liście znajduje się typ kodu, który chcesz debugować. Domyślne ustawienie **Automatyczne** działa w przypadku większości typów aplikacji.

   Jeśli używasz **domyślnego** typu połączenia, możesz ręcznie wybrać typ kodu, do którego chcesz dołączyć. W przeciwnym razie **opcja Wybierz** może być wyłączona.

   Aby ręcznie wybrać typy kodu:
   1. Kliknij pozycję **Wybierz**.
   1. W **oknie dialogowym Wybieranie typu** kodu wybierz pozycję **Debuguj te typy kodu.**
      Jeśli podczas próby dołączenia do procesu na liście wystąpi błąd, możesz użyć okna dialogowego Wybierz typ [kodu,](../debugger/select-code-type-dialog-box.md) aby [rozwiązać](#BKMK_Troubleshoot_attach_errors) problem.
   1. Wybierz przycisk **OK**.

6. Wybierz pozycję **Dołącz**.

>[!NOTE]
>Można dołączyć do wielu aplikacji na potrzeby debugowania, ale tylko jedna aplikacja jest aktywna w debugerze jednocześnie. Aktywną aplikację można ustawić na pasku narzędzi Visual Studio **debugowania** lub **w oknie Procesy.**

W niektórych przypadkach podczas debugowania w sesji usługi Pulpit zdalny (usługi terminalowe) lista Dostępne procesy nie będzie wyświetlać wszystkich dostępnych procesów.  Jeśli korzystasz z Visual Studio, który ma ograniczone konto  użytkownika, na liście Dostępne procesy nie będą wyświetlane procesy działające w sesji 0. Sesja 0 jest używana dla usług i innych procesów serwera, w tym *w3wp.exe*. Możesz rozwiązać ten problem, uruchamiając program na koncie administratora lub za pomocą konsoli serwera zamiast [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sesji usług terminalowych.

Jeśli żadne z tych obejść nie jest możliwe, trzecią opcją jest dołączenie do procesu przez uruchomienie polecenia `vsjitdebugger.exe -p <ProcessId>` z wiersza polecenia systemu Windows. Identyfikator procesu można określić przy użyciu *tlist.exe*. Aby uzyskać *tlist.exe*, pobierz i zainstaluj narzędzia debugowania dla systemu Windows, dostępne na stronie [WDK i WinDbg do pobrania.](/windows-hardware/drivers/download-the-wdk)

## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>Dołączanie do procesu .NET Core uruchomionego w systemie Linux przy użyciu SSH

Aby uzyskać więcej informacji, zobacz [Remote debug .NET Core running on Linux using SSH (Zdalne debugowanie na platformie .NET Core działającej w systemie Linux przy użyciu połączenia SSH).](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)

::: moniker range=">= vs-2019"

## <a name="attach-to-a-process-running-on-a-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a> Dołączanie do procesu uruchomionego w kontenerze platformy Docker

Począwszy od Visual Studio 2019 r., można dołączyć debuger Visual Studio do procesu uruchomionego w kontenerze platformy Docker. Aby uzyskać informacje o kontenerze platformy Docker dla platformy .NET Core dla systemu Linux, zobacz Dołączanie do [procesu uruchomionego w kontenerze platformy Docker systemu Linux](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-linux-docker-container). Aby uzyskać informacje o kontenerze platformy Docker systemu Windows, zobacz [Attach to a process running on a Windows Docker container (Dołączanie do procesu uruchomionego w kontenerze platformy Docker systemu Windows).](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-windows-docker-container)

::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a> Ponowne dołączanie do procesu

Możesz szybko ponownie dołączyć do procesów, do których wcześniej dołączono, wybierając opcję  >  **Debuguj ponowne dołączanie do procesu** **(Shift** + **Alt** + **P).** Po wybraniu tego polecenia debuger natychmiast podejmie próbę dołączenia do ostatnich procesów, do których dołączono, próbując najpierw dopasować poprzedni identyfikator procesu, a jeśli to się nie powiedzie, przez dopasowanie do poprzedniej nazwy procesu. Jeśli dopasowania nie zostaną znalezione lub jeśli kilka  procesów ma taką samą nazwę, zostanie otwarte okno dialogowe Dołączanie do procesu, aby można było wybrać właściwy proces.

> [!NOTE]
> Polecenie **Ponowne dołączanie do procesu** jest dostępne od Visual Studio 2017 r.

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a> Typowe scenariusze debugowania

W poniższej tabeli  przedstawiono kilka typowych scenariuszy debugowania wraz z linkami do większej liczby instrukcji tam, gdzie są dostępne, aby ułatwić określenie, czy należy użyć funkcji Dołącz do procesu i do jakiego procesu dołączyć. (Lista nie jest wyczerpująca).

W przypadku niektórych typów aplikacji, takich jak aplikacje uniwersalnej systemu Windows (UWP), nie dołącza się bezpośrednio do nazwy procesu, ale zamiast tego należy użyć opcji menu **Debuguj** zainstalowany pakiet aplikacji w Visual Studio (zobacz tabelę).

Aby debuger dołączał do kodu napisanego w języku C++, kod musi emitować `DebuggableAttribute` . Możesz dodać go do kodu automatycznie, łącząc się z opcją [linku /ASSEMBLYDEBUG.](/cpp/build/reference/assemblydebug-add-debuggableattribute)

W przypadku debugowania skryptów po stronie klienta debugowanie skryptów musi być włączone w przeglądarce. Aby debugować skrypt po stronie klienta w przeglądarce Chrome, wybierz typ kodu **JavaScript (Chrome)** lub **JavaScript (Microsoft Edge — Chromium).** W zależności od typu aplikacji może być konieczne zamknięcie wszystkich wystąpień przeglądarki Chrome i uruchomienie przeglądarki w trybie debugowania (wpisz w wierszu `chrome.exe --remote-debugging-port=9222` polecenia). We wcześniejszych wersjach programu Visual Studio debuger skryptów dla programu Chrome był **zestawem internetowym**.

Aby szybko wybrać uruchomiony proces do dołączenia, w Visual Studio naciśnij klawisze **Ctrl** Alt P, a następnie wpisz pierwszą +  + literę nazwy procesu.

|Scenariusz|Metoda debugowania|Nazwa procesu|Uwagi i linki|
|-|-|-|-|
|Zdalne debugowanie ASP.NET 4 lub 4.5 na serwerze usług IIS|Używanie narzędzi zdalnych i **dołączanie do procesu**|*w3wp.exe*|Zobacz [Zdalne debugowanie ASP.NET zdalnym komputerze usług IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Zdalne debugowanie ASP.NET Core na serwerze usług IIS|Używanie narzędzi zdalnych i **dołączanie do procesu**|*w3wp.exe* lub *dotnet.exe*|Począwszy od programu .NET Core 3, *w3wp.exe* jest używany dla domyślnego modelu [hostingu w aplikacji.](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1&preserve-view=true#hosting-models) Aby uzyskać informacje na temat wdrażania aplikacji, [zobacz Publikowanie w usługach IIS.](/aspnet/core/host-and-deploy/iis/) Aby uzyskać bardziej szczegółowe informacje, zobacz [Zdalne debugowanie ASP.NET Core na zdalnym komputerze usług IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md#BKMK_attach)|
|Debugowanie skryptu po stronie klienta na lokalnym serwerze usług IIS dla obsługiwanych typów aplikacji |Używanie **dołączania do procesu**|*chrome.exe*, *MicrosoftEdgeCP.exe* lub *iexplore.exe*|Debugowanie skryptu musi być włączone. W przypadku przeglądarki Chrome należy również uruchomić przeglądarkę Chrome w trybie debugowania (wpisz w wierszu polecenia) i wybrać pozycję `chrome.exe --remote-debugging-port=9222` **JavaScript (Chrome)** w **polu Dołącz do.**|
|Debugowanie aplikacji w języku C#, Visual Basic lub C++ na komputerze lokalnym|Użyj standardowego debugowania **(F5)** lub **dołącz do procesu**|*\<appname>.exe*|W większości scenariuszy używaj debugowania standardowego, a nie **dołączania do procesu**.|
|Zdalne debugowanie aplikacji klasycznej systemu Windows|Zdalne narzędzia|Nie dotyczy| Zobacz [Zdalne debugowanie aplikacji C# lub Visual Basic lub](../debugger/remote-debugging-csharp.md) Zdalne [debugowanie aplikacji języka C++](../debugger/remote-debugging-cpp.md)|
|Debugowanie na platformie .NET Core w systemie Linux|Używanie **dołączania do procesu**|*dotnet.exe* lub unikatową nazwę procesu|Aby użyć połączenia SSH, zobacz [Remote debug .NET Core running on Linux using SSH (Zdalne debugowanie programu .NET Core uruchomionego w systemie Linux przy użyciu połączenia SSH).](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md) W przypadku aplikacji konteneryzowanych zobacz [Attach to a process running in a Docker container (Dołączanie do procesu uruchomionego w kontenerze platformy Docker).](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-linux-docker-container)|
|Debugowanie aplikacji konteneryzowanej|Używanie **dołączania do procesu**|*dotnet.exe* lub unikatową nazwę procesu|Zobacz [Dołączanie do procesu uruchomionego w kontenerze platformy Docker](../debugger/attach-to-process-running-in-docker-container.md)|
|Debugowanie zdalne języka Python w systemie Linux|Używanie **dołączania do procesu**|*debugpy*|Zobacz [Zdalne dołączanie z narzędzi języka Python](../python/debugging-python-code-on-remote-linux-machines.md#attach-remotely-from-python-tools)|
|Debugowanie ASP.NET aplikacji na komputerze lokalnym po uruchomieniu aplikacji bez debugera|Używanie **dołączania do procesu**|*iiexpress.exe*|Może to być przydatne, aby przyspieszyć ładowanie aplikacji, na przykład podczas profilowania. |
|Debugowanie innych obsługiwanych typów aplikacji w procesie serwera|Jeśli serwer jest zdalny, użyj narzędzi zdalnych i **dołącz do procesu**|*chrome.exe,* *iexplore.exe* lub inne procesy|W razie potrzeby użyj Monitor zasobów, aby ułatwić identyfikację procesu. Zobacz [Zdalne debugowanie](../debugger/remote-debugging.md).|
|Debugowanie zdalne aplikacji uniwersalnej systemu Windows ( UWP), OneCore, HoloLens lub aplikacji IoT|Debugowanie zainstalowanego pakietu aplikacji|Nie dotyczy|Zobacz Debug an installed app package instead of using Attach to Process (Debugowanie [zainstalowanego pakietu aplikacji](debug-installed-app-package.md) zamiast **używania dołączania do procesu)**|
|Debugowanie aplikacji uniwersalnej systemu Windows( UWP), OneCore, HoloLens lub aplikacji IoT, która nie została przez Ciebie Visual Studio|Debugowanie zainstalowanego pakietu aplikacji|Nie dotyczy|Zobacz Debug an installed app package instead of using Attach to Process (Debugowanie [zainstalowanego pakietu aplikacji](debug-installed-app-package.md) zamiast **używania dołączania do procesu)**|

## <a name="use-debugger-features"></a>Korzystanie z funkcji debugera

Aby korzystać z pełnych funkcji debugera Visual Studio (na przykład trafiania punktów przerwania) podczas dołączania do procesu, aplikacja musi dokładnie odpowiadać lokalnego źródła i symboli. Oznacza to, że debuger musi mieć możliwość załadowania prawidłowych [plików symboli (pdb).](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) Domyślnie wymaga to kompilacji debugowania.

W przypadku scenariuszy zdalnego debugowania kod źródłowy (lub jego kopia) musi być już otwarty w Visual Studio. Skompilowane pliki binarne aplikacji na komputerze zdalnym muszą pochodzić z tej samej kompilacji co na komputerze lokalnym.

W niektórych scenariuszach debugowania lokalnego można debugować w programie Visual Studio bez dostępu do źródła, jeśli w aplikacji znajdują się poprawne pliki symboli. Domyślnie wymaga to kompilacji debugowania. Aby uzyskać więcej informacji, zobacz [Określanie plików symboli i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> Rozwiązywanie problemów z błędami dołączania

W niektórych scenariuszach debuger może potrzebować pomocy w prawidłowym zidentyfikowaniu typu kodu do debugowania. Jeśli wartości połączenia są ustawione prawidłowo (możesz wyświetlić  prawidłowy proces na liście Dostępne procesy), ale debuger nie może  dołączyć, spróbuj wybrać najbardziej odpowiedni typ połączenia z listy Typ połączenia, który może być wymagany, na przykład w przypadku debugowania aplikacji dla systemu Linux lub Python. Jeśli używasz domyślnego typu połączenia, możesz też wybrać określony typ kodu, z który chcesz nawiązać połączenie, zgodnie z opisem w dalszej części tej sekcji.

Gdy debuger jest dołączany do uruchomionego procesu, proces może zawierać co najmniej jeden typ kodu. Typy kodu, do których debuger może dołączyć, są wyświetlane i wybierane w [oknie dialogowym Wybieranie typu](../debugger/select-code-type-dialog-box.md) kodu.

Czasami debuger może pomyślnie dołączyć do jednego typu kodu, ale nie do innego typu kodu. Zwykle dzieje się tak, gdy:

- Próbujesz dołączyć do procesu, który jest uruchomiony na komputerze zdalnym. Na komputerze zdalnym mogą być zainstalowane składniki zdalnego debugowania dla niektórych typów kodu, ale nie dla innych.
- Próbujesz dołączyć do co najmniej dwóch procesów na potrzeby bezpośredniego debugowania bazy danych. Debugowanie SQL obsługuje dołączanie tylko do jednego procesu.

Jeśli debuger jest w stanie dołączyć do niektórych, ale nie wszystkich typów kodu, zostanie wyświetlony komunikat identyfikujący typy, których nie udało się dołączyć.

Jeśli debuger pomyślnie dołączy do co najmniej jednego typu kodu, możesz kontynuować debugowanie procesu. Będzie można debugować tylko te typy kodu, które zostały pomyślnie dołączone. Niedołąowany kod w procesie będzie nadal działać, ale nie będzie można ustawiać punktów przerwania, wyświetlać danych ani wykonywać innych operacji debugowania na tym kodzie.

Jeśli chcesz uzyskać bardziej szczegółowe informacje o tym, dlaczego debuger nie może dołączyć do typu kodu, spróbuj ponownie dołączyć tylko do tego typu kodu.

**Aby uzyskać konkretne informacje o tym, dlaczego nie można dołączyć typu kodu:**

1. Odłącz od procesu. W menu **Debug (Debugowanie)** wybierz pozycję Detach All **(Odłącz wszystko).**

1. Ponownie dołącz do procesu, wybierając tylko typ kodu, który nie może dołączyć.

    1. W **oknie dialogowym Dołączanie** do procesu wybierz proces z **listy Dostępne procesy.**

    2. Wybierz pozycję **Wybierz**.

    3. W **oknie dialogowym Select Code Type (Wybieranie** typu kodu) wybierz pozycję **Debuguj te typy** kodu i typ kodu, który nie został dołączyć. Usuń zaznaczenie innych typów kodu.

    4. Wybierz przycisk **OK**.

    5. W **oknie dialogowym Dołączanie** do procesu wybierz pozycję **Dołącz**.

    Tym razem dołączenie nie powiedzie się całkowicie i zostanie wyświetlony konkretny komunikat o błędzie.

## <a name="see-also"></a>Zobacz też

- [Debugowanie wielu procesów](../debugger/debug-multiple-processes.md)
- [Debugowanie just in time](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)
