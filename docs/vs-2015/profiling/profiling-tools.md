---
title: narzędzia profilowania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.diagnosticshub.overview
ms.assetid: 0fb6cd5d-e16a-4526-84a5-19e63c625bc5
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bcb230532da4a0b84ea0102d86534c28afe35558
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686290"
---
# <a name="profiling-tools"></a>narzędzia profilowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Narzędzia profilowania i diagnostyki pomagają zdiagnozować problemy dotyczące użycia pamięci i procesora oraz inne problemy na poziomie aplikacji. Za pomocą tych narzędzi można zbierać dane (takie jak wartości zmiennych, wywołania funkcji i zdarzenia) w czasie uruchamiania aplikacji w debugerze. Stan aplikacji można wyświetlić w różnych punktach podczas wykonywania kodu.  
  
 Zapoznaj się z podsumowaniem u dołu, aby zobaczyć, jakie narzędzia są dostępne dla typu projektu (na przykład Desktop, platformy UWP, ASP.NET).  
  
 Dostęp do narzędzi profilowania można uzyskać za pomocą polecenia **Debug/Windows/Show narzędzia diagnostyczne** , aby używać narzędzi w trakcie sesji debugowania lub za pomocą **profilera debugowania/wydajności...** , aby przeprowadzić skoncentrowaną analizę wydajności.  Aby uzyskać więcej informacji na temat różnych metod, zobacz [uruchamianie narzędzia profilowania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md) .  
  
 ![DebugDiagnosticsToolsMenu](../profiling/media/debugdiagnosticstoolsmenu.png "DebugDiagnosticsToolsMenu")  
  
 Zobacz [co nowego w narzędzia profilowania](../profiling/what-s-new-in-profiling-tools.md) , aby poznać nowe funkcje tej wersji.  
  
 W poniższych sekcjach opisano różne narzędzia do oceny wydajności, które są dostępne w programie Visual Studio.  
  
