---
title: Reguły wydajności monitorowania zasobu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0f77faf-0a05-4718-a2c5-47934be40868
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7e4071820aece2f58f0a1345e1110a80c9f76f0f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947923"
---
# <a name="resource-monitoring-performance-rules"></a>Reguły wydajności monitorowania zasobu
Komunikaty wydajności w kategorii monitorowanie zasobów zawierają dodatkowe dane dotyczące wydajności aplikacji. Te dane można użyć do analizowania problemów z wydajnością. Te zasady są informacyjne i podać dla każdego uruchomienia profilowania.  
  
|||  
|-|-|  
|[DA0501: Średnie użycie Procesora przez profilowany proces.](../profiling/da0501-average-cpu-consumption-by-the-process-being-profiled.md)|Ten komunikat raporty procent czasu procesor był zajęty, wykonując instrukcje z aplikacji. Wystąpienia wartości zgłoszonej jest średnią we wszystkich interwałach pomiarowych, w których była aktywna PROFILOWANEGO procesu.|  
|[DA0502: Maksymalne użycie Procesora przez profilowany proces](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|Ten komunikat zgłasza maksymalny procent czasu procesor był zajęty, wykonując instrukcje z aplikacji. Wystąpienia wartości zgłoszonej jest maksymalną wartość zgłaszaną wśród wszystkich interwałów pomiarowych, w których był aktywny proces poddawany profilowaniu.|  
|[DA0503: Średni zestaw roboczy w bajtach dla procesu poddawanego profilowaniu](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|Ten komunikat raporty średniej ilości pamięci fizycznej w bajtach, przez proces używała podczas profilowania jest aktywny. Ta miara ilości pamięci fizycznej jest określany jako zestaw roboczy.|  
|[DA0504: Maksymalny zestaw roboczy w bajtach dla procesu poddawanego profilowaniu](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|Ten komunikat raporty maksymalną ilość pamięci fizycznej w bajtach, przez proces używała podczas profilowania jest aktywny.|  
|[DA0505: Średnia liczba bajtów prywatnych alokowanych dla PROFILOWANEGO procesu](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|Ten komunikat raporty średniej ilości pamięci wirtualnej wygasłych procesu przydzielone w bajtach podczas profilowania. Ta miara pamięci wirtualnej jest nazywany *Bajty prywatne*. Bajty prywatne reprezentuje lokalizacje pamięci wirtualnej, które zostały przydzielone przez proces, który może zostać oceniony jedynie przez działający proces wątki.|  
|[DA0506: Maksymalna liczba bajtów prywatnych alokowanych dla PROFILOWANEGO procesu](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|Ten komunikat raporty maksymalną ilość pamięci wirtualnej wygasłych procesu przydzielone w Bajty prywatne podczas profilowania.|