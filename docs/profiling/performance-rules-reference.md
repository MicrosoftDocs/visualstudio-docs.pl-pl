---
title: Wydajność reguły odniesienia | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59fc9424-76ca-4365-ae47-bb14a736c9c2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b3d947dbc3fae436fa64d3effa963df5445991be
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53831290"
---
# <a name="performance-rules-reference"></a>Zasady wydajności — Odwołanie
Reguły wydajności narzędzi profilowania zapewniają dodatkowe ostrzeżenia i informacje o wydajności aplikacji. Reguły wydajności analizy danych profilowania zbieranych ze źródeł takich jak liczniki wydajności procesora i Windows. Reguł komunikaty są wyświetlane w oknie dane wyjściowe błędu [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] zintegrowanego środowiska programistycznego. Komunikaty są wyświetlane przy użyciu jednego z następujących poziomów reguły:  
  
|||  
|-|-|  
|**Error**|Kilka reguł generowania komunikaty o błędach, ponieważ większość problemów z wydajnością nie są od razu wykupić błędy. Komunikat o błędzie może wskazywać na błąd podczas zbierania danych profilowania.|  
|**Ostrzeżenie**|Ostrzeżenia wskazuje obszar aplikację, która może potencjalnie być źródłem problemów z wydajnością lub które mogą skorzystać z optymalizacji.|  
|**Informacje o**|Komunikaty z informacjami o wskazują, że analiza warunku reguły nie osiągnął próg, aby wygenerować komunikat o błędzie albo jest przydatne informacje w wiadomości, ale nie będzie odzwierciedlał problem z wydajnością.|  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Reguły wydajności według identyfikatora](../profiling/performance-rules-by-id.md)  
  
 Reguły wydajności narzędzi profilowania są zorganizowane w cztery kategorie:  
  
|||  
|-|-|  
|[Reguły wydajności dotyczące użycia programu .NET Framework](../profiling/dotnet-framework-usage-performance-rules.md)|Reguły, które ułatwiają używać programu .NET Framework wydajnie.|  
|[Reguły wydajności pamięci i stronicowania](../profiling/memory-and-paging-performance-rules.md)|Reguły, które analizują zarządzanej pamięci i stronicowania działanie aplikacji.|  
|[Reguły korzystania z narzędzi profilowania](../profiling/profiling-tools-usage-rules.md)|Reguły, które ułatwiają narzędzia profilowania wydajnie.|  
|[Reguły wydajności monitorowania zasobu](../profiling/resource-monitoring-performance-rules.md)|Uruchom komunikaty informacyjne dotyczące wykorzystania procesora i pamięci w profilowania.|