---
title: 'Porady: zbieranie danych licznika Procesora | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.property.cpucounters
helpviewer_keywords:
- profiling tools, using portable CPU counters
- performance tools, portable CPU counters
ms.assetid: 102fb6ca-5fbf-4b05-925f-56912ce3f44b
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46ade222b6032baca17afe37d72dd6e5657ae1c2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51763400"
---
# <a name="how-to-collect-cpu-counter-data"></a>Porady: zbieranie danych licznika procesora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Licznik zdarzeń procesora CPU jest używane do zbierania danych wydajności specyficzne dla sprzętu. W tym temacie opisano zbieranie danych licznika zdarzeń, gdy używasz metoda profilowania instrumentacji.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Występują dwa typy zdarzeń licznika procesora CPU:  
  
- Zdarzenia przenośne — zdarzenia procesora CPU, które mogą być zbierane, niezależnie od określonego procesora CPU.  
  
- Zdarzenia platformy — zdarzenia procesora CPU, które są ściśle do określonego procesora CPU.  
  
  Zdarzenia przenośne zawierają ogólne zdarzeń, takich jak instrukcje wycofana i nie został zatrzymany cykle, zdarzenia buforu procesora CPU, rozgałęziania zdarzeń i zdarzenia pamięci podręcznej L2. Liczniki zdarzeń dostępną platformę są określane przez producenta procesora.  
  
  Kategorie zdarzeń mogą być współużytkowane między liczniki przenośne i platformy. Na przykład następujące kategorie danych są często wspólny dla obu typów:  
  
- Zdarzenia pamięci.  
  
- Zdarzenia frontonu.  
  
- Zdarzenia dotyczące gałęzi.  
  
  Można zbierać dane licznika wydajności w Profiler dwa sposoby:  
  
- Podczas profilowania za pomocą Instrumentacji, zbieranie danych z co najmniej jeden licznik.  
  
- Określ zdarzeń licznika jako interwał próbkowania, podczas profilowania za pomocą próbkowania. Aby uzyskać więcej informacji, zobacz [porady: Wybieranie zdarzeń próbkowania](../profiling/how-to-choose-sampling-events.md).  
  
### <a name="to-collect-cpu-performance-counter-data-when-you-profile-by-instrumentation"></a>Do zbierania danych licznika wydajności procesora CPU podczas profilowania za pomocą Instrumentacji  
  
1.  W sesji wydajności **stron właściwości**, kliknij przycisk **liczniki procesora CPU.**  
  
2.  Wybierz **zbierania liczników Procesora** pole wyboru.  
  
3.  Rozwiń **dostępnych liczników wydajności** drzewa, aż znajdziesz próbkowane zdarzenia, które mają być zbierane.  
  
4.  Dla każdego zdarzenia, które mają być zbierane, wybierz zdarzenie, a następnie kliknij strzałkę w prawo, aby dodać wydarzenie do **wybrane liczniki** listy.  
  
    > [!NOTE]
    >  **Dostępne liczniki wydajności** jest włączona, tylko jeśli wybierzesz **liczniki CPU zbieranie** pole wyboru.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Właściwości sesji wydajności](../profiling/performance-session-properties.md)   
 [CPU i liczniki Windows](../profiling/cpu-and-windows-counters.md)   
 [Instrukcje: wybieranie zdarzeń próbkowania](../profiling/how-to-choose-sampling-events.md)



