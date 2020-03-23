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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77558120"
---
# <a name="measure-application-performance-from-the-command-line"></a>Mierzenie wydajności aplikacji z wiersza polecenia

Informacje o wydajności aplikacji można zbierać za pomocą narzędzi wiersza polecenia.

W przykładzie opisanym w tym artykule można zbierać informacje o wydajności dla Microsoft Notepad, ale tej samej metody można użyć do profilowania dowolnego procesu.

## <a name="prerequisites"></a>Wymagania wstępne

* Visual Studio 2019 Wersja zapoznawcza 3 lub nowsza wersje

* Znajomość narzędzi wiersza polecenia

## <a name="collect-performance-data"></a>Zbieranie danych dotyczących wydajności

Profilowanie przy użyciu narzędzi interfejsu wiersza polecenia diagnostyki programu Visual Studio działa przez dołączenie narzędzia profilowania, wraz z jednym z agentów modułu zbierającego, do procesu. Po dołączeniu narzędzia profilowania rozpoczynasz sesję diagnostyczną, która przechwytuje i przechowuje dane profilowania, dopóki narzędzie nie zostanie zatrzymane, w którym to momencie dane są eksportowane do pliku *.diagsession.* Następnie można otworzyć ten plik w programie Visual Studio do analizy wyników.

1. Uruchom Notatnik, a następnie otwórz Menedżera zadań, aby uzyskać jego identyfikator procesu (PID). W Menedżerze zadań znajdź identyfikator PID na karcie **Szczegóły.**

1. Otwórz wiersz polecenia i zmień katalog z plikiem wykonywalnym agenta windykacji, zazwyczaj tutaj.

   ```<Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\```

1. Uruchom *program VSDiagnostics.exe,* wpisując następujące polecenie.

   ```cmd
   VSDiagnostics.exe start <id> /attach:<pid> /loadConfig:<configFile>
   ```

   Argumenty, które muszą być uwzględnione są:

   * \<*identyfikator*> identyfikuje sesję kolekcji. Identyfikator musi być liczbą w zakresie od 1 do 255.
   * \<*pid*>, PID procesu, który chcesz profilować, w tym przypadku PID, który znalazłeś w kroku 1
   * \<*configFile*>, plik konfiguracyjny dla agenta windykacyjnego, który chcesz uruchomić. Aby uzyskać więcej informacji, zobacz [Pliki konfiguracyjne dla agentów](#config_file).

1. Zmienić rozmiar Notatnika lub wpisać w nim coś, aby upewnić się, że zbierane są ciekawe informacje profilowania.

1. Zatrzymaj sesję kolekcji i wyślij dane wyjściowe do pliku, wpisując następujące polecenie.

   ```cmd
   VSDiagnostics.exe stop <id> /output:<path to file>
   ```

1. Przejdź do pliku wyjściowego z poprzedniego polecenia i otwórz go w programie Visual Studio, aby sprawdzić zebrane informacje.

## <a name="agent-configuration-files"></a><a name="config_file"></a>Pliki konfiguracyjne agenta

Agenci zbierania są wymiennymi składnikami, które zbierają różne typy danych w zależności od tego, co próbujesz zmierzyć.

Dla wygody można przechowywać te informacje w pliku konfiguracji agenta. Plik konfiguracyjny jest plikiem *.json,* który zawiera co najmniej nazwę *pliku dll* i jej com CLSID. Oto przykładowe pliki konfiguracyjne, które można znaleźć w następującym folderze:

```<Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\AgentConfigs\```

* Konfiguracje CpuUsage (Base/High/Low), które odpowiadają danym zebranym dla narzędzia do profilowania [użycia procesora CPU.](../profiling/cpu-usage.md)
* Konfiguracje DotNetObjectAlloc (Base/Low), które odpowiadają danym zebranym dla [narzędzia .NET Object Allocation](../profiling/dotnet-alloc-tool.md).

Konfiguracje podstawowe/niskie/wysokie odnoszą się do częstotliwości próbkowania. Na przykład Low wynosi 100 próbek/sekundę, a Wysoki to 4000 próbek na sekundę.

Dla narzędzia *VSDiagnostics.exe* do pracy z agentem kolekcji, wymaga zarówno biblioteki DLL i COM CLSID dla odpowiedniego agenta, a agent może mieć dodatkowe opcje konfiguracji, jak również. Jeśli używasz agenta bez pliku konfiguracyjnego, użyj formatu w następującym poleceniu.

```cmd
VSDiagnostics.exe start <id> /attach:<pid> /loadAgent:<agentCLSID>;<agentName>[;<config>]
```

## <a name="permissions"></a>Uprawnienia

Aby profilować aplikację, która wymaga uprawnień z podwyższonym poziomem uprawnień, należy to zrobić z wiersza polecenia z podwyższonym poziomem uprawnień.
