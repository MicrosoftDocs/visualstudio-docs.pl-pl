---
title: Mierzenie wydajności z poziomu wiersza polecenia
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
ms.openlocfilehash: 6de4291d08b3a6b6897b3ae41562f70fad5372b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "89053432"
---
# <a name="measure-application-performance-from-the-command-line"></a>Mierzenie wydajności aplikacji z poziomu wiersza polecenia

Informacje o wydajności aplikacji można zbierać przy użyciu narzędzi wiersza polecenia.

W przykładzie opisanym w tym artykule zbierasz informacje o wydajności dla Notatnika firmy Microsoft, ale ta sama metoda może służyć do profilowania dowolnego procesu.

## <a name="prerequisites"></a>Wymagania wstępne

* Program Visual Studio 2019 lub nowszy

* Znajomość narzędzi wiersza polecenia

* Aby zebrać informacje o wydajności na komputerze zdalnym bez zainstalowanego programu Visual Studio, zainstaluj [Narzędzia do oceny wydajności dla programu Visual Studio](https://visualstudio.microsoft.com/downloads#remote-tools-for-visual-studio-2019) na maszynie zdalnej. Wersja narzędzi musi być zgodna z wersją programu Visual Studio.

## <a name="collect-performance-data"></a>Zbieranie danych wydajności

Profilowanie przy użyciu narzędzi interfejsu wiersza polecenia programu Visual Studio Diagnostics działa przez dołączenie narzędzia profilowania wraz z jednym z agentów modułu zbierającego do procesu. Po dołączeniu narzędzia profilowania rozpocznie się sesja diagnostyczna, która przechwytuje i przechowuje dane profilowania do momentu zatrzymania narzędzia. w tym momencie dane są eksportowane do pliku *. diagsession* . Następnie możesz otworzyć ten plik w programie Visual Studio, aby analizować wyniki.

1. Uruchom Notatnik, a następnie otwórz Menedżera zadań, aby uzyskać identyfikator procesu (PID). W Menedżerze zadań Znajdź identyfikator PID na karcie **szczegóły** .

1. Otwórz wiersz polecenia i przejdź do katalogu przy użyciu pliku wykonywalnego agenta kolekcji, zwykle w tym miejscu (dla Visual Studio Enterprise).

   ```<Visual Studio installation folder>\2019\Enterprise\Team Tools\DiagnosticsHub\Collector\```

1. Rozpocznij *VSDiagnostics.exe* , wpisując następujące polecenie.

   ```cmd
   VSDiagnostics.exe start <id> /attach:<pid> /loadConfig:<configFile>
   ```

   Argumenty, które muszą być dołączone:

   * \<*id*> Identyfikuje sesję zbierania danych. Identyfikator musi być liczbą z zakresu od 1-255 do.
   * \<*pid*>, Identyfikator PID procesu, który chcesz profilować, w tym przypadku Identyfikator PID znaleziony w kroku 1.
   * \<*configFile*>, plik konfiguracyjny agenta kolekcji, który chcesz uruchomić. Aby uzyskać więcej informacji, zobacz [pliki konfiguracji dla agentów](#config_file).

   Na przykład można użyć następującego polecenia dla agenta CPUUsageBase, zastępując *Identyfikator PID* opisany wcześniej.

   ```cmd
   VSDiagnostics.exe start 1 /attach:<pid> /loadConfig:AgentConfigs\CPUUsageLow.json
   ```

1. Zmień rozmiar Notatnika lub wpisz coś w nim, aby upewnić się, że zbierane są pewne interesujące informacje profilowania.

1. Zatrzymaj sesję zbierania i wysyłaj dane wyjściowe do pliku, wpisując następujące polecenie.

   ```cmd
   VSDiagnostics.exe stop <id> /output:<path to file>
   ```

1. Znajdź plik *. diagsession* danych wyjściowych z poprzedniego polecenia i otwórz go w programie Visual Studio (**File**  >  **Otwórz**plik), aby przejrzeć zebrane informacje.

   Aby przeanalizować wyniki, zapoznaj się z dokumentacją odpowiedniego narzędzia do oceny wydajności. Może to być na przykład [użycie procesora CPU](../profiling/cpu-usage.md), [Narzędzie alokacji obiektów platformy .NET](../profiling/dotnet-alloc-tool.md)lub narzędzie [bazy danych](../profiling/analyze-database.md) .

## <a name="agent-configuration-files"></a><a name="config_file"></a> Pliki konfiguracji agenta

Agenci kolekcji są składnikami, które zbierają różne typy danych w zależności od tego, co próbujesz zmierzyć.

Dla wygody można przechowywać te informacje w pliku konfiguracji agenta. Plik konfiguracji to plik *JSON* , który zawiera co najmniej nazwę pliku *. dll* i jego identyfikator CLSID com. Poniżej przedstawiono przykładowe pliki konfiguracyjne, które można znaleźć w następującym folderze:

```<Visual Studio installation folder>Team Tools\DiagnosticsHub\Collector\AgentConfigs\```

Aby pobrać i wyświetlić pliki konfiguracji agentów, zobacz następujące linki:

- https://aka.ms/vs/diaghub/agentconfig/cpubase
- https://aka.ms/vs/diaghub/agentconfig/cpuhigh
- https://aka.ms/vs/diaghub/agentconfig/cpulow
- https://aka.ms/vs/diaghub/agentconfig/database
- https://aka.ms/vs/diaghub/agentconfig/dotnetasyncbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetallocbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetalloclow
- https://aka.ms/vs/diaghub/agentconfig/dotnetcountersbase

Konfiguracje CpuUsage (podstawowa/wysoka/niska) odpowiadają danym zebranym dla narzędzia profilowania [użycia procesora CPU](../profiling/cpu-usage.md) .
Konfiguracje DotNetObjectAlloc (podstawowa/niska) odpowiadają danym zebranym dla [Narzędzia alokacji obiektów platformy .NET](../profiling/dotnet-alloc-tool.md).

Konfiguracje Base/niska/wysoka odnoszą się do częstotliwości próbkowania. Na przykład niska jest 100 próbek/s i wysoka to 4000 próbek/sekundę.

Aby narzędzie *VSDiagnostics.exe* działało z agentem kolekcji, wymaga zarówno biblioteki DLL, jak i identyfikatora CLSID dla odpowiedniego agenta, a agent może również mieć dodatkowe opcje konfiguracji. Jeśli używasz agenta bez pliku konfiguracji, użyj formatu w poniższym poleceniu.

```cmd
VSDiagnostics.exe start <id> /attach:<pid> /loadAgent:<agentCLSID>;<agentName>[;<config>]
```

## <a name="permissions"></a>Uprawnienia

Aby profilować aplikację, która wymaga podwyższonego poziomu uprawnień, należy to zrobić z poziomu wiersza polecenia z podwyższonymi uprawnieniami.
