---
title: Reguły wydajności monitorowania zasobu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f0f77faf-0a05-4718-a2c5-47934be40868
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 258cb329adac23ea1bd463e22a0fd6ada7b526bc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745620"
---
# <a name="resource-monitoring-performance-rules"></a>Reguły wydajności monitorowania zasobu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Komunikaty wydajności w kategorii monitorowanie zasobów zawierają dodatkowe dane dotyczące wydajności aplikacji. Te dane można użyć do analizowania problemów z wydajnością. Te zasady są informacyjne i podać dla każdego uruchomienia profilowania.  
  
|||  
|-|-|  
|[DA0501: Średnie użycie procesora CPU przez profilowany proces](../profiling/da0501-average-cpu-consumption-by-the-process-being-profiled.md)|Ten komunikat raporty procent czasu procesor był zajęty, wykonując instrukcje z aplikacji. Wystąpienia wartości zgłoszonej jest średnią we wszystkich interwałach pomiarowych, w których była aktywna PROFILOWANEGO procesu.|  
|[DA0502: Maksymalne użycie procesora CPU przez profilowany proces](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|Ten komunikat zgłasza maksymalny procent czasu procesor był zajęty, wykonując instrukcje z aplikacji. Wystąpienia wartości zgłoszonej jest maksymalną wartość zgłaszaną wśród wszystkich interwałów pomiarowych, w których był aktywny proces poddawany profilowaniu.|  
|[DA0503: Średni zestaw roboczy w bajtach dla profilowanego procesu](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|Ten komunikat raporty średniej ilości pamięci fizycznej w bajtach, przez proces używała podczas profilowania jest aktywny. Ta miara ilości pamięci fizycznej jest określany jako zestaw roboczy.|  
|[DA0504: Maksymalny zestaw roboczy w bajtach dla profilowanego procesu](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|Ten komunikat raporty maksymalną ilość pamięci fizycznej w bajtach, przez proces używała podczas profilowania jest aktywny.|  
|[DA0505: Średnia liczba bajtów prywatnych alokowanych dla profilowanego procesu](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|Ten komunikat raporty średniej ilości pamięci wirtualnej wygasłych procesu przydzielone w bajtach podczas profilowania. Ta miara pamięci wirtualnej jest nazywany *Bajty prywatne*. Bajty prywatne reprezentuje lokalizacje pamięci wirtualnej, które zostały przydzielone przez proces, który może zostać oceniony jedynie przez działający proces wątki.|  
|[DA0506: Maksymalna liczba bajtów prywatnych alokowanych dla profilowanego procesu](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|Ten komunikat raporty maksymalną ilość pamięci wirtualnej wygasłych procesu przydzielone w Bajty prywatne podczas profilowania.|



