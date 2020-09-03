---
title: Dołączanie do uruchomionych procesów za pomocą debugera | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
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
- C++
- CSharp
- FSharp
- VB
- c++
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
caps.latest.revision: 62
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf4d63d7d00e91daa2564992f801896075f73aab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918944"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Dołączanie do uruchomionego procesu za pomocą debugera programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debuger programu Visual Studio można dołączyć do działającego procesu na komputerze lokalnym lub zdalnym. Po uruchomieniu procesu kliknij pozycję **Debuguj/Dołącz do procesu** (lub naciśnij **kombinację klawiszy Ctrl + Alt + P**), aby otworzyć okno dialogowe **Dołącz do procesu** .

Tej funkcji można użyć do debugowania aplikacji uruchomionych na komputerze lokalnym lub zdalnym, debugowania wielu procesów jednocześnie lub debugowania aplikacji, która nie została utworzona w programie Visual Studio. Często jest to przydatne, gdy chcesz debugować aplikację, ale (z dowolnego powodu) nie uruchomiono aplikacji z programu Visual Studio z dołączonym debugerem. Jeśli na przykład aplikacja jest uruchamiana bez debugera i wystąpi wyjątek, można dołączyć do procesu, w którym uruchomiono aplikację, aby rozpocząć debugowanie.

