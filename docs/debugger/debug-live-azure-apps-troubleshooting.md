---
title: Rozwiązywanie problemów z debugowaniem migawek | Microsoft Docs
description: Poznaj Rozwiązywanie problemów i znane problemy dotyczące debugowania migawek w programie Visual Studio. Ładuj ICorProfiler bez powodowania przestojów w witrynie produkcyjnej.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b5a76c1cae508acd08e5f077d466facf02e0211a
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728647"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Rozwiązywanie problemów i znane problemy dotyczące debugowania migawek w programie Visual Studio

Jeśli kroki opisane w tym artykule nie rozwiążą problemu, wyszukaj problem dotyczący [społeczności deweloperów](https://aka.ms/feedback/suggest?space=8) lub zgłoś nowy problem, wybierając pozycję **Pomoc**  >  **Wyślij opinię**  >  **Zgłoś problem** w programie Visual Studio.

## <a name="issue-attach-snapshot-debugger-encounters-an-http-status-code-error"></a>Problem: "Attach Snapshot Debugger" napotka błąd kodu stanu HTTP

Jeśli w oknie **danych wyjściowych** wystąpi następujący błąd podczas próby dołączenia, może to być znany problem wymieniony poniżej. Wypróbuj proponowane rozwiązania, a jeśli problem będzie nadal występował, skontaktuj się z poprzednim aliasem.

`[TIMESTAMP] Error --- Unable to Start Snapshot Debugger - Attach Snapshot Debugger failed: System.Net.WebException: The remote server returned an error: (###) XXXXXX`

### <a name="401-unauthorized"></a>(401) — nieautoryzowane

Ten błąd wskazuje, że wywołanie REST wystawione przez program Visual Studio na platformę Azure używa nieprawidłowego poświadczenia. 

Wykonaj następujące kroki:

* Upewnij się, że konto personalizacji programu Visual Studio ma uprawnienia do subskrypcji i zasobu platformy Azure, do którego dołączasz. Aby szybko ustalić, czy zasób jest dostępny w oknie dialogowym z   >  **dołączania debugowania Snapshot Debugger...**  >  **Zasób**  >  platformy Azure **Wybierz pozycję istniejący** lub w Eksploratorze chmury.
* Jeśli ten błąd będzie nadal występował, użyj jednego z kanałów opinii opisanych na początku tego artykułu.

Jeśli włączono uwierzytelnianie/autoryzację (EasyAuth) na App Service, w komunikacie o błędzie stosu wywołań może wystąpić błąd 401 z LaunchAgentAsync. Upewnij się, że **Jeśli żądanie nie zostało uwierzytelnione** , jest ustawione tak, aby **zezwalać na żądania anonimowe (bez akcji)** w Azure Portal i zamiast tego podać authorization.jsw D:\Home\sites\wwwroot z następującą zawartością. 

```
{
  "routes": [
    {
      "path_prefix": "/",
      "policies": {
        "unauthenticated_action": "RedirectToLoginPage"
      }
    },
    {
      "http_methods": [ "POST" ],
      "path_prefix": "/41C07CED-2E08-4609-9D9F-882468261608/api/agent",
      "policies": {
        "unauthenticated_action": "AllowAnonymous"
      }
    }
  ]
}
```

Pierwsza droga efektywnie zabezpiecza domenę aplikacji podobną do **zalogowania się za pomocą programu [IdentityProvider]**. Druga trasa udostępnia punkt końcowy debugera migawek AgentLaunch poza uwierzytelnianiem, który wykonuje wstępnie zdefiniowaną akcję uruchamiania agenta diagnostyki debugera migawek tylko wtedy, *gdy* dla usługi App Service jest włączone rozszerzenie preinstalowanej lokacji debugera migawek. Aby uzyskać więcej informacji na authorization.jskonfiguracji, zobacz [reguły autoryzacji adresów URL](https://azure.github.io/AppService/2016/11/17/URL-Authorization-Rules.html).

### <a name="403-forbidden"></a>(403) zabronione

Ten błąd wskazuje, że uprawnienie jest odrzucane. Może to być spowodowane przez wiele różnych problemów.

Wykonaj następujące kroki:

* Sprawdź, czy Twoje konto programu Visual Studio ma prawidłową subskrypcję platformy Azure z wymaganymi uprawnieniami Role-Based Access Control (RBAC) dla zasobu. W przypadku usługi AppService Sprawdź, czy masz uprawnienia do [wykonywania zapytań](/rest/api/appservice/appserviceplans/get) dotyczących planu App Service, który obsługuje aplikację.
* Sprawdź, czy sygnatura czasowa komputera klienckiego jest prawidłowa i aktualna. Serwery z sygnaturami czasowymi wyciętymi przez ponad 15 minut sygnatury czasowej żądania zwykle powodują ten błąd.
* Jeśli ten błąd będzie nadal występował, użyj jednego z kanałów opinii opisanych na początku tego artykułu.

### <a name="404-not-found"></a>(404) nie znaleziono

Ten błąd oznacza, że nie można odnaleźć witryny sieci Web na serwerze.

Wykonaj następujące kroki:

* Sprawdź, czy witryna sieci Web została wdrożona i uruchomiona na zasobie App Service, do której dołączasz.
* Sprawdź, czy witryna jest dostępna pod adresem https:// \<resource\> . azurewebsites.NET
* Sprawdź, czy prawidłowo uruchomiona niestandardowa aplikacja sieci Web nie zwraca kodu stanu 404 w przypadku uzyskania dostępu do elementu https:// \<resource\> . azurewebsites.NET
* Jeśli ten błąd będzie nadal występował, użyj jednego z kanałów opinii opisanych na początku tego artykułu.

### <a name="406-not-acceptable"></a>(406) nie akceptowalny

Ten błąd wskazuje, że serwer nie może odpowiedzieć na typ ustawiony w nagłówku Accept żądania.

Wykonaj następujące kroki:

* Sprawdź, czy witryna jest dostępna pod adresem https:// \<resource\> . azurewebsites.NET
* Sprawdź, czy lokacja nie została zmigrowana do nowych wystąpień. Snapshot Debugger używa koncepcji ARRAffinity w przypadku żądań routingu do określonych wystąpień, co sporadycznie może spowodować wystąpienie tego błędu.
* Jeśli ten błąd będzie nadal występował, użyj jednego z kanałów opinii opisanych na początku tego artykułu.

### <a name="409-conflict"></a>(409) konflikt

Ten błąd wskazuje, że żądanie powoduje konflikt z bieżącym stanem serwera.

Jest to znany problem, który występuje, gdy użytkownik podejmie próbę dołączenia Snapshot Debugger do AppService z włączonym ApplicationInsights. ApplicationInsights ustawia dla AppSettings inną wielkość liter niż program Visual Studio, powodując ten problem.

::: moniker range=">= vs-2019"
Ten problem został rozwiązany w programie Visual Studio 2019.
::: moniker-end

Wykonaj następujące kroki:

::: moniker range="vs-2017"

* Sprawdź, czy w Azure Portal są wielkie litery dla debugera migawek (SNAPSHOTDEBUGGER_EXTENSION_VERSION) i InstrumentationEngine (INSTRUMENTATIONENGINE_EXTENSION_VERSION). W przeciwnym razie zaktualizuj ustawienia ręcznie, co wymusza ponowne uruchomienie lokacji.
::: moniker-end
* Jeśli ten błąd będzie nadal występował, użyj jednego z kanałów opinii opisanych na początku tego artykułu.

### <a name="500-internal-server-error"></a>(500) wewnętrzny błąd serwera

Ten błąd oznacza, że witryna jest całkowicie wyłączona lub serwer nie może obsłużyć żądania. Snapshot Debugger tylko funkcje na uruchomionych aplikacjach. [Application Insights Snapshot Debugger](/azure/azure-monitor/app/snapshot-debugger) udostępnia snapshotting na wyjątkach i może być najlepszym narzędziem do Twoich potrzeb.

### <a name="502-bad-gateway"></a>(502) zła Brama

Ten błąd wskazuje na problem z siecią po stronie serwera i może być tymczasowy.

Wykonaj następujące kroki:

* Poczekaj kilka minut, a następnie ponownie dołączaj Snapshot Debugger.
* Jeśli ten błąd będzie nadal występował, użyj jednego z kanałów opinii opisanych na początku tego artykułu.

## <a name="issue-snappoint-does-not-turn-on"></a>Problem: punkt przyciągania nie jest włączona

Jeśli zobaczysz ikonę ostrzeżenia ![punkt przyciągania ikonę ostrzeżenia](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "Ikona ostrzeżenia punkt przyciągania") z punkt przyciągania zamiast zwykłej ikony punkt przyciągania, wówczas punkt przyciągania nie jest włączona.

![Punkt przyciągania nie jest włączona](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Punkt przyciągania nie jest włączona")

Wykonaj następujące kroki:

1. Upewnij się, że masz taką samą wersję kodu źródłowego, która była używana do kompilowania i wdrażania aplikacji. Upewnij się, że ładujesz poprawne symbole dla danego wdrożenia. W tym celu Wyświetl okno **moduły** podczas debugowania migawek i sprawdź, czy w kolumnie plik symboli jest wyświetlany plik. pdb załadowany dla debugowanego modułu. Snapshot Debugger spróbuje automatycznie pobrać symbole i użyć ich do wdrożenia.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problem: symbole nie są ładowane, gdy otwieram migawkę

Jeśli zobaczysz następujące okno, symbole nie zostały załadowane.

![Symbole nie są ładowane](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "Symbole nie są ładowane")

Wykonaj następujące kroki:

- Kliknij pozycję **Zmień ustawienia symboli...** link na tej stronie. W ustawieniach **symboli > debugowania** Dodaj Katalog pamięci podręcznej symboli. Uruchom ponownie debugowanie migawek po ustawieniu ścieżki symboli.

   Symbole lub pliki. pdb, dostępne w projekcie, muszą być zgodne z wdrożeniem App Service. Większość wdrożeń (wdrażanie za pomocą programu Visual Studio, CI/CD z Azure Pipelines lub kudu itp.) spowoduje opublikowanie plików symboli wraz z App Service. Ustawienie katalogu pamięci podręcznej symboli umożliwia programowi Visual Studio używanie tych symboli.

   ![Ustawienia symboli](../debugger/media/snapshot-troubleshooting-symbol-settings.png "Ustawienia symboli")

- Alternatywnie, jeśli Twoja organizacja korzysta z serwera symboli lub opuszcza symbole w innej ścieżce, Użyj ustawień symboli, aby załadować poprawne symbole dla danego wdrożenia.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problem: nie widzę opcji "Dołącz Snapshot Debugger" w programie Cloud Explorer

Wykonaj następujące kroki:

- Upewnij się, że składnik Snapshot Debugger jest zainstalowany. Otwórz Instalator programu Visual Studio i sprawdź składnik **Snapshot Debugger** w obciążeniu platformy Azure.
::: moniker range="< vs-2019"
- Upewnij się, że aplikacja jest obsługiwana. Obecnie obsługiwane są tylko aplikacje ASP.NET (4.6.1 +) i ASP.NET Core (2.0 +) wdrożone na platformie Azure App Services.
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

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problem: w narzędzia diagnostyczne są widoczne tylko migawki z ograniczeniami

![Punkt przyciągania z ograniczeniami](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "Punkt przyciągania z ograniczeniami")

Wykonaj następujące kroki:

- Migawki zajmują niewiele pamięci, ale mają naliczane opłaty. Jeśli Snapshot Debugger wykryje, że serwer jest w dużym obciążeniu pamięci, nie zajmie migawek. Istnieje możliwość usunięcia już przechwyconych migawek, zatrzymując sesję Snapshot Debugger i ponawiając próbę.

::: moniker range=">= vs-2019"
## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>Problem: debugowanie migawek z wieloma wersjami programu Visual Studio zawiera błędy

W Azure App Service programu Visual Studio 2019 jest wymagana nowsza wersja rozszerzenia witryny Snapshot Debugger.  Ta wersja nie jest zgodna ze starszą wersją rozszerzenia witryny Snapshot Debugger używanego przez program Visual Studio 2017.  Podczas próby dołączenia Snapshot Debugger w programie Visual Studio 2019 do Azure App Service, który został wcześniej debugowany przez Snapshot Debugger w programie Visual Studio 2017, zostanie wyświetlony następujący błąd:

![Niezgodne Snapshot Debugger rozszerzenia witryny programu Visual Studio 2019](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "Niezgodne Snapshot Debugger rozszerzenia witryny programu Visual Studio 2019")

Jeśli używasz programu Visual Studio 2017 do dołączania Snapshot Debugger do Azure App Service, który został wcześniej debugowany przez Snapshot Debugger w programie Visual Studio 2019, wystąpi następujący błąd:

![Niezgodne Snapshot Debugger rozszerzenia witryny programu Visual Studio 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "Niezgodne Snapshot Debugger rozszerzenia witryny programu Visual Studio 2017")

Aby rozwiązać ten problem, Usuń następujące ustawienia aplikacji z Azure Portal i Dołącz Snapshot Debugger ponownie:

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION
::: moniker-end

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>Problem: mam problemy z debugowaniem migawek i muszę włączyć więcej rejestrowania

### <a name="enable-agent-logs"></a>Włącz dzienniki agenta

Aby włączyć i wyłączyć rejestrowanie agenta, Otwórz program Visual Studio przejdź do *menu narzędzia>opcje>Snapshot Debugger>włączyć rejestrowanie agenta*. Zwróć uwagę, że po włączeniu *usuwania starych dzienników agentów podczas uruchamiania sesji* wszystkie pomyślne dołączenie do programu Visual Studio zostaną usunięte z poprzednich dzienników agenta.

Dzienniki agentów można znaleźć w następujących lokalizacjach:

- App Services:
  - Przejdź do witryny kudu App Service (czyli yourappservice.**SCM**. azurewebsites.NET) i przejdź do konsoli debugowania.
  - Dzienniki agentów są przechowywane w następującym katalogu: D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\
- MASZYNA WIRTUALNA/VMSS:
  - Zaloguj się do maszyny wirtualnej, dzienniki agentów są przechowywane w następujący sposób: C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics \<Version> \ SnapshotDebuggerAgent_ *. txt
- AKS
  - Przejdź do następującego katalogu:/tmp/diag/AgentLogs/*

### <a name="enable-profilerinstrumentation-logs"></a>Włączenie profilera/dzienników Instrumentacji

Dzienniki Instrumentacji można znaleźć w następujących lokalizacjach:

- App Services:
  - Rejestrowanie błędów jest automatycznie wysyłane do D:\Home\LogFiles\eventlog.xml, zdarzenia są oznaczane za pomocą `<Provider Name="Instrumentation Engine" />` lub "punktami przerwania produkcyjnego"
- MASZYNA WIRTUALNA/VMSS:
  - Zaloguj się do maszyny wirtualnej i Otwórz Podgląd zdarzeń.
  - Otwórz następujący widok: *Dzienniki systemu Windows>aplikacji*.
  - *Filtruj bieżący dziennik* według *źródła zdarzeń* przy użyciu *punktów przerwania produkcji* lub *aparatu oprzyrządowania*.
- AKS
  - Rejestrowanie aparatu Instrumentacji w/tmp/diag/log.txt (Ustaw MicrosoftInstrumentationEngine_FileLogPath w pliku dockerfile)
  - Rejestrowanie ProductionBreakpoint w/tmp/diag/shLog.txt

## <a name="known-issues"></a>Znane problemy

- Debugowanie migawek z wieloma klientami programu Visual Studio na tym samym App Service nie jest obecnie obsługiwane.
- Optymalizacje IL Roslyn nie są w pełni obsługiwane w projektach ASP.NET Core. W przypadku niektórych projektów ASP.NET Core może nie być możliwe wyświetlenie niektórych zmiennych lub użycie niektórych zmiennych w instrukcjach warunkowych.
- Zmienne specjalne, takie jak *$Function* lub *$Caller*, nie mogą być oceniane w instrukcjach warunkowych ani punkty rejestrowania dla projektów ASP.NET Core.
- Debugowanie migawek nie działa na App Services z włączonym [buforowaniem lokalnym](/azure/app-service/app-service-local-cache) .
- API Apps debugowania migawek nie jest obecnie obsługiwana.

## <a name="site-extension-upgrade"></a>Uaktualnienie rozszerzenia witryny

Debugowanie migawek i Application Insights zależą od ICorProfiler, które są ładowane do procesu lokacji i powodują problemy z blokowaniem plików podczas uaktualniania. Zalecamy wykonanie tego procesu, aby upewnić się, że witryna produkcyjna nie ma czasu na czas nieokreślony.

- Utwórz [miejsce wdrożenia](/azure/app-service/web-sites-staged-publishing) w ramach App Service i Wdróż swoją lokację w gnieździe.
- Zamień miejsce na środowisko produkcyjne z programu Cloud Explorer w programie Visual Studio lub z Azure Portal.
- Zatrzymaj lokację miejsca. To potrwa kilka sekund, aby wycofać proces w3wp.exe lokacji ze wszystkich wystąpień.
- Uaktualnij rozszerzenie witryny miejsca z witryny kudu lub Azure Portal (*App Service bloku > narzędzia deweloperskie > rozszerzenia > Update*).
- Rozpocznij pracę z miejscem. Zalecamy odwiedzanie witryny w celu jej ponownego rozgrzania.
- Zamień miejsce na środowisko produkcyjne.

## <a name="see-also"></a>Zobacz też

- [Debugowanie w Visual Studio](../debugger/index.yml)
- [Debuguj aplikacje Live ASP.NET przy użyciu Snapshot Debugger](../debugger/debug-live-azure-applications.md)
- [Debuguj zestawy skalowania maszyn wirtualnych ASP.NET platformy Azure na żywo przy użyciu Snapshot Debugger](../debugger/debug-live-azure-virtual-machines.md)
- [Debuguj Live ASP.NET Azure Kubernetes przy użyciu Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md)
- [Debugowanie migawek — często zadawane pytania](../debugger/debug-live-azure-apps-faq.md)
