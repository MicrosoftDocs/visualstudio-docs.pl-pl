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
ms.openlocfilehash: dad698f2ba660b6848e614f13751335894a17ae0
ms.sourcegitcommit: 0e22ead8234b2c4467bcd0dc047b4ac5fb39b977
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59366409"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Dołączanie do uruchomionego procesu za pomocą debugera programu Visual Studio
Debuger programu Visual Studio można dołączyć do procesu uruchomionego na komputerze lokalnym lub zdalnym. Po uruchomieniu procesu wybierz **debugowania** > **dołączyć do procesu** lub naciśnij **Ctrl**+**Alt** + **P** w programie Visual Studio oraz za pomocą **dołączyć do procesu** okno dialogowe, aby dołączyć debuger do procesu.

Możesz użyć **dołączyć do procesu** Aby debugować aplikacje uruchomione na komputerze lokalnym lub zdalnym, Debuguj kilka procesów jednocześnie, debugowanie aplikacji, które nie zostały utworzone w programie Visual Studio lub debugowanie dowolna aplikacja nie została uruchomiona w programie Visual Studio Debuger jest dołączony. Na przykład jeśli korzystasz z aplikacji bez debugera i napotkała wyjątek, należy można dołączyć debuger do procesu uruchamiania aplikacji i rozpocząć debugowanie.

