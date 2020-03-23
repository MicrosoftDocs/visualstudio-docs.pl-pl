---
title: Reguły skuteczności monitorowania zasobów | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0f77faf-0a05-4718-a2c5-47934be40868
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2389c23b9089ebbdd96d337a3b47d5be9d576b4b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778326"
---
# <a name="resource-monitoring-performance-rules"></a>Reguły wydajności monitorowania zasobu
Komunikaty o wydajności w kategorii Monitorowanie zasobów zawierają dodatkowe dane dotyczące wydajności aplikacji. Te dane można użyć do analizowania problemów z wydajnością. Te reguły są informacyjne i zgłaszane dla każdego przebiegu profilowania.

|||
|-|-|
|[DA0501: Średnie zużycie procesora CPU przez proces profilowany.](../profiling/da0501-average-cpu-consumption-by-the-process-being-profiled.md)|Ten komunikat informuje procent czasu, przez który procesor był zajęty wykonywaniem instrukcji z aplikacji. Zgłoszona wartość jest średnią we wszystkich interwałach pomiaru, w których profilowany proces był aktywny.|
|[DA0502: Maksymalne użycie procesora CPU przez profilowany proces](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|Ten komunikat informuje o maksymalnym procentowym czasie, przez który procesor był zajęty wykonywaniem instrukcji z aplikacji. Zgłoszona wartość jest maksymalną wartością zgłoszoną dla wszystkich interwałów pomiaru, w których profilowany proces był aktywny.|
|[DA0503: Średni zestaw roboczy w bajtach dla profilowanego procesu](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|Ten komunikat informuje o średniej ilości pamięci fizycznej w bajtach, że proces był używany podczas profilowania był aktywny. Ta miara pamięci fizycznej jest znana jako zestaw roboczy.|
|[DA0504: Maksymalny zestaw roboczy w bajtach dla profilowanego procesu](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|Ten komunikat informuje o maksymalnej ilości pamięci fizycznej w bajtach, że proces był używany podczas profilowania był aktywny.|
|[DA0505: Średnie bajty prywatne przydzielone dla procesu poddawanego profilowaniu](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|Ten komunikat informuje o średniej ilości pamięci wirtualnej, która proces przydzielony w bajtach podczas profilowania był aktywny. Ta miara pamięci wirtualnej jest znana jako *bajty prywatne*. Bajty prywatne reprezentuje lokalizacje pamięci wirtualnej, które zostały przydzielone przez proces, który jest dostępny tylko przez wątki uruchomione wewnątrz procesu.|
|[DA0506: Maksymalne bajty prywatne przydzielone dla procesu poddawanego profilowaniu](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|Ten komunikat informuje o maksymalnej ilości pamięci wirtualnej, jaką proces został przydzielony w bajtach prywatnych podczas profilowania.|
