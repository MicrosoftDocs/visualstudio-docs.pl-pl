---
title: 'Instrukcje: Zbieranie zdarzeń śledzenia for Windows (ETW) — dane | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f4259a28976f7fc622c0b0cf8948bc2ad891a8b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55024932"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Instrukcje: Zbieraj dane zdarzenia śledzenia dla Windows (ETW)

Śledzenie zdarzeń dla Windows (ETW) jest mechanizmem wydajne śledzenia na poziomie jądra, umożliwiającą jądra dziennika profilera lub zdarzeń zdefiniowanych przez aplikację. Dane, które są zbierane z Dostawca zdarzeń można wyświetlić tylko przy użyciu /**Summary: ETW** opcji [VSPerfReport](../profiling/vsperfreport.md) narzędzie wiersza polecenia. Ten raport służy do określenia, gdzie występują problemy z wydajnością w aplikacji.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-enable-event-trace-providers"></a>Aby włączyć dostawców śledzenia zdarzeń

1. W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij **właściwości**.

2. W **stron właściwości**, kliknij przycisk **zdarzeń Windows** właściwości.

3. W **dostawca śledzenia zdarzeń wybierz opcję, aby zebrać dane z** wybierz dostawców zdarzeń, które chcesz użyć do profilu aplikacji.

## <a name="see-also"></a>Zobacz także

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)