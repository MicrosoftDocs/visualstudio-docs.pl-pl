---
title: Wizualizator współbieżności | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.viewnavigation
- vs.cv.overview
- vs.cv.performance.gettingstarted
- vs.cv.gettingstarted
helpviewer_keywords:
- Concurrency Visualizer, Concurrency Visualizer
ms.assetid: ae5879a0-1e1a-455a-ba72-148e57f59289
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e7061acabbe5ce18ff6e1f210fe0003bdaf88980
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "82586810"
---
# <a name="concurrency-visualizer"></a>Concurrency Visualizer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

KORYGUJĄC
> Wizualizator współbieżności jest opcjonalnym rozszerzeniem programu Visual Studio. Pobierz narzędzie Concurrency Visualizer i narzędzia kolekcji Concurrency Visualizer z następujących linków:  
> 
> - Pobierz rozszerzenie              [Concurrency Visualizer](https://visualstudiogallery.msdn.microsoft.com/a6c24ce9-beec-4545-9261-293061436ee9) .  
>   - Pobierz              [Narzędzia do zbierania danych Concurrency Visualizer dla programu Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=49103).  
> 
>   [Narzędzie wiersza polecenia narzędzia Concurrency Visualizer (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md) umożliwia zbieranie śladów z wiersza polecenia, które można wyświetlić w programie Concurrency Visualizer dla programu Visual Studio 2015. Narzędzia można używać na komputerach, na których nie zainstalowano programu Visual Studio.  
  
 Możesz użyć wizualizatora współbieżności, aby zobaczyć, jak działa aplikacja wielowątkowa. Widoki w wizualizatorze współbieżności zapewniają dane graficzne, tabelaryczne i tekstowe, które pokazują relacje czasowe między wątkami w programie i systemem jako całością. Można użyć wizualizatora współbieżności do lokalizowania wąskich gardeł wydajności, niedostatecznego wykorzystania procesora, rywalizacji wątków, migracji wątków międzyrdzeniowych, opóźnień synchronizacji, aktywności DirectX, obszarów nakładających się operacji we/wy i innych informacji. Widoki zawierają dane, które można wykonywać, łącząc ich graficzne dane wyjściowe z stosami wywołań i kodem źródłowym.  
  
 Wizualizator współbieżności korzysta z funkcji [śledzenia zdarzeń dla systemu Windows](https://msdn.microsoft.com/library/bb968803(VS.85).aspx) .  
  
> [!NOTE]
> Wizualizator współbieżności nie obsługuje projektów sieci Web.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Widok wykorzystania](../profiling/utilization-view.md)|Opisuje sposób wyświetlania i analizowania aktywności systemu na wszystkich procesorach.|  
|[Widok wątków](../profiling/threads-view-parallel-performance.md)|Opisuje sposób analizowania interakcji między wątkami w programie.|  
|[Widok rdzeni](../profiling/cores-view.md)|Opisuje sposób analizowania migracji wątków między rdzeniami.|  
|[Typowe wzorce dla źle działających aplikacji wielowątkowych](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md)|Opisuje kilka typowych wzorców i pokazuje, jak pojawiają się one w wizualizatorze współbieżności.|  
|[Programowanie równoległe w blogu programu Visual Studio](https://docs.microsoft.com/archive/blogs/visualizeparallel/)|Zawiera wskazówki i najlepsze rozwiązania dotyczące wizualizatora współbieżności.|  
|[Widoki raportu wydajności](../profiling/performance-report-views.md)|Zawiera informacje referencyjne dotyczące raportów i widoków narzędzia profilowania programu Visual Studio.|  
|[Concurrency Visualizer SDK](../profiling/concurrency-visualizer-sdk.md)|Opisuje sposób Instrumentacji kodu źródłowego do wyświetlania dodatkowych informacji w wizualizatorze współbieżności.|  
|[Narzędzie wiersza polecenia Concurrency Visualizer (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|Opisuje, jak używać narzędzia wiersza polecenia Concurrency Visualizer (CVCollectionCmd.exe) do zbierania i przetwarzania śladów na maszynach, które nie mają programu Visual Studio.|  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia profilowania](../profiling/profiling-tools.md)