## <a name="memory-usage"></a>Użycie pamięci  
 ![DiagMemorySmall](../profiling/media/diagmemorysmall.png "DiagMemorySmall")  
  
 Znajdowanie przecieków pamięci i niewydajnej pamięci podczas debugowania za pomocą narzędzia **użycie pamięci** . Narzędzie umożliwia wykonywanie migawek sterty pamięci zarządzanego i natywnego. Możesz użyć tego narzędzia z aplikacjami klasycznymi, aplikacjami uniwersalnymi systemu Windows i aplikacjami ASP.NET. Narzędzie **użycie pamięci** można uruchomić z okna **Narzędzia diagnostyczne** podczas debugowania (**debugowanie/Windows/show narzędzia diagnostyczne**) lub poza debugerem (Narzędzie**debugowania/wydajności.**..). Aby uzyskać więcej informacji, zobacz  [użycie pamięci](../profiling/memory-usage.md) i [użycie pamięci bez debugowania](https://msdn.microsoft.com/library/8883bc5f-df86-4f84-aa2b-a21150f499b0) .  
  
## <a name="cpu-usage"></a>Użycie procesora  
 ![DiagCPUSmall](../profiling/media/diagcpusmall.png "DiagCPUSmall")  
  
 Narzędzie **użycie procesora CPU** pokazuje, gdzie procesor spędza czas wykonywania w języku C++, C#/VB i kodzie JavaScript.  Za pomocą tego narzędzia można używać aplikacji uniwersalnych dla komputerów stacjonarnych i systemu Windows, a także aplikacji platformy Azure App Services. Narzędzie **użycie procesora CPU** można uruchomić z okna **Narzędzia diagnostyczne** podczas debugowania (**debugowanie/Windows/show narzędzia diagnostyczne**) lub poza debugerem (Narzędzie**debugowania/wydajności.**..). Aby uzyskać więcej informacji, zobacz [użycie procesora CPU](../profiling/cpu-usage.md) .  
  
## <a name="performance-explorer"></a>Eksplorator wydajności  
 ![PerfTools](../profiling/media/perftools.png "PerfTools")  
  
 **Eksplorator wydajności** (**debugowanie/Profiler/Eksplorator wydajności**) umożliwia korzystanie z wielu różnych narzędzi, w tym **próbkowanie procesora**, **Instrumentacja**, **alokacja pamięci platformy .NET**i **rywalizacja o zasoby**. Narzędzi Eksplorator wydajności można używać z aplikacjami klasycznymi i aplikacjami ASP.NET, ale nie aplikacjami uniwersalnymi systemu Windows. Aby uzyskać więcej informacji, zobacz [Eksplorator wydajności](../profiling/performance-explorer.md).  
  
## <a name="gpu-usage"></a>Użycie procesora GPU  
 ![DiagGPUUsage](../profiling/media/diaggpuusage.png "DiagGPUUsage")  
  
 Użyj narzędzia [użycie procesora GPU](../debugger/gpu-usage.md) , aby lepiej zrozumieć użycie sprzętu w aplikacji Direct3D. Tego narzędzia można używać zarówno w przypadku komputerów stacjonarnych, jak i aplikacji uniwersalnych systemu Windows, ale nie aplikacji ASP.NET. Narzędzie **użycie procesora GPU** można uruchomić z okna **Narzędzia diagnostyczne** podczas debugowania (**debugowanie/wyświetlanie narzędzia diagnostyczne**) lub poza debugerem (Narzędzie**debugowania/wydajności.**..).  
  
## <a name="application-timeline"></a>Oś czasu aplikacji  
 ![DiagAppTimeline](../profiling/media/diagapptimeline.png "DiagAppTimeline")  
  
 Narzędzie [oś czasu aplikacji](../profiling/application-timeline.md) pomaga ulepszyć wydajność aplikacji XAML, zapewniając szczegółowy widok użycia zasobów. Możesz użyć **oś czasu aplikacji** z aplikacjami stacjonarnymi i klasycznymi systemu Windows, ale nie ASP.NET aplikacji. Narzędzie **oś czasu aplikacji** można uruchomić w oknie **Narzędzia diagnostyczne** (Narzędzie**debugowania/wydajności**).  
  
## <a name="perftips"></a>Wskazówki dotyczące wydajności  
 ![DiagPerfTips](../profiling/media/diagperftips.png "DiagPerfTips")  
  
 Gdy debuger przerywa wykonywanie w punkcie przerwania lub operacji krokowej, czas między przerwaniem a poprzednim punktem przerwania pojawia się jako Porada w oknie edytora. Te [Funkcja PerfTip](../profiling/perftips.md) ułatwiają monitorowanie i analizowanie wydajności aplikacji podczas debugowania. Możesz zobaczyć **Funkcja PerfTip** w aplikacjach klasycznych Desktop, Windows Universal i ASP.NET.  
  
## <a name="javascript-memory"></a>Pamięć języka JavaScript  
 ![DiagJSMemory](../profiling/media/diagjsmemory.png "DiagJSMemory")  
  
 Narzędzie [pamięci języka JavaScript](../profiling/javascript-memory.md) umożliwia mierzenie, ocenę i ukierunkowanie problemów związanych z wydajnością w kodzie przez gromadzenie informacji o chronometrażu na wejściu i wyjściu każdej funkcji w aplikacji. Możesz użyć tego narzędzia z uniwersalnymi aplikacjami HTML systemu Windows. Narzędzie **chronometrażu funkcji języka JavaScript** można uruchomić z poziomu okna **Narzędzia diagnostyczne** (**program do debugowania/wydajności**).  
  
## <a name="html-ui-responsiveness"></a>Czas odpowiedzi interfejsu użytkownika HTML  
 ![DiagHTMLResp](../profiling/media/diaghtmlresp.png "DiagHTMLResp")  
  
 Narzędzie do [odpowiedzi interfejsu użytkownika HTML](../profiling/html-ui-responsiveness.md) pomaga wyizolować problemy z wydajnością w aplikacjach, w tym brak reakcji, czas wolnego ładowania i aktualizacje wizualne, które są mniej częste niż oczekiwano. Możesz użyć tego narzędzia z uniwersalnymi aplikacjami HTML systemu Windows. Narzędzie do **odpowiedzi interfejsu użytkownika HTML** można uruchomić z poziomu okna **Narzędzia diagnostyczne** (tag**debugowania/wydajności.**..).  
  
## <a name="intellitrace"></a>IntelliTrace  
 ![DiagIntelliTrace](../profiling/media/diagintellitrace.png "DiagIntelliTrace")  
  
 [IntelliTrace](../debugger/intellitrace.md) umożliwia rejestrowanie określonych zdarzeń, badanie danych w oknie **zmiennych lokalnych** podczas zdarzeń debugera i wywołań funkcji oraz Debugowanie błędów, które są trudne do odtworzenia.  IntelliTrace jest przede wszystkim narzędziem do debugowania, ale również zawiera informacje, które mogą być używane do celów badania wydajności. Tego narzędzia można używać tylko w Visual Studio Enterprise z aplikacjami klasycznymi i ASP.NET w języku C#. IntelliTrace można znaleźć w oknie **Narzędzia diagnostyczne** podczas debugowania (**Debugowanie/Windows/show narzędzia diagnostyczne**).  
  
## <a name="profiling-in-production"></a>Profilowanie w środowisku produkcyjnym  
 Zalecanym podejściem do profilowania w środowisku produkcyjnym jest profilowanie z [wiersza polecenia przy użyciu vsperf.exe](../profiling/using-the-profiling-tools-from-the-command-line.md) do zbierania profilu procesora. Aby umożliwić obsługę profilowania zdalnego w Azure App Service, można profilować za pomocą [portalu Eksplorator serwera lub kudu](https://azure.microsoft.com/blog/remote-profiling-support-in-azure-app-service/).  
  
## <a name="which-tool-should-i-use"></a>Którego narzędzia należy użyć?  
 Poniżej znajduje się tabela zawierająca listę różnych narzędzi oferowanych przez program Visual Studio i różne typy projektów, z których można korzystać:  
  
|Narzędzie wydajności|Pulpit systemu Windows|Uniwersalny/magazyn systemu Windows|ASP.NET|  
|----------------------|---------------------|------------------------------|-------------|  
|[Użycie pamięci](../profiling/memory-usage.md)|tak|tak|nie|  
|[Użycie procesora](../profiling/cpu-usage.md)|tak|tak|Tylko Azure App Service|  
|[Użycie procesora GPU](../debugger/gpu-usage.md)|tak|tak|nie|  
|[Oś czasu aplikacji](../profiling/application-timeline.md)|tak|tak|nie|  
|[Wskazówki dotyczące wydajności](../profiling/perftips.md)|tak|tak dla języka XAML, nie dla HTML|nie|  
|[Eksplorator wydajności](../profiling/performance-explorer.md)|tak|nie|tak|  
|[IntelliTrace](../debugger/intellitrace.md)|Tylko .NET Enterprise|Tylko .NET Enterprise|Tylko .NET Enterprise|  
|[Czas odpowiedzi interfejsu użytkownika języka HTML](../profiling/html-ui-responsiveness.md)|nie|tak dla języka HTML, nie dla języka XAML|nie|  
|[Pamięć języka JavaScript](../profiling/javascript-memory.md)|nie|tak dla języka HTML, nie dla języka XAML|nie|  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio IDE](../ide/visual-studio-ide.md)
