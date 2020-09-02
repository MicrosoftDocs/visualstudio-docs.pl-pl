---
title: Reguły wydajności monitorowania zasobów | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0f77faf-0a05-4718-a2c5-47934be40868
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 39df18811a47dfb41c17333121cd9a23d8f46940
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544537"
---
# <a name="resource-monitoring-performance-rules"></a>Reguły wydajności monitorowania zasobu
Komunikaty o wydajności w kategorii Monitorowanie zasobów zapewniają dodatkowe dane dotyczące wydajności aplikacji. Za pomocą tych danych można analizować problemy z wydajnością. Te reguły są informacyjne i raportowane dla każdego przebiegu profilowania.

|Reguła|Opis|
|-|-|
|[DA0501: średnie użycie procesora przez profilowany proces.](../profiling/da0501-average-cpu-consumption-by-the-process-being-profiled.md)|Ten komunikat przedstawia wartość procentową czasu, przez który procesor był zajęty wykonywaniem instrukcji z aplikacji. Raportowana wartość jest wartością średnią dla wszystkich interwałów pomiarowych, w przypadku których proces profilowany jest aktywny.|
|[DA0502: Maksymalne użycie procesora przez profilowany proces](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|Ten komunikat zgłasza maksymalny procent czasu, przez który procesor był zajęty wykonywaniem instrukcji z aplikacji. Raportowana wartość jest wartością maksymalną raportowaną we wszystkich interwałach pomiarowych, w których proces profilowany był aktywny.|
|[DA0503: Średni zestaw roboczy w bajtach dla profilowanego procesu](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|Ten komunikat przedstawia średnią ilość pamięci fizycznej (w bajtach), z której korzysta proces podczas aktywności profilowania. Ta miara pamięci fizycznej jest znana jako zestaw roboczy.|
|[DA0504: Maksymalny zestaw roboczy w bajtach dla profilowanego procesu](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|Ten komunikat przedstawia maksymalną ilość pamięci fizycznej (w bajtach), z której korzysta proces podczas aktywności profilowania.|
|[DA0505: Średnia liczba bajtów prywatnych przydzielonych dla profilowanego procesu](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|Ten komunikat przedstawia średnią ilość pamięci wirtualnej, którą proces przydzielił w bajtach, podczas gdy profilowanie było aktywne. Ta miara pamięci wirtualnej jest nazywana *bajtami prywatnymi*. Bajty prywatne reprezentują lokalizacje pamięci wirtualnej, które zostały przydzielone przez proces, do którego można uzyskać dostęp tylko przez wątki działające w procesie.|
|[DA0506: Maksymalna liczba bajtów prywatnych przydzielonych dla profilowanego procesu](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|Ten komunikat przedstawia maksymalną ilość pamięci wirtualnej przydzieloną przez proces w bajtach prywatnych podczas aktywności profilowania.|
