---
title: Dołączanie do uruchomionego procesu za pomocą debugera | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: d439f0b13c0284d203c917c748b178c6d443220a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53056647"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Dołączanie do uruchomionego procesu za pomocą debugera programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debuger programu Visual Studio można dołączyć do procesu uruchomionego na komputerze lokalnym lub zdalnym. Po uruchomieniu procesu kliknij przycisk **debugowanie / dołączanie do procesu** (lub naciśnij **CTRL + ALT + P**) aby otworzyć **dołączyć do procesu** okno dialogowe.

Ta funkcja umożliwia debugowanie aplikacji, które są uruchomione na komputerze lokalnym lub zdalnym, Debuguj kilka procesów jednocześnie lub debugowania aplikacji, która nie została utworzona w programie Visual Studio. Często jest przydatne debugować aplikację, ale (niezależnie od przyczyny) nie zostało rozpoczęte aplikacji z programu Visual Studio w debugerze. Na przykład jeśli używasz aplikacji bez debugera i napotkała wyjątek, może być następnie dołączysz do procesu uruchamiania aplikacji, aby rozpocząć debugowanie.

> [!TIP]
> Nie masz pewności czy należy użyć **dołączyć do procesu** dla danego scenariusza debugowania? Zobacz [typowych scenariuszy debugowania](#BKMK_Scenarios). Jeśli chcesz debugować aplikacje ASP.NET, które zostały wdrożone w usługach IIS, zobacz temat [zdalnego debugowania ASP.NET, na komputerze zdalnym IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

##  <a name="BKMK_Attach_to_a_running_process"></a> Dołączanie do uruchomionego procesu na komputerze lokalnym
 Aby dołączyć do procesu, musisz znać nazwę procesu (zobacz [typowych scenariuszy debugowania](#BKMK_Scenarios) dla kilku typowych nazw procesów).

1.  W programie Visual Studio, wybierz **debugowanie / dołączanie do procesu** (lub naciśnij **CTRL + ALT + P**).

2.  W **dołączyć do procesu** okno dialogowe Znajdź program, który chcesz połączyć się z **dostępne procesy** listy.

     Aby szybko wybrać proces, który ma, wpisz pierwszą literę nazwy procesu. Jeśli nie znasz nazwy procesu, zobacz [typowych scenariuszy debugowania](#BKMK_Scenarios).

     ![DBG_Basics_Attach_To_Process](../debugger/media/dbg-basics-attach-to-process.png "DBG_Basics_Attach_To_Process")

     Jeśli proces działa przy użyciu konta innego użytkownika, wybierz opcję **Pokaż procesy wszystkich użytkowników** pole wyboru.

3.  W **dołączyć do** upewnij się, że typ kodu będziesz debugował jest wymieniony. Wartość domyślna **automatyczne** ustawienie próbuje określić, jakiego typu kod chcesz debugować. Aby ręcznie ustawić typ kodu, wykonaj następujące czynności

    1.  W **dołączyć do** kliknij **wybierz**.

    2.  W **Wybieranie typu kodu** okno dialogowe, kliknij przycisk **debugowania tych typów kodu** i wybierz typy do debugowania.

    3.  Kliknij przycisk **OK**.

4.  Kliknij przycisk **dołączyć**.

##  <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Dołącz do procesu na komputerze zdalnym
 Aby dołączyć do procesu, musisz znać nazwę procesu (zobacz [typowych scenariuszy debugowania](#BKMK_Scenarios) dla kilku typowych nazw procesów). Aby uzyskać bardziej szczegółowy wskazówki w przypadku aplikacji ASP.NET, które zostały wdrożone w usługach IIS, zobacz [zdalnego debugowania ASP.NET, na komputerze zdalnym IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). W przypadku innych aplikacji można znaleźć nazwę procesu, w Menedżerze zadań.

 Kiedy używasz **dołączyć do procesu** okno dialogowe, możesz wybrać inny komputer, który skonfigurowano dla zdalnego debugowania. Aby uzyskać więcej informacji, zobacz [zdalne debugowanie](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c). Po wybraniu komputera zdalnego można wyświetlić listę dostępnych procesów uruchomionych na tym komputerze i dołączyć do jednego lub kilku procesów debugowania.

 **Aby wybrać komputer zdalny:**

1. W programie Visual Studio, wybierz **debugowanie / dołączanie do procesu** (lub naciśnij **CTRL + ALT + P**).

2. W **dołączyć do procesu** okno dialogowe, wybierz odpowiedni typ połączenia z **transportu** listy. **Domyślne** jest poprawne ustawienia dla większości przypadków.

   **Transportu** ustawienie utrzymuje się między sesjami debugowania.

3. Użyj **kwalifikator** pola listy, aby wybrać nazwę komputera zdalnego za pomocą jednej z następujących metod:

   1. Wpisz nazwę w **kwalifikator** pola listy.

      >**Uwaga** Jeśli w kolejnych krokach, nie możesz się połączyć przy użyciu nazwy komputera zdalnego, użyj adresu IP. (Numer portu może pojawić się automatycznie po wybraniu procesu. Możesz również wprowadzić go ręcznie. Na poniższej ilustracji 4020 jest domyślnym portem dla zdalnego debugera).

   2. Kliknij strzałkę listy rozwijanej, dołączone do **kwalifikator** pola listy, a następnie wybierz nazwę komputera, z listy rozwijanej.

   3. Kliknij przycisk **znaleźć** znajdujący się obok **kwalifikator** liście, aby otworzyć **wybierz połączenie ze zdalnym debugerem** okno dialogowe. **Wybierz połączenie ze zdalnym debugerem** okno dialogowe wyświetla listę wszystkich urządzeń, które znajdują się w lokalnej podsieci i dowolnego urządzenia, który jest podłączony bezpośrednio do komputera za pomocą kabla Ethernet. Kliknij komputer lub urządzenie, a następnie kliknij **wybierz**.

      **Kwalifikator** ustawienie utrzymuje się między sesjami debugowania tylko wtedy, gdy nastąpi udane połączenie debugowania z tym kwalifikatorem.

4. Kliknij przycisk **Odśwież**.

     **Dostępne procesy** zostanie wyświetlona lista automatycznie po otwarciu **procesy** okno dialogowe. Procesy można uruchomić i zatrzymać w tle, gdy jest otwarte okno dialogowe. Jednakże zawartość nie jest zawsze aktualna. Można odświeżyć listę w dowolnym momencie, aby wyświetlić bieżącą listę procesów, klikając **Odśwież**.

5. W **dołączyć do procesu** okno dialogowe Znajdź program, który chcesz połączyć się z **dostępne procesy** listy.

    Jeśli proces działa przy użyciu konta innego użytkownika, wybierz opcję **Pokaż procesy wszystkich użytkowników** pole wyboru.

6. Kliknij przycisk **dołączyć**.

## <a name="additional-info"></a>Dodatkowe informacje

Można być dołączonym do wielu programów podczas debugowania, ale tylko jeden program jest aktywny w debugerze w dowolnym momencie. Można ustawić aktywny program w **Lokalizacja debugowania** paska narzędzi lub **procesy** okna. Aby uzyskać więcej informacji, zobacz [porady: Ustawianie bieżącego programu](http://msdn.microsoft.com/en-us/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).

Jeśli próbujesz dołączyć do procesu, którego właścicielem jest niezaufane konto użytkownika, pojawi się ostrzeżenie potwierdzenie okno dialogowe zabezpieczeń. Aby uzyskać więcej informacji, zobacz [ostrzeżenie o zabezpieczeniach: dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli informacje wyglądają podejrzanie lub niepewne, nie dołączaj do tego procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md).

W niektórych przypadkach podczas debugowania w sesji pulpitu zdalnego (usług terminalowych) **dostępne procesy** listy nie będą wyświetlane wszystkie dostępne procesy. Jeśli korzystasz z programu Visual Studio jako użytkownik mający konto użytkownika z ograniczonymi **dostępne procesy** listy nie pokaże procesów uruchomionych w sesji 0, który jest używany dla usług i innych procesów serwera, w tym w3wp.exe. Ten problem można rozwiązać, uruchamiając [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] przy użyciu konta administratora lub uruchamiając [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] z konsoli serwera zamiast sesji usług terminalowych. Jeśli żadna z tych obejść nie jest możliwe, trzecią opcją jest dołączenie do procesu, uruchamiając `vsjitdebugger.exe -p` *ProcessId* w wierszu polecenia Windows. Można określić identyfikator procesu przy użyciu tlist.exe. Aby uzyskać tlist.exe, Pobierz i zainstaluj debugowanie Tools for Windows, dostępne pod adresem [WDK i WinDbg pliki do pobrania](http://go.microsoft.com/fwlink/?LinkId=168279).

## <a name="BKMK_Scenarios"></a> Typowe scenariusze debugowania

Aby ustalić, czy należy użyć **dołączyć do procesu** i jakie procesy do dołączenia, poniżej przedstawiono kilka typowych scenariuszy debugowania (lista nie jest wyczerpująca). W przypadku, gdy dostępnych jest więcej instrukcji, firma Microsoft zapewnia łącza.

W przypadku niektórych typów aplikacji (takich jak aplikacje Windows Store), nie dołączaj bezpośrednio na nazwę procesu, ale użyć **pakietu debugowania zainstalowanej aplikacji** zamiast opcji menu (patrz tabela).

> [!NOTE]
> Aby dowiedzieć się, jak podstawowe debugowania w programie Visual Studio, zobacz [wprowadzenie do debugera](../debugger/getting-started-with-the-debugger.md).

|Scenariusz|Debugowanie — metoda|Nazwa procesu|Uwagi i łączy|
|-|-|-|-|
|Debugowanie zarządzane lub natywne aplikacji na komputerze lokalnym|Użyj dołączyć do procesu lub [standardowego debugowania](../debugger/getting-started-with-the-debugger.md)|*AppName*.exe|Aby szybko uzyskać dostęp do okna dialogowego, należy użyć **CTRL + ALT + P** , a następnie wpisz pierwszą literę nazwy procesu.|
|Debugowanie aplikacji ASP.NET na komputerze lokalnym po uruchomieniu aplikacji bez debugera|Użyj dołączyć do procesu|iiexpress.exe|Może to być przydatne zapewnić aplikacji obciążenia szybciej, takich jak (na przykład) podczas profilowania. |
|Zdalne debugowanie platformy ASP.NET 4 lub 4.5 na serwerze IIS|Użyj narzędzi zdalnych i Dołącz do procesu|W3wp.exe|Zobacz [zdalnego debugowania ASP.NET, na zdalnym komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Platforma ASP.NET Core debugowania zdalnego na serwerze IIS|Użyj narzędzi zdalnych i Dołącz do procesu|DNX.exe|Wdrożenie aplikacji, zobacz [publikowania w usługach IIS](https://docs.asp.net/en/latest/publishing/iis.html). Do debugowania, zobacz [zdalnego debugowania ASP.NET, na zdalnym komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Debugowanie innych typów aplikacji obsługiwanych w proces serwera|Użyj narzędzia zdalne (jeśli jest to serwer jest zdalna) i dołączyć do procesu|Iexplore.exe lub inne procesy|Jeśli to konieczne, należy użyć Menedżera zadań do identyfikowania procesu. Zobacz [zdalne debugowanie](../debugger/remote-debugging.md) oraz kolejnych sekcjach tego tematu|
|Zdalne debugowanie aplikacji pulpitu Windows|Remote Tools i F5|Brak| Zobacz [zdalnego debugowania](../debugger/remote-debugging.md)|
|Zdalne debugowanie aplikacji Windows (UWP, Universal), OneCore, HoloLens i IoT|Debugowanie zainstalowanego pakietu aplikacji|Brak|Użyj **Debuguj / inne cele debugowania / Debug zainstalowany pakiet aplikacji** zamiast **dołączyć do procesu**|
|Debugowanie aplikacji Windows (UWP, Universal), OneCore, HoloLens i IoT, która nie została uruchomiona z programu Visual Studio|Debugowanie zainstalowanego pakietu aplikacji|Brak|Użyj **Debuguj / inne cele debugowania / Debug zainstalowany pakiet aplikacji** zamiast **dołączyć do procesu**|

> [!WARNING]
>  Aby dołączyć do aplikacji Windows Universal, która jest napisany w języku JavaScript, należy najpierw włączyć debugowanie dla aplikacji. Zobacz [dołączyć debuger](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) w Centrum deweloperów Windows.

> [!NOTE]
>  Aby debuger dołączał do kodu napisanego w języku C++, kod musi wysyłać właściwość `DebuggableAttribute`. Można dodać to w kodzie automatycznie przez powiązanie z [/assemblydebug](http://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) — opcja konsolidatora.

## <a name="what-debugger-features-can-i-use"></a>Jakie funkcje debugera można używać?

Aby użyć wszystkich funkcji debugera programu Visual Studio (np. osiągnięcia punktów przerwania) podczas dołączania do procesu, plik wykonywalny musi dokładnie odpowiadać lokalnego źródła i symboli (oznacza to, debuger musi być w stanie załadować poprawny [(.pbd) pliki symboli ](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)). Domyślnie ta migracja wymaga kompilacji debugowania.

W przypadku scenariuszy debugowania zdalnego musi mieć kod źródłowy (lub kopię kodu źródłowego) już otwarty w programie Visual Studio. Plików binarnych skompilowanych aplikacji na komputerze zdalnym muszą pochodzić z tej samej kompilacji na komputerze lokalnym.

W niektórych scenariuszach debugowania lokalnego można debugować w programie Visual Studio bez dostępu do źródła, jeśli pliki symboli poprawne znajdują się w aplikacji (domyślnie ta opcja wymaga kompilacji debugowania). Aby uzyskać więcej informacji, zobacz [Określ symboli i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

##  <a name="BKMK_Troubleshoot_attach_errors"></a> Rozwiązywanie problemów z błędami dołączenia
 Gdy debuger jest dołączony do uruchomionego procesu, proces może zawierać jeden lub więcej typów kodu. Typy kodu, do których może dołączyć debuger do są wyświetlane i zaznaczone w **Wybieranie typu kodu** okno dialogowe.

 Czasami debuger może pomyślnie dołączyć do jednego typu kodu, ale nie do innego typu kodu. Taka sytuacja może wystąpić, jeśli próbujesz dołączyć do procesu, który jest uruchomiony na komputerze zdalnym. Komputer zdalny może mieć zainstalowane dla niektórych typów kodu, ale nie dla innych składniki debugowania zdalnego. Może również wystąpić, jeśli próbujesz dołączyć do dwóch lub więcej rpocesów do bezpośredniego debugowania bazy danych. Debugowanie SQL obsługuje dołączanie do tylko jednego procesu.

 Jeśli debuger może dołączyć do niektórych, ale nie wszystkich, typów kodu, zostanie wyświetlony komunikat identyfikujący, jakie typy dołączenie nie powiodło się.

 Jeśli debuger pomyślnie dołącza do co najmniej jednego typu kodu, możesz przejść do debugowania procesu. Będzie można debugować tylko typy kodu, które zostały pomyślnie dołączone. Poprzedni komunikat przykładowy pokazuje, że niepowodzenia dołączenia typu kodu skryptu. W związku z tym czy nie można debugować kodu skryptu w ramach procesu. Kod skryptu w procesie będzie nadal działać, ale nie będzie mógł ustawić punkty przerwania, wyświetlać danych ani wykonywać innych operacji debugowania w skrypcie.

 Jeśli chcesz, aby uzyskać więcej informacji o niepowodzeniu debugera można dołączyć do typu kodu, możesz spróbować ponownie dołączyć do tego typu kodu.

 **Aby uzyskać szczegółowe informacje na temat przyczyny niepowodzenia dołączenia typu kodu**

1. Odłączyć od procesu. Na **debugowania** menu, kliknij przycisk **Odłącz wszystkie**.

2. Ponownie Dołącz do procesu, wybierając tylko pojedynczy typ kodu.

   1. W **dołączyć do procesu** okna dialogowego Wybierz ten proces w **dostępne procesy** listy.

   2. Kliknij przycisk **wybierz**.

   3. W **Wybieranie typu kodu** okno dialogowe, wybierz **debugowania tych typów kodu** i typy kodu, których nie można dołączyć. Wyczyść inny kod.

   4. Kliknij przycisk **OK**. **Wybieranie typu kodu** zamyka okno dialogowe.

   5. W **dołączyć do procesu** okno dialogowe, kliknij przycisk **Dołącz**.

      Tym razem dołączanie nie powiedzie się całkowicie i otrzymasz komunikat o błędzie.

## <a name="see-also"></a>Zobacz też
 [Debugowanie wielu procesów](../debugger/debug-multiple-processes.md) [debugowania Just In Time](../debugger/just-in-time-debugging-in-visual-studio.md) [zdalnego debugowania](../debugger/remote-debugging.md)
