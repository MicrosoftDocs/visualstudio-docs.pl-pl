---
title: Narzędzie CONCURRENCY Visualizer | Dokumentacja firmy Microsoft
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
manager: ghogen
ms.openlocfilehash: 91fd9e0872529c61ffbfee42d1f3517c106340e0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733818"
---
# <a name="concurrency-visualizer"></a>Concurrency Visualizer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UWAGA]
>  Narzędzie Concurrency Visualizer to opcjonalne rozszerzenie programu Visual Studio. Pobierz narzędzia Concurrency Visualizer i Concurrency Visualizer Collection Tools z następujących linków:  
> 
> - Pobierz [Concurrency Visualizer](https://visualstudiogallery.msdn.microsoft.com/a6c24ce9-beec-4545-9261-293061436ee9) rozszerzenia.  
>   -   Pobierz [Concurrency Visualizer Collection Tools dla programu Visual Studio 2015](http://www.microsoft.com/download/details.aspx?id=49103).  
> 
>   [Concurrency Visualizer Command-Line Utility (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md) pozwala zbierać dane śledzenia w wierszu polecenia, który można wyświetlić w Wizualizatorze współbieżności dla programu Visual Studio 2015. Narzędzie może służyć na komputerach, które nie mają zainstalowanego programu Visual Studio.  
  
 Narzędzie Concurrency Visualizer można użyć, aby zobaczyć, jak działa dana aplikacja wielowątkowa. Widoki w Concurrency Visualizer zapewniają graficzne, tabelaryczne i tekstowe dane, które Pokazuję tymczasowe relacje między wątkami w programie i systemie jako całości. Można użyć Concurrency Visualizer można zlokalizować wąskie gardła wydajności, procesora CPU niepełnego, rywalizacji wątków, migracji wątku między rdzeniami, opóźnień synchronizacji, DirectX działania, obszarów nakładania się wejść / i inne informacje. Widoki dostarczają danych, którymi można pracować, łącząc ich wynik graficzny ze stosem wywołań i kodem źródłowym.  
  
 Wizualizator współbieżności opiera się na [Event Tracing for Windows](http://go.microsoft.com/fwlink/?LinkId=234579) funkcji.  
  
> [!NOTE]
>  Narzędzie Concurrency Visualizer nie obsługuje projektów sieci Web.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Widok wykorzystania](../profiling/utilization-view.md)|W tym artykule opisano sposób wyświetlania i analizowania aktywności systemu dla wszystkich procesorów.|  
|[Widok wątków](../profiling/threads-view-parallel-performance.md)|Opisuje sposób analizowania wzajemnych relacji między wątkami w programie.|  
|[Widok rdzeni](../profiling/cores-view.md)|Opisuje sposób analizy migracji wątku między rdzeniami.|  
|[Typowe wzorce dla nieprawidłowo działających aplikacji wielowątkowych](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md)|W tym artykule opisano kilka typowych wzorców i pokazuje, jak pojawiają się w Wizualizatorze współbieżności.|  
|[Programowanie równoległe w blogu programu Visual Studio](http://go.microsoft.com/fwlink/?LinkId=235385)|Zawiera wskazówki i najlepsze rozwiązania dotyczące programu Concurrency Visualizer.|  
|[Widoki raportu wydajności](../profiling/performance-report-views.md)|Dostarcza informacji dotyczących raportów i widoków programu Visual Studio Profiling Tools.|  
|[Zestaw SDK narzędzia Concurrency Visualizer](../profiling/concurrency-visualizer-sdk.md)|W tym artykule opisano, jak zmodyfikować kod źródłowy, aby wyświetlić dodatkowe informacje w Wizualizatorze współbieżności.|  
|[Narzędzie wiersza polecenia narzędzia Concurrency Visualizer (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|W tym artykule opisano, jak używać narzędzia wiersza polecenia Concurrency Visualizer (CVCollectionCmd.exe) do zbierania i przetwarzania śladów na komputerach, na których nie zainstalowano oprogramowania Visual Studio.|  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia profilowania](../profiling/profiling-tools.md)