> [!TIP]
> Nie masz pewności czy użyć **dołączyć do procesu** dla danego scenariusza debugowania? Zobacz [typowych scenariuszy debugowania](#BKMK_Scenarios).

##  <a name="BKMK_Attach_to_a_running_process"></a> Dołączanie do uruchomionego procesu na komputerze lokalnym

Szybko ponownie dołączyć do procesu dołączona do wcześniej, zobacz [ponownie dołączyć do procesu](#BKMK_reattach).

Aby debugować proces na komputerze zdalnym, zobacz [dołączyć do procesu na komputerze zdalnym](#BKMK_Attach_to_a_process_on_a_remote_computer).

**Aby dołączyć do procesu na komputerze lokalnym:**

1. W programie Visual Studio, wybierz **debugowania** > **dołączyć do procesu** (lub naciśnij **Ctrl**+**Alt** + **P**) aby otworzyć **dołączyć do procesu** okno dialogowe.

   **Typ połączenia** powinna być równa **domyślne**. **Adres docelowy połączenia** powinna być nazwą komputera lokalnego.

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

2. W **dostępne procesy** listy, Znajdź i wybierz proces lub procesy, które chcesz dołączyć do.

   - Aby szybko wybierz proces, wpisz jego nazwę lub pierwsza litera w **Filtruj procesy** pole.

   - Jeśli nie znasz nazwy procesu, przeglądać listę lub zobaczyć [typowych scenariuszy debugowania](#BKMK_Scenarios) dla niektórych typowych nazw procesów.

   >[!TIP]
   >Procesy mogą uruchamiać i zatrzymywać w tle podczas **dołączyć do procesu** okno dialogowe jest otwarty, więc listy uruchomionych procesów nie zawsze jest bieżąca. Możesz wybrać **Odśwież** w dowolnym momencie, aby wyświetlić bieżącą listę.

3. W **dołączyć do** pola, upewnij się, typ planu do debugowania kodu, który ma na liście. Wartość domyślna **automatyczne** ustawienie działa w przypadku większości typów aplikacji.

   Aby ręcznie wybrać typy kodu:
   1. Kliknij przycisk **wybierz**.
   1. W **Wybieranie typu kodu** okno dialogowe, wybierz **debugowania tych typów kodu**.
   1. Wybierz typy kodu, który chcesz debugować.
   1. Wybierz **OK**.

4. Wybierz **dołączyć**.

>[!NOTE]
>Użytkownik może zostać dołączony do wielu aplikacji na potrzeby debugowania, ale tylko jednej aplikacji jest aktywny w debugerze w danym momencie. Można ustawić aktywnej aplikacji w programie Visual Studio **Lokalizacja debugowania** paska narzędzi lub **procesy** okna.

##  <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Dołącz do procesu na komputerze zdalnym

Możesz również wybrać komputer zdalny w **dołączyć do procesu** okno dialogowe, wyświetlić listę dostępnych procesów uruchomionych na tym komputerze i dołączyć do jednego lub kilku procesów debugowania. Zdalny debuger (*msvsmon.exe*) musi być uruchomiona na komputerze zdalnym. Aby uzyskać więcej informacji, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).

Więcej instrukcje dotyczące debugowania aplikacji ASP.NET, które zostały wdrożone w usługach IIS, zobacz [zdalnego debugowania programu ASP.NET na komputerze zdalnym IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**Aby dołączyć do procesu uruchomionego na komputerze zdalnym:**

1. W programie Visual Studio, wybierz **debugowania** > **dołączyć do procesu** (lub naciśnij **Ctrl**+**Alt** + **P**) aby otworzyć **dołączyć do procesu** okno dialogowe.

2. **Typ połączenia** powinien być **domyślne** w większości przypadków. W **adres docelowy połączenia** wybierz komputera zdalnego, przy użyciu jednej z następujących metod:

   - Wybierz strzałkę listy rozwijanej obok pozycji **adres docelowy połączenia**, a następnie wybierz nazwę komputera, z listy rozwijanej.
   - Wpisz nazwę komputera w **adres docelowy połączenia** pole i naciśnij klawisz **Enter**.

     Sprawdź, czy program Visual Studio dodaje wymaganego portu z nazwą komputera, który jest wyświetlany w formacie:  **\<nazwy komputera zdalnego >: port**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Jeśli nie możesz się połączyć przy użyciu nazwy komputera zdalnego, spróbuj użyć adresu IP i portu adresu (na przykład `123.45.678.9:4022`). 4024 jest domyślnym portem dla zdalnego debugera programu Visual Studio 2019 x64. Aby uzyskać inne przypisania portów debugera zdalnego, zobacz [przypisania portów debugera zdalnego](remote-debugger-port-assignments.md).

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Jeśli nie możesz się połączyć przy użyciu nazwy komputera zdalnego, spróbuj użyć adresu IP i portu adresu (na przykład `123.45.678.9:4022`). 4022 jest domyślnym portem dla zdalnego debugera programu Visual Studio 2017 x64. Aby uzyskać inne przypisania portów debugera zdalnego, zobacz [przypisania portów debugera zdalnego](remote-debugger-port-assignments.md).

     ::: moniker-end

   - Wybierz **znaleźć** znajdujący się obok **adres docelowy połączenia** , aby otworzyć okno **połączeń zdalnych** okno dialogowe. **Połączeń zdalnych** okno dialogowe wyświetla listę wszystkich urządzeń, które znajdują się w podsieci lokalnej lub podłączone bezpośrednio do komputera. Konieczne może być [Otwórz UDP port 3702](../debugger/remote-debugger-port-assignments.md) na serwerze w celu odnajdywania urządzeń zdalnych. Wybierz komputer lub urządzenie, a następnie kliknij **wybierz**.

   > [!NOTE]
   > **Typu połączenia** ustawienie utrzymuje się między sesjami debugowania. **Adres docelowy połączenia** ustawienie utrzymuje się między sesjami debugowania tylko wtedy, gdy wystąpił udane połączenie debugowania, z których platformą docelową.

3. Kliknij przycisk **Odśwież** do wypełniania **dostępne procesy** listy.

    >[!TIP]
    >Procesy mogą uruchamiać i zatrzymywać w tle podczas **dołączyć do procesu** okno dialogowe jest otwarty, więc listy uruchomionych procesów nie zawsze jest bieżąca. Możesz wybrać **Odśwież** w dowolnym momencie, aby wyświetlić bieżącą listę.

4. W **dostępne procesy** listy, Znajdź i wybierz proces lub procesy, które chcesz dołączyć do.

   - Aby szybko wybierz proces, wpisz jego nazwę lub pierwsza litera w **Filtruj procesy** pole.

   - Jeśli nie znasz nazwy procesu, przeglądać listę lub zobaczyć [typowych scenariuszy debugowania](#BKMK_Scenarios) dla niektórych typowych nazw procesów.

   - Aby wyszukać procesy uruchomione na wszystkich kontach użytkownika, wybierz **Pokaż procesy wszystkich użytkowników** pole wyboru.

     >[!NOTE]
     >Jeśli próbujesz dołączyć do procesu, którego właścicielem jest niezaufane konto użytkownika, pojawi się ostrzeżenie potwierdzenie okno dialogowe zabezpieczeń. Aby uzyskać więcej informacji, zobacz [ostrzeżenie o zabezpieczeniach: Dołączanie do procesu należącego do niezaufanego użytkownika może być niebezpieczne. Jeśli informacje wyglądają podejrzanie lub niepewne, nie dołączaj do tego procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).

5. W **dołączyć do** pola, upewnij się, typ planu do debugowania kodu, który ma na liście. Wartość domyślna **automatyczne** ustawienie działa w przypadku większości typów aplikacji.

   Aby ręcznie wybrać typy kodu:
   1. Kliknij przycisk **wybierz**.
   1. W **Wybieranie typu kodu** okno dialogowe, wybierz **debugowania tych typów kodu**.
   1. Wybierz typy kodu, który chcesz debugować.
   1. Wybierz **OK**.

6. Wybierz **dołączyć**.

>[!NOTE]
>Użytkownik może zostać dołączony do wielu aplikacji na potrzeby debugowania, ale tylko jednej aplikacji jest aktywny w debugerze w danym momencie. Można ustawić aktywnej aplikacji w programie Visual Studio **Lokalizacja debugowania** paska narzędzi lub **procesy** okna.

W niektórych przypadkach podczas debugowania w sesji pulpitu zdalnego (usług terminalowych) **dostępne procesy** listy nie będą wyświetlane wszystkie dostępne procesy. Jeśli korzystasz z programu Visual Studio jako użytkownik mający konto użytkownika z ograniczonymi **dostępne procesy** lista nie będzie zawierać procesów uruchomionych w sesji 0. Sesja 0 jest używana dla usług i innych procesów serwera, w tym *w3wp.exe*. Ten problem można rozwiązać, uruchamiając [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] przy użyciu konta administratora lub uruchamiając [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] z konsoli serwera zamiast sesji usług terminalowych.

Jeśli żadna z tych obejść nie jest możliwe, trzecią opcją jest dołączenie do procesu, uruchamiając `vsjitdebugger.exe -p <ProcessId>` w wierszu polecenia Windows. Można określić przy użyciu Identyfikatora procesu *tlist.exe*. Aby uzyskać *tlist.exe*, Pobierz i zainstaluj debugowanie Tools for Windows, dostępne pod adresem [WDK i WinDbg pliki do pobrania](/windows-hardware/drivers/download-the-wdk).

## <a name="BKMK_reattach"></a> Ponownie Dołącz do procesu

Szybko można dołączyć ponownie do procesów, które zostały wcześniej dołączone do, wybierając **debugowania** > **ponownie Dołącz do procesu** (**Shift** + **Alt**+**P**). Po wybraniu tego polecenia, debuger spowoduje natychmiastową próbę dołączenia do ostatniego procesy, które są dołączone do, najpierw próbując dopasować poprzedni identyfikator procesu i jeśli się nie powiedzie, dopasowując do poprzedniej nazwa procesu. Jeśli nie znaleziono żadnych dopasowań lub kilka procesów mają taką samą nazwę **dołączyć do procesu** zostanie otwarte okno dialogowe, dzięki czemu można wybrać prawidłowy proces.

> [!NOTE]
> **Ponownie Dołącz do procesu** polecenie jest dostępna, począwszy od programu Visual Studio 2017.

## <a name="BKMK_Scenarios"></a> Typowe scenariusze debugowania

Aby ułatwić ustalenie, czy ma być używany **dołączyć do procesu** i jakie procesy do dołączenia do, w poniższej tabeli przedstawiono kilka typowych scenariuszy debugowania, wraz z łączami, aby uzyskać więcej instrukcji w przypadku, gdy jest to dostępne. (Lista nie jest wyczerpująca).

W przypadku niektórych typów aplikacji, takich jak aplikacje Windows aplikacji Uniwersalnej, nie dołączaj bezpośrednio na nazwę procesu, ale użyć **pakietu debugowania zainstalowanej aplikacji** menu zamiast opcji w programie Visual Studio (patrz tabela).

Aby debuger dołączał do kodu napisanego w języku C++, kod musi wysyłać właściwość `DebuggableAttribute`. Można dodać to w kodzie automatycznie przez powiązanie z [/assemblydebug](/cpp/build/reference/assemblydebug-add-debuggableattribute) — opcja konsolidatora.

Debugowanie skryptu po stronie klienta debugowanie skryptu musi być włączone w przeglądarce. Debugowanie skryptu po stronie klienta w przeglądarce Chrome, wybierz **Web kit** pisania kodu, a także w zależności od typu aplikacji, należy zamknąć wszystkie instancje, Chrome i uruchom przeglądarkę w trybie debugowania (typ `chrome.exe --remote-debugging-port=9222` z wiersza polecenia).

Szybkie wybieranie uruchomionego procesu można dołączyć do programu Visual Studio wpisz **Ctrl**+**Alt**+**P**, a następnie wpisz pierwszą literę Nazwa procesu.

|Scenariusz|Debugowanie — metoda|Nazwa procesu|Uwagi i łączy|
|-|-|-|-|
|Zdalne debugowanie platformy ASP.NET 4 lub 4.5 na serwerze IIS|Użyj narzędzi zdalnych i **dołączyć do procesu**|*W3wp.exe*|Zobacz [zdalne debugowanie dla platform ASP.NET na zdalnym komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Platforma ASP.NET Core debugowania zdalnego na serwerze IIS|Użyj narzędzi zdalnych i **dołączyć do procesu**|*dotnet.exe*|Wdrożenie aplikacji, zobacz [publikowania w usługach IIS](https://docs.asp.net/en/latest/publishing/iis.html). Do debugowania, zobacz [zdalnego debugowania programu ASP.NET Core na zdalnym komputerze IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|Debugowanie skryptu po stronie klienta na lokalnym serwerze usług IIS, dla typów obsługiwanych aplikacji |Użyj **dołączyć do procesu**|*Chrome.exe*, *MicrosoftEdgeCP.exe*, lub *iexplore.exe*|Debugowanie skryptu musi być włączona. Dla programu Chrome, należy uruchomić dla programu Chrome w trybie debugowania i wybierz pozycję **kodu aparatu Webkit** w **dołączyć do** pola.|
|Debugowanie aplikacji w języku C#, Visual Basic lub C++ na komputerze lokalnym|Użyj standardowego debugowania (**F5**) lub **dołączyć do procesu**|*\<appname>.exe*|W większości przypadków użyć standardowego debugowania i nie **dołączyć do procesu**.|
|Zdalne debugowanie aplikacji pulpitu Windows|Zdalne narzędzia|Brak| Zobacz [zdalne debugowanie aplikacji w języku C# lub Visual Basic](../debugger/remote-debugging-csharp.md) lub [zdalne debugowanie aplikacji w języku C++](../debugger/remote-debugging-cpp.md)|
|Debugowanie aplikacji platformy ASP.NET na komputerze lokalnym, po uruchomieniu aplikacji bez debugera|Użyj **dołączyć do procesu**|*iiexpress.exe*|Może to być przydatne zapewnić aplikacji obciążenia szybciej, takich jak (na przykład) podczas profilowania. |
|Debugowanie innych typów aplikacji obsługiwanych w proces serwera|Jeśli serwer jest zdalny, należy użyć narzędzia zdalnej i **dołączyć do procesu**|*Chrome.exe*, *iexplore.exe*, lub inne procesy|Jeśli to konieczne, należy użyć Monitora zasobów ułatwiają identyfikację procesu. Zobacz [zdalne debugowanie](../debugger/remote-debugging.md).|
|Zdalne debugowanie aplikacji Windows aplikacji Uniwersalnej, OneCore, HoloLens i IoT|Debugowanie zainstalowanego pakietu aplikacji|Brak|Zobacz [debugowanie zainstalowanego pakietu aplikacji](debug-installed-app-package.md) zamiast **dołączyć do procesu**|
|Debugowanie aplikacji Windows aplikacji Uniwersalnej, OneCore, HoloLens i IoT, która nie została uruchomiona z programu Visual Studio|Debugowanie zainstalowanego pakietu aplikacji|Brak|Zobacz [debugowanie zainstalowanego pakietu aplikacji](debug-installed-app-package.md) zamiast **dołączyć do procesu**|

## <a name="use-debugger-features"></a>Korzystanie z funkcji debugera

Aby użyć wszystkich funkcji debugera programu Visual Studio (np. osiągnięcia punktów przerwania) podczas dołączania do procesu, aplikacja musi dokładnie odpowiadać lokalnego źródła i symboli. Oznacza to, debuger musi być w stanie załadować poprawny [symboli (.pdb) plików](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Domyślnie ta migracja wymaga kompilacji debugowania.

W przypadku scenariuszy debugowania zdalnego musi mieć kod źródłowy (lub kopię kodu źródłowego) już otwarty w programie Visual Studio. Plików binarnych skompilowanych aplikacji na komputerze zdalnym muszą pochodzić z tej samej kompilacji na komputerze lokalnym.

W niektórych scenariuszach debugowania lokalnego można debugować w programie Visual Studio bez dostępu do źródła, jeśli pliki symboli poprawne znajdują się w aplikacji. Domyślnie ta migracja wymaga kompilacji debugowania. Aby uzyskać więcej informacji, zobacz [określanie plików symboli i źródeł](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

##  <a name="BKMK_Troubleshoot_attach_errors"></a> Rozwiązywanie problemów z błędami dołączenia
 Gdy debuger jest dołączony do uruchomionego procesu, proces może zawierać jeden lub więcej typów kodu. Typy kodu, do których może dołączyć debuger do są wyświetlane i zaznaczone w **Wybieranie typu kodu** okno dialogowe.

 Czasami debuger może pomyślnie dołączyć do jednego typu kodu, ale nie do innego typu kodu. Taka sytuacja może wystąpić, jeśli próbujesz dołączyć do procesu, który jest uruchomiony na komputerze zdalnym. Komputer zdalny może mieć zainstalowane dla niektórych typów kodu, ale nie dla innych składniki debugowania zdalnego. Może również wystąpić, jeśli próbujesz dołączyć do dwóch lub więcej rpocesów do bezpośredniego debugowania bazy danych. Debugowanie SQL obsługuje dołączanie do tylko jednego procesu.

 Jeśli debuger może dołączyć do niektórych, ale nie wszystkich, typów kodu, zobaczysz komunikat identyfikujący, do których typów nie można dołączyć.

 Jeśli debuger pomyślnie dołącza do co najmniej jednego typu kodu, możesz przejść do debugowania procesu. Będzie można debugować tylko typy kodu, które zostały pomyślnie dołączone. Niedołączone kodu w procesie będą nadal działać, ale nie będzie można ustawiać punkty przerwania, wyświetlać dane lub wykonywać inne operacje debugowania, w tym kodem.

 Jeśli chcesz, aby uzyskać więcej informacji o niepowodzeniu debugera można dołączyć do typu kodu, spróbuj ponownie dołączyć do tego typu kodu.

 **Aby uzyskać szczegółowe informacje na temat przyczyny niepowodzenia dołączenia typu kodu:**

1.  Odłączyć od procesu. Na **debugowania** menu, wybierz opcję **Odłącz wszystkie**.

1.  Ponownie Dołącz do procesu, wybierając tylko typy kodu, których nie można dołączyć.

    1.  W **dołączyć do procesu** okna dialogowego Wybierz ten proces w **dostępne procesy** listy.

    2.  Wybierz **wybierz**.

    3.  W **Wybieranie typu kodu** okno dialogowe, wybierz **debugowania tych typów kodu** i typy kodu, których nie można dołączyć. Usuń zaznaczenie innych typów kodu.

    4.  Wybierz **OK**.

    5.  W **dołączyć do procesu** okno dialogowe, wybierz opcję **Dołącz**.

    Tym razem dołączanie nie powiedzie się całkowicie i otrzymasz komunikat o błędzie.

## <a name="see-also"></a>Zobacz także

- [Debugowanie wielu procesów](../debugger/debug-multiple-processes.md)
- [debugowanie just in time](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)