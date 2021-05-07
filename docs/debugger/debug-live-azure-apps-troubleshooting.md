---
title: Rozwiązywanie problemów z debugowaniem migawek | Microsoft Docs
description: Informacje na temat rozwiązywania problemów i znanych problemów dotyczących debugowania migawek w Visual Studio. Załaduj obiekt ICorProfiler bez powodowania przestoju w lokacji produkcyjnej.
ms.custom: SEO-VS-2020
ms.date: 04/24/2019
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: aad883ac0c3f703b2d6a4e10d3a0ef2468cd8465
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798443"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Rozwiązywanie problemów i znane problemy dotyczące debugowania migawek w Visual Studio

Jeśli kroki opisane w tym artykule nie rozwiążą problemu, wyszukaj problem w Developer Community lub zgłoś nowy problem, wybierając opcję Pomoc w wysyłaniu opinii Zgłoś problem w [](https://aka.ms/feedback/suggest?space=8)  >    >   Visual Studio.

## <a name="issue-attach-snapshot-debugger-encounters-an-http-status-code-error"></a>Problem: "Dołącz Snapshot Debugger" napotyka błąd kodu stanu HTTP

Jeśli podczas próby dołączenia  zostanie wyświetlony następujący błąd w oknie Dane wyjściowe, może to być znany problem wymieniony poniżej. Wypróbuj proponowane rozwiązania i jeśli problem będzie nadal występował, skontaktuj się z poprzednim aliasem.

`[TIMESTAMP] Error --- Unable to Start Snapshot Debugger - Attach Snapshot Debugger failed: System.Net.WebException: The remote server returned an error: (###) XXXXXX`

### <a name="401-unauthorized"></a>(401) Brak autoryzacji

Ten błąd wskazuje, że wywołanie REST wystawione przez Visual Studio do platformy Azure używa nieprawidłowych poświadczeń. 

Należy wykonać następujące czynności:

* Upewnij się, że Visual Studio personalizacji ma uprawnienia do subskrypcji platformy Azure i zasobu, do których się dołączasz. Szybkim sposobem ustalenia tego jest sprawdzenie, czy zasób jest dostępny w oknie dialogowym z  >  **debugowania dołączania Snapshot Debugger...**  >  **Zasób platformy Azure**  >  **Wybierz pozycję Istniejący** lub w Eksploratorze chmury.
* Jeśli ten błąd będzie się powtarzać, użyj jednego z kanałów opinii opisanych na początku tego artykułu.

Jeśli włączono uwierzytelnianie/autoryzację (EasyAuth) na komputerze App Service, w komunikacie o błędzie stosu wywołań może wystąpić błąd 401 z komunikatem o błędzie LaunchAgentAsync. Upewnij  się, że ustawienie Akcja do podjęcia, gdy żądanie nie jest uwierzytelnione, ma wartość Zezwalaj na żądania anonimowe **(bez akcji)** w witrynie Azure Portal i podaj adres authorization.jsw folderze D:\Home\sites\wwwroot z następującą zawartością. 

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

Pierwsza trasa skutecznie zabezpiecza domenę aplikacji podobnie jak logowanie **za pomocą [IdentityProvider]**. Druga trasa uwidacznia punkt końcowy SnapshotDebugger AgentLaunch poza uwierzytelnianiem, który wykonuje wstępnie  zdefiniowaną akcję uruchamiania agenta diagnostycznego SnapshotDebugger tylko wtedy, gdy dla usługi App Service jest włączone wstępnie zainstalowane rozszerzenie lokacji SnapshotDebugger. Aby uzyskać więcej informacji na temat authorization.jskonfiguracji, zobacz Reguły [autoryzacji adresów URL.](https://azure.github.io/AppService/2016/11/17/URL-Authorization-Rules.html)

### <a name="403-forbidden"></a>(403) Zabronione

Ten błąd wskazuje, że odmówiono uprawnień. Może to być spowodowane wieloma różnymi problemami.

Należy wykonać następujące czynności:

* Sprawdź, Visual Studio konto ma prawidłową subskrypcję platformy Azure z wymaganymi Role-Based Access Control (RBAC) dla zasobu. W przypadku usługi AppService sprawdź, czy masz uprawnienia do [wykonywania](/rest/api/appservice/appserviceplans/get) zapytań App Service planie hostującym aplikację.
* Sprawdź, czy sygnatura czasowa maszyny klienckiej jest poprawna i aktualne. Serwery ze znacznikami czasu wyłączonymi przez więcej niż 15 minut znacznika czasu żądania zwykle tworzyć ten błąd.
* Jeśli ten błąd będzie się powtarzać, użyj jednego z kanałów opinii opisanych na początku tego artykułu.

### <a name="404-not-found"></a>(404) Nie znaleziono

Ten błąd wskazuje, że nie można odnaleźć witryny internetowej na serwerze.

Należy wykonać następujące czynności:

* Sprawdź, czy witryna internetowa jest wdrożona i uruchomiona w App Service zasobów, do których się dołączasz.
* Sprawdź, czy witryna jest dostępna na stronie https:// \<resource\> .azurewebsites.net
* Sprawdź, czy prawidłowo uruchomiona niestandardowa aplikacja internetowa nie zwraca kodu stanu 404 w przypadku dostępu do witryny https:// \<resource\> .azurewebsites.net
* Jeśli ten błąd będzie się powtarzać, użyj jednego z kanałów opinii opisanych na początku tego artykułu.

### <a name="406-not-acceptable"></a>(406) Nie do przyjęcia

Ten błąd wskazuje, że serwer nie może odpowiedzieć na typ ustawiony w nagłówku Accept żądania.

Należy wykonać następujące czynności:

* Sprawdź, czy witryna jest dostępna na stronie https:// \<resource\> .azurewebsites.net
* Sprawdź, czy lokacja nie została zmigrowana do nowych wystąpień. Snapshot Debugger używa pojmowania koligacji ARRAffinity do kierowania żądań do określonych wystąpień, co może powodować ten błąd sporadycznie.
* Jeśli ten błąd będzie się powtarzać, użyj jednego z kanałów opinii opisanych na początku tego artykułu.

### <a name="409-conflict"></a>(409) Konflikt

Ten błąd wskazuje, że żądanie powoduje konflikt z bieżącym stanem serwera.

Jest to znany problem, który występuje, gdy użytkownik próbuje dołączyć Snapshot Debugger do usługi AppService, która włączyła usługę ApplicationInsights. Program ApplicationInsights ustawia ustawienia AppSettings z inną wielkością Visual Studio, co powoduje ten problem.

::: moniker range=">= vs-2019"
Rozwiązaliśmy ten problem w Visual Studio 2019 r.
::: moniker-end

Należy wykonać następujące czynności:

::: moniker range="vs-2017"

* Sprawdź w Azure Portal, czy ustawienia AppSettings dla snapshotDebugger (SNAPSHOTDEBUGGER_EXTENSION_VERSION) i InstrumentationEngine (INSTRUMENTATIONENGINE_EXTENSION_VERSION) są wielkie. Jeśli nie, zaktualizuj ustawienia ręcznie, co wymusza ponowne uruchomienie lokacji.
::: moniker-end
* Jeśli ten błąd będzie się powtarzać, użyj jednego z kanałów opinii opisanych na początku tego artykułu.

### <a name="500-internal-server-error"></a>(500) Wewnętrzny błąd serwera

Ten błąd wskazuje, że lokacja jest całkowicie niesłużąca lub serwer nie może obsłużyć żądania. Snapshot Debugger działa tylko na uruchomionych aplikacjach. [Application Insights Snapshot Debugger](/azure/azure-monitor/app/snapshot-debugger) udostępnia migawki wyjątków i może być najlepszym narzędziem do twoich potrzeb.

### <a name="502-bad-gateway"></a>(502) Zła brama

Ten błąd wskazuje na problem z siecią po stronie serwera i może być tymczasowy.

Należy wykonać następujące czynności:

* Spróbuj poczekać kilka minut przed dołączeniu Snapshot Debugger ponownie.
* Jeśli ten błąd będzie się powtarzać, użyj jednego z kanałów opinii opisanych na początku tego artykułu.

## <a name="issue-snappoint-does-not-turn-on"></a>Problem: Punkt przyciągania nie jest włączany

Jeśli jest wyświetlana ikona ostrzeżenia ![Ikona](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "Ikona ostrzeżenia punktu przyciągania") ostrzeżenia punktu przyciągania z punktem przyciągania zamiast ikoną zwykłego punktu przyciągania, punkt przyciągania nie jest włączony.

![Punkt przyciągania nie jest włączany](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Punkt przyciągania nie jest włączany")

Należy wykonać następujące czynności:

1. Upewnij się, że masz tę samą wersję kodu źródłowego, która została użyta do skompilowania i wdrożenia aplikacji. Upewnij się, że ładujesz poprawne symbole dla wdrożenia. Aby to zrobić, wyświetl okno **Moduły** podczas debugowania migawki i sprawdź, czy w kolumnie Plik symboli jest załadowany plik .pdb dla debugego modułu. Program Snapshot Debugger automatycznie pobrać i używać symboli dla wdrożenia.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problem: Symbole nie są ładowane po otwarciu migawki

Jeśli zobaczysz następujące okno, symbole nie zostały załadowane.

![Symbole nie są ładowane](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "Symbole nie są ładowane")

Należy wykonać następujące czynności:

- Kliknij pozycję **Zmień ustawienia symboli...** na tej stronie. W **ustawieniach > symbolu** dodaj katalog pamięci podręcznej symboli. Uruchom ponownie debugowanie migawek po skonfigurowaniu ścieżki symboli.

   Symbole lub pliki .pdb dostępne w projekcie muszą być zgodne z App Service wdrożenia. Większość wdrożeń (wdrażanie za pośrednictwem Visual Studio, CI/CD z Azure Pipelines lub Kudu itp.) będzie publikować pliki symboli wraz z App Service. Ustawienie katalogu pamięci podręcznej symboli Visual Studio tych symboli.

   ![Ustawienia symboli](../debugger/media/snapshot-troubleshooting-symbol-settings.png "Ustawienia symboli")

- Alternatywnie, jeśli organizacja używa serwera symboli lub porzuca symbole w innej ścieżce, użyj ustawień symboli, aby załadować poprawne symbole dla wdrożenia.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problem: Nie widzę opcji "Dołącz Snapshot Debugger" w eksploratorze chmury

Należy wykonać następujące czynności:

- Upewnij się, Snapshot Debugger zainstalowany składnik. Otwórz Instalator programu Visual Studio i sprawdź składnik **Snapshot Debugger** w obciążeniu platformy Azure.
::: moniker range="< vs-2019"
- Upewnij się, że aplikacja jest obsługiwana. Obecnie obsługiwane są ASP.NET (4.6.1+) i ASP.NET Core (2.0+) wdrożone w usłudze Azure App Services.
::: moniker-end
::: moniker range=">= vs-2019"
- Upewnij się, że aplikacja jest obsługiwana:
  - Azure App Services — ASP.NET aplikacje działające w .NET Framework 4.6.1 lub nowszej.
  - Azure App Services — ASP.NET Core działających na platformie .NET Core 2.0 lub nowszej w systemie Windows.
  - Azure Virtual Machines (i zestaw skalowania maszyn wirtualnych) — ASP.NET aplikacje działające w .NET Framework 4.6.1 lub nowszej.
  - Azure Virtual Machines (i zestaw skalowania maszyn wirtualnych) — aplikacje ASP.NET Core działające na platformie .NET Core 2.0 lub nowszej w systemie Windows.
  - Azure Kubernetes Services — ASP.NET Core działających na platformie .NET Core 2.2 lub nowszej w systemie Debian 9.
  - Azure Kubernetes Services — ASP.NET Core działających na platformie .NET Core 2.2 lub nowszej w systemie Alpine 3.8.
  - Azure Kubernetes Services — ASP.NET Core działających na platformie .NET Core 2.2 lub nowszej w systemie Ubuntu 18.04.
::: moniker-end

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problem: W chmurze widzę tylko migawki z ograniczeniami narzędzia diagnostyczne

![Punkt przyciągania z ograniczeniami](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "Punkt przyciągania z ograniczeniami")

Należy wykonać następujące czynności:

- Migawki mają małą ilość pamięci, ale są naliczane opłaty za zatwierdzenie. Jeśli Snapshot Debugger wykryje, że serwer jest pod dużym obciążeniem pamięci, nie będzie zrób migawek. Przechwycone migawki można usunąć, zatrzymując sesję Snapshot Debugger i próbując ponownie.

::: moniker range=">= vs-2019"
## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>Problem: Debugowanie migawek z wieloma wersjami Visual Studio powoduje błędy

Visual Studio 2019 wymaga nowszej wersji rozszerzenia witryny Snapshot Debugger na komputerze Azure App Service.  Ta wersja nie jest zgodna ze starszą wersją rozszerzenia Snapshot Debugger używanego przez program Visual Studio 2017.  Jeśli spróbujesz dołączyć program Snapshot Debugger w programie Visual Studio 2019 do serwera Azure App Service, który został wcześniej debugowany przez program Snapshot Debugger w programie Visual Studio 2017, wystąpi następujący błąd:

![Niezgodne Snapshot Debugger witryny Visual Studio 2019](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "Niezgodne Snapshot Debugger lokacji Visual Studio 2019")

Z kolei w przypadku dołączania Snapshot Debugger do serwera Visual Studio Azure App Service 2017, który został wcześniej debugowany przez program Snapshot Debugger w programie Visual Studio 2019, wystąpi następujący błąd:

![Niezgodne Snapshot Debugger lokacji Visual Studio 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "Niezgodne Snapshot Debugger lokacji Visual Studio 2017")

Aby rozwiązać ten problem, usuń następujące ustawienia aplikacji w Azure Portal i ponownie dołącz Snapshot Debugger aplikację:

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION
::: moniker-end

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>Problem: Mam problemy z debugowaniem migawek i muszę włączyć więcej rejestrowania

### <a name="enable-agent-logs"></a>Włączanie dzienników agenta

Aby włączyć i wyłączyć rejestrowanie agentów, otwórz Visual Studio narzędzia i>*opcje>Snapshot Debugger>Włącz rejestrowanie agenta.* Pamiętaj, *że jeśli opcja Usuń stare dzienniki agenta podczas* uruchamiania sesji jest również włączona, każde pomyślne Visual Studio dołączania spowoduje usunięcie poprzednich dzienników agenta.

Dzienniki agenta można znaleźć w następujących lokalizacjach:

- App Services:
  - Przejdź do App Service Kudu twojej aplikacji (to jest Twojausługa Aplikacji).**scm**.azurewebsites.net) i przejdź do konsoli debugowania.
  - Dzienniki agenta są przechowywane w następującym katalogu: D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\
- Vm/VMSS:
  - Zaloguj się do maszyny wirtualnej. Dzienniki agenta są przechowywane w następujący sposób: C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics \<Version> \SnapshotDebuggerAgent_*.txt
- AKS
  - Przejdź do następującego katalogu: /tmp/diag/AgentLogs/*

### <a name="enable-profilerinstrumentation-logs"></a>Włączanie dzienników profilera/instrumentacji

Dzienniki instrumentacji można znaleźć w następujących lokalizacjach:

- App Services:
  - Rejestrowanie błędów jest automatycznie wysyłane do D:\Home\LogFiles\eventlog.xml, zdarzenia są oznaczone za pomocą lub `<Provider Name="Instrumentation Engine" />` "Produkcyjne punkty przerwania"
- Vm/VMSS:
  - Zaloguj się do maszyny wirtualnej i otwórz Podgląd zdarzeń.
  - Otwórz następujący widok: *Dzienniki systemu Windows>Aplikacji*.
  - *Filtruj bieżący dziennik* *według źródła zdarzeń* przy użyciu *produkcyjnych punktów przerwania* lub aparatu *instrumentacji.*
- AKS
  - Rejestrowanie aparatu instrumentacji w pliku /tmp/diag/log.txt (ustaw MicrosoftInstrumentationEngine_FileLogPath w pliku DockerFile)
  - Rejestrowanie ProductionBreakpoint w /tmp/diag/shLog.txt

## <a name="known-issues"></a>Znane problemy

- Debugowanie migawek Visual Studio wielu klientów z tym samym App Service nie jest obecnie obsługiwane.
- Optymalizacje il Roslyn nie są w pełni obsługiwane w ASP.NET Core. W przypadku ASP.NET Core niektóre zmienne mogą nie być w stanie zobaczyć lub użyć niektórych zmiennych w instrukcjach warunkowych.
- Zmiennych specjalnych, takich jak *$FUNCTION* lub *$CALLER*, nie można oceniać w instrukcjach warunkowych ani punktach dziennika dla ASP.NET Core.
- Debugowanie migawek nie działa App Services z [włączonym buforowaniem](/azure/app-service/app-service-local-cache) lokalnym.
- Debugowanie migawek API Apps nie jest obecnie obsługiwane.

## <a name="site-extension-upgrade"></a>Uaktualnienie rozszerzenia lokacji

Debugowanie migawek i Application Insights zależą od obiektu ICorProfiler, który jest ładowany do procesu lokacji i powoduje problemy z blokowaniem plików podczas uaktualniania. Zalecamy ten proces, aby upewnić się, że lokacja produkcyjna nie zostanie przesłoniła żadnego czasu.

- Utwórz miejsce [wdrożenia w](/azure/app-service/web-sites-staged-publishing) ramach App Service i wd wdrażaj lokację w miejscu.
- Zamień miejsce na produkcyjne z programu Cloud Explorer Visual Studio lub z Azure Portal.
- Zatrzymaj witrynę miejsca. Wyłączenie procesu lokacji ze wszystkich wystąpień w3wp.exe potrwa kilka sekund.
- Uaktualnij rozszerzenie witryny miejsca z witryny Kudu lub witryny Azure Portal (*App Service Blade > Development Tools > Extensions > Update).*
- Uruchom lokację gniazda. Zalecamy odwiedzenie witryny, aby ponownie ją rozgrzać.
- Zamień miejsce na produkcyjne.

## <a name="see-also"></a>Zobacz też

- [Debugowanie w Visual Studio](../debugger/index.yml)
- [Debugowanie aplikacji ASP.NET na żywo przy użyciu Snapshot Debugger](../debugger/debug-live-azure-applications.md)
- [Debugowanie zestawów skalowania ASP.NET usługi Azure Virtual Machines\Virtual Machines przy użyciu usługi Snapshot Debugger](../debugger/debug-live-azure-virtual-machines.md)
- [Debugowanie dzienników ASP.NET azure Kubernetes przy użyciu narzędzia Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md)
- [Debugowanie migawek — często zadawane pytania](../debugger/debug-live-azure-apps-faq.yml)
