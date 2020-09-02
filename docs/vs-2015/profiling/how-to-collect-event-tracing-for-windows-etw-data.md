---
title: 'Instrukcje: zbieranie danych śledzenia zdarzeń dla systemu Windows (ETW) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
ms.assetid: aa2261fe-d5f5-49fc-a171-d18842e1dc7d
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9d113a32622c40c68a030fdbc670ec19c6038de2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64810200"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Porady: zbieranie danych śledzenia zdarzeń dla systemu Windows (ETW)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Śledzenie zdarzeń systemu Windows (ETW) to wydajna funkcja śledzenia na poziomie jądra, która umożliwia jądro dzienników profilera lub zdarzenia zdefiniowane przez aplikację. Dane zbierane od dostawcy zdarzeń mogą być wyświetlane tylko przy użyciu opcji/**Summary: ETW** w narzędziu wiersza polecenia [VSPerfReport](../profiling/vsperfreport.md) . Możesz użyć tego raportu, aby określić, gdzie występują problemy z wydajnością w aplikacji.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje ze sklepu Windows wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### <a name="to-enable-event-trace-providers"></a>Aby włączyć dostawców śledzenia zdarzeń  
  
1. W **Eksplorator wydajności**kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij polecenie **Właściwości**.  
  
2. Na **stronie właściwości**kliknij pozycję właściwości **zdarzeń systemu Windows** .  
  
3. Z listy **Wybierz dostawcę śledzenia zdarzeń do zbierania danych z** wybierz dostawców zdarzeń, których chcesz użyć do profilowania aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
