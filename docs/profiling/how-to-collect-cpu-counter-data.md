---
title: 'Instrukcje: Zbieranie danych licznika Procesora | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.cpucounters
helpviewer_keywords:
- profiling tools, using portable CPU counters
- performance tools, portable CPU counters
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ab80ba010a91df11efac21366a812015defa3b23
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53897238"
---
# <a name="how-to-collect-cpu-counter-data"></a>Instrukcje: Zbieranie danych licznika procesora CPU

Licznik zdarzeń procesora CPU jest używane do zbierania danych wydajności specyficzne dla sprzętu. W tym artykule pokazano, jak zbieranie danych licznika zdarzeń, gdy używasz metoda profilowania instrumentacji.

Występują dwa typy zdarzeń licznika procesora CPU:

- Zdarzenia przenośne — zdarzenia procesora CPU, które mogą być zbierane, niezależnie od określonego procesora CPU.

- Zdarzenia platformy — zdarzenia procesora CPU, które są ściśle do określonego procesora CPU.

  Zdarzenia przenośne zawierają ogólne zdarzeń, takich jak instrukcje wycofana i nie został zatrzymany cykle, zdarzenia buforu procesora CPU, rozgałęziania zdarzeń i zdarzenia pamięci podręcznej L2. Liczniki zdarzeń dostępną platformę są określane przez producenta procesora.

  Kategorie zdarzeń mogą być współużytkowane między liczniki przenośne i platformy. Na przykład następujące kategorie danych są często wspólny dla obu typów:

- Zdarzenia pamięci.

- Zdarzenia frontonu.

- Zdarzenia dotyczące gałęzi.

  Można zbierać dane licznika wydajności w profiler dwa sposoby:

- Podczas profilowania za pomocą Instrumentacji, zbieranie danych z co najmniej jeden licznik.

- Określ zdarzeń licznika jako interwał próbkowania, podczas profilowania za pomocą próbkowania. Aby uzyskać więcej informacji, zobacz [jak: Wybieranie zdarzeń próbkowania](../profiling/how-to-choose-sampling-events.md).

## <a name="to-collect-cpu-performance-counter-data-when-you-profile-by-instrumentation"></a>Do zbierania danych licznika wydajności procesora CPU podczas profilowania za pomocą Instrumentacji

1. W sesji wydajności **stron właściwości**, kliknij przycisk **liczniki procesora CPU.**

2. Wybierz **zbierania liczników Procesora** pole wyboru.

3. Rozwiń **dostępnych liczników wydajności** drzewa, aż znajdziesz próbkowane zdarzenia, które mają być zbierane.

4. Dla każdego zdarzenia, które mają być zbierane, wybierz zdarzenie, a następnie kliknij strzałkę w prawo, aby dodać wydarzenie do **wybrane liczniki** listy.

    > [!NOTE]
    > **Dostępne liczniki wydajności** jest włączona, tylko jeśli wybierzesz **liczniki CPU zbieranie** pole wyboru.

## <a name="see-also"></a>Zobacz także

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)  
[Właściwości sesji wydajności](../profiling/performance-session-properties.md)  
[Liczniki procesora CPU i systemu Windows](../profiling/cpu-and-windows-counters.md)  
[Instrukcje: Wybieranie zdarzeń pobierania próbek](../profiling/how-to-choose-sampling-events.md)