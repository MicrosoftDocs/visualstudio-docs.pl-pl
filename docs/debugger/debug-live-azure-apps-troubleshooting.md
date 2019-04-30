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
ms.openlocfilehash: e7a04d5761d7b67c58dc71b185e6d5db0b80c766
ms.sourcegitcommit: f01d9cab3f9e457b365d58e2008137ce786003fa
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346879"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Rozwiązywanie problemów i znane problemy dotyczące debugowania migawek w programie Visual Studio

Jeśli kroki opisane w tym artykule nie rozwiązują problemu, należy wyszukać problemu na [społeczności deweloperów](https://developercommunity.visualstudio.com/spaces/8/index.html) lub zgłosić nowy problem, wybierając **pomocy** > **Prześlij opinię**   >  **Zgłoś Problem** w programie Visual Studio.

## <a name="issue-attach-snapshot-debugger-encounters-an-http-status-code-error"></a>Problem: "Dołączanie rozszerzenia Snapshot Debugger" wystąpi błąd kodu stanu HTTP

Jeśli zostanie wyświetlony następujący błąd w **dane wyjściowe** okna podczas próby dołączenia, może być to znany problem wymienione poniżej. Spróbuj proponowanych rozwiązań, a jeśli problem pozostaje nierozwiązany skontaktuj się z poprzednim alias.

`[TIMESTAMP] Error --- Unable to Start Snapshot Debugger - Attach Snapshot Debugger failed: System.Net.WebException: The remote server returned an error: (###) XXXXXX`

### <a name="401-unauthorized"></a>(401) nieautoryzowane

Ten błąd wskazuje, czy wywołania REST wystawiony przez program Visual Studio do platformy Azure wykorzystuje poświadczenia są nieprawidłowe. To znana usterka. za pomocą modułu Azure Active Directory łatwe OAuth mogą dawać tego błędu.

Wykonaj następujące czynności:

* Upewnij się, że konta personalizacji programu Visual Studio ma uprawnienia do subskrypcji platformy Azure i zasobów, który jest podłączany do. Szybko określić, to jest sprawdzenie, czy zasób jest dostępny w oknie dialogowym z **debugowania** > **dołączyć rozszerzenie Snapshot Debugger...**   >  **Zasobów platformy azure** > **wybierz istniejący**, lub w programie Cloud Explorer.
* Jeśli ten błąd nie ustąpi, użyj jednej z kanałami przesyłania opinii, opisano na początku tego artykułu.

### <a name="403-forbidden"></a>Zabronione (403)

Ten błąd wskazuje, że odmówiono udzielenia uprawnienia. Może to być spowodowane przez wiele różnych problemów.

Wykonaj następujące czynności:

* Sprawdź, czy Twoje konto programu Visual Studio ma prawidłową subskrypcję platformy Azure z odpowiednimi uprawnieniami kontroli dostępu opartej na rolach (RBAC) dla zasobu. Dla usługi App Service, sprawdź, czy uprawnienia do [zapytania](https://docs.microsoft.com/rest/api/appservice/appserviceplans/get) planu usługi App Service hostującego twoją aplikację.
* Sprawdź, czy sygnatury czasowej na komputerze klienckim jest prawidłowe i aktualne. Serwery z sygnaturami czasowymi wyłączona przez więcej niż 15 minut sygnatura czasowa żądania zazwyczaj generują ten błąd.
* Jeśli ten błąd nie ustąpi, użyj jednej z kanałami przesyłania opinii, opisano na początku tego artykułu.

### <a name="404-not-found"></a>(404) nie znaleziono

Ten błąd wskazuje, że na serwerze nie można odnaleźć witryny sieci Web.

Wykonaj następujące czynności:

* Sprawdź, czy masz wdrożenia i uruchomienia na zasób usługi App Service, które są związane z witryny sieci Web.
* Sprawdź, czy witryna jest dostępne pod adresem https://\<zasobów\>. azurewebsites.net
* Jeśli ten błąd nie ustąpi, użyj jednej z kanałami przesyłania opinii, opisano na początku tego artykułu.

### <a name="406-not-acceptable"></a>(406) nie do przyjęcia

Ten błąd wskazuje, że serwer jest w stanie odpowiadać na typ ustawiony w nagłówku Accept żądania.

Wykonaj następujące czynności:

* Sprawdź, czy witryna jest dostępne pod adresem https://\<zasobów\>. azurewebsites.net
* Sprawdź, czy witryny nie została zmigrowana do nowych wystąpień. Rozszerzenie Snapshot Debugger używa pojęcie ARRAffinity na potrzeby kierowania żądań do konkretnych wystąpień, które mogą wygenerować sporadycznie tego błędu.
* Jeśli ten błąd nie ustąpi, użyj jednej z kanałami przesyłania opinii, opisano na początku tego artykułu.

### <a name="409-conflict"></a>Konflikt (409)

Ten błąd wskazuje, czy żądanie jest w konflikcie z bieżącego stanu serwera.

Jest to znany problem, który występuje, gdy użytkownik próbuje dołączyć rozszerzenie Snapshot Debugger dla usługi App Service, która włączyła dotycząca usługi Application Insights. Dotycząca usługi Application Insights ustawia AppSettings z inną wielkością liter niż program Visual Studio przyczyną tego problemu.

::: moniker range=">= vs-2019"
Firma Microsoft został rozwiązany w programie Visual Studio 2019 r.
::: moniker-end

Wykonaj następujące czynności:

::: moniker range="vs-2017"

* Sprawdź w witrynie Azure portal, że AppSettings dla debugera migawek (SNAPSHOTDEBUGGER_EXTENSION_VERSION) i InstrumentationEngine (INSTRUMENTATIONENGINE_EXTENSION_VERSION) są wielkie litery. Jeśli nie, zaktualizuj ustawienia ręcznie, która wymusza ponowne uruchomienie witryny.
::: moniker-end
* Jeśli ten błąd nie ustąpi, użyj jednej z kanałami przesyłania opinii, opisano na początku tego artykułu.

### <a name="500-internal-server-error"></a>(500) wewnętrzny błąd serwera

Ten błąd wskazuje, że witryna jest całkowicie w dół lub serwer nie może obsłużyć żądania. Snapshot Debugger tylko funkcje na uruchamianie aplikacji. [Application Insights Snapshot Debugger](https://docs.microsoft.com/azure/azure-monitor/app/snapshot-debugger) zapewnia tworzenia migawek przy wyjątkach i może być najlepszym narzędziem do Twoich potrzeb.

### <a name="502-bad-gateway"></a>(502): Nieprawidłowa brama

Ten błąd wskazuje na problem z siecią po stronie serwera i mogą być tymczasowe.

Wykonaj następujące czynności:

* Należy poczekać kilka minut przed ponownie dołączanie rozszerzenia Snapshot Debugger.
* Jeśli ten błąd nie ustąpi, użyj jednej z kanałami przesyłania opinii, opisano na początku tego artykułu.

## <a name="issue-snappoint-does-not-turn-on"></a>Problem: Punkt przyciągania jest wyłączone

Jeśli widoczna jest ikona ostrzeżenia ![ikona ostrzeżenia punktu przyciągania](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "ikona ostrzeżenia punktu przyciągania") przy użyciu punktu przyciągania zamiast ikony regularne punktu przyciągania następnie punktu przyciągania nie jest włączona.

![Punkt przyciągania nie włączać](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "punktu przyciągania jest wyłączone")

Wykonaj następujące czynności:

1. Upewnij się, że mają tę samą wersję kodu źródłowego, który został użyty do tworzenia i wdrażania aplikacji. Upewnij się, że są ładowane poprawne symbole dla danego wdrożenia. Aby to zrobić, należy wyświetlić **modułów** okno podczas debugowania migawki i sprawdź kolumna plik symboli zawiera plik .pdb załadowanych modułów, debugowania. Rozszerzenie Snapshot Debugger podejmie próbę automatycznego pobrania i zastosowania symbole dla danego wdrożenia.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problem: Symbole nie są ładowane podczas otwierania migawki

Jeśli zostanie wyświetlone następujące okno, symboli nie został załadowany.

![Symbole nie są ładowane](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "symbole nie są ładowane.")

Wykonaj następujące czynności:

- Kliknij przycisk **Zmień ustawienia symboli...** Połącz na tej stronie. W **debugowanie > Symbol** ustawienia, Dodaj katalog pamięci podręcznej symboli. Uruchom ponownie debugowanie migawki po ustawieniu ścieżki symboli.

   Symbole lub pliki .pdb, dostępne w projekcie musi odpowiadać wdrożenia usługi App Service. Większości wdrożeń (wdrożenia za pomocą programu Visual Studio, ciągłej integracji/ciągłego wdrażania za pomocą potoków usługi Azure lub programu Kudu, itp.) będzie publikować swoje pliki symboli, wzdłuż do usługi App Service. Ustawianie katalogu pamięci podręcznej symboli umożliwia środowisku Visual Studio za pomocą tych symboli.

   ![Ustawienia symboli](../debugger/media/snapshot-troubleshooting-symbol-settings.png "ustawienia symboli")

- Również jeśli Twoja organizacja korzysta z serwera symboli lub porzuca symbole w inną ścieżkę, aby załadować symbole prawidłowy dla danego wdrożenia należy użyć ustawienia symboli.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problem: Nie widzę opcji "Dołączanie rozszerzenia Snapshot Debugger" w Eksploratorze chmury

Wykonaj następujące czynności:

- Upewnij się, że jest zainstalowany składnik rozszerzenia Snapshot Debugger. Otwórz Instalatora programu Visual Studio i sprawdź **rozszerzenia Snapshot Debugger** składnik pakietu roboczego platformy Azure.
::: moniker range="< vs-2019"
- Upewnij się, że Twoja aplikacja jest obsługiwana. Obecnie tylko ASP.NET (4.6.1+) i aplikacji platformy ASP.NET Core (w wersji 2.0 i nowsze) wdrożonych w usłudze Azure App Services są obsługiwane.
::: moniker-end
::: moniker range=">= vs-2019"
- Upewnij się, że Twoja aplikacja jest obsługiwana:
  - Usługi aplikacji Azure — aplikacji ASP.NET uruchomionych w programie .NET Framework 4.6.1 lub nowszej.
  - Usługa Azure App Services — aplikacje platformy ASP.NET Core uruchomiony w programie .NET Core 2.0 lub nowszych na Windows.
  - Usługa Azure Virtual Machines (i zestawu skalowania maszyn wirtualnych) - aplikacji ASP.NET uruchomionych w programie .NET Framework 4.6.1 lub nowszej.
  - Usługa Azure Virtual Machines (i zestawu skalowania maszyn wirtualnych) — aplikacje platformy ASP.NET Core uruchomiony w programie .NET Core 2.0 lub nowszych na Windows.
  - Usługi platformy Azure Kubernetes — aplikacje platformy ASP.NET Core uruchomionej na platformy .NET Core 2.2 lub później na Debian 9.
  - Usługi platformy Azure Kubernetes — aplikacje platformy ASP.NET Core uruchomionej na platformy .NET Core 2.2 lub później na Alpine 3.8.
  - Usługi platformy Azure Kubernetes — aplikacje platformy ASP.NET Core uruchomionej na platformy .NET Core 2.2 lub później na Ubuntu 18.04.
::: moniker-end

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problem: Można wyświetlić tylko ograniczona migawek w narzędziach diagnostycznych

![Punkt przyciągania ograniczona](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "punkt przyciągania z ograniczoną przepływnością")

Wykonaj następujące czynności:

- Migawki zajmują mało pamięci, ale charakteryzują się opłaty zatwierdzenia. Jeśli rozszerzenie Snapshot Debugger wykryje, że usługi na serwerze występuje duże obciążenie pamięci duże, nie będzie wykonywać migawek. Możesz usunąć migawki już przechwycony przez zatrzymanie sesji rozszerzenia Snapshot Debugger i podjęcie ponownej próby.

::: moniker range=">= vs-2019"
## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>Problem: Debugowanie migawki z wieloma wersjami programu Visual Studio pozwala mi błędy

2019 usługi Visual Studio wymaga nowszej wersji rozszerzenie witryny Snapshot Debugger w usłudze Azure App Service.  Ta wersja nie jest zgodny ze starszą wersją programu rozszerzenie witryny Snapshot Debugger, które są używane przez program Visual Studio 2017.  Jeśli próbujesz dołączyć rozszerzenie Snapshot Debugger w Visual Studio 2019 r do usługi Azure App Service, w którym ma zostały wcześniej debugowane debugera migawki programu Visual Studio 2017, zostanie wyświetlony następujący błąd:

![Niezgodne rozszerzenie witryny Snapshot Debugger Visual Studio 2019](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "rozszerzenie witryny niezgodne rozszerzenia Snapshot Debugger Visual Studio 2019 r.")

Z drugiej strony Jeśli używasz programu Visual Studio 2017 można dołączyć rozszerzenie Snapshot Debugger do usługi Azure App Service, w którym ma zostały wcześniej debugowane debugera migawki w programie Visual Studio 2019 r, zostanie wyświetlony następujący błąd:

![Niezgodne rozszerzenie witryny Snapshot Debugger programu Visual Studio 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "rozszerzenie witryny niezgodne rozszerzenia Snapshot Debugger programu Visual Studio 2017")

Aby rozwiązać ten problem, Usuń następujące ustawienia aplikacji w witrynie Azure portal i ponownie dołączyć rozszerzenie Snapshot Debugger:

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION
::: moniker-end

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>Problem: Występują problemy z debugowania migawek i trzeba włączyć rejestrowanie większej ilości

### <a name="enable-agent-logs"></a>Włączanie dzienników agenta

Aby włączyć lub wyłączyć agenta rejestrowania Otwórz program Visual Studio przejdź do *Narzędzia > Opcje > rozszerzenia Snapshot Debugger > agent Włącz rejestrowanie*. Należy pamiętać, jeśli *usuwania starego agenta loguje rozpoczęcia sesji* jest również włączone, każdy pomyślne programu Visual Studio dołączyć będzie usunąć poprzednie dzienniki agenta.

Dzienniki agenta można znaleźć w następujących lokalizacjach:

- App Services:
  - Przejdź do witryny Kudu usługi App Service (czyli yourappservice. **Menedżer sterowania usługami**. azurewebsites.net) i przejdź do konsoli debugowania.
  - Dzienniki agenta są przechowywane w następującym katalogu:  D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\
- VM/VMSS:
  - Zaloguj się do maszyny Wirtualnej agenta, dzienniki są przechowywane w następujący sposób:  C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics\<Version>\SnapshotDebuggerAgent_*.txt
- AKS
  - Przejdź do następującego katalogu: / tmp/diag/AgentLogs / *

### <a name="enable-profilerinstrumentation-logs"></a>Włączanie dzienników Profiler/Instrumentacji

Dzienniki Instrumentacji można znaleźć w następujących lokalizacjach:

- App Services:
  - Rejestrowanie błędów jest automatycznie przesyłany do D:\Home\LogFiles\eventlog.xml, są oznaczone zdarzenia << nazwa dostawcy = "Instrumentacji aparatu" / / >> lub "Produkcyjne punkty przerwania"
- VM/VMSS:
  - Zaloguj się do maszyny Wirtualnej, a następnie otwórz Podgląd zdarzeń.
  - Otwórz następujący widok: *Dzienniki Windows > Aplikacja*.
  - *Filtruj bieżący dziennik* przez *źródła zdarzeń* za pomocą *punktów przerwania w środowisku produkcyjnym* lub *aparatu Instrumentacji*.
- AKS
  - Instrumentacja aparatu rejestrowania na /tmp/diag/log.txt (ustawiana MicrosoftInstrumentationEngine_FileLogPath w pliku DockerFile)
  - Rejestrowanie ProductionBreakpoint na /tmp/diag/shLog.txt

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

- [Debugowanie w programie Visual Studio](../debugger/index.md)
- [Debugowanie na żywo aplikacji ASP.NET, przy użyciu rozszerzenia Snapshot Debugger](../debugger/debug-live-azure-applications.md)
- [Debugowanie na żywo ASP.NET Azure wirtualnego Machines\Virtual maszyn Scale Sets przy użyciu rozszerzenia Snapshot Debugger](../debugger/debug-live-azure-virtual-machines.md)
- [Debugowanie na żywo ASP.NET Azure Kubernetes za pomocą rozszerzenia Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md)
- [Debugowanie migawek — często zadawane pytania](../debugger/debug-live-azure-apps-faq.md)
