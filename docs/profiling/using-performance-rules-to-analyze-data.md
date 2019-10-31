---
title: Korzystanie z reguł wydajności do analizowania danych | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1deed23e-b31b-4714-982f-08ceebfc3096
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc0c1b5245817a8946b1ccbd0fb244b3f0608c6e
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189319"
---
# <a name="use-performance-rules-to-analyze-data"></a>Korzystanie z reguł wydajności do analizowania danych
Ostrzeżenia dotyczące wydajności [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania wskazują problemy w profilowanej aplikacji, która może spowalniać wykonywanie programu. Ostrzeżenia mogą również wskazywać, że może zajść potrzeba zmiany metod zbierania danych w celu zebrania bardziej użytecznych informacji. Ostrzeżenia o wydajności są generowane automatycznie w sesji profilowania. Ostrzeżenia są wyświetlane w oknie **Lista błędów** , gdy plik danych profilowania zostanie otwarty w programie Visual Studio. W oknie **Lista błędów** można zlokalizować kod źródłowy problemu i wyświetlić szczegółowe informacje o błędzie, takie jak informacje o sposobie rozwiązania problemu. Możesz również wyłączyć ostrzeżenia, które nie są interesujące.

> [!NOTE]
> Ostrzeżenia wydajności profilera są generowane przez analizę dynamiczną wykonywania programu i są niezależne od ostrzeżeń dotyczących analizy kodu. Analiza kodu może również generować ostrzeżenia wydajności dla kodu zarządzanego na podstawie statycznej analizy kodu źródłowego. Aby uzyskać więcej informacji, zobacz Analizowanie [ostrzeżeń dotyczących](../code-quality/performance-warnings.md)jakości i wydajności [kodu zarządzanego](../code-quality/code-analysis-for-managed-code-overview.md) .

## <a name="in-this-section"></a>W tej sekcji
- [Instrukcje: wyświetlanie ostrzeżeń dotyczących wydajności](../profiling/how-to-view-performance-warnings.md)

 Zawiera informacje dotyczące sposobu otwierania okna **Lista błędów** w celu wyświetlenia ostrzeżeń wydajności profilera.

- [Instrukcje: konfigurowanie zasad wydajności](../profiling/how-to-configure-performance-rules.md)

 Zawiera informacje na temat włączania lub wyłączania poszczególnych ostrzeżeń dotyczących wydajności.

- [Reguły wydajności — dokumentacja](../profiling/performance-rules-reference.md)

 Zawiera szczegółowe informacje na temat ostrzeżeń wydajności profilera