---
title: Zbierz dane śledzenia zdarzeń systemu Windows (ETW) | Microsoft Docs
description: Dowiedz się, jak używać funkcji Śledzenie zdarzeń systemu Windows (ETW) do określenia, gdzie występują problemy z wydajnością w aplikacji. Dane można przeglądać za pomocą VSPerfReport.exe.
ms.custom: SEO-VS-2020
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
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 77ddd22450786091c5240f26213633a7935c03dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886291"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Instrukcje: zbieranie danych śledzenia zdarzeń dla systemu Windows (ETW)

Śledzenie zdarzeń systemu Windows (ETW) to wydajna funkcja śledzenia na poziomie jądra, która umożliwia jądro dzienników profilera lub zdarzenia zdefiniowane przez aplikację. Dane zbierane od dostawcy zdarzeń mogą być wyświetlane tylko przy użyciu opcji/**Summary: ETW** w narzędziu wiersza polecenia [VSPerfReport](../profiling/vsperfreport.md) . Możesz użyć tego raportu, aby określić, gdzie występują problemy z wydajnością w aplikacji.

> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje platformy UWP wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="to-enable-event-trace-providers"></a>Aby włączyć dostawców śledzenia zdarzeń

1. W **Eksplorator wydajności** kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij polecenie **Właściwości**.

2. Na **stronie właściwości** kliknij pozycję właściwości **zdarzeń systemu Windows** .

3. Z listy **Wybierz dostawcę śledzenia zdarzeń do zbierania danych z** wybierz dostawców zdarzeń, których chcesz użyć do profilowania aplikacji.

## <a name="see-also"></a>Zobacz też

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