> [!TIP]
> Nie masz pewności, czy musisz użyć **dołączania do procesu** debugowania? Zobacz [typowe scenariusze debugowania](#BKMK_Scenarios). Jeśli chcesz debugować aplikacje ASP.NET, które zostały wdrożone w usługach IIS, zobacz [zdalne debugowanie ASP.NET na zdalnym komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

## <a name="attach-to-a-running-process-on-the-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> Dołącz do uruchomionego procesu na komputerze lokalnym
 W celu dołączenia do procesu należy znać nazwę procesu (patrz [typowe scenariusze debugowania](#BKMK_Scenarios) dla kilku typowych nazw procesów).

1. W programie Visual Studio wybierz kolejno opcje **Debuguj/Dołącz do procesu** (lub naciśnij **kombinację klawiszy Ctrl + Alt + P**).

2. W oknie dialogowym **Dołącz do procesu** Znajdź program, który chcesz dołączyć z listy **dostępne procesy** .

     Aby szybko wybrać żądany proces, wpisz pierwszą literę nazwy procesu. Jeśli nie znasz nazwy procesu, zobacz [typowe scenariusze debugowania](#BKMK_Scenarios).

     ![DBG_Basics_Attach_To_Process](../debugger/media/dbg-basics-attach-to-process.png "DBG_Basics_Attach_To_Process")

     Jeśli proces jest uruchomiony przy użyciu innego konta użytkownika, zaznacz pole wyboru **Pokaż procesy dla wszystkich użytkowników** .

3. W polu **Dołącz do** upewnij się, że na liście znajduje się typ kodu, który będzie debugowany. Domyślne ustawienie **Automatyczne** próbuje określić typ kodu, który ma być debugowany. Aby ręcznie ustawić typ kodu, wykonaj następujące czynności:

    1. W polu **Dołącz do** kliknij pozycję **Wybierz**.

    2. W oknie dialogowym **Wybierz typ kodu** kliknij pozycję **Debuguj te typy kodu** i wybierz typy do debugowania.

    3. Kliknij przycisk **OK**.

4. Kliknij przycisk **Dołącz**.

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Dołączanie do procesu na komputerze zdalnym
 W celu dołączenia do procesu należy znać nazwę procesu (patrz [typowe scenariusze debugowania](#BKMK_Scenarios) dla kilku typowych nazw procesów). Aby uzyskać bardziej szczegółowe wskazówki dotyczące aplikacji ASP.NET, które zostały wdrożone w usługach IIS, zobacz [zdalne debugowanie ASP.NET na zdalnym komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). W przypadku innych aplikacji może być możliwe znalezienie nazwy procesu w Menedżerze zadań.

 W przypadku korzystania z okna dialogowego **Dołącz do procesu** możesz wybrać inny komputer, który został skonfigurowany do zdalnego debugowania. Aby uzyskać więcej informacji, zobacz [debugowanie zdalne](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c). Po wybraniu komputera zdalnego można wyświetlić listę dostępnych procesów uruchomionych na tym komputerze i dołączyć do jednego lub kilku procesów debugowania.

 **Aby wybrać komputer zdalny:**

1. W programie Visual Studio wybierz kolejno opcje **Debuguj/Dołącz do procesu** (lub naciśnij **kombinację klawiszy Ctrl + Alt + P**).

2. W oknie dialogowym **Dołącz do procesu** wybierz odpowiedni typ połączenia z listy **transport** . **Wartość domyślna** to poprawne ustawienie dla większości przypadków.

   Ustawienie **transportu** utrzymuje się między sesjami debugowania.

3. Użyj pola listy **kwalifikator** , aby wybrać nazwę komputera zdalnego przy użyciu jednej z następujących metod:

   1. Wpisz nazwę w polu listy **kwalifikator** .

      > [!NOTE]
      > Jeśli w dalszych krokach nie można nawiązać połączenia przy użyciu nazwy komputera zdalnego, użyj adresu IP. (Numer portu może pojawić się automatycznie po wybraniu procesu. Możesz również wprowadzić ją ręcznie. Na poniższej ilustracji 4020 jest domyślnym portem dla zdalnego debugera.)

   2. Kliknij strzałkę listy rozwijanej dołączoną do pola listy **kwalifikator** i wybierz nazwę komputera z listy rozwijanej.

   3. Kliknij przycisk **Znajdź** obok listy **kwalifikator** , aby otworzyć okno dialogowe **Wybieranie połączenia ze zdalnym debugerem** . W oknie dialogowym **Wybieranie połączenia debugera zdalnego** są wyświetlane wszystkie urządzenia, które znajdują się w lokalnej podsieci, oraz wszystkie urządzenia, które są podłączone bezpośrednio do komputera za pośrednictwem kabla Ethernet. Kliknij żądany komputer lub urządzenie, a następnie kliknij przycisk **Wybierz**.

      Ustawienie **kwalifikator** utrzymuje się między sesjami debugowania tylko wtedy, gdy nastąpi pomyślne połączenie debugowania z tym kwalifikatorem.

4. Kliknij przycisk **Odśwież**.

     Lista **dostępne procesy** jest wyświetlana automatycznie po otwarciu okna dialogowego **procesy** . Procesy można uruchamiać i zatrzymywać w tle, gdy okno dialogowe jest otwarte. Jednak zawartość nie zawsze jest aktualna. Można odświeżyć listę w dowolnym momencie, aby wyświetlić bieżącą listę procesów, klikając przycisk **Odśwież**.

5. W oknie dialogowym **Dołącz do procesu** Znajdź program, który chcesz dołączyć z listy **dostępne procesy** .

    Jeśli proces jest uruchomiony przy użyciu innego konta użytkownika, zaznacz pole wyboru **Pokaż procesy dla wszystkich użytkowników** .

6. Kliknij przycisk **Dołącz**.

## <a name="additional-info"></a>Dodatkowe informacje

Podczas debugowania można dołączyć do wielu programów, ale tylko jeden program jest aktywny w debugerze w dowolnym momencie. Można ustawić aktywny program na pasku narzędzi **lokalizacji debugowania** lub w oknie **procesy** . Aby uzyskać więcej informacji, zobacz [How to: Set the current program](https://msdn.microsoft.com/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).

W przypadku próby dołączenia do procesu należącego do niezaufanego konta użytkownika zostanie wyświetlone potwierdzenie okna dialogowego ostrzeżenia o zabezpieczeniach. Aby uzyskać więcej informacji, zobacz [Ostrzeżenie o zabezpieczeniach: dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli poniższe informacje wyglądają podejrzanie lub nie masz pewności, nie dołączaj do tego procesu](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015).

W niektórych przypadkach podczas debugowania w ramach sesji Pulpit zdalny (usług terminalowych) na liście **dostępne procesy** nie będą wyświetlane wszystkie dostępne procesy. Jeśli używasz programu Visual Studio jako użytkownika z ograniczonym kontem użytkownika, lista **dostępne procesy** nie będzie zawierać procesów uruchomionych w sesji 0, która jest używana w przypadku usług i innych procesów serwera, w tym w3wp.exe. Problem można rozwiązać, uruchamiając [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] konto administratora lub uruchamiając [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] z poziomu konsoli serwera zamiast z sesji usług terminalowych. Jeśli żadne z tych obejść nie jest możliwe, trzecią opcją jest dołączenie do procesu przez uruchomienie procesu uruchomienia `vsjitdebugger.exe -p` *ProcessId* z wiersza polecenia systemu Windows. Identyfikator procesu można określić przy użyciu tlist.exe. Aby uzyskać tlist.exe, Pobierz i zainstaluj narzędzia debugowania dla systemu Windows, które są dostępne w  [plikach WDK i WinDbg](/windows-hardware/drivers/dashboard/).

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a> Typowe scenariusze debugowania

Aby pomóc w ustaleniu, czy konieczne jest użycie **dołączania do procesu** i dołączenia do niego procesu, poniżej przedstawiono kilka typowych scenariuszy debugowania (lista nie jest wyczerpująca). Gdy dostępne są więcej instrukcji, udostępniamy linki.

W przypadku niektórych typów aplikacji (takich jak aplikacje ze sklepu Windows) nie można dołączyć bezpośrednio do nazwy procesu, ale zamiast tego należy użyć opcji menu **Debuguj zainstalowany pakiet aplikacji** (patrz tabela).

> [!NOTE]
> Aby uzyskać informacje na temat debugowania podstawowego w programie Visual Studio, zobacz [wprowadzenie do debugera](../debugger/getting-started-with-the-debugger.md).

|Scenariusz|Debug — Metoda|Nazwa procesu|Notatki i linki|
|-|-|-|-|
|Debugowanie aplikacji zarządzanej lub natywnej na komputerze lokalnym|Użyj dołączania do procesu lub [debugowania standardowego](../debugger/getting-started-with-the-debugger.md)|*nazwa_aplikacji*. exe|Aby szybko uzyskać dostęp do okna dialogowego, użyj **kombinacji klawiszy Ctrl + Alt + P** , a następnie wpisz pierwszą literę nazwy procesu.|
|Debuguj aplikacje ASP.NET na maszynie lokalnej po uruchomieniu aplikacji bez debugera|Użyj dołączania do procesu|iiexpress.exe|Może to być przydatne do szybszego ładowania aplikacji, takich jak (na przykład), podczas profilowania. |
|Debugowanie zdalne ASP.NET 4 lub 4,5 na serwerze IIS|Korzystanie z zdalnych narzędzi i dołączanie do procesu|w3wp.exe|Zobacz [zdalne debugowanie ASP.NET na zdalnym komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|ASP.NET Core debugowania zdalnego na serwerze IIS|Korzystanie z zdalnych narzędzi i dołączanie do procesu|dnx.exe|W przypadku wdrażania aplikacji zobacz [Publikowanie w usługach IIS](https://docs.asp.net/en/latest/publishing/iis.html). Aby debugować, zobacz [zdalne debugowanie ASP.NET na zdalnym komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Debuguj inne obsługiwane typy aplikacji w procesie serwera|Użyj narzędzi zdalnych (Jeśli serwer jest zdalny) i Dołącz do procesu|iexplore.exe lub inne procesy|W razie potrzeby użyj Menedżera zadań, aby ułatwić identyfikację tego procesu. Zobacz [debugowanie zdalne](../debugger/remote-debugging.md) i dalsze sekcje w tym temacie|
|Debugowanie zdalne aplikacji klasycznej systemu Windows|Narzędzia zdalne i F5|Brak| Zobacz [debugowanie zdalne](../debugger/remote-debugging.md)|
|Zdalne debugowanie aplikacji uniwersalnej systemu Windows (platformy UWP), OneCore, HoloLens lub IoT|Debuguj zainstalowany pakiet aplikacji|Brak|Użyj **debugowania/innych elementów docelowych debugowania/Debuguj zainstalowany pakiet aplikacji** zamiast **dołączania do procesu**|
|Debugowanie aplikacji uniwersalnej systemu Windows (platformy UWP), OneCore, HoloLens lub IoT, która nie została uruchomiona z programu Visual Studio|Debuguj zainstalowany pakiet aplikacji|Brak|Użyj **debugowania/innych elementów docelowych debugowania/Debuguj zainstalowany pakiet aplikacji** zamiast **dołączania do procesu**|

> [!WARNING]
> Aby dołączyć do aplikacji uniwersalnej systemu Windows, która jest zapisywana w języku JavaScript, należy najpierw włączyć debugowanie dla aplikacji. Zobacz [Dołącz debuger](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) w centrum deweloperów systemu Windows.

> [!NOTE]
> Aby debuger dołączał do kodu pisanego w języku C++, kod musi emitować `DebuggableAttribute` . Możesz dodać to do kodu automatycznie, łącząc się z opcją konsolidatora [/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) .

## <a name="what-debugger-features-can-i-use"></a>Jakich funkcji debugera mogę używać?

Aby skorzystać z pełnych funkcji debugera programu Visual Studio (na przykład naciśnięcia punktów przerwania) podczas dołączania do procesu, plik wykonywalny musi dokładnie pasować do lokalnego źródła i symboli (czyli debuger musi być w stanie załadować poprawne [pliki symboli (. PBD)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). Domyślnie wymaga to kompilacji debugowania.

W przypadku scenariuszy zdalnego debugowania trzeba mieć kod źródłowy (lub kopię kodu źródłowego), który jest już otwarty w programie Visual Studio. Skompilowane pliki binarne aplikacji na maszynie zdalnej muszą pochodzić z tej samej kompilacji co na komputerze lokalnym.

W niektórych lokalnych scenariuszach debugowania można debugować w programie Visual Studio bez dostępu do źródła, jeśli poprawne pliki symboli są obecne w aplikacji (domyślnie wymaga to kompilacji debugowania). Aby uzyskać więcej informacji, zobacz [Określanie symboli i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> Rozwiązywanie problemów z dołączaniem błędów
 Gdy debuger dołącza do uruchomionego procesu, proces może zawierać jeden lub więcej typów kodu. Typy kodu, do których debuger może dołączyć, są wyświetlane i wybierane w oknie dialogowym **Wybieranie typu kodu** .

 Czasami debuger może pomyślnie dołączyć do jednego typu kodu, ale nie do innego typu kodu. Taka sytuacja może wystąpić, jeśli próbujesz dołączyć do procesu, który jest uruchomiony na komputerze zdalnym. Komputer zdalny może mieć zainstalowane składniki debugowania zdalnego dla niektórych typów kodu, ale nie dla innych. Może również wystąpić w przypadku próby dołączenia do co najmniej dwóch procesów w celu bezpośredniego debugowania bazy danych. Debugowanie SQL obsługuje dołączanie tylko do jednego procesu.

 Jeśli debuger może dołączyć do niektórych, ale nie wszystkich typów kodu, zobaczysz komunikat informujący o tym, które typy nie zostały dołączone.

 Jeśli debuger pomyślnie dołączy do co najmniej jednego typu kodu, można wykonać debugowanie tego procesu. Będzie można debugować tylko te typy kodu, które zostały pomyślnie dołączone. Poprzedni przykładowy komunikat pokazuje, że nie można dołączyć typu kodu skryptu. W związku z tym nie będzie można debugować kodu skryptu w ramach procesu. Kod skryptu w procesie nadal będzie działać, ale nie będzie można ustawiać punktów przerwania, wyświetlać danych ani wykonywać innych operacji debugowania w skrypcie.

 Jeśli potrzebujesz bardziej szczegółowych informacji o tym, dlaczego debuger nie mógł dołączyć do typu kodu, możesz spróbować ponownie dołączyć tylko do tego typu kodu.

 **Aby uzyskać szczegółowe informacje na temat przyczyny niepowodzenia dołączenia typu kodu**

1. Odłącz od procesu. W menu **debugowanie** kliknij **Odłącz wszystkie**.

2. Dołącz ponownie do procesu, wybierając tylko jeden typ kodu.

   1. W oknie dialogowym **Dołącz do procesu** wybierz proces z listy **dostępne procesy** .

   2. Kliknij pozycję **Wybierz**.

   3. W oknie dialogowym **Wybierz typ kodu** wybierz **Debuguj te typy kodu** i typ kodu, który nie mógł zostać dołączony. Wyczyść każdy inny kod.

   4. Kliknij przycisk **OK**. Okno dialogowe **Wybieranie typu kodu** zostanie zamknięte.

   5. W oknie dialogowym **Dołącz do procesu** kliknij pozycję **Dołącz**.

      Tym razem dołączenie zakończy się niepowodzeniem i zostanie wyświetlony konkretny komunikat o błędzie.

## <a name="see-also"></a>Zobacz też
 Debugowanie [wielu procesów](../debugger/debug-multiple-processes.md) debugowanie [zdalne](../debugger/remote-debugging.md) debugowania [just in Time](../debugger/just-in-time-debugging-in-visual-studio.md)
