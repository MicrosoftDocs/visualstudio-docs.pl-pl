---
title: Dołączanie do uruchomionych procesów za pomocą debugera | Dokumenty firmy Microsoft
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
ms.openlocfilehash: b5305be7615e426d7792d8dd3fefb2579e2ab6be
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233029"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Dołączanie do uruchomionego procesu za pomocą debugera programu Visual Studio
Debuger programu Visual Studio można dołączyć do uruchomionego procesu na komputerze lokalnym lub zdalnym. Po uruchomieniu procesu wybierz **debugowanie** > **Dołącz do procesu** lub naciśnij klawisz **Ctrl**+**Alt**+**P** w programie Visual Studio, a następnie użyj okna **dialogowego Dołącz do procesu,** aby dołączyć debuger do procesu.

Za pomocą **funkcji Dołącz do procesu** można debugować uruchomione aplikacje na komputerach lokalnych lub zdalnych, debugować wiele procesów jednocześnie, debugować aplikacje, które nie zostały utworzone w programie Visual Studio, lub debugować dowolną aplikację, która nie została uruchomiona z programu Visual Studio z dołączonym debugerem. Na przykład jeśli korzystasz z aplikacji bez debugera i naciśnij wyjątek, możesz następnie dołączyć debuger do procesu uruchamiania aplikacji i rozpocząć debugowanie.

