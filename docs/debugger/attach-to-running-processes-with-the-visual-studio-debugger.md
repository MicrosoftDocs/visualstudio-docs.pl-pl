---
title: Dołączanie do uruchomionych procesów za pomocą debugera | Microsoft Docs
ms.custom: seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5970e7e4408c826058cb27590254b278d4cdb9b7
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281009"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Dołączanie do uruchomionego procesu za pomocą debugera programu Visual Studio

Debuger programu Visual Studio można dołączyć do działającego procesu na komputerze lokalnym lub zdalnym. Po uruchomieniu procesu wybierz pozycję **Debuguj**  >  **Dołącz do procesu** lub naciśnij **klawisze CTRL** + **Alt** + **P** w programie Visual Studio, a następnie użyj okna dialogowego **Dołącz do procesu** , aby dołączyć debuger do procesu.

**Aby przeprowadzić** debugowanie uruchomionych aplikacji na komputerach lokalnych lub zdalnych, należy przeprowadzić debugowanie wielu procesów jednocześnie, debugować aplikacje, które nie zostały utworzone w programie Visual Studio, lub debugować dowolną aplikację, której nie uruchomiono w programie Visual Studio z dołączonym debugerem. Na przykład jeśli używasz aplikacji bez debugera i wystąpi wyjątek, możesz dołączyć debuger do procesu, w którym uruchomiono aplikację, i rozpocząć debugowanie.

