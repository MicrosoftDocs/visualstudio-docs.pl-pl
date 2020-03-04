---
title: Dołączanie do uruchomionego procesu za pomocą debugera | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 04/08/2019
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
ms.openlocfilehash: f2f00cde0c2ea3fad79c0f5ef75f3c33ad7afc22
ms.sourcegitcommit: c98e0ccf236765b44e47095ee52836cb012e3854
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78257192"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Dołączanie do uruchomionego procesu za pomocą debugera programu Visual Studio
Debuger programu Visual Studio można dołączyć do procesu uruchomionego na komputerze lokalnym lub zdalnym. Po uruchomieniu procesu wybierz kolejno opcje **debuguj** > **Dołącz do procesu** lub naciśnij **klawisze CTRL**+**Alt**+**P** w programie Visual Studio, a następnie użyj okna dialogowego **Dołącz do procesu** , aby dołączyć debuger do procesu.

**Aby przeprowadzić** debugowanie uruchomionych aplikacji na komputerach lokalnych lub zdalnych, należy przeprowadzić debugowanie wielu procesów jednocześnie, debugować aplikacje, które nie zostały utworzone w programie Visual Studio, lub debugować dowolną aplikację, której nie uruchomiono w programie Visual Studio z dołączonym debugerem. Na przykład jeśli korzystasz z aplikacji bez debugera i napotkała wyjątek, należy można dołączyć debuger do procesu uruchamiania aplikacji i rozpocząć debugowanie.