> [!TIP]
> Nie wiesz, czy używać **dołącz do procesu** dla scenariusza debugowania? Zobacz [Typowe scenariusze debugowania](#BKMK_Scenarios).

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a>Podłączanie do uruchomionego procesu na komputerze lokalnym

Aby szybko ponownie dołączyć do procesu dołączonego do poprzedniego, zobacz [Ponowne dołączanie do procesu](#BKMK_reattach).

Aby debugować proces na komputerze zdalnym, zobacz [Dołączanie do procesu na komputerze zdalnym](#BKMK_Attach_to_a_process_on_a_remote_computer).

::: moniker range=">= vs-2019"
Aby debugować proces .NET Core w kontenerze platformy Docker systemu Linux, zobacz [Dołączanie do kontenera platformy Docker systemu Linux](#BKMK_Linux_Docker_Attach).
::: moniker-end

**Aby dołączyć do procesu na komputerze lokalnym:**

1. W programie Visual Studio wybierz pozycję+ **Debugowanie** > **dołączanie do procesu** (lub naciśnij klawisz **Ctrl****Alt**+**P),** aby otworzyć okno dialogowe **Dołączanie do procesu.**

   **Typ połączenia** powinien być ustawiony na **Domyślny**. **Miejsce docelowe połączenia** powinno być nazwą komputera lokalnego.

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

2. Na liście **Dostępne procesy** znajdź i wybierz proces lub procesy, do których chcesz dołączyć.

   - Aby szybko wybrać proces, wpisz jego nazwę lub pierwszą literę w polu **Filtruj procesy.**

   - Jeśli nie znasz nazwy procesu, przejrzyj listę lub zobacz [Typowe scenariusze debugowania](#BKMK_Scenarios) dla niektórych typowych nazw procesów.

   >[!TIP]
   >Procesy można uruchamiać i zatrzymywać w tle, gdy okno dialogowe **Dołącz do procesu** jest otwarte, więc lista uruchomionych procesów może nie zawsze być aktualna. Możesz wybrać **Odśwież** w dowolnym momencie, aby wyświetlić bieżącą listę.

3. W polu **Dołącz do** upewnij się, że na liście znajduje się typ kodu, który ma być debugowany. Domyślne ustawienie **Automatyczne** działa w przypadku większości typów aplikacji.

   Aby ręcznie wybrać typy kodów:
   1. Kliknij **pozycję Wybierz**.
   1. W oknie dialogowym **Wybieranie typu kodu** wybierz pozycję **Debuguj te typy kodów**.
   1. Wybierz typy kodów, które chcesz debugować.
   1. Kliknij przycisk **OK**.

4. Wybierz **pozycję Dołącz**.

>[!NOTE]
>Możesz być dołączony do wielu aplikacji do debugowania, ale tylko jedna aplikacja jest aktywna w debugerze w czasie. Możesz ustawić aktywną aplikację na pasku narzędzi **Lokalizacji debugowania** programu Visual Studio lub w oknie **Procesy.**

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a>Dołączanie do procesu na komputerze zdalnym

Można również wybrać komputer zdalny w oknie dialogowym **Dołączanie do procesu,** wyświetlić listę dostępnych procesów uruchomionych na tym komputerze i dołączyć do jednego lub więcej procesów do debugowania. Debuger zdalny (*msvsmon.exe*) musi być uruchomiony na komputerze zdalnym. Aby uzyskać więcej informacji, zobacz [Zdalne debugowanie](../debugger/remote-debugging.md).

Aby uzyskać bardziej kompletne instrukcje dotyczące debugowania ASP.NET aplikacji wdrożonych w serwisach IIS, zobacz [Zdalne debugowanie ASP.NET na zdalnym komputerze usług IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**Aby dołączyć do uruchomionego procesu na komputerze zdalnym:**

1. W programie Visual Studio wybierz pozycję+ **Debugowanie** > **dołączanie do procesu** (lub naciśnij klawisz **Ctrl****Alt**+**P),** aby otworzyć okno dialogowe **Dołączanie do procesu.**

2. **Typ połączenia** powinien być **domyślny** w większości przypadków. W polu **Docelowe połączenie** wybierz komputer zdalny, korzystając z jednej z następujących metod:

   - Wybierz strzałkę rozwijaną obok pozycji **Miejsce docelowe połączenia**i wybierz nazwę komputera z listy rozwijanej.
   - Wpisz nazwę komputera w polu **Docelowy połączenie** i naciśnij klawisz **Enter**.

     Sprawdź, czy program Visual Studio dodaje wymagany port do nazwy komputera, który jest wyświetlany w formacie: ** \<nazwa komputera zdalnego>:port**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Jeśli nie możesz połączyć się przy użyciu nazwy komputera zdalnego, `123.45.678.9:4022`spróbuj użyć adresu IP i portu (na przykład ). 4024 jest domyślnym portem zdalnego debugera programu Visual Studio 2019 x64. Aby uzyskać inne przypisania portów debugera [zdalnego, zobacz Przypisania portów debugera zdalnego](remote-debugger-port-assignments.md).

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Jeśli nie możesz połączyć się przy użyciu nazwy komputera zdalnego, `123.45.678.9:4022`spróbuj użyć adresu IP i portu (na przykład ). 4022 jest domyślnym portem zdalnego debugera programu Visual Studio 2017 x64. Aby uzyskać inne przypisania portów debugera [zdalnego, zobacz Przypisania portów debugera zdalnego](remote-debugger-port-assignments.md).

     ::: moniker-end

   - Wybierz przycisk **Znajdź** obok pola **Docelowe połączenie,** aby otworzyć okno dialogowe **Połączenia zdalne.** Okno **dialogowe Połączenia zdalne** zawiera listę wszystkich urządzeń, które znajdują się w podsieci lokalnej lub są bezpośrednio podłączone do komputera. W celu odnajdywanie urządzeń zdalnych może być konieczne [otwarcie portu UDP 3702](../debugger/remote-debugger-port-assignments.md) na serwerze. Wybierz odpowiedni komputer lub urządzenie, a następnie kliknij przycisk **Wybierz**.

   > [!NOTE]
   > Ustawienie **Typ połączenia** jest zachowywane między sesjami debugowania. Ustawienie **docelowe połączenia** utrzymuje się między sesjami debugowania tylko wtedy, gdy wystąpiło pomyślne połączenie debugowania z tym obiektem docelowym.

3. Kliknij **przycisk Odśwież,** aby wypełnić listę **Dostępne procesy.**

    >[!TIP]
    >Procesy można uruchamiać i zatrzymywać w tle, gdy okno dialogowe **Dołącz do procesu** jest otwarte, więc lista uruchomionych procesów może nie zawsze być aktualna. Możesz wybrać **Odśwież** w dowolnym momencie, aby wyświetlić bieżącą listę.

4. Na liście **Dostępne procesy** znajdź i wybierz proces lub procesy, do których chcesz dołączyć.

   - Aby szybko wybrać proces, wpisz jego nazwę lub pierwszą literę w polu **Filtruj procesy.**

   - Jeśli nie znasz nazwy procesu, przejrzyj listę lub zobacz [Typowe scenariusze debugowania](#BKMK_Scenarios) dla niektórych typowych nazw procesów.

   - Aby znaleźć procesy uruchomione na wszystkich kontach użytkowników, zaznacz pole wyboru **Pokaż procesy spośród wszystkich użytkowników.**

     >[!NOTE]
     >Jeśli spróbujesz dołączyć do procesu należącego do niezaufanego konta użytkownika, zostanie wyświetlone okno dialogowe z ostrzeżeniem o zabezpieczeniach. Aby uzyskać więcej informacji, zobacz [Ostrzeżenie o zabezpieczeniach: Dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli poniższe informacje wyglądają podejrzanie lub nie masz pewności, nie dołączaj do tego procesu.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)

5. W polu **Dołącz do** upewnij się, że na liście znajduje się typ kodu, który ma być debugowany. Domyślne ustawienie **Automatyczne** działa w przypadku większości typów aplikacji.

   Aby ręcznie wybrać typy kodów:
   1. Kliknij **pozycję Wybierz**.
   1. W oknie dialogowym **Wybieranie typu kodu** wybierz pozycję **Debuguj te typy kodów**.
   1. Wybierz typy kodów, które chcesz debugować.
   1. Kliknij przycisk **OK**.

6. Wybierz **pozycję Dołącz**.

>[!NOTE]
>Możesz być dołączony do wielu aplikacji do debugowania, ale tylko jedna aplikacja jest aktywna w debugerze w czasie. Możesz ustawić aktywną aplikację na pasku narzędzi **Lokalizacji debugowania** programu Visual Studio lub w oknie **Procesy.**

W niektórych przypadkach podczas debugowania w sesji pulpitu zdalnego (usług terminalowych) lista **Dostępne procesy** nie będą wyświetlane we wszystkich dostępnych procesach. Jeśli program Visual Studio jest uruchomiony jako użytkownik, który ma ograniczone konto użytkownika, lista **Dostępne procesy** nie będą wyświetlane procesy uruchomione w sesji 0. Sesja 0 jest używana do usług i innych procesów serwerowych, w tym *w3wp.exe*. Problem można rozwiązać, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] uruchamiając konto administratora [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lub uruchamiając z konsoli serwera zamiast sesji usług terminalowych.

Jeśli żadne z tych obejść nie jest możliwe, trzecią opcją jest `vsjitdebugger.exe -p <ProcessId>` dołączenie do procesu przez uruchomienie z wiersza polecenia systemu Windows. Identyfikator procesu można określić za pomocą *pliku tlist.exe*. Aby uzyskać *tlist.exe*, pobierz i zainstaluj narzędzia debugowania dla systemu Windows, dostępne w [plikach WDK i WinDbg do pobrania](/windows-hardware/drivers/download-the-wdk).

::: moniker range=">= vs-2019"


## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>Dołącz do procesu .NET Core działającego w systemie Linux przy użyciu SSH

Aby uzyskać więcej informacji, zobacz [Zdalne debugowanie .NET Core uruchomionego w systemie Linux przy użyciu programu SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md).

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a>Dołączanie do procesu uruchomionego w kontenerze platformy Docker systemu Linux

Debuger programu Visual Studio można dołączyć do procesu uruchomionego w kontenerze platformy Docker programu Linux .NET Core na komputerze lokalnym lub zdalnym za pomocą okna dialogowego **Dołącz do procesu.**

> [!IMPORTANT]
> Aby korzystać z tej funkcji, należy zainstalować obciążenie programistyczne .NET Core cross-platform development i mieć lokalny dostęp do kodu źródłowego.

**Aby dołączyć do uruchomionego procesu w kontenerze platformy Docker systemu Linux:**

1. W programie Visual Studio wybierz pozycję **Debug > Dołącz do procesu (CTRL+ALT+P),** aby otworzyć okno dialogowe **Dołączanie do procesu.**

![Dołącz do menu procesu](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. Ustaw **typ połączenia** na **dok(Linux Container)**.
3. Wybierz **pozycję Znajdź...,** aby ustawić **obiekt docelowy połączenia** za pomocą okna dialogowego Wybierz kontener **docker.**

    Można debugować proces kontenera platformy Docker lokalnie lub zdalnie.
    
    **Aby debugować proces kontenera platformy Docker lokalnie:**
    1. Ustaw **hosta interfejsu wiersza polecenia** platformy Docker na **komputer lokalny**.
    1. Wybierz uruchomiony kontener, do który chcesz dołączyć z listy, i naciśnij **przycisk OK**.
    
    ![Wybierz menu kontenera platformy Docker](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")
 
    **B. Aby zdalnie debugować proces kontenera platformy Docker:**
    
    > [!NOTE] 
    > Istnieją dwie opcje łączenia zdalnie z uruchomionym procesem w kontenerze platformy Docker. Pierwsza opcja, aby użyć SSH, jest idealnym rozwiązaniem, jeśli nie masz narzędzi platformy Docker zainstalowanych na komputerze lokalnym.  Jeśli masz zainstalowane lokalnie narzędzia platformy Docker i masz demon docker, który jest skonfigurowany do akceptowania żądań zdalnych, wypróbuj drugą opcję, używając demona platformy Docker.

    1. ***Aby połączyć się ze zdalnym urządzeniem za pośrednictwem protokołu SSH:***
        1. Wybierz **dodaj...** aby połączyć się z systemem zdalnym.<br/>
        ![Łączenie się z systemem zdalnym](../debugger/media/connect-remote-system.png "Łączenie się z systemem zdalnym")
        1. Wybierz uruchomiony kontener, do którego chcesz dołączyć po pomyślnym połączeniu się z SSH lub demonem, i naciśnij **przycisk OK**.

    
    1. ***Aby ustawić obiekt docelowy na zdalny kontener z uruchomionym procesem za pośrednictwem [demona platformy Docker](https://docs.docker.com/engine/reference/commandline/dockerd/)***
        1. Określ adres demona (tj. za pośrednictwem protokołu TCP, IP itp.) w obszarze **Host platformy Docker (Opcjonalnie)** i kliknij łącze odświeżania.
        1. Wybierz uruchomiony kontener, do którego chcesz dołączyć po pomyślnym nawiązaniu połączenia z demonem i naciśnij **przycisk OK**.

4. Wybierz odpowiedni proces kontenera z listy **Dostępnych procesów** i wybierz **Dołącz,** aby rozpocząć debugowanie procesu kontenera języka C# w programie Visual Studio!

    ![Ukończone menu dołączania docker](../debugger/media/docker-attach-complete.png "Ukończone menu dołączania dołączona do platformy Linux")
    

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a><a name="BKMK_Windows_Docker_Attach"></a>Dołączanie do procesu uruchomionego w kontenerze platformy Windows

Debuger programu Visual Studio można dołączyć do procesu uruchomionego w kontenerze platformy Windows docker na komputerze lokalnym za pomocą okna dialogowego **Dołącz do procesu.**

> [!IMPORTANT]
> Aby użyć tej funkcji z procesem .NET Core, należy zainstalować obciążenie programistyczne .NET Core cross-platform development i mieć lokalny dostęp do kodu źródłowego.

**Aby dołączyć do uruchomionego procesu w kontenerze platformy Windows:**

1. W programie Visual Studio wybierz pozycję **Debug > Dołącz do procesu** (lub **CTRL+ALT+P**), aby otworzyć okno dialogowe **Dołączanie do procesu.**

   ![Dołącz do menu procesu](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. Ustaw **typ połączenia** na **dok(Kontener systemu Windows)**.
3. Wybierz **pozycję Znajdź...,** aby ustawić **obiekt docelowy połączenia** za pomocą okna dialogowego Wybierz kontener **docker.**

    > [!IMPORTANT]
    > Proces docelowy musi mieć taką samą architekturę procesora jak kontener systemu Windows platformy Docker, na który jest uruchomiony.
    
   Ustawienie obiektu docelowego na kontener zdalny za pośrednictwem protokołu SSH jest obecnie niedostępne i można je wykonać tylko za pomocą demona platformy Docker.
    
    ***Aby ustawić obiekt docelowy na zdalny kontener z uruchomionym procesem za pośrednictwem [demona platformy Docker](https://docs.docker.com/engine/reference/commandline/dockerd/)***
    1. Określ adres demona (tj. za pośrednictwem protokołu TCP, IP itp.) w obszarze **Host platformy Docker (Opcjonalnie)** i kliknij łącze odświeżania. 

    1. Wybierz uruchomiony kontener, do którego chcesz dołączyć po pomyślnym nawiązaniu połączenia z demonem, i wybierz przycisk OK.
    
4. Wybierz odpowiedni proces kontenera z listy **Dostępnych procesów** i wybierz **Dołącz,** aby rozpocząć debugowanie procesu kontenera języka C#.

    ![Ukończone menu dołączania docker](../debugger/media/docker-attach-complete-windows.png "Ukończone menu dołączania do doklin systemu Windows")
    

5.  Wybierz odpowiedni proces kontenera z listy dostępnych procesów i **wybierz** dołącz, aby rozpocząć debugowanie procesu kontenera języka C#.


::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a>Ponowne dołączanie do procesu

Można szybko ponownie dołączyć do procesów, do których wcześniej dołączono, wybierając **debugowanie** > **ponownie do procesu** **(Shift**+**Alt**+**P).** Po wybraniu tego polecenia debuger natychmiast spróbuje dołączyć do ostatnich procesów dołączonych do przez pierwszą próbę dopasowania poprzedniego identyfikatora procesu, a jeśli to się nie powiedzie, przez dopasowanie do poprzedniej nazwy procesu. Jeśli nie zostaną znalezione żadne dopasowania lub kilka procesów ma taką samą nazwę, zostanie otwarte okno dialogowe **Dołącz do procesu,** aby można było wybrać właściwy proces.

> [!NOTE]
> Polecenie **Ponowne dołączanie do procesu** jest dostępne od programu Visual Studio 2017.

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a>Typowe scenariusze debugowania

Aby ułatwić określenie, czy używać **Dołącz do procesu** i jaki proces dołączyć do, w poniższej tabeli przedstawiono kilka typowych scenariuszy debugowania, z łączami do więcej instrukcji, jeśli są dostępne. (Lista nie jest wyczerpująca.

W przypadku niektórych typów aplikacji, takich jak aplikacje uniwersalnej aplikacji systemu Windows (UWP), nie należy dołączać bezpośrednio do nazwy procesu, ale zamiast tego należy użyć opcji menu **Debug installed App Package** w programie Visual Studio (zobacz tabelę).

Aby debuger dołączyć do kodu napisanego w języku C++, kod musi emitować `DebuggableAttribute`. Możesz dodać to do kodu automatycznie, łącząc się z opcją konsolidatora [/ASSEMBLYDEBUG.](/cpp/build/reference/assemblydebug-add-debuggableattribute)

W przypadku debugowania skryptów po stronie klienta debugowanie skryptów musi być włączone w przeglądarce. W przypadku debugowania skryptu po stronie klienta w Chrome wybierz **zestaw sieci Web** jako typ kodu, a w zależności od typu `chrome.exe --remote-debugging-port=9222` aplikacji może być konieczne zamknięcie wszystkich wystąpień Chrome i uruchomienie przeglądarki w trybie debugowania (wpisz z wiersza polecenia).

Aby szybko wybrać uruchomiony proces do dołączenia do programu Visual Studio wpisz **klawisz Ctrl**+**Alt**+**P**, a następnie wpisz pierwszą literę nazwy procesu.

|Scenariusz|Metoda debugowania|Nazwa procesu|Uwagi i łącza|
|-|-|-|-|
|Zdalne debugowanie ASP.NET 4 lub 4,5 na serwerze usług IIS|Użyj narzędzi zdalnych i **dołącz do procesu**|*plik w3wp.exe*|Zobacz [Zdalne debugowanie ASP.NET na zdalnym komputerze usług IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Zdalne debugowanie ASP.NET Core na serwerze usług IIS|Użyj narzędzi zdalnych i **dołącz do procesu**|*dotnet.exe* lub *appname.exe*|Aby zapoznać się z wdrażaniem aplikacji, zobacz [Publikowanie w usługach IIS](https://docs.asp.net/en/latest/publishing/iis.html). Aby debugować, zobacz [Zdalne debugowanie ASP.NET rdzenia na zdalnym komputerze usług IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|Debugowanie skryptu po stronie klienta na lokalnym serwerze usług IIS dla obsługiwanych typów aplikacji |Użyj **dołączania do procesu**|*chrome.exe*, *MicrosoftEdgeCP.exe*lub *iexplore.exe*|Debugowanie skryptów musi być włączone. W chrome musisz również uruchomić Chrome w trybie debugowania i wybrać **kod Webkit** w polu **Dołącz do.**|
|Debugowanie aplikacji C#, Visual Basic lub C++ na komputerze lokalnym|Użyj standardowego debugowania **(F5)** lub **dołącz do procesu**|*\<nazwa>.exe*|W większości scenariuszy należy użyć standardowego debugowania i nie **dołączać do procesu**.|
|Zdalne debugowanie aplikacji klasycznej systemu Windows|Narzędzia zdalne|Nie dotyczy| Zobacz [Zdalne debugowanie aplikacji Języka C# lub Visual Basic](../debugger/remote-debugging-csharp.md) lub [zdalnego debugowania aplikacji języka C++](../debugger/remote-debugging-cpp.md)|
|Debugowanie .NET Core na Linuksie|Użyj **dołączania do procesu**|*plik dotnet.exe*|Aby użyć SSH, zobacz [Zdalne debugowanie .NET Core uruchomionego w systemie Linux przy użyciu programu SSH](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md). |
|Debugowanie aplikacji ASP.NET na komputerze lokalnym po uruchomieniu aplikacji bez debugera|Użyj **dołączania do procesu**|*iiexpress.exe*|Może to być przydatne, aby przyspieszyć ładowanie aplikacji, na przykład (na przykład) podczas profilowania. |
|Debugowanie innych obsługiwanych typów aplikacji w procesie serwera|Jeśli serwer jest zdalny, użyj narzędzi zdalnych i **Dołącz do procesu**|*chrome.exe*, *iexplore.exe*lub inne procesy|W razie potrzeby użyj Monitora zasobów, aby zidentyfikować proces. Zobacz [Zdalne debugowanie](../debugger/remote-debugging.md).|
|Zdalne debugowanie uniwersalnej aplikacji systemu Windows (UWP), OneCore, HoloLens lub aplikacji IoT|Pakiet aplikacji zainstalowany debugowania|Nie dotyczy|Zobacz [Debugowanie zainstalowanego pakietu aplikacji](debug-installed-app-package.md) zamiast **dołączania do procesu**|
|Debugowanie uniwersalnej aplikacji systemu Windows (UWP), OneCore, HoloLens lub IoT, która nie została uruchamiana z programu Visual Studio|Pakiet aplikacji zainstalowany debugowania|Nie dotyczy|Zobacz [Debugowanie zainstalowanego pakietu aplikacji](debug-installed-app-package.md) zamiast **dołączania do procesu**|

## <a name="use-debugger-features"></a>Korzystanie z funkcji debugera

Aby użyć pełnych funkcji debugera programu Visual Studio (takich jak trafienie punktów przerwania) podczas dołączania do procesu, aplikacja musi dokładnie odpowiadać lokalnemu źródłu i symbolom. Oznacza to, że debuger musi być w stanie załadować poprawne [pliki symbolu (pdb).](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) Domyślnie wymaga to kompilacji debugowania.

W przypadku scenariuszy zdalnego debugowania musi być już otwarty kod źródłowy (lub kopia kodu źródłowego) w programie Visual Studio. Skompilowane pliki binarne aplikacji na komputerze zdalnym muszą pochodzić z tej samej kompilacji, co na komputerze lokalnym.

W niektórych scenariuszach debugowania lokalnego można debugować w programie Visual Studio bez dostępu do źródła, jeśli w aplikacji znajdują się poprawne pliki symboli. Domyślnie wymaga to kompilacji debugowania. Aby uzyskać więcej informacji, zobacz [Określanie symboli i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a>Rozwiązywanie problemów z dołączania błędów
 Gdy debuger dołącza do uruchomionego procesu, proces może zawierać jeden lub więcej typów kodu. Typy kodu, do których debuger może dołączyć, są wyświetlane i wybierane w oknie dialogowym **Wybieranie typu kodu.**

 Czasami debuger można pomyślnie dołączyć do jednego typu kodu, ale nie do innego typu kodu. Może to nastąpić, jeśli próbujesz dołączyć do procesu, który jest uruchomiony na komputerze zdalnym. Komputer zdalny może mieć składniki zdalnego debugowania zainstalowane dla niektórych typów kodu, ale nie dla innych. Może również wystąpić, jeśli spróbujesz dołączyć do dwóch lub więcej procesów do bezpośredniego debugowania bazy danych. Debugowanie SQL obsługuje dołączanie tylko do jednego procesu.

 Jeśli debuger jest w stanie dołączyć do niektórych, ale nie wszystkie typy kodu, zostanie wyświetlony komunikat identyfikujący typy, których nie można dołączyć.

 Jeśli debuger pomyślnie dołącza do co najmniej jednego typu kodu, można przystąpić do debugowania procesu. Będzie można debugować tylko typy kodu, które zostały pomyślnie dołączone. Nieprzyłączony kod w procesie będzie nadal działać, ale nie będzie można ustawić punktów przerwania, wyświetlić dane lub wykonać inne operacje debugowania na tym kodzie.

 Jeśli chcesz bardziej szczegółowe informacje o tym, dlaczego debuger nie można dołączyć do typu kodu, spróbuj ponownie dołączyć tylko do tego typu kodu.

 **Aby uzyskać szczegółowe informacje o tym, dlaczego nie można dołączyć typu kodu:**

1. Odłączyć się od procesu. W menu **Debugowanie** wybierz polecenie **Odłącz wszystkie**.

1. Ponowne dołączenie do procesu, wybierając tylko typ kodu, który nie został dołączony.

    1. W oknie dialogowym **Dołączanie do procesu** wybierz proces na liście **Dostępne procesy.**

    2. Wybierz przycisk **Wybierz**.

    3. W oknie dialogowym **Wybieranie typu kodu** wybierz opcję **Debuguj te typy kodów** i typ kodu, który nie został dołączony. Usuń zaznaczenie innych typów kodu.

    4. Kliknij przycisk **OK**.

    5. W oknie dialogowym **Dołączanie do procesu** wybierz pozycję **Dołącz**.

    Tym razem dołączenie zakończy się niepowodzeniem całkowicie, a otrzymasz konkretny komunikat o błędzie.

## <a name="see-also"></a>Zobacz też

- [Debugowanie wielu procesów](../debugger/debug-multiple-processes.md)
- [Debugowanie just-in-time](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)
