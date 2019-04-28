---
title: 'Instrukcje: Zbieranie zdarzeń śledzenia for Windows (ETW) — dane | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432820"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Instrukcje: Zbieraj zdarzenia śledzenia dla Windows (ETW) danych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Śledzenie zdarzeń dla Windows (ETW) jest mechanizmem wydajne śledzenia na poziomie jądra, umożliwiającą jądra dziennika profilera lub zdarzeń zdefiniowanych przez aplikację. Dane, które są zbierane z Dostawca zdarzeń można wyświetlić tylko przy użyciu /**Summary: ETW** opcji [VSPerfReport](../profiling/vsperfreport.md) narzędzie wiersza polecenia. Ten raport służy do określenia, gdzie występują problemy z wydajnością w aplikacji.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje Windows Store również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### <a name="to-enable-event-trace-providers"></a>Aby włączyć dostawców śledzenia zdarzeń  
  
1. W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij **właściwości**.  
  
2. W **stron właściwości**, kliknij przycisk **zdarzeń Windows** właściwości.  
  
3. W **dostawca śledzenia zdarzeń wybierz opcję, aby zebrać dane z** wybierz dostawców zdarzeń, które chcesz użyć do profilu aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)
