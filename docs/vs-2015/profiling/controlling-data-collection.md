---
title: Kontrolowanie zbierania danych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- advanced tasks for profiling tools
- profiling tools, advanced tasks
ms.assetid: e713ad63-b948-46f3-8db9-59b30922ebe5
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e34c4db965cacefabe752774e393a4339042040e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68182709"
---
# <a name="controlling-data-collection"></a>Kontrolowanie zbierania danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Narzędzia profilowania umożliwiają kontroli po danych profilowania zbieranych podczas sesji wydajności i określić funkcje, które są profilowane. W tej sekcji opisano sposób uruchamiają i zatrzymują zbieranie danych z **Eksplorator wydajności** i **kontroli zbierania danych** systemu windows oraz sposób ograniczyć liczbę obiektów, dla których są zbierane dane profilowania.  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Rozpoczęcie i zatrzymanie profilowania:** Można uruchomić do profilu aplikacji podczas uruchamiania aplikacji, lub można dołączyć profiler do procesu, który jest już uruchomiony. Gdy uruchomiona jest aplikacja docelowa, można wstrzymywać i wznawiać zbieranie danych. Możesz zakończyć sesję profilowania, zamknij aplikację docelową lub odłączenia profilera z uruchomionego procesu.|-   [Jak: Rozpoczynanie i zatrzymywanie zbierania danych wydajności](../profiling/how-to-start-and-end-performance-data-collection.md)<br />-   [Jak: Dołączanie narzędzi do oceny wydajności do uruchomionych procesów i ich odłączanie](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md)<br />-   [Jak: Wstrzymywanie i wznawianie zbierania danych wydajności](../profiling/how-to-pause-and-resume-performance-data-collection.md)|  
|**Skonfiguruj profilowania, aby ograniczyć ilość zebranych danych Instrumentacji:** Aby ograniczyć dane, które są zbierane w profilowania, które używają metody instrumentacji, można użyć właściwości konfiguracji sesji wydajności. Można uwzględnić lub wykluczyć pliki z rozszerzeniem dll określonych, przestrzenie nazw, klasy i funkcje. Można również wykluczyć funkcje, które nie spełniają próg rozmiaru, który określisz.|-   [Jak: Ograniczanie instrumentacji do określonych bibliotek DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)<br />-   [Jak: Ograniczanie instrumentacji do określonych funkcji](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Jak: Wykluczanie lub uwzględnianie krótkich funkcji z instrumentacji](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)|  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Eksplorator wydajności](../profiling/performance-explorer.md)
