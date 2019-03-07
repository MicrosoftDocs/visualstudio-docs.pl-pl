---
title: Rozwiązywanie problemów z debugowaniem migawki | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 11/07/2018
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9e2213c1e573efa1811d3b578c3d7bd92f1b77f2
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526424"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Rozwiązywanie problemów i znane problemy dotyczące debugowania migawek w programie Visual Studio

Jeśli kroki opisane w tym artykule nie rozwiązują problemu, skontaktuj się z snaphelp@microsoft.com.

## <a name="issue-snappoint-does-not-turn-on"></a>Problem: Punkt przyciągania jest wyłączone

Jeśli widoczna jest ikona ostrzeżenia ![ikona ostrzeżenia punktu przyciągania](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "ikona ostrzeżenia punktu przyciągania") przy użyciu punktu przyciągania zamiast ikony regularne punktu przyciągania następnie punktu przyciągania nie jest włączona.

![Punkt przyciągania nie włączać](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "punktu przyciągania jest wyłączone")

Wykonaj następujące czynności:

1. Upewnij się, że mają tę samą wersję kodu źródłowego, który został użyty do tworzenia i wdrażania usługi app.isua1. Upewnij się, że są ładowane poprawne symbole dla danego wdrożenia. Aby to zrobić, należy wyświetlić **modułów** okno podczas debugowania migawki i sprawdź kolumna plik symboli zawiera plik .pdb załadowanych modułów, debugowania. Rozszerzenie Snapshot Debugger podejmie próbę automatycznego pobrania i zastosowania symbole dla danego wdrożenia.

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
  - Azure Virtual Machines (i zestawu skalowania maszyn wirtualnych) — aplikacji ASP.NET uruchomionych w .NET Framework 4.6.1 lub nowszej.
  - Azure maszyn wirtualnych (i zestawu skalowania maszyn wirtualnych) - platformy ASP.NET Core aplikacji uruchomionych na zestaw .NET Core 2.0 lub nowszych na Windows.
  - Usługi platformy Azure Kubernetes — aplikacje platformy ASP.NET Core uruchomionej na platformy .NET Core 2.2 lub później na Debian 9.
  - Usługi platformy Azure Kubernetes — aplikacje platformy ASP.NET Core uruchomionej na platformy .NET Core 2.2 lub później na Alpine 3.8.
  - Usługi platformy Azure Kubernetes — aplikacje platformy ASP.NET Core uruchomionej na platformy .NET Core 2.2 lub później na Ubuntu 18.04.
::: moniker-end

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problem: Można wyświetlić tylko ograniczona migawek w narzędziach diagnostycznych

![Punkt przyciągania ograniczona](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "punkt przyciągania z ograniczoną przepływnością")

Wykonaj następujące czynności:

- Migawki zajmują mało pamięci, ale charakteryzują się opłaty zatwierdzenia. Jeśli rozszerzenie Snapshot Debugger wykryje, że usługi na serwerze występuje duże obciążenie pamięci duże, nie będzie wykonywać migawek. Możesz usunąć migawki już przechwycony przez zatrzymanie sesji rozszerzenia Snapshot Debugger i podjęcie ponownej próby.

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