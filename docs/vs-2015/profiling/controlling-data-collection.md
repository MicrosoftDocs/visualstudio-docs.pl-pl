---
title: Kontrolowanie zbierania danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- advanced tasks for profiling tools
- profiling tools, advanced tasks
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c8022dd8fdd480e4bc545923eeb96d64f16ed9a9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803425"
---
# <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Narzędzia profilowania umożliwiają kontroli po danych profilowania zbieranych podczas sesji wydajności i określić funkcje, które są profilowane. W tej sekcji opisano sposób uruchamiają i zatrzymują zbieranie danych z **Eksplorator wydajności** i **kontroli zbierania danych** systemu windows oraz sposób ograniczyć liczbę obiektów, dla których są zbierane dane profilowania.  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Rozpoczęcie i zatrzymanie profilowania:** można uruchomić do profilu aplikacji podczas uruchamiania aplikacji, lub można dołączyć profiler do procesu, który jest już uruchomiony. Gdy uruchomiona jest aplikacja docelowa, można wstrzymywać i wznawiać zbieranie danych. Możesz zakończyć sesję profilowania, zamknij aplikację docelową lub odłączenia profilera z uruchomionego procesu.|-   [Porady: rozpoczęcia i zakończenia zbierania danych o wydajności](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [Porady: dołączanie i odłączanie narzędzi wydajności do uruchomionego procesu](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [Porady: wstrzymywanie i wznawianie zbierania danych o wydajności](../profiling/how-to-pause-and-resume-performance-data-collection.md)|  
|**Konfigurowanie profilowania, aby ograniczyć ilość zebranych danych Instrumentacji:** można użyć właściwości konfiguracji sesji wydajności, aby ograniczyć dane, które są zbierane w profilowania, które używają metody instrumentacji. Można uwzględnić lub wykluczyć pliki z rozszerzeniem dll określonych, przestrzenie nazw, klasy i funkcje. Można również wykluczyć funkcje, które nie spełniają próg rozmiaru, który określisz.|-   [Instrukcje: ograniczanie Instrumentacji do określonych bibliotek DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [Instrukcje: ograniczanie Instrumentacji do określonych funkcji](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Porady: wykluczanie lub uwzględnianie krótkich funkcji z Instrumentacji](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Eksplorator wydajności](../profiling/performance-explorer.md)



