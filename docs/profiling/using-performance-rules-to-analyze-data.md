---
title: Korzystanie z reguł wydajności do analizowania danych | Microsoft Docs
description: Dowiedz się, jak ostrzeżenia o wydajności w programie Visual Studio narzędzia profilowania wskazują problemy w profilowanej aplikacji, która może spowalniać wykonywanie programu.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1deed23e-b31b-4714-982f-08ceebfc3096
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9a896e128f949897b64fd6a273784f39543a9663
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721141"
---
# <a name="use-performance-rules-to-analyze-data"></a>Korzystanie z reguł wydajności do analizowania danych
Ostrzeżenia dotyczące wydajności [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania wskazują problemy w profilowanej aplikacji, która może spowalniać wykonywanie programu. Ostrzeżenia mogą również wskazywać, że może zajść potrzeba zmiany metod zbierania danych w celu zebrania bardziej użytecznych informacji. Ostrzeżenia o wydajności są generowane automatycznie w sesji profilowania. Ostrzeżenia są wyświetlane w oknie **Lista błędów** , gdy plik danych profilowania zostanie otwarty w programie Visual Studio. W oknie **Lista błędów** można zlokalizować kod źródłowy problemu i wyświetlić szczegółowe informacje o błędzie, takie jak informacje o sposobie rozwiązania problemu. Możesz również wyłączyć ostrzeżenia, które nie są interesujące.

> [!NOTE]
> Ostrzeżenia wydajności profilera są generowane przez analizę dynamiczną wykonywania programu i są niezależne od ostrzeżeń dotyczących analizy kodu. Analiza kodu może również generować ostrzeżenia wydajności dla kodu zarządzanego na podstawie statycznej analizy kodu źródłowego. Aby uzyskać więcej informacji, zobacz Analizowanie [ostrzeżeń dotyczących](/dotnet/fundamentals/code-analysis/quality-rules/performance-warnings)jakości i wydajności [kodu zarządzanego](../code-quality/code-analysis-for-managed-code-overview.md) .

## <a name="in-this-section"></a>W tej sekcji
- [Instrukcje: wyświetlanie ostrzeżeń dotyczących wydajności](../profiling/how-to-view-performance-warnings.md)

 Zawiera informacje dotyczące sposobu otwierania okna **Lista błędów** w celu wyświetlenia ostrzeżeń wydajności profilera.

- [Instrukcje: Konfigurowanie reguł wydajności](../profiling/how-to-configure-performance-rules.md)

 Zawiera informacje na temat włączania lub wyłączania poszczególnych ostrzeżeń dotyczących wydajności.

- [Reguły wydajności — dokumentacja](../profiling/performance-rules-reference.md)

 Zawiera szczegółowe informacje na temat ostrzeżeń wydajności profilera