> [!TIP]
> Nie masz pewności, czy chcesz użyć **dołączania do procesu** debugowania? Zobacz [typowe scenariusze debugowania](#BKMK_Scenarios).

## <a name="BKMK_Attach_to_a_running_process"></a>Dołączanie do uruchomionego procesu na komputerze lokalnym

Aby szybko ponownie dołączyć do dołączonego wcześniej procesu, zobacz Ponowne [dołączanie do procesu](#BKMK_reattach).

Aby debugować proces na komputerze zdalnym, zobacz [dołączanie do procesu na komputerze zdalnym](#BKMK_Attach_to_a_process_on_a_remote_computer).

::: moniker range=">= vs-2019"
Aby debugować proces .NET Core w kontenerze platformy Docker Linux, zobacz [dołączanie do kontenera Docker systemu Linux](#BKMK_Docker_Attach).
::: moniker-end

**Aby dołączyć do procesu na komputerze lokalnym:**

1. W programie Visual Studio wybierz kolejno opcje **debuguj** > **Dołącz do procesu** (lub naciśnij klawisz **Ctrl**+**Alt**+**P**), aby otworzyć okno dialogowe **Dołącz do procesu** .

   **Typ połączenia** powinien mieć wartość **default**. **Celem połączenia** powinna być nazwa komputera lokalnego.

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

2. Z listy **dostępne procesy** Znajdź i wybierz proces lub procesy, do których chcesz dołączyć.

   - Aby szybko wybrać proces, wpisz jego nazwę lub pierwszą literę w polu **Filtruj procesy** .

   - Jeśli nie znasz nazwy procesu, przejrzyj listę lub zapoznaj się z [typowymi scenariuszami debugowania](#BKMK_Scenarios) dla niektórych typowych nazw procesów.

   >[!TIP]
   >Procesy można uruchamiać i zatrzymywać w tle, gdy jest otwarte okno dialogowe **dołączanie do procesu** , więc Lista uruchomionych procesów może być nieaktualna. W dowolnym momencie możesz wybrać opcję **Odśwież** , aby wyświetlić bieżącą listę.

3. W polu **Dołącz do** upewnij się, że na liście znajduje się typ kodu, który ma być debugowany. Domyślne ustawienie **Automatyczne** działa w przypadku większości typów aplikacji.

   Aby ręcznie wybrać typy kodu:
   1. Kliknij pozycję **Wybierz**.
   1. W oknie dialogowym **Wybierz typ kodu** wybierz **Debuguj te typy kodu**.
   1. Wybierz typy kodu, który chcesz debugować.
   1. Kliknij przycisk **OK**.

4. Wybierz pozycję **Dołącz**.

>[!NOTE]
>Użytkownik może zostać dołączony do wielu aplikacji na potrzeby debugowania, ale tylko jednej aplikacji jest aktywny w debugerze w danym momencie. Aktywną aplikację można ustawić na pasku narzędzi lub w oknie **procesy** **debugowania** programu Visual Studio.

## <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a>Dołączanie do procesu na komputerze zdalnym

Możesz również wybrać komputer zdalny w oknie dialogowym **Dołącz do procesu** , wyświetlić listę dostępnych procesów uruchomionych na tym komputerze, a następnie dołączyć do jednego lub kilku procesów debugowania. Zdalny debuger (*msvsmon. exe*) musi być uruchomiony na komputerze zdalnym. Aby uzyskać więcej informacji, zobacz [debugowanie zdalne](../debugger/remote-debugging.md).

Aby uzyskać pełniejsze instrukcje dotyczące debugowania aplikacji ASP.NET, które zostały wdrożone w usługach IIS, zobacz [zdalne debugowanie ASP.NET na zdalnym komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**Aby dołączyć do uruchomionego procesu na komputerze zdalnym:**

1. W programie Visual Studio wybierz kolejno opcje **debuguj** > **Dołącz do procesu** (lub naciśnij klawisz **Ctrl**+**Alt**+**P**), aby otworzyć okno dialogowe **Dołącz do procesu** .

2. **Typ połączenia** powinien być **wartością domyślną** w większości przypadków. W polu **cel połączenia** wybierz komputer zdalny przy użyciu jednej z następujących metod:

   - Wybierz strzałkę listy rozwijanej obok pozycji **cel połączenia**i wybierz z listy rozwijanej nazwę komputera.
   - Wpisz nazwę komputera w polu **cel połączenia** i naciśnij klawisz **Enter**.

     Sprawdź, czy program Visual Studio dodaje wymagany port do nazwy komputera, która jest wyświetlana w formacie: **\<nazwa komputera zdalnego >:p**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Jeśli nie można nawiązać połączenia przy użyciu nazwy komputera zdalnego, spróbuj użyć adresu IP i portu (na przykład `123.45.678.9:4022`). 4024 jest domyślnym portem dla zdalnego debugera programu Visual Studio 2019 x64. W przypadku innych przypisań portów zdalnego debugera zobacz [zdalne przydziały portów zdalnego debugera](remote-debugger-port-assignments.md).

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Jeśli nie można nawiązać połączenia przy użyciu nazwy komputera zdalnego, spróbuj użyć adresu IP i portu (na przykład `123.45.678.9:4022`). 4022 jest domyślnym portem dla zdalnego debugera programu Visual Studio 2017 x64. W przypadku innych przypisań portów zdalnego debugera zobacz [zdalne przydziały portów zdalnego debugera](remote-debugger-port-assignments.md).

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
     >Jeśli próbujesz dołączyć do procesu, którego właścicielem jest niezaufane konto użytkownika, pojawi się ostrzeżenie potwierdzenie okno dialogowe zabezpieczeń. Aby uzyskać więcej informacji, zobacz [Ostrzeżenie o zabezpieczeniach: dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli poniższe informacje wyglądają podejrzanie lub nie masz pewności, nie dołączaj do tego procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).

5. W polu **Dołącz do** upewnij się, że na liście znajduje się typ kodu, który ma być debugowany. Domyślne ustawienie **Automatyczne** działa w przypadku większości typów aplikacji.

   Aby ręcznie wybrać typy kodu:
   1. Kliknij pozycję **Wybierz**.
   1. W oknie dialogowym **Wybierz typ kodu** wybierz **Debuguj te typy kodu**.
   1. Wybierz typy kodu, który chcesz debugować.
   1. Kliknij przycisk **OK**.

6. Wybierz pozycję **Dołącz**.

>[!NOTE]
>Użytkownik może zostać dołączony do wielu aplikacji na potrzeby debugowania, ale tylko jednej aplikacji jest aktywny w debugerze w danym momencie. Aktywną aplikację można ustawić na pasku narzędzi lub w oknie **procesy** **debugowania** programu Visual Studio.

W niektórych przypadkach podczas debugowania w ramach sesji Pulpit zdalny (usług terminalowych) na liście **dostępne procesy** nie będą wyświetlane wszystkie dostępne procesy. Jeśli używasz programu Visual Studio jako użytkownika z ograniczonym kontem użytkownika, lista **dostępne procesy** nie będzie zawierać procesów uruchomionych w sesji 0. Sesja 0 jest używana dla usług i innych procesów serwera, w tym *w3wp. exe*. Problem można rozwiązać, uruchamiając [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] w ramach konta administratora lub uruchamiając [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] z poziomu konsoli serwera zamiast z sesji usług terminalowych.

Jeśli żadne z tych obejść nie jest możliwe, trzecią opcją jest dołączenie do procesu, uruchamiając `vsjitdebugger.exe -p <ProcessId>` z wiersza polecenia systemu Windows. Identyfikator procesu można określić za pomocą *tlist. exe*. Aby uzyskać *tlist. exe*, Pobierz i zainstaluj narzędzia debugowania dla systemu Windows, które są dostępne w [plikach WDK i WinDbg](/windows-hardware/drivers/download-the-wdk).

::: moniker range=">= vs-2019"

## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>Dołączanie do procesu .NET Core działającego w systemie Linux przy użyciu protokołu SSH

Aby uzyskać więcej informacji, zobacz [zdalne debugowanie .NET Core działającego w systemie Linux przy użyciu protokołu SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md).

## <a name="BKMK_Docker_Attach"></a>Dołączanie do procesu działającego w kontenerze platformy Docker systemu Linux

Debuger programu Visual Studio można dołączyć do procesu działającego w kontenerze Docker platformy Linux .NET Core na komputerze lokalnym lub zdalnym przy użyciu okna dialogowego **Dołącz do procesu** .

> [!IMPORTANT]
> Aby użyć tej funkcji, należy zainstalować środowisko programistyczne dla wielu platform .NET Core i mieć lokalny dostęp do kodu źródłowego.

**Aby dołączyć do uruchomionego procesu w kontenerze platformy Docker systemu Linux:**

1. W programie Visual Studio wybierz kolejno opcje **debuguj > Dołącz do procesu (Ctrl + Alt + P)** , aby otworzyć okno dialogowe **Dołącz do procesu** .

![Dołącz do menu procesu](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. Ustaw **Typ połączenia** na **Docker (kontener systemu Linux)** .
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

4. Wybierz odpowiedni proces kontenera z listy **dostępnych procesów** , a następnie wybierz pozycję **Dołącz** , aby rozpocząć debugowanie C# procesu kontenera w programie Visual Studio.

    ![Gotowe menu dołączone do platformy Docker](../debugger/media/docker-attach-complete.png "Gotowe menu dołączone do platformy Docker")


::: moniker-end

## <a name="BKMK_reattach"></a>Dołącz ponownie do procesu

Można szybko ponownie dołączyć do procesów, do których wcześniej dołączono, wybierając **debuguj** > **ponownie dołączyć do procesu** (**SHIFT**+**Alt**+**P**). Po wybraniu tego polecenia, debuger spowoduje natychmiastową próbę dołączenia do ostatniego procesy, które są dołączone do, najpierw próbując dopasować poprzedni identyfikator procesu i jeśli się nie powiedzie, dopasowując do poprzedniej nazwa procesu. Jeśli nie znaleziono żadnych dopasowań lub jeśli kilka procesów ma taką samą nazwę, zostanie otwarte okno dialogowe **Dołącz do procesu** , aby można było wybrać właściwy proces.

> [!NOTE]
> Polecenie **ponownie Dołącz do procesu** jest dostępne w programie Visual Studio 2017.

## <a name="BKMK_Scenarios"></a>Typowe scenariusze debugowania

W poniższej tabeli przedstawiono kilka typowych scenariuszy debugowania z linkami do dodatkowych instrukcji, jeśli są dostępne, aby ułatwić określenie, czy należy użyć **dołączania do procesu** i dołączenia do niego. (Lista nie jest wyczerpująca).

W przypadku niektórych typów aplikacji, takich jak aplikacje uniwersalne systemu Windows (platformy UWP), nie dołączasz bezpośrednio do nazwy procesu, ale zamiast tego użyj opcji menu **Debuguj zainstalowany pakiet aplikacji** w programie Visual Studio (patrz tabela).

Aby debuger mógł dołączyć kod zapisany w C++, kod musi emitować `DebuggableAttribute`. Możesz dodać to do kodu automatycznie, łącząc się z opcją konsolidatora [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) .

Debugowanie skryptu po stronie klienta debugowanie skryptu musi być włączone w przeglądarce. W przypadku debugowania skryptu po stronie klienta w programie Chrome wybierz **zestaw Web Kit** jako typ kodu i w zależności od typu aplikacji może być konieczne zamknięcie wszystkich wystąpień programu Chrome i uruchomienie przeglądarki w trybie debugowania (wpisz `chrome.exe --remote-debugging-port=9222` z wiersza polecenia).

Aby szybko wybrać uruchomiony proces do dołączenia, w programie Visual Studio wpisz **Ctrl**+**Alt**+**P**, a następnie wpisz pierwszą literę nazwy procesu.

|Scenariusz|Debugowanie — metoda|Nazwa procesu|Uwagi i łączy|
|-|-|-|-|
|Zdalne debugowanie platformy ASP.NET 4 lub 4.5 na serwerze IIS|Korzystanie z zdalnych narzędzi i **dołączanie do procesu**|*W3wp.exe*|Zobacz [zdalne debugowanie ASP.NET na zdalnym komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Platforma ASP.NET Core debugowania zdalnego na serwerze IIS|Korzystanie z zdalnych narzędzi i **dołączanie do procesu**|*dotnet. exe* lub *nazwa_aplikacji. exe*|W przypadku wdrażania aplikacji zobacz [Publikowanie w usługach IIS](https://docs.asp.net/en/latest/publishing/iis.html). Aby debugować, zobacz [zdalne debugowanie ASP.NET Core na zdalnym komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|Debugowanie skryptu po stronie klienta na lokalnym serwerze usług IIS, dla typów obsługiwanych aplikacji |Użyj **dołączania do procesu**|*Chrome. exe*, *MicrosoftEdgeCP. exe*lub *iexplore. exe*|Debugowanie skryptu musi być włączona. Dla programu Chrome należy również uruchomić polecenie Chrome w trybie debugowania, a następnie w polu **Dołącz do** wybrać pozycję **kod WebKit** .|
|Debugowanie aplikacji w języku C#, Visual Basic lub C++ na komputerze lokalnym|Użyj standardowego debugowania (**F5**) lub **Dołącz do procesu**|*\<nazwa_aplikacji >. exe*|W większości scenariuszy należy używać debugowania standardowego i nie **dołączać do procesu**.|
|Zdalne debugowanie aplikacji pulpitu Windows|Zdalne narzędzia|Nie dotyczy| Zobacz [debugowanie zdalne a C# lub Visual Basic aplikacji](../debugger/remote-debugging-csharp.md) lub [debugowania zdalnego C++ aplikacji](../debugger/remote-debugging-cpp.md)|
|Debugowanie programu .NET Core w systemie Linux|Użyj **dołączania do procesu**|*dotnet. exe*|Aby korzystać z protokołu SSH, zobacz [zdalne debugowanie programu .NET Core działającego w systemie Linux przy użyciu protokołu SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md). |
|Debugowanie aplikacji platformy ASP.NET na komputerze lokalnym, po uruchomieniu aplikacji bez debugera|Użyj **dołączania do procesu**|*iiexpress. exe*|Może to być przydatne zapewnić aplikacji obciążenia szybciej, takich jak (na przykład) podczas profilowania. |
|Debugowanie innych typów aplikacji obsługiwanych w proces serwera|Jeśli serwer jest zdalny, użyj narzędzi zdalnych i **Dołącz do procesu**|*Chrome. exe*, *iexplore. exe*lub inne procesy|Jeśli to konieczne, należy użyć Monitora zasobów ułatwiają identyfikację procesu. Zobacz [debugowanie zdalne](../debugger/remote-debugging.md).|
|Zdalne debugowanie aplikacji Windows aplikacji Uniwersalnej, OneCore, HoloLens i IoT|Debugowanie zainstalowanego pakietu aplikacji|Nie dotyczy|Zobacz [debugowanie zainstalowanego pakietu aplikacji](debug-installed-app-package.md) zamiast używania **dołączania do procesu**|
|Debugowanie aplikacji Windows aplikacji Uniwersalnej, OneCore, HoloLens i IoT, która nie została uruchomiona z programu Visual Studio|Debugowanie zainstalowanego pakietu aplikacji|Nie dotyczy|Zobacz [debugowanie zainstalowanego pakietu aplikacji](debug-installed-app-package.md) zamiast używania **dołączania do procesu**|

## <a name="use-debugger-features"></a>Korzystanie z funkcji debugera

Aby użyć wszystkich funkcji debugera programu Visual Studio (np. osiągnięcia punktów przerwania) podczas dołączania do procesu, aplikacja musi dokładnie odpowiadać lokalnego źródła i symboli. Oznacza to, że debuger musi mieć możliwość załadowania poprawnych [plików symboli (. pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Domyślnie ta migracja wymaga kompilacji debugowania.

W przypadku scenariuszy debugowania zdalnego musi mieć kod źródłowy (lub kopię kodu źródłowego) już otwarty w programie Visual Studio. Plików binarnych skompilowanych aplikacji na komputerze zdalnym muszą pochodzić z tej samej kompilacji na komputerze lokalnym.

W niektórych scenariuszach debugowania lokalnego można debugować w programie Visual Studio bez dostępu do źródła, jeśli pliki symboli poprawne znajdują się w aplikacji. Domyślnie ta migracja wymaga kompilacji debugowania. Aby uzyskać więcej informacji, zobacz [Określanie symboli i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="BKMK_Troubleshoot_attach_errors"></a>Rozwiązywanie problemów z dołączaniem błędów
 Gdy debuger jest dołączony do uruchomionego procesu, proces może zawierać jeden lub więcej typów kodu. Typy kodu, do których debuger może dołączyć, są wyświetlane i wybierane w oknie dialogowym **Wybieranie typu kodu** .

 Czasami debuger może pomyślnie dołączyć do jednego typu kodu, ale nie do innego typu kodu. Taka sytuacja może wystąpić, jeśli próbujesz dołączyć do procesu, który jest uruchomiony na komputerze zdalnym. Komputer zdalny może mieć zainstalowane dla niektórych typów kodu, ale nie dla innych składniki debugowania zdalnego. Może również wystąpić, jeśli próbujesz dołączyć do dwóch lub więcej rpocesów do bezpośredniego debugowania bazy danych. Debugowanie SQL obsługuje dołączanie do tylko jednego procesu.

 Jeśli debuger może dołączyć do niektórych, ale nie wszystkich, typów kodu, zobaczysz komunikat identyfikujący, do których typów nie można dołączyć.

 Jeśli debuger pomyślnie dołącza do co najmniej jednego typu kodu, możesz przejść do debugowania procesu. Będzie można debugować tylko typy kodu, które zostały pomyślnie dołączone. Niedołączone kodu w procesie będą nadal działać, ale nie będzie można ustawiać punkty przerwania, wyświetlać dane lub wykonywać inne operacje debugowania, w tym kodem.

 Jeśli chcesz, aby uzyskać więcej informacji o niepowodzeniu debugera można dołączyć do typu kodu, spróbuj ponownie dołączyć do tego typu kodu.

 **Aby uzyskać szczegółowe informacje na temat przyczyny niepowodzenia dołączenia typu kodu:**

1. Odłączyć od procesu. W menu **Debuguj** wybierz opcję **Odłącz wszystkie**.

1. Ponownie Dołącz do procesu, wybierając tylko typy kodu, których nie można dołączyć.

    1. W oknie dialogowym **Dołącz do procesu** wybierz proces z listy **dostępne procesy** .

    2. Wybierz przycisk **Wybierz**.

    3. W oknie dialogowym **Wybierz typ kodu** wybierz **Debuguj te typy kodu** i typ kodu, który nie mógł zostać dołączony. Usuń zaznaczenie innych typów kodu.

    4. Kliknij przycisk **OK**.

    5. W oknie dialogowym **Dołącz do procesu** wybierz pozycję **Dołącz**.

    Tym razem dołączanie nie powiedzie się całkowicie i otrzymasz komunikat o błędzie.

## <a name="see-also"></a>Zobacz też

- [Debugowanie wielu procesów](../debugger/debug-multiple-processes.md)
- [Debugowanie just in Time](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)