> [!TIP]
> Nie masz pewności, czy chcesz użyć **dołączania do procesu** debugowania? Zobacz [typowe scenariusze debugowania](#BKMK_Scenarios).

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a>Dołączanie do uruchomionego procesu na komputerze lokalnym

Aby szybko ponownie dołączyć do dołączonego wcześniej procesu, zobacz Ponowne [dołączanie do procesu](#BKMK_reattach).

**Aby dołączyć do procesu na komputerze lokalnym:**

1. W programie Visual Studio wybierz pozycję **Debuguj**  >  **Dołącz do procesu** (lub naciśnij **klawisze CTRL** + **Alt** + **P**), aby otworzyć okno dialogowe **Dołącz do procesu** .

1. Sprawdź **Typ połączenia**.

   W większości scenariuszy można użyć **ustawień domyślnych**. Niektóre scenariusze mogą wymagać innego typu połączenia. Aby uzyskać więcej informacji, zobacz inne sekcje w tym artykule lub [typowe scenariusze debugowania](#BKMK_Scenarios).

1. Ustaw adres **docelowy połączenia** jako nazwę komputera lokalnego.

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

1. Z listy **dostępne procesy** Znajdź i wybierz proces lub procesy, do których chcesz dołączyć.

   - Aby szybko wybrać proces, wpisz jego nazwę lub pierwszą literę w polu **Filtruj procesy** .

   - Jeśli nie znasz nazwy procesu, przejrzyj listę lub zapoznaj się z [typowymi scenariuszami debugowania](#BKMK_Scenarios) dla niektórych typowych nazw procesów.

   >[!TIP]
   >Procesy można uruchamiać i zatrzymywać w tle, gdy jest otwarte okno dialogowe **dołączanie do procesu** , więc Lista uruchomionych procesów może być nieaktualna. W dowolnym momencie możesz wybrać opcję **Odśwież** , aby wyświetlić bieżącą listę.

1. W polu **Dołącz do** upewnij się, że na liście znajduje się typ kodu, który ma być debugowany. Domyślne ustawienie **Automatyczne** działa w przypadku większości typów aplikacji.

   Jeśli używasz **domyślnego** typu połączenia, możesz ręcznie wybrać typ kodu, do którego chcesz dołączyć. W przeciwnym razie opcja **SELECT** może być wyłączona.

   Aby ręcznie wybrać typy kodu:
   1. Kliknij pozycję **Wybierz**.
   1. W oknie dialogowym **Wybierz typ kodu** wybierz **Debuguj te typy kodu**.
      Jeśli wystąpi błąd podczas próby dołączenia do procesu na liście, możesz użyć okna dialogowego [Wybierz typ kodu](../debugger/select-code-type-dialog-box.md) , aby pomóc w [rozwiązaniu](#BKMK_Troubleshoot_attach_errors) problemu.
   1. Wybierz typy kodu do debugowania.
   1. Wybierz przycisk **OK**.

1. Wybierz pozycję **Dołącz**.

>[!NOTE]
>Można dołączać do wielu aplikacji do debugowania, ale tylko jedna aplikacja jest aktywna w debugerze w danym momencie. Aktywną aplikację można ustawić na pasku narzędzi lub w oknie **procesy** **debugowania** programu Visual Studio.

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a>Dołączanie do procesu na komputerze zdalnym

Możesz również wybrać komputer zdalny w oknie dialogowym **Dołącz do procesu** , wyświetlić listę dostępnych procesów uruchomionych na tym komputerze, a następnie dołączyć do jednego lub kilku procesów debugowania. Zdalny debuger (*msvsmon.exe*) musi być uruchomiony na komputerze zdalnym. Aby uzyskać więcej informacji, zobacz [debugowanie zdalne](../debugger/remote-debugging.md).

Aby uzyskać pełniejsze instrukcje dotyczące debugowania aplikacji ASP.NET, które zostały wdrożone w usługach IIS, zobacz [zdalne debugowanie ASP.NET na zdalnym komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**Aby dołączyć do uruchomionego procesu na komputerze zdalnym:**

1. W programie Visual Studio wybierz pozycję **Debuguj**  >  **Dołącz do procesu** (lub naciśnij **klawisze CTRL** + **Alt** + **P**), aby otworzyć okno dialogowe **Dołącz do procesu** .

1. Sprawdź **Typ połączenia**.

   W większości scenariuszy można użyć **ustawień domyślnych**. Niektóre scenariusze, takie jak debugowanie systemu Linux lub aplikacji w kontenerze, wymagają innego typu połączenia. Aby uzyskać więcej informacji, zobacz inne sekcje w tym artykule lub [typowe scenariusze debugowania](#BKMK_Scenarios).

1. W polu **cel połączenia** wybierz komputer zdalny przy użyciu jednej z następujących metod:

   - Wybierz strzałkę listy rozwijanej obok pozycji **cel połączenia**i wybierz z listy rozwijanej nazwę komputera.
   - Wpisz nazwę komputera w polu **cel połączenia** i naciśnij klawisz **Enter**.

     Sprawdź, czy program Visual Studio dodaje wymagany port do nazwy komputera, która jest wyświetlana w formacie: ** \<remote computer name> :p** .

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Jeśli nie można nawiązać połączenia przy użyciu nazwy komputera zdalnego, spróbuj użyć adresu IP i portu (na przykład `123.45.678.9:4022` ). 4024 jest domyślnym portem dla zdalnego debugera programu Visual Studio 2019 x64. W przypadku innych przypisań portów zdalnego debugera zobacz [zdalne przydziały portów zdalnego debugera](remote-debugger-port-assignments.md).

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Jeśli nie można nawiązać połączenia przy użyciu nazwy komputera zdalnego, spróbuj użyć adresu IP i portu (na przykład `123.45.678.9:4022` ). 4022 jest domyślnym portem dla zdalnego debugera programu Visual Studio 2017 x64. W przypadku innych przypisań portów zdalnego debugera zobacz [zdalne przydziały portów zdalnego debugera](remote-debugger-port-assignments.md).

     ::: moniker-end

   - Zaznacz przycisk **Znajdź** obok pola **cel połączenia** , aby otworzyć okno dialogowe **połączenia zdalne** . W oknie dialogowym **połączenia zdalne** są wyświetlane wszystkie urządzenia znajdujące się w podsieci lokalnej lub podłączone bezpośrednio do komputera. Może być konieczne [otwarcie portu UDP 3702](../debugger/remote-debugger-port-assignments.md) na serwerze w celu odnalezienia urządzeń zdalnych. Wybierz żądany komputer lub urządzenie, a następnie kliknij przycisk **Wybierz**.

   > [!NOTE]
   > Ustawienie **Typ połączenia** utrzymuje się między sesjami debugowania. Ustawienie **cel połączenia** utrzymuje się między sesjami debugowania tylko wtedy, gdy nastąpiło udane połączenie debugowania z tym obiektem docelowym.

3. Kliknij przycisk **Odśwież** , aby wypełnić listę **dostępne procesy** .

    >[!TIP]
    >Procesy można uruchamiać i zatrzymywać w tle, gdy jest otwarte okno dialogowe **dołączanie do procesu** , więc Lista uruchomionych procesów może być nieaktualna. W dowolnym momencie możesz wybrać opcję **Odśwież** , aby wyświetlić bieżącą listę.

4. Z listy **dostępne procesy** Znajdź i wybierz proces lub procesy, do których chcesz dołączyć.

   - Aby szybko wybrać proces, wpisz jego nazwę lub pierwszą literę w polu **Filtruj procesy** .

   - Jeśli nie znasz nazwy procesu, przejrzyj listę lub zapoznaj się z [typowymi scenariuszami debugowania](#BKMK_Scenarios) dla niektórych typowych nazw procesów.

   - Aby znaleźć procesy działające w ramach wszystkich kont użytkowników, zaznacz pole wyboru **Pokaż procesy wszystkich użytkowników** .

     >[!NOTE]
     >W przypadku próby dołączenia do procesu należącego do niezaufanego konta użytkownika zostanie wyświetlone potwierdzenie okna dialogowego ostrzeżenia o zabezpieczeniach. Aby uzyskać więcej informacji, zobacz [Ostrzeżenie o zabezpieczeniach: dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli poniższe informacje wyglądają podejrzanie lub nie masz pewności, nie dołączaj do tego procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).

5. W polu **Dołącz do** upewnij się, że na liście znajduje się typ kodu, który ma być debugowany. Domyślne ustawienie **Automatyczne** działa w przypadku większości typów aplikacji.

   Jeśli używasz **domyślnego** typu połączenia, możesz ręcznie wybrać typ kodu, do którego chcesz dołączyć. W przeciwnym razie opcja **SELECT** może być wyłączona.

   Aby ręcznie wybrać typy kodu:
   1. Kliknij pozycję **Wybierz**.
   1. W oknie dialogowym **Wybierz typ kodu** wybierz **Debuguj te typy kodu**.
      Jeśli wystąpi błąd podczas próby dołączenia do procesu na liście, możesz użyć okna dialogowego [Wybierz typ kodu](../debugger/select-code-type-dialog-box.md) , aby pomóc w [rozwiązaniu](#BKMK_Troubleshoot_attach_errors) problemu.
   1. Wybierz przycisk **OK**.

6. Wybierz pozycję **Dołącz**.

>[!NOTE]
>Można dołączać do wielu aplikacji do debugowania, ale tylko jedna aplikacja jest aktywna w debugerze w danym momencie. Aktywną aplikację można ustawić na pasku narzędzi lub w oknie **procesy** **debugowania** programu Visual Studio.

W niektórych przypadkach podczas debugowania w ramach sesji Pulpit zdalny (usług terminalowych) na liście **dostępne procesy** nie będą wyświetlane wszystkie dostępne procesy. Jeśli używasz programu Visual Studio jako użytkownika z ograniczonym kontem użytkownika, lista **dostępne procesy** nie będzie zawierać procesów uruchomionych w sesji 0. Sesja 0 jest używana dla usług i innych procesów serwera, w tym *w3wp.exe*. Problem można rozwiązać, uruchamiając [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] konto administratora lub uruchamiając [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] z poziomu konsoli serwera zamiast z sesji usług terminalowych.

Jeśli żadne z tych obejść nie jest możliwe, trzecią opcją jest dołączenie do procesu przez uruchomienie `vsjitdebugger.exe -p <ProcessId>` z wiersza polecenia systemu Windows. Identyfikator procesu można określić przy użyciu *tlist.exe*. Aby uzyskać *tlist.exe*, Pobierz i zainstaluj narzędzia debugowania dla systemu Windows, które są dostępne w [plikach WDK i WinDbg](/windows-hardware/drivers/download-the-wdk).

::: moniker range=">= vs-2019"

## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>Dołączanie do procesu .NET Core działającego w systemie Linux przy użyciu protokołu SSH

Aby uzyskać więcej informacji, zobacz [zdalne debugowanie .NET Core działającego w systemie Linux przy użyciu protokołu SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md).

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a>Dołączanie do procesu działającego w kontenerze platformy Docker systemu Linux

Debuger programu Visual Studio można dołączyć do procesu działającego w kontenerze Docker platformy Linux .NET Core na komputerze lokalnym lub zdalnym przy użyciu okna dialogowego **Dołącz do procesu** .

> [!IMPORTANT]
> Aby użyć tej funkcji, należy zainstalować środowisko programistyczne dla wielu platform .NET Core i mieć lokalny dostęp do kodu źródłowego.

**Aby dołączyć do uruchomionego procesu w kontenerze platformy Docker systemu Linux:**

1. W programie Visual Studio wybierz kolejno opcje **debuguj > Dołącz do procesu (Ctrl + Alt + P)** , aby otworzyć okno dialogowe **Dołącz do procesu** .

![Dołącz do menu procesu](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. Ustaw **Typ połączenia** na **Docker (kontener systemu Linux)**.
3. Wybierz pozycję **Znajdź...** , aby ustawić **cel połączenia** za pomocą okna dialogowego **Wybieranie kontenera platformy Docker** .

    Proces kontenera Docker można debugować lokalnie lub zdalnie.
    
    **Aby debugować proces kontenera platformy Docker lokalnie:**
    1. Ustaw **hosta interfejsu wiersza polecenia platformy Docker** na **maszynę lokalną**.
    1. Wybierz uruchomiony kontener do dołączenia z listy i kliknij przycisk **OK**.
    
    ![Wybierz menu kontenera platformy Docker](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")
 
    **B. Aby debugować proces kontenera Docker zdalnie:**
    
    > [!NOTE] 
    > Dostępne są dwie opcje łączenia zdalnego z uruchomionym procesem w kontenerze platformy Docker. Pierwsza opcja, aby korzystać z protokołu SSH, jest idealna, jeśli nie masz zainstalowanych narzędzi platformy Docker na komputerze lokalnym.  Jeśli masz zainstalowane narzędzia platformy Docker lokalnie i masz demona platformy Docker, która jest skonfigurowana do akceptowania żądań zdalnych, wypróbuj drugą opcję przy użyciu demona Docker.

    1. ***Aby nawiązać połączenie z komputerem zdalnym za pośrednictwem protokołu SSH:***
        1. Wybierz pozycję **Dodaj...** , aby połączyć się z systemem zdalnym.<br/>
        ![Nawiązywanie połączenia z systemem zdalnym](../debugger/media/connect-remote-system.png "Nawiązywanie połączenia z systemem zdalnym")
        1. Wybierz uruchomiony kontener do dołączenia po pomyślnym nawiązaniu połączenia z protokołem SSH lub demonem, a następnie naciśnij przycisk **OK**.

    
    1. ***Aby ustawić docelowy kontener zdalny, na którym działa proces za pośrednictwem [demona platformy Docker](https://docs.docker.com/engine/reference/commandline/dockerd/)***
        1. Określ adres demona (tj. za pośrednictwem protokołu TCP, IP itp.) w obszarze **host platformy Docker (opcjonalnie)** , a następnie kliknij link Refresh (Odśwież).
        1. Wybierz uruchomiony kontener do dołączenia po pomyślnym nawiązaniu połączenia z demonem, a następnie naciśnij przycisk **OK**.

4. Wybierz odpowiedni proces kontenera z listy **dostępnych procesów** , a następnie wybierz pozycję **Dołącz** , aby rozpocząć debugowanie procesu kontenera języka C# w programie Visual Studio.

    ![Gotowe menu dołączone do platformy Docker](../debugger/media/docker-attach-complete.png "Ukończono menu dołączania Docker systemu Linux")
    

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a><a name="BKMK_Windows_Docker_Attach"></a>Dołączanie do procesu działającego w kontenerze platformy Docker systemu Windows

Debuger programu Visual Studio można dołączyć do procesu działającego w kontenerze platformy Docker systemu Windows na komputerze lokalnym przy użyciu okna dialogowego **Dołącz do procesu** .

> [!IMPORTANT]
> Aby użyć tej funkcji w procesie .NET Core, należy zainstalować Międzyplatformowe obciążenie dla programu .NET Core i uzyskać lokalny dostęp do kodu źródłowego.

**Aby dołączyć do uruchomionego procesu w kontenerze platformy Docker systemu Windows:**

1. W programie Visual Studio wybierz kolejno opcje **debuguj > Dołącz do procesu** (lub **Ctrl + Alt + P**), aby otworzyć okno dialogowe **Dołącz do procesu** .

   ![Dołącz do menu procesu](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. Ustaw **Typ połączenia** na **Docker (kontener systemu Windows)**.
3. Wybierz pozycję **Znajdź...** , aby ustawić **cel połączenia** przy użyciu okna dialogowego **Wybieranie kontenera platformy Docker** .

    > [!IMPORTANT]
    > Proces docelowy musi mieć taką samą architekturę procesora jak kontener systemu Windows platformy Docker, na którym działa.
    
   Ustawienie obiektu docelowego na kontener zdalny za pośrednictwem protokołu SSH jest obecnie niedostępne i można go wykonać tylko przy użyciu demona platformy Docker.
    
    ***Aby ustawić docelowy kontener zdalny, na którym działa proces za pośrednictwem [demona platformy Docker](https://docs.docker.com/engine/reference/commandline/dockerd/)***
    1. Określ adres demona (tj. za pośrednictwem protokołu TCP, IP itp.) w obszarze **host platformy Docker (opcjonalnie)** , a następnie kliknij link Refresh (Odśwież). 

    1. Wybierz uruchomiony kontener do dołączenia po pomyślnym nawiązaniu połączenia z demonem, a następnie wybierz przycisk OK.
    
4. Wybierz odpowiedni proces kontenera z listy **dostępnych procesów** , a następnie wybierz pozycję **Dołącz** , aby rozpocząć debugowanie procesu kontenera języka C#.

    ![Gotowe menu dołączone do platformy Docker](../debugger/media/docker-attach-complete-windows.png "Zakończono menu dołączania Docker systemu Windows")
    

5.  Wybierz odpowiedni proces kontenera z listy dostępnych procesów, a następnie wybierz pozycję **Dołącz** , aby rozpocząć debugowanie procesu kontenera języka C#.


::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a>Dołącz ponownie do procesu

Można szybko ponownie dołączyć do procesów, do których wcześniej dołączono, wybierając **debugowanie**ponownie  >  **Dołącz do procesu** (**SHIFT** + **Alt** + **P**). Po wybraniu tego polecenia debuger natychmiast podejmie próbę dołączenia do ostatnich procesów, do których dołączono, najpierw próbując dopasować poprzedni identyfikator procesu i jeśli to się nie powiedzie, dopasowując do poprzedniej nazwy procesu. Jeśli nie znaleziono żadnych dopasowań lub jeśli kilka procesów ma taką samą nazwę, zostanie otwarte okno dialogowe **Dołącz do procesu** , aby można było wybrać właściwy proces.

> [!NOTE]
> Polecenie **ponownie Dołącz do procesu** jest dostępne w programie Visual Studio 2017.

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a>Typowe scenariusze debugowania

W poniższej tabeli przedstawiono kilka typowych scenariuszy debugowania z linkami do dodatkowych instrukcji, jeśli są dostępne, aby ułatwić określenie, czy należy użyć **dołączania do procesu** i dołączenia do niego. (Lista nie jest wyczerpująca).

W przypadku niektórych typów aplikacji, takich jak aplikacje uniwersalne systemu Windows (platformy UWP), nie dołączasz bezpośrednio do nazwy procesu, ale zamiast tego użyj opcji menu **Debuguj zainstalowany pakiet aplikacji** w programie Visual Studio (patrz tabela).

Aby debuger dołączał do kodu pisanego w języku C++, kod musi emitować `DebuggableAttribute` . Możesz dodać to do kodu automatycznie, łącząc się z opcją konsolidatora [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) .

W przypadku debugowania skryptów po stronie klienta należy włączyć debugowanie skryptów w przeglądarce. W przypadku debugowania skryptu po stronie klienta w programie Chrome wybierz opcję **JavaScript (Chrome)** lub **JavaScript (Microsoft Edge-chrom)** jako typ kodu i w zależności od typu aplikacji może być konieczne zamknięcie wszystkich wystąpień programu Chrome i uruchomienie przeglądarki w trybie debugowania (typ `chrome.exe --remote-debugging-port=9222` z wiersza polecenia). We wcześniejszych wersjach programu Visual Studio debuger skryptów dla programu Chrome jest **zestawem internetowym**.

Aby szybko wybrać uruchomiony proces do dołączenia, w programie Visual Studio wpisz **Ctrl** + **Alt** + **P**, a następnie wpisz pierwszą literę nazwy procesu.

|Scenariusz|Debug — Metoda|Nazwa procesu|Notatki i linki|
|-|-|-|-|
|Debugowanie zdalne ASP.NET 4 lub 4,5 na serwerze IIS|Korzystanie z zdalnych narzędzi i **dołączanie do procesu**|*w3wp.exe*|Zobacz [zdalne debugowanie ASP.NET na zdalnym komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|ASP.NET Core debugowania zdalnego na serwerze IIS|Korzystanie z zdalnych narzędzi i **dołączanie do procesu**|*w3wp.exe* lub *dotnet.exe*|Począwszy od platformy .NET Core 3, proces *w3wp.exe* jest używany dla domyślnego [modelu hostingu w aplikacji](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1#hosting-models). W przypadku wdrażania aplikacji zobacz [Publikowanie w usługach IIS](/aspnet/core/host-and-deploy/iis/). Aby uzyskać szczegółowe informacje, zobacz [zdalne debugowanie ASP.NET Core na zdalnym komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md#BKMK_attach)|
|Debugowanie skryptu po stronie klienta na lokalnym serwerze usług IIS, dla obsługiwanych typów aplikacji |Użyj **dołączania do procesu**|*chrome.exe*, *MicrosoftEdgeCP.exe*lub *iexplore.exe*|Debugowanie skryptów musi być włączone. Dla programu Chrome należy również uruchomić polecenie Chrome w trybie debugowania (typ `chrome.exe --remote-debugging-port=9222` z wiersza polecenia) i wybrać **JavaScript (Chrome)** w polu **Dołącz do** .|
|Debugowanie aplikacji C#, Visual Basic lub C++ na komputerze lokalnym|Użyj standardowego debugowania (**F5**) lub **Dołącz do procesu**|*\<appname>. exe*|W większości scenariuszy należy używać debugowania standardowego i nie **dołączać do procesu**.|
|Debugowanie zdalne aplikacji klasycznej systemu Windows|Narzędzia zdalne|Nie dotyczy| Zobacz [debugowanie zdalne w języku C# lub aplikacji Visual Basic](../debugger/remote-debugging-csharp.md) lub [zdalne debugowanie aplikacji w języku C++](../debugger/remote-debugging-cpp.md)|
|Debugowanie programu .NET Core w systemie Linux|Użyj **dołączania do procesu**|*dotnet.exe*|Aby korzystać z protokołu SSH, zobacz [zdalne debugowanie programu .NET Core działającego w systemie Linux przy użyciu protokołu SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md). W przypadku aplikacji kontenerowych zapoznaj się z poprzednimi sekcjami w tym artykule.|
|Zdalne debugowanie Python w systemie Linux|Użyj **dołączania do procesu**|*debugpy*|Zobacz [dołączanie zdalnie z narzędzi Python](../python/debugging-python-code-on-remote-linux-machines.md#attach-remotely-from-python-tools)|
|Debuguj aplikację ASP.NET na maszynie lokalnej po uruchomieniu aplikacji bez debugera|Użyj **dołączania do procesu**|*iiexpress.exe*|Może to być przydatne do szybszego ładowania aplikacji, takich jak (na przykład), podczas profilowania. |
|Debuguj inne obsługiwane typy aplikacji w procesie serwera|Jeśli serwer jest zdalny, użyj narzędzi zdalnych i **Dołącz do procesu**|*chrome.exe*, *iexplore.exe*lub inne procesy|W razie potrzeby użyj Monitor zasobów, aby pomóc w zidentyfikowaniu procesu. Zobacz [debugowanie zdalne](../debugger/remote-debugging.md).|
|Debugowanie zdalne aplikacji uniwersalnej systemu Windows (platformy UWP), OneCore, HoloLens lub IoT|Debuguj zainstalowany pakiet aplikacji|Nie dotyczy|Zobacz [debugowanie zainstalowanego pakietu aplikacji](debug-installed-app-package.md) zamiast używania **dołączania do procesu**|
|Debuguj aplikację uniwersalną systemu Windows (platformy UWP), OneCore, HoloLens lub IoT, której nie uruchomiono w programie Visual Studio|Debuguj zainstalowany pakiet aplikacji|Nie dotyczy|Zobacz [debugowanie zainstalowanego pakietu aplikacji](debug-installed-app-package.md) zamiast używania **dołączania do procesu**|

## <a name="use-debugger-features"></a>Korzystanie z funkcji debugera

Aby korzystać z pełnych funkcji debugera programu Visual Studio (na przykład naciśnięcia punktów przerwania) podczas dołączania do procesu, aplikacja musi dokładnie odpowiadać Twojemu lokalnemu źródłu i symbolom. Oznacza to, że debuger musi mieć możliwość załadowania poprawnych [plików symboli (. pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Domyślnie wymaga to kompilacji debugowania.

W przypadku scenariuszy zdalnego debugowania trzeba mieć kod źródłowy (lub kopię kodu źródłowego), który jest już otwarty w programie Visual Studio. Skompilowane pliki binarne aplikacji na maszynie zdalnej muszą pochodzić z tej samej kompilacji co na komputerze lokalnym.

W niektórych lokalnych scenariuszach debugowania można debugować w programie Visual Studio bez dostępu do źródła, jeśli w aplikacji znajdują się poprawne pliki symboli. Domyślnie wymaga to kompilacji debugowania. Aby uzyskać więcej informacji, zobacz [Określanie symboli i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a>Rozwiązywanie problemów z dołączaniem błędów

W niektórych scenariuszach debuger może potrzebować pomocy w celu poprawnego zidentyfikowania typu kodu do debugowania. Jeśli wartości połączenia są ustawione prawidłowo (można wyświetlić poprawny proces na liście **dostępne procesy** ), ale debuger nie może dołączyć, spróbuj wybrać najbardziej odpowiedni typ połączenia na liście **Typ połączenia** , który może być wymagany, na przykład w przypadku debugowania aplikacji systemu Linux lub Python. Jeśli używasz domyślnego typu połączenia, możesz alternatywnie wybrać konkretny typ kodu, z którym chcesz się połączyć, zgodnie z opisem w dalszej części tej sekcji.

Gdy debuger dołącza do uruchomionego procesu, proces może zawierać jeden lub więcej typów kodu. Typy kodu, do których debuger może dołączyć, są wyświetlane i wybierane w oknie dialogowym [Wybieranie typu kodu](../debugger/select-code-type-dialog-box.md) .

Czasami debuger może pomyślnie dołączyć do jednego typu kodu, ale nie do innego typu kodu. Zwykle zdarza się to, gdy:

- Podjęto próbę dołączenia do procesu, który jest uruchomiony na komputerze zdalnym. Komputer zdalny może mieć zainstalowane składniki debugowania zdalnego dla niektórych typów kodu, ale nie dla innych.
- Podjęto próbę dołączenia do co najmniej dwóch procesów w celu bezpośredniego debugowania bazy danych. Debugowanie SQL obsługuje dołączanie tylko do jednego procesu.

Jeśli debuger może dołączyć do niektórych, ale nie wszystkich typów kodu, zobaczysz komunikat informujący o tym, które typy nie zostały dołączone.

Jeśli debuger pomyślnie dołączy do co najmniej jednego typu kodu, można wykonać debugowanie tego procesu. Będzie można debugować tylko te typy kodu, które zostały pomyślnie dołączone. Niedołączony kod w procesie będzie nadal działać, ale nie będzie można ustawiać punktów przerwania, wyświetlać danych ani wykonywać innych operacji debugowania dla tego kodu.

Jeśli potrzebujesz bardziej szczegółowych informacji o tym, dlaczego debuger nie mógł dołączyć do typu kodu, spróbuj ponownie dołączyć tylko do tego typu kodu.

**Aby uzyskać szczegółowe informacje na temat przyczyny niepowodzenia dołączenia typu kodu:**

1. Odłącz od procesu. W menu **Debuguj** wybierz opcję **Odłącz wszystkie**.

1. Dołącz ponownie do procesu, wybierając tylko kod, którego nie udało się dołączyć.

    1. W oknie dialogowym **Dołącz do procesu** wybierz proces z listy **dostępne procesy** .

    2. Wybierz pozycję **Wybierz**.

    3. W oknie dialogowym **Wybierz typ kodu** wybierz **Debuguj te typy kodu** i typ kodu, który nie mógł zostać dołączony. Usuń zaznaczenie innych typów kodu.

    4. Wybierz przycisk **OK**.

    5. W oknie dialogowym **Dołącz do procesu** wybierz pozycję **Dołącz**.

    Tym razem dołączenie zakończy się niepowodzeniem i zostanie wyświetlony konkretny komunikat o błędzie.

## <a name="see-also"></a>Zobacz też

- [Debugowanie wielu procesów](../debugger/debug-multiple-processes.md)
- [Debugowanie just in Time](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)
