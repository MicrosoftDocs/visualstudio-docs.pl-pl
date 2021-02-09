---
title: Informacje o regułach wydajności | Microsoft Docs
description: Dowiedz się, w jaki sposób reguły wydajności narzędzia profilowania zapewniają dodatkowe ostrzeżenia i informacje o wydajności aplikacji.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59fc9424-76ca-4365-ae47-bb14a736c9c2
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b2c23f32e2368ffa269deeb7eddb5fb05839e4af
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922145"
---
# <a name="performance-rules-reference"></a>Zasady wydajności — Odwołanie
Reguły wydajności narzędzia profilowania zawierają dodatkowe ostrzeżenia i informacje o wydajności aplikacji. Reguły wydajności analizują dane w przebiegu profilowania, który jest zbierany ze źródeł, takich jak liczniki wydajności systemu Windows i procesora. Komunikaty reguły są wyświetlane w oknie dane wyjściowe błędu [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] zintegrowanego środowiska deweloperskiego. Komunikaty są wyświetlane z jednym z następujących poziomów reguł:

|Kategoria|Opis|
|-|-|
|**Błąd**|Niektóre reguły generują komunikaty o błędach, ponieważ większość problemów z wydajnością nie jest błędem. Komunikat o błędzie może wskazywać na awarię zbierania danych profilowania.|
|**Ostrzeżenie**|Ostrzeżenia wskazują obszar aplikacji, który może być źródłem problemów z wydajnością lub które mogą korzystać z optymalizacji.|
|**Informacje**|Komunikaty informacyjne wskazują, że analiza warunku reguły nie osiągnęła progu w celu wygenerowania komunikatu o błędzie lub że informacje w komunikacie są przydatne, ale nie odzwierciedlają problemu z wydajnością.|

## <a name="in-this-section"></a>W tej sekcji

[Reguły wydajności według identyfikatora](../profiling/performance-rules-by-id.md)

Reguły wydajności narzędzia profilowania są zorganizowane w czterech kategoriach:

|Kategoria|Opis|
|-|-|
|[Reguły wydajności .NET Framework użycia](../profiling/dotnet-framework-usage-performance-rules.md)|Reguły ułatwiające korzystanie z .NET Framework wydajnie.|
|[Reguły wydajności pamięci i stronicowania](../profiling/memory-and-paging-performance-rules.md)|Reguły, które analizują pamięć zarządzaną i zachowanie stronicowania aplikacji.|
|[narzędzia profilowania reguł użycia](../profiling/profiling-tools-usage-rules.md)|Reguły ułatwiające korzystanie z narzędzia profilowania wydajnie.|
|[Reguły wydajności monitorowania zasobów](../profiling/resource-monitoring-performance-rules.md)|Komunikaty informacyjne dotyczące użycia procesora i pamięci w przebiegu profilowania.|
