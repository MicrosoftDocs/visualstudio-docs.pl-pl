---
title: Jak zbierać dane śledzenia zdarzeń systemu Windows (ETW) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0545ee7fe64d26e21d2a9f34def8dd618c08e630
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85330911"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Instrukcje: zbieranie danych śledzenia zdarzeń dla systemu Windows (ETW)

Śledzenie zdarzeń systemu Windows (ETW) to wydajna funkcja śledzenia na poziomie jądra, która umożliwia jądro dzienników profilera lub zdarzenia zdefiniowane przez aplikację. Dane zbierane od dostawcy zdarzeń mogą być wyświetlane tylko przy użyciu opcji/**Summary: ETW** w narzędziu wiersza polecenia [VSPerfReport](../profiling/vsperfreport.md) . Możesz użyć tego raportu, aby określić, gdzie występują problemy z wydajnością w aplikacji.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-enable-event-trace-providers"></a>Aby włączyć dostawców śledzenia zdarzeń

1. W **Eksplorator wydajności**kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij polecenie **Właściwości**.

2. Na **stronie właściwości**kliknij pozycję właściwości **zdarzeń systemu Windows** .

3. Z listy **Wybierz dostawcę śledzenia zdarzeń do zbierania danych z** wybierz dostawców zdarzeń, których chcesz użyć do profilowania aplikacji.

## <a name="see-also"></a>Zobacz też

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
