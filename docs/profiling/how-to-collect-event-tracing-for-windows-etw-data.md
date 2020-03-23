---
title: 'Jak: Zbieranie danych śledzenia zdarzeń dla systemu Windows (ETW) | Dokumenty firmy Microsoft'
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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2fa0547682351d1a7ba4efe4ce3b4350b906462c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779028"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Jak: Zbieranie danych śledzenia zdarzeń dla systemu Windows (ETW)

Śledzenie zdarzeń dla systemu Windows (ETW) to wydajna funkcja śledzenia na poziomie jądra, która umożliwia jądro dziennika profilera lub zdarzenia zdefiniowane przez aplikację. Dane zbierane od dostawcy zdarzeń można wyświetlać tylko za pomocą opcji /**Summary:ETW** narzędzia wiersza polecenia [VSPerfReport.](../profiling/vsperfreport.md) Ten raport służy do określenia, gdzie występują problemy z wydajnością w aplikacji.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki profiler programu Visual Studio zbiera dane na tych platformach. Aplikacje platformy uniwersalnej systemu Windows wymagają również nowych technik zbierania. Zobacz [Narzędzia wydajności w aplikacjach dla systemów Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-enable-event-trace-providers"></a>Aby włączyć dostawców śledzenia zdarzeń

1. W **Eksploratorze wydajności**kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij polecenie **Właściwości**.

2. Na **stronach właściwości**kliknij właściwości **Zdarzenia systemu Windows.**

3. W **wybierz dostawcę śledzenia zdarzeń do zbierania danych z** listy wybierz dostawców zdarzeń, które mają być używane do profilowania aplikacji.

## <a name="see-also"></a>Zobacz też

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
