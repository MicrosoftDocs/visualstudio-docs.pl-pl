---
title: 'Instrukcje: zbieranie danych licznika procesora | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.cpucounters
helpviewer_keywords:
- profiling tools, using portable CPU counters
- performance tools, portable CPU counters
ms.assetid: 102fb6ca-5fbf-4b05-925f-56912ce3f44b
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 76dac6e20cc85eeb5784b0b6e29ee8d1b23fbd92
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64823411"
---
# <a name="how-to-collect-cpu-counter-data"></a>Porady: zbieranie danych licznika procesora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Licznik zdarzeń procesora CPU służy do zbierania danych wydajności związanych z sprzętem. W tym temacie pokazano, jak zbierać dane licznika zdarzeń przy użyciu metody profilowania Instrumentacji.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Występują dwa typy zdarzeń licznika procesora:  
  
- Zdarzenia przenośne — zdarzenia procesora CPU, które mogą być zbierane niezależnie od określonego procesora.  
  
- Zdarzenia platformy — zdarzenia procesora CPU, które są połączone z określonym procesorem CPU.  
  
  Zdarzenia przenośne obejmują zdarzenia ogólne, takie jak wycofane i niezatrzymane cykle, zdarzenia buforu procesora, zdarzenia rozgałęzienia i zdarzenia pamięci podręcznej L2. Dostępne liczniki zdarzeń platformy są określane przez producenta procesora.  
  
  Kategorie zdarzeń mogą być współużytkowane przez liczniki przenośne i platformy. Na przykład następujące kategorie danych często są wspólne dla obu typów:  
  
- Zdarzenia pamięci.  
  
- Zdarzenia frontonu.  
  
- Zdarzenia gałęzi.  
  
  Dane licznika wydajności można zbierać na dwa sposoby:  
  
- Zbieraj dane z co najmniej jednego licznika podczas profilowania przez instrumentację.  
  
- Określ zdarzenie licznika jako interwał próbkowania podczas profilowania przez próbkowanie. Aby uzyskać więcej informacji, zobacz [How to: Choose Events próbking](../profiling/how-to-choose-sampling-events.md).  
  
### <a name="to-collect-cpu-performance-counter-data-when-you-profile-by-instrumentation"></a>Zbieranie danych licznika wydajności procesora CPU podczas profilowania przez instrumentację  
  
1. Na **stronie właściwości**sesji wydajności kliknij pozycję **liczniki procesora.**  
  
2. Zaznacz pole wyboru **Zbieraj liczniki procesora CPU** .  
  
3. Rozwiń drzewo **dostępne liczniki wydajności** , aż znajdziesz Przykładowe zdarzenia, które chcesz zebrać.  
  
4. Dla każdego zdarzenia, które chcesz zebrać, wybierz zdarzenie, a następnie kliknij strzałkę w prawo, aby dodać zdarzenie do listy **wybrane liczniki** .  
  
    > [!NOTE]
    > **Dostępne liczniki wydajności** są włączone tylko po zaznaczeniu pola wyboru **Zbieraj liczniki procesora CPU** .  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Właściwości sesji wydajności](../profiling/performance-session-properties.md)   
 [Liczniki procesora i systemu Windows](../profiling/cpu-and-windows-counters.md)   
 [Instrukcje: wybieranie zdarzeń próbkowania](../profiling/how-to-choose-sampling-events.md)
