---
title: Użycie pomiar procesora CPU z wiersza polecenia
description: Mierzenie wydajności procesora CPU w aplikacji z poziomu wiersza polecenia.
ms.custom: ''
ms.date: 02/19/2019
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
ms.openlocfilehash: 87bf0c236f34e753866ea114dfc7f45e8f16a979
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62972423"
---
# <a name="measure-application-performance-from-the-command-line"></a>Miara wydajności aplikacji z poziomu wiersza polecenia

Użytkownik może zbierania informacji o wydajności aplikacji za pomocą narzędzia wiersza polecenia.

W tym przykładzie opisano w tym artykule zbieranie informacji o wydajności dla Microsoft Notepad, ale tej samej metody można profilować żaden proces.

## <a name="prerequisites"></a>Wymagania wstępne

* Program Visual Studio 2019 r w wersji zapoznawczej 3 lub nowszy

* Znajomość narzędzia wiersza polecenia

## <a name="collect-performance-data"></a>Zbieranie danych dotyczących wydajności

Profilowanie przy użyciu narzędzi interfejsu wiersza polecenia programu Visual Studio diagnostyki polega na dołączanie narzędzie profilowania, wraz z jednym z agentów zbierających dane do procesu. Dołączanie narzędzie profilowania, można rozpocząć sesji diagnostycznej, która przechwytuje i magazynów danych profilowania, dopóki nie zostanie zatrzymana narzędzia, w tym momencie dane są eksportowane *.diagsession* pliku. Następnie można otworzyć tego pliku w programie Visual Studio można analizować wyniki.

1. Uruchom program Notatnik, a następnie otwórz Menedżera zadań, aby uzyskać jego identyfikator procesu (PID). W Menedżerze zadań Znajdź identyfikator PID w **szczegóły** kartę.

1. Otwórz wiersz polecenia i przejdź do katalogu przy użyciu agenta zbierania pliku wykonywalnego, zwykle w tym miejscu.

   ```<Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\```

1. Rozpocznij *VSDiagnostics.exe* , wpisując następujące polecenie.

   ```cmd
   VSDiagnostics.exe start <id> /attach:<pid> /loadConfig:<configFile>
   ```

   Argumenty, które muszą być uwzględnione są:

   * \<*Identyfikator*> identyfikuje sesji zbierania. Identyfikator musi być liczbą z przedziału od 1 do 255.
   * \<*Identyfikator PID*> Identyfikator PID procesu chcesz profilu, w tym przypadku identyfikator PID można znaleźć w kroku 1
   * \<*configFile*>, plik konfiguracyjny dla agenta kolekcji ma zostać uruchomione. Aby uzyskać więcej informacji, zobacz [pliki konfiguracji agentów](#config_file).

1. Zmień rozmiar Notatnik lub wpisz coś w nim, aby upewnić się, że niektóre ciekawe profilowania informacje są zbierane.

1. Zatrzymaj sesję zbierania, a następnie wysłać dane wyjściowe do pliku, wpisując następujące polecenie.

   ```cmd
   VSDiagnostics.exe stop <id> /output:<path to file>
   ```

1. Przejdź do pozycji Plik wyjściowy z poprzedniego polecenia, a następnie otwórz go w programie Visual Studio, aby sprawdzić informacje zebrane.

## <a name="config_file"></a> Pliki konfiguracyjne agenta

Agenci są wymienne składnikami, które zbieranie różnych typów danych w zależności od tego, co próbujesz zmierzyć.

Dla wygody można przechowywać tych informacji w pliku konfiguracji agenta. Plik konfiguracji jest *.json* pliku, który zawiera co najmniej nazwę *.dll* i jego CLSID COM. Poniżej przedstawiono przykład pliki konfiguracyjne, które znajdują się w następującym folderze:

```<Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\AgentConfigs\```

* Konfiguracje CpuUsage (podstawowy/wysoka/niska), które odnosi się do danych zbieranych dla [użycie procesora CPU](../profiling/cpu-usage.md) narzędzia profilowania.
* Konfiguracje DotNetObjectAlloc (podstawowy/niska), które odnosi się do danych zbieranych dla [narzędzia przydziału obiektu .NET](https://devblogs.microsoft.com/visualstudio/visual-studio-2017-version-15-8-preview-3/#tooling).

Konfiguracje Base/niski/wysoki odnoszą się do próbkowania. Na przykład Niski wynosi 100 próbek/s i wysoka wartość jest 4000 próbek/s.

Aby uzyskać *VSDiagnostics.exe* narzędzia do pracy z agentem kolekcji, wymaga biblioteki DLL i COM CLSID odpowiedniego agenta i agent może być również opcji dodatkowych czynności konfiguracyjnych. Jeśli używasz agenta bez pliku konfiguracji, należy użyć formatu w następującym poleceniu.

```cmd
VSDiagnostics.exe start <id> /attach:<pid> /loadAgent:<agentCLSID>;<agentName>[;<config>]
```

## <a name="permissions"></a>Uprawnienia

Aby profilować aplikację, która wymaga podniesionych uprawnień, należy to zrobić z wiersza polecenia z podwyższonym poziomem uprawnień.
