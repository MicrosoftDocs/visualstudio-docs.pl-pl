---
title: Dokumentacja reguł wydajności | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59fc9424-76ca-4365-ae47-bb14a736c9c2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 446e47f50c81fa5bad979117936faef53ad3ef63
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772192"
---
# <a name="performance-rules-reference"></a>Zasady wydajności — Odwołanie
Reguły wydajności narzędzi profilowania zapewniają dodatkowe ostrzeżenia i informacje o wydajności aplikacji. Reguły wydajności analizują dane w przebiegu profilowania, który jest zbierany ze źródeł, takich jak windows i liczniki wydajności procesora. Komunikaty reguły są wyświetlane [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] w oknie Dane wyjściowe błędu zintegrowanego środowiska programistycznego. Komunikaty są wyświetlane z jednym z następujących poziomów reguły:

|||
|-|-|
|**Błąd**|Kilka reguł generuje komunikaty o błędach, ponieważ większość problemów z wydajnością nie są wręcz błędy. Komunikat o błędzie może wskazywać na niepowodzenie w zbieraniu danych profilowania.|
|**Ostrzeżenie**|Ostrzeżenia wskazują obszar aplikacji, który może być źródłem problemów z wydajnością lub które mogą korzystać z optymalizacji.|
|**Informacje**|Komunikaty informacyjne wskazują, że analiza warunku reguły nie osiągnęła progu w celu wygenerowania komunikatu o błędzie lub że informacje w wiadomości są przydatne, ale nie odzwierciedlają problemu z wydajnością.|

## <a name="in-this-section"></a>W tej sekcji

[Reguły wydajności według identyfikatora](../profiling/performance-rules-by-id.md)

Reguły wydajności Narzędzia profilowania są podzielone na cztery kategorie:

|||
|-|-|
|[Reguły wydajności użycia programu .NET Framework](../profiling/dotnet-framework-usage-performance-rules.md)|Reguły ułatwiające efektywne korzystanie z programu .NET Framework.|
|[Reguły wydajności pamięci i stronicowania](../profiling/memory-and-paging-performance-rules.md)|Reguły analizujące pamięć zarządzaną i zachowanie stronicowania aplikacji.|
|[Reguły korzystania z narzędzi profilowania](../profiling/profiling-tools-usage-rules.md)|Reguły ułatwiające efektywne korzystanie z narzędzi profilowania.|
|[Reguły wydajności monitorowania zasobu](../profiling/resource-monitoring-performance-rules.md)|Komunikaty informacyjne dotyczące wykorzystania procesora i pamięci w przebiegu profilowania.|
