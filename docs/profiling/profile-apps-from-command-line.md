---
title: Mierzenie wydajności z wiersza polecenia
description: Zmierz wydajność procesora CPU i użycie pamięci zarządzanej w aplikacji z wiersza polecenia.
ms.custom: ''
ms.date: 02/21/2020
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, command-line
- Diagnostics Tools, command-line
- CPU Usage, command-line
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: c109e2ae1db28f8e08ed7c34a7ee0871a6efe670
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2020
ms.locfileid: "77558120"
---
# <a name="measure-application-performance-from-the-command-line"></a>Mierzenie wydajności aplikacji z poziomu wiersza polecenia

Informacje o wydajności aplikacji można zbierać przy użyciu narzędzi wiersza polecenia.

W przykładzie opisanym w tym artykule zbierasz informacje o wydajności dla Notatnika firmy Microsoft, ale ta sama metoda może służyć do profilowania dowolnego procesu.

## <a name="prerequisites"></a>Wymagania wstępne

* Visual Studio 2019 w wersji zapoznawczej 3 lub nowszej

* Znajomość narzędzi wiersza polecenia

## <a name="collect-performance-data"></a>Zbieranie danych wydajności

Profilowanie przy użyciu narzędzi interfejsu wiersza polecenia programu Visual Studio Diagnostics działa przez dołączenie narzędzia profilowania wraz z jednym z agentów modułu zbierającego do procesu. Po dołączeniu narzędzia profilowania rozpocznie się sesja diagnostyczna, która przechwytuje i przechowuje dane profilowania do momentu zatrzymania narzędzia. w tym momencie dane są eksportowane do pliku *. diagsession* . Następnie możesz otworzyć ten plik w programie Visual Studio, aby analizować wyniki.

1. Uruchom Notatnik, a następnie otwórz Menedżera zadań, aby uzyskać identyfikator procesu (PID). W Menedżerze zadań Znajdź identyfikator PID na karcie **szczegóły** .

1. Otwórz wiersz polecenia i przejdź do katalogu przy użyciu pliku wykonywalnego agenta kolekcji, zwykle w tym miejscu.

   ```<Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\```

1. Uruchom *VSDiagnostics. exe* , wpisując następujące polecenie.

   ```cmd
   VSDiagnostics.exe start <id> /attach:<pid> /loadConfig:<configFile>
   ```

   Argumenty, które muszą być dołączone:

   * *identyfikator*\<> identyfikuje sesję kolekcji. Identyfikator musi być liczbą z zakresu od 1-255 do.
   * \<*Identyfikator pid*>, Identyfikator PID procesu, który chcesz profilować, w tym przypadku Identyfikator PID znaleziony w kroku 1
   * \<*configFile*>, plik konfiguracyjny dla agenta kolekcji, który chcesz uruchomić. Aby uzyskać więcej informacji, zobacz [pliki konfiguracji dla agentów](#config_file).

1. Zmień rozmiar Notatnika lub wpisz coś w nim, aby upewnić się, że zbierane są pewne interesujące informacje profilowania.

1. Zatrzymaj sesję zbierania i wysyłaj dane wyjściowe do pliku, wpisując następujące polecenie.

   ```cmd
   VSDiagnostics.exe stop <id> /output:<path to file>
   ```

1. Przejdź do pliku wyjściowego z poprzedniego polecenia i otwórz go w programie Visual Studio, aby przejrzeć zebrane informacje.

## <a name="config_file"></a>Pliki konfiguracji agenta

Agenci kolekcji są składnikami, które zbierają różne typy danych w zależności od tego, co próbujesz zmierzyć.

Dla wygody można przechowywać te informacje w pliku konfiguracji agenta. Plik konfiguracji to plik *JSON* , który zawiera co najmniej nazwę pliku *. dll* i jego identyfikator CLSID com. Poniżej przedstawiono przykładowe pliki konfiguracyjne, które można znaleźć w następującym folderze:

```<Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\AgentConfigs\```

* Konfiguracje CpuUsage (podstawowa/wysoka/niska), które odnoszą się do danych zbieranych dla narzędzia profilowania [użycia procesora CPU](../profiling/cpu-usage.md) .
* Konfiguracje DotNetObjectAlloc (podstawowa/niska), które odnoszą się do danych zbieranych dla [Narzędzia alokacji obiektów platformy .NET](../profiling/dotnet-alloc-tool.md).

Konfiguracje Base/niska/wysoka odnoszą się do częstotliwości próbkowania. Na przykład niska jest 100 próbek/s i wysoka to 4000 próbek/sekundę.

Aby narzędzie *VSDiagnostics. exe* działało z agentem kolekcji, wymaga zarówno biblioteki DLL, jak i identyfikatora CLSID dla odpowiedniego agenta, a agent może również mieć dodatkowe opcje konfiguracji. Jeśli używasz agenta bez pliku konfiguracji, użyj formatu w poniższym poleceniu.

```cmd
VSDiagnostics.exe start <id> /attach:<pid> /loadAgent:<agentCLSID>;<agentName>[;<config>]
```

## <a name="permissions"></a>Uprawnienia

Aby profilować aplikację, która wymaga podwyższonego poziomu uprawnień, należy to zrobić z poziomu wiersza polecenia z podwyższonymi uprawnieniami.
