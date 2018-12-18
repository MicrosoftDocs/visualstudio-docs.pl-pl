---
title: Narzędzia profilowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.diagnosticshub.overview
ms.assetid: 0fb6cd5d-e16a-4526-84a5-19e63c625bc5
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 380e98a8cd52fe77486dae245eee910a65a41057
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782105"
---
# <a name="profiling-tools"></a>narzędzia profilowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Narzędzia profilowania i diagnostyki ułatwiają diagnozowanie użycie procesora CPU i pamięci oraz inne problemy z poziomu aplikacji. Za pomocą tych narzędzi można zbierać dane (takie jak wartości zmiennych, wywołania funkcji i zdarzenia) wraz z upływem czasu, po uruchomieniu aplikacji w debugerze. Można wyświetlić stan aplikacji w różnych momentach podczas wykonywania kodu.  
  
 Zapoznaj się z podsumowania na dole, aby zobaczyć, jakie narzędzia są dostępne dla danego typu projektu (na przykład pulpitu, platformy uniwersalnej systemu Windows, platformy ASP.NET).  
  
 Dostęp do narzędzi do profilowania za pomocą **debugowanie / Windows / Pokaż narzędzia diagnostyczne** do korzystania z narzędzi, podczas sesji debugowania lub za pomocą **debugowanie / Profiler wydajności...**  wykonywać analizę wydajności wąsko zdefiniowany.  Zobacz [uruchamiania profilowania narzędzia z lub bez debugera](../profiling/running-profiling-tools-with-or-without-the-debugger.md) więcej informacji na temat różnych metod.  
  
 ![DebugDiagnosticsToolsMenu](../profiling/media/debugdiagnosticstoolsmenu.png "DebugDiagnosticsToolsMenu")  
  
 Zobacz [What's New in Profiling Tools](../profiling/what-s-new-in-profiling-tools.md) Aby dowiedzieć się więcej o nowych funkcjach w tej wersji.  
  
 W poniższych sekcjach opisano narzędzia wydajności, które są dostępne w programie Visual Studio.  
  
## <a name="memory-usage"></a>Użycie pamięci  
 ![DiagMemorySmall](../profiling/media/diagmemorysmall.png "DiagMemorySmall")  
  
 Podczas debugowania za pomocą umożliwia znajdowanie przecieków pamięci i pamięci nieefektywne **użycie pamięci** narzędzia. To narzędzie pozwala wykonać migawki stosu pamięci zarządzanego i natywnego. Narzędzie to za pomocą aplikacji komputerowych, Windows Universal apps i aplikacje platformy ASP.NET. **Użycie pamięci** narzędzie można uruchomić z **narzędzia diagnostyczne** okna podczas debugowania (**debugowanie / Windows / Pokaż narzędzia diagnostyczne**) lub na zewnątrz debugera (**Debugowanie / Profiler wydajności...**). Zobacz [użycie pamięci](../profiling/memory-usage.md) i [użycie pamięci bez debugowania](http://msdn.microsoft.com/library/8883bc5f-df86-4f84-aa2b-a21150f499b0) Aby uzyskać więcej informacji.  
  
## <a name="cpu-usage"></a>Użycie procesora CPU  
 ![DiagCPUSmall](../profiling/media/diagcpusmall.png "DiagCPUSmall")  
  
 **Użycie procesora CPU** narzędziu jest wyświetlany, gdy Procesor spędza czasu wykonywania języka C++, C# / VB oraz kodu JavaScript.  Narzędzie to jest przydatna przy użyciu zarówno desktop i Windows Universal apps, a także aplikacji usługi Azure App Services. **Użycie procesora CPU** narzędzie można uruchomić z **narzędzia diagnostyczne** okna podczas debugowania (**debugowanie / Windows / Pokaż narzędzia diagnostyczne**) lub na zewnątrz debugera (**Debugowanie / Profiler wydajności...**). Zobacz [użycie procesora CPU](../profiling/cpu-usage.md) Aby uzyskać więcej informacji.  
  
## <a name="performance-explorer"></a>Eksplorator wydajności  
 ![PerfTools](../profiling/media/perftools.png "PerfTools")  
  
 **Eksplorator wydajności** (**debugowanie / Profiler / Eksplorator wydajności**) pozwala na używanie wielu różnych narzędzi, w tym **próbkowania Procesora**,  **Instrumentacja**, **alokacji pamięci .NET**, i **rywalizacji o zasoby**. Za pomocą narzędzia Eksplorator wydajności za pomocą aplikacji komputerowych i aplikacji w technologii ASP.NET, ale nie Windows Universal apps. Aby uzyskać więcej informacji, zobacz [Eksplorator wydajności](../profiling/performance-explorer.md).  
  
## <a name="gpu-usage"></a>Użycie procesora GPU  
 ![DiagGPUUsage](../profiling/media/diaggpuusage.png "DiagGPUUsage")  
  
 Użyj [użycie procesora GPU](../debugger/gpu-usage.md) narzędzie, aby lepiej zrozumieć wykorzystanie sprzętu wysokiego poziomu aplikacji Direct3D. Narzędzie to jest przydatna przy użyciu zarówno desktop i Windows Universal apps, ale nie aplikacje platformy ASP.NET. **Użycie procesora GPU** narzędzie można uruchomić z **narzędzia diagnostyczne** okna podczas debugowania (**debugowanie / Pokaż narzędzia diagnostyczne**) lub poza debugerem (**Debugowanie / Profiler wydajności...**).  
  
## <a name="application-timeline"></a>Oś czasu aplikacji  
 ![DiagAppTimeline](../profiling/media/diagapptimeline.png "DiagAppTimeline")  
  
 [Oś czasu aplikacji](../profiling/application-timeline.md) narzędzie pomaga zwiększyć wydajność aplikacji XAML, zapewniając wyświetlenia szczegółowych informacji o ich zużycia zasobów. Możesz użyć **oś czasu aplikacji** z desktop i Windows Universal apps, ale nie aplikacje platformy ASP.NET. **Oś czasu aplikacji** narzędzie można uruchomić z **narzędzia diagnostyczne** okna (**debugowanie / Profiler wydajności...** ).  
  
## <a name="perftips"></a>Perftip  
 ![DiagPerfTips](../profiling/media/diagperftips.png "DiagPerfTips")  
  
 Gdy debuger zatrzymuje wykonywanie w punkcie przerwania lub operacji przechodzenia krok po kroku, czas, jaki upłynął od przerwania i poprzedniego punktu przerwania pojawia się jako wskazówkę w oknie edytora. Te [Perftip](../profiling/perftips.md) ułatwiają monitorowanie i analizowanie wydajności aplikacji podczas debugowania. Możesz zobaczyć **Perftip** pulpitu, Windows Universal i aplikacje platformy ASP.NET.  
  
## <a name="javascript-memory"></a>Pamięć języka JavaScript  
 ![DiagJSMemory](../profiling/media/diagjsmemory.png "DiagJSMemory")  
  
 [Pamięci JavaScript](../profiling/javascript-memory.md) narzędzie służy do pomiaru, oceny i określania elementów docelowych problemy związane z wydajnością w kodzie, zbieranie informacji o chronometrażu przy wejściu i zakończenia poszczególnych funkcji w aplikacji. Narzędzie to jest przydatna przy użyciu aplikacji Windows Universal HTML. **Synchronizacja funkcji JavaScript** narzędzie można uruchomić z **narzędzia diagnostyczne** okna (**debugowanie / Profiler wydajności...** ).  
  
## <a name="html-ui-responsiveness"></a>Czas odpowiedzi interfejsu użytkownika HTML  
 ![DiagHTMLResp](../profiling/media/diaghtmlresp.png "DiagHTMLResp")  
  
 [HTML UI responsiveness](../profiling/html-ui-responsiveness.md) narzędzie pomaga wyizolować problemy z wydajnością w aplikacjach, łącznie z brakiem czas reakcji, powolne ładowanie czasu i częste visual aktualizacji, które są mniej, niż oczekiwano. Narzędzie to jest przydatna przy użyciu aplikacji Windows Universal HTML. **HTML UI Responsiveness** narzędzie można uruchomić z **narzędzia diagnostyczne** okna (**debugowanie / Profiler wydajności...** ).  
  
## <a name="intellitrace"></a>IntelliTrace  
 ![DiagIntelliTrace](../profiling/media/diagintellitrace.png "DiagIntelliTrace")  
  
 [IntelliTrace](../debugger/intellitrace.md) umożliwia rejestrowanie konkretnych zdarzeń, sprawdź dane w **lokalne** okna podczas zdarzenia debuger i wywołania funkcji i błędy debugowania, które są trudne do odtworzenia.  Funkcja IntelliTrace jest przede wszystkim narzędzie debugowania, ale także zawiera informacje, które mogą służyć do badania wydajności. Umożliwia to narzędzie tylko w programie Visual Studio Enterprise z pulpitu, Windows Universal i aplikacji C# ASP.NET. Można znaleźć funkcji IntelliTrace w **narzędzia diagnostyczne** okna podczas debugowania (**debugowanie / Windows / Pokaż narzędzia diagnostyczne**).  
  
## <a name="profiling-in-production"></a>Profilowanie w środowisku produkcyjnym  
 Zalecane podejście do profilowania w środowisku produkcyjnym zaleca się wykonywanie profilowania z [wiersza polecenia przy użyciu vsperf.exe](../profiling/using-the-profiling-tools-from-the-command-line.md) zbierać profil procesora CPU. Obsługę zdalnego profilowania w usłudze Azure App Service, można profilować za pośrednictwem [Eksploratora serwera lub portalu Kudu](https://azure.microsoft.com/en-us/blog/remote-profiling-support-in-azure-app-service/).  
  
## <a name="which-tool-should-i-use"></a>Narzędzie, które należy używać?  
 Poniżej przedstawiono listę różnych narzędzi oferowanych przez program Visual Studio i różnych typach projektów można ich używać za pomocą:  
  
|Narzędzia wydajności|Windows desktop|Windows Universal/Store|ASP.NET|  
|----------------------|---------------------|------------------------------|-------------|  
|[Użycie pamięci](../profiling/memory-usage.md)|Tak|Tak|Brak|  
|[Użycie procesora CPU](../profiling/cpu-usage.md)|Tak|Tak|Usługi Azure App Service tylko|  
|[Użycie procesora GPU](../debugger/gpu-usage.md)|Tak|Tak|Brak|  
|[Oś czasu aplikacji](../profiling/application-timeline.md)|Tak|Tak|Brak|  
|[Wskazówki dotyczące wydajności](../profiling/perftips.md)|Tak|tak, aby XAML nie dla kodu HTML|Brak|  
|[Eksplorator wydajności](../profiling/performance-explorer.md)|Tak|Brak|Tak|  
|[IntelliTrace](../debugger/intellitrace.md)|Tylko Enterprise platformy .NET|Tylko Enterprise platformy .NET|Tylko Enterprise platformy .NET|  
|[Czas odpowiedzi interfejsu użytkownika HTML](../profiling/html-ui-responsiveness.md)|Brak|tak w języku HTML, nie dla XAML|Brak|  
|[Pamięć języka JavaScript](../profiling/javascript-memory.md)|Brak|tak w języku HTML, nie dla XAML|Brak|  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio IDE](../ide/visual-studio-ide.md)



