---
title: Rozwiązywanie problemów z debugowaniem migawki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/24/2019
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1ee8633a9ad58981297f00338cd6c375c5cf721e
ms.sourcegitcommit: ea182703e922c74725045afc251bcebac305068a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71211238"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Rozwiązywanie problemów i znane problemy dotyczące debugowania migawek w programie Visual Studio

Jeśli kroki opisane w tym artykule nie rozwiążą problemu, wyszukaj problem dotyczący [społeczności deweloperów](https://developercommunity.visualstudio.com/spaces/8/index.html) lub zgłoś nowy problem, wybierając pozycję **Pomoc** > **Wyślij opinię** > **Zgłoś problem** w programie Visual Studio.

## <a name="issue-attach-snapshot-debugger-encounters-an-http-status-code-error"></a>Problem: "Attach Snapshot Debugger" napotka błąd kodu stanu HTTP

Jeśli w oknie **danych wyjściowych** wystąpi następujący błąd podczas próby dołączenia, może to być znany problem wymieniony poniżej. Wypróbuj proponowane rozwiązania, a jeśli problem będzie nadal występował, skontaktuj się z poprzednim aliasem.

`[TIMESTAMP] Error --- Unable to Start Snapshot Debugger - Attach Snapshot Debugger failed: System.Net.WebException: The remote server returned an error: (###) XXXXXX`

### <a name="401-unauthorized"></a>(401) — nieautoryzowane

Ten błąd wskazuje, że wywołanie REST wystawione przez program Visual Studio na platformę Azure używa nieprawidłowego poświadczenia. Przyczyną tego błędu może być znany błąd z modułem Easy OAuth Azure Active Directory.

Wykonaj następujące czynności:

* Upewnij się, że konto personalizacji programu Visual Studio ma uprawnienia do subskrypcji i zasobu platformy Azure, do którego dołączasz. Aby szybko ustalić, czy zasób jest dostępny w oknie dialogowym z > **dołączania debugowania Snapshot Debugger...**  > Zasób >  **platformy Azure** **Wybierz istniejący**lub w Eksploratorze chmury.
* Jeśli ten błąd będzie nadal występował, użyj jednego z kanałów opinii opisanych na początku tego artykułu.

### <a name="403-forbidden"></a>(403) zabronione

Ten błąd wskazuje, że uprawnienie jest odrzucane. Może to być spowodowane przez wiele różnych problemów.

Wykonaj następujące czynności:

* Sprawdź, czy Twoje konto programu Visual Studio ma prawidłową subskrypcję platformy Azure z wymaganymi uprawnieniami Access Control opartymi na rolach (RBAC) dla zasobu. W przypadku usługi AppService Sprawdź, czy masz uprawnienia do [wykonywania zapytań](https://docs.microsoft.com/rest/api/appservice/appserviceplans/get) dotyczących planu App Service, który obsługuje aplikację.
* Sprawdź, czy sygnatura czasowa komputera klienckiego jest prawidłowa i aktualna. Serwery z sygnaturami czasowymi wyciętymi przez ponad 15 minut sygnatury czasowej żądania zwykle powodują ten błąd.
* Jeśli ten błąd będzie nadal występował, użyj jednego z kanałów opinii opisanych na początku tego artykułu.

### <a name="404-not-found"></a>(404) nie znaleziono

Ten błąd oznacza, że nie można odnaleźć witryny sieci Web na serwerze.

Wykonaj następujące czynności:

* Sprawdź, czy witryna sieci Web została wdrożona i uruchomiona na zasobie App Service, do której dołączasz.
* Sprawdź, czy witryna jest dostępna pod adresem\<https://\>Resource. azurewebsites.NET
* Jeśli ten błąd będzie nadal występował, użyj jednego z kanałów opinii opisanych na początku tego artykułu.

### <a name="406-not-acceptable"></a>(406) nie akceptowalny

Ten błąd wskazuje, że serwer nie może odpowiedzieć na typ ustawiony w nagłówku Accept żądania.

Wykonaj następujące czynności:

* Sprawdź, czy witryna jest dostępna pod adresem\<https://\>Resource. azurewebsites.NET
* Sprawdź, czy lokacja nie została zmigrowana do nowych wystąpień. Snapshot Debugger używa koncepcji ARRAffinity w przypadku żądań routingu do określonych wystąpień, co sporadycznie może spowodować wystąpienie tego błędu.
* Jeśli ten błąd będzie nadal występował, użyj jednego z kanałów opinii opisanych na początku tego artykułu.

### <a name="409-conflict"></a>(409) konflikt

Ten błąd wskazuje, że żądanie powoduje konflikt z bieżącym stanem serwera.

Jest to znany problem, który występuje, gdy użytkownik podejmie próbę dołączenia Snapshot Debugger do AppService z włączonym ApplicationInsights. ApplicationInsights ustawia dla AppSettings inną wielkość liter niż program Visual Studio, powodując ten problem.

::: moniker range=">= vs-2019"
Ten problem został rozwiązany w programie Visual Studio 2019.
::: moniker-end

Wykonaj następujące czynności:

::: moniker range="vs-2017"

* Sprawdź, czy w Azure Portal są wielkie litery dla debugera migawek (SNAPSHOTDEBUGGER_EXTENSION_VERSION) i InstrumentationEngine (INSTRUMENTATIONENGINE_EXTENSION_VERSION). W przeciwnym razie zaktualizuj ustawienia ręcznie, co wymusza ponowne uruchomienie lokacji.
::: moniker-end
* Jeśli ten błąd będzie nadal występował, użyj jednego z kanałów opinii opisanych na początku tego artykułu.

### <a name="500-internal-server-error"></a>(500) wewnętrzny błąd serwera

Ten błąd oznacza, że witryna jest całkowicie wyłączona lub serwer nie może obsłużyć żądania. Snapshot Debugger tylko funkcje na uruchomionych aplikacjach. [Application Insights Snapshot Debugger](https://docs.microsoft.com/azure/azure-monitor/app/snapshot-debugger) udostępnia snapshotting na wyjątkach i może być najlepszym narzędziem do Twoich potrzeb.

### <a name="502-bad-gateway"></a>(502) zła Brama

Ten błąd wskazuje na problem z siecią po stronie serwera i może być tymczasowy.

Wykonaj następujące czynności:

* Poczekaj kilka minut, a następnie ponownie dołączaj Snapshot Debugger.
* Jeśli ten błąd będzie nadal występował, użyj jednego z kanałów opinii opisanych na początku tego artykułu.

## <a name="issue-snappoint-does-not-turn-on"></a>Problem: Punkt przyciągania nie jest włączona

Jeśli widoczna jest ikona ostrzeżenia ![ikona ostrzeżenia punktu przyciągania](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "ikona ostrzeżenia punktu przyciągania") przy użyciu punktu przyciągania zamiast ikony regularne punktu przyciągania następnie punktu przyciągania nie jest włączona.

![Punkt przyciągania nie włączać](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "punktu przyciągania jest wyłączone")

Wykonaj następujące czynności:

1. Upewnij się, że masz taką samą wersję kodu źródłowego, która była używana do kompilowania i wdrażania aplikacji. Upewnij się, że są ładowane poprawne symbole dla danego wdrożenia. Aby to zrobić, należy wyświetlić **modułów** okno podczas debugowania migawki i sprawdź kolumna plik symboli zawiera plik .pdb załadowanych modułów, debugowania. Rozszerzenie Snapshot Debugger podejmie próbę automatycznego pobrania i zastosowania symbole dla danego wdrożenia.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problem: Symbole nie są ładowane, gdy otwieram migawkę

Jeśli zostanie wyświetlone następujące okno, symboli nie został załadowany.

![Symbole nie są ładowane](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "symbole nie są ładowane.")

Wykonaj następujące czynności:

- Kliknij przycisk **Zmień ustawienia symboli...** Połącz na tej stronie. W **debugowanie > Symbol** ustawienia, Dodaj katalog pamięci podręcznej symboli. Uruchom ponownie debugowanie migawki po ustawieniu ścieżki symboli.

   Symbole lub pliki .pdb, dostępne w projekcie musi odpowiadać wdrożenia usługi App Service. Większości wdrożeń (wdrożenia za pomocą programu Visual Studio, ciągłej integracji/ciągłego wdrażania za pomocą potoków usługi Azure lub programu Kudu, itp.) będzie publikować swoje pliki symboli, wzdłuż do usługi App Service. Ustawianie katalogu pamięci podręcznej symboli umożliwia środowisku Visual Studio za pomocą tych symboli.

   ![Ustawienia symboli](../debugger/media/snapshot-troubleshooting-symbol-settings.png "ustawienia symboli")

- Również jeśli Twoja organizacja korzysta z serwera symboli lub porzuca symbole w inną ścieżkę, aby załadować symbole prawidłowy dla danego wdrożenia należy użyć ustawienia symboli.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problem: Nie widzę opcji "Dołącz Snapshot Debugger" w programie Cloud Explorer

Wykonaj następujące czynności:

- Upewnij się, że jest zainstalowany składnik rozszerzenia Snapshot Debugger. Otwórz Instalatora programu Visual Studio i sprawdź **rozszerzenia Snapshot Debugger** składnik pakietu roboczego platformy Azure.
::: moniker range="< vs-2019"
- Upewnij się, że Twoja aplikacja jest obsługiwana. Obecnie tylko ASP.NET (4.6.1+) i aplikacji platformy ASP.NET Core (w wersji 2.0 i nowsze) wdrożonych w usłudze Azure App Services są obsługiwane.
::: moniker-end
::: moniker range=">= vs-2019"
- Upewnij się, że aplikacja jest obsługiwana:
  - Azure App Services — aplikacje ASP.NET uruchomione na .NET Framework 4.6.1 lub nowszych.
  - App Services platformy Azure — aplikacje ASP.NET Core uruchomione na platformie .NET Core 2,0 lub nowszej w systemie Windows.
  - Platforma Azure Virtual Machines (i zestaw skalowania maszyn wirtualnych) — aplikacje ASP.NET uruchomione na .NET Framework 4.6.1 lub nowszych.
  - Platforma Azure Virtual Machines (i zestaw skalowania maszyn wirtualnych) — ASP.NET Core aplikacje działające na platformie .NET Core 2,0 lub nowszej w systemie Windows.
  - Usługi Azure Kubernetes Services — ASP.NET Core aplikacje działające na platformie .NET Core 2,2 lub nowszej w systemie Debian 9.
  - Usługi Azure Kubernetes Services — ASP.NET Core aplikacje działające na platformie .NET Core 2,2 lub nowszej na Alpine 3,8.
  - Usługi Azure Kubernetes Services — ASP.NET Core aplikacje działające na platformie .NET Core 2,2 lub nowszej w systemie Ubuntu 18,04.
::: moniker-end

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problem: W narzędzia diagnostyczne są widoczne tylko migawki z ograniczeniami

![Punkt przyciągania ograniczona](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "punkt przyciągania z ograniczoną przepływnością")

Wykonaj następujące czynności:

- Migawki zajmują mało pamięci, ale charakteryzują się opłaty zatwierdzenia. Jeśli rozszerzenie Snapshot Debugger wykryje, że usługi na serwerze występuje duże obciążenie pamięci duże, nie będzie wykonywać migawek. Możesz usunąć migawki już przechwycony przez zatrzymanie sesji rozszerzenia Snapshot Debugger i podjęcie ponownej próby.

::: moniker range=">= vs-2019"
## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>Problem: Debugowanie migawek z wieloma wersjami programu Visual Studio zawiera błędy

W Azure App Service programu Visual Studio 2019 jest wymagana nowsza wersja rozszerzenia witryny Snapshot Debugger.  Ta wersja nie jest zgodna ze starszą wersją rozszerzenia witryny Snapshot Debugger używanego przez program Visual Studio 2017.  Podczas próby dołączenia Snapshot Debugger w programie Visual Studio 2019 do Azure App Service, który został wcześniej debugowany przez Snapshot Debugger w programie Visual Studio 2017, zostanie wyświetlony następujący błąd:

![Niezgodne Snapshot Debugger rozszerzenia witryny programu Visual Studio 2019](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "Niezgodne Snapshot Debugger rozszerzenia witryny programu Visual Studio 2019")

Jeśli używasz programu Visual Studio 2017 do dołączania Snapshot Debugger do Azure App Service, który został wcześniej debugowany przez Snapshot Debugger w programie Visual Studio 2019, wystąpi następujący błąd:

![Niezgodne Snapshot Debugger rozszerzenia witryny programu Visual Studio 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "Niezgodne Snapshot Debugger rozszerzenia witryny programu Visual Studio 2017")

Aby rozwiązać ten problem, Usuń następujące ustawienia aplikacji z Azure Portal i Dołącz Snapshot Debugger ponownie:

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION
::: moniker-end

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>Problem: Mam problemy z debugowaniem migawek i muszę włączyć więcej rejestrowania

### <a name="enable-agent-logs"></a>Włącz dzienniki agenta

Aby włączyć i wyłączyć rejestrowanie agenta, Otwórz program Visual Studio przejdź do *menu narzędzia > opcje > Snapshot Debugger > włączyć rejestrowanie agenta*. Zwróć uwagę, że po włączeniu *usuwania starych dzienników agentów podczas uruchamiania sesji* wszystkie pomyślne dołączenie do programu Visual Studio zostaną usunięte z poprzednich dzienników agenta.

Dzienniki agentów można znaleźć w następujących lokalizacjach:

- App Services:
  - Przejdź do witryny kudu App Service (czyli yourappservice. **SCM**. azurewebsites.NET) i przejdź do konsoli debugowania.
  - Dzienniki agentów są przechowywane w następującym katalogu:  D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\
- MASZYNA WIRTUALNA/VMSS:
  - Zaloguj się do maszyny wirtualnej, dzienniki agentów są przechowywane w następujący sposób:  C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics\<Version>\SnapshotDebuggerAgent_*.txt
- AKS
  - Przejdź do następującego katalogu:/tmp/diag/AgentLogs/*

### <a name="enable-profilerinstrumentation-logs"></a>Włączenie profilera/dzienników Instrumentacji

Dzienniki Instrumentacji można znaleźć w następujących lokalizacjach:

- App Services:
  - Rejestrowanie błędów jest wysyłane automatycznie do D:\Home\LogFiles\eventlog.XML, zdarzenia są oznaczane `<Provider Name="Instrumentation Engine" />` za pomocą lub "punktami przerwania produkcyjnego"
- MASZYNA WIRTUALNA/VMSS:
  - Zaloguj się do maszyny wirtualnej i Otwórz Podgląd zdarzeń.
  - Otwórz następujący widok: *Dzienniki systemu Windows > aplikacji*.
  - *Filtruj bieżący dziennik* według *źródła zdarzeń* przy użyciu *punktów przerwania produkcji* lub *aparatu oprzyrządowania*.
- AKS
  - Rejestrowanie aparatu Instrumentacji w lokalizacji/tmp/diag/log.txt (Ustaw MicrosoftInstrumentationEngine_FileLogPath w pliku dockerfile)
  - Rejestrowanie ProductionBreakpoint w/tmp/diag/shLog.txt

## <a name="known-issues"></a>Znane problemy

- Debugowanie migawki za pomocą wielu klientów programu Visual Studio dla tej samej usługi App Service nie jest obecnie obsługiwane.
- Optymalizacje Roslyn IL nie są w pełni obsługiwane w projektach ASP.NET Core. Dla niektórych projektów ASP.NET Core może nie mieć możliwość Zobacz pewnych zmiennych, lub użyj niektóre zmienne w instrukcjach warunkowych.
- Zmienne specjalne, takie jak *$FUNCTION* lub *$CALLER*, nie można obliczyć w instrukcjach warunkowych lub punkty rejestrowania dla projektów ASP.NET Core.
- Debugowanie migawki nie działa na temat usług aplikacji, które mają [buforowaniem lokalnym](/azure/app-service/app-service-local-cache) włączona.
- Migawka debugowania aplikacji interfejsu API nie jest obecnie obsługiwane.

## <a name="site-extension-upgrade"></a>Uaktualnienia rozszerzenia lokacji

Debugowanie migawki i usługi Application Insights są zależne od ICorProfiler, ładuje do procesu lokacji, która powoduje problemy podczas uaktualniania. Firma Microsoft zaleca tego procesu, aby upewnić się, że ma nie czas przestoju, do witryny produkcyjnej.

- Tworzenie [miejsce wdrożenia](/azure/app-service/web-sites-staged-publishing) w ramach usługi App Service i wdrażanie witryny do gniazda.
- W programie Cloud Explorer programu Visual Studio lub w witrynie Azure portal, należy zamienić gniazda z produkcji.
- Zatrzymaj witrynę miejsca. To może potrwać kilka sekund, aby skasować procesu w3wp.exe lokacji ze wszystkich wystąpień.
- Uaktualnianie miejsca rozszerzenia witryny z witryny Kudu lub witryny Azure portal (*bloku usługi App Service > Narzędzia programistyczne > Rozszerzenia > Aktualizacja*).
- Uruchom witrynę miejsca. Firma Microsoft zaleca, odwiedzając witrynę do rozgrzewki go ponownie.
- Zamienić gniazda z produkcji.

## <a name="see-also"></a>Zobacz także

- [Debugowanie w programie Visual Studio](../debugger/index.yml)
- [Debugowanie na żywo aplikacji ASP.NET, przy użyciu rozszerzenia Snapshot Debugger](../debugger/debug-live-azure-applications.md)
- [Debuguj zestawy skalowania maszyn wirtualnych ASP.NET platformy Azure na żywo przy użyciu Snapshot Debugger](../debugger/debug-live-azure-virtual-machines.md)
- [Debuguj Live ASP.NET Azure Kubernetes przy użyciu Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md)
- [Debugowanie migawek — często zadawane pytania](../debugger/debug-live-azure-apps-faq.md)
