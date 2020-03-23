---
title: 'Jak: Zbieranie danych licznika procesora | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.cpucounters
helpviewer_keywords:
- profiling tools, using portable CPU counters
- performance tools, portable CPU counters
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 98291051a135a95ab72b4c3bfa09743d9620b94e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776374"
---
# <a name="how-to-collect-cpu-counter-data"></a>Instrukcje: zbieranie danych licznika procesora CPU

Licznik zdarzeń procesora CPU służy do zbierania danych wydajności specyficznych dla sprzętu. W tym artykule pokazano, jak zbierać dane licznika zdarzeń podczas korzystania z metody profilowania instrumentacji.

Występują dwa typy zdarzeń licznika procesora CPU:

- Zdarzenia przenośne — zdarzenia procesora CPU, które mogą być zbierane, niezależnie od określonego procesora CPU.

- Zdarzenia platformy — zdarzenia procesora CPU, które są powiązane z określonym procesorem.

  Zdarzenia przenośne obejmują zdarzenia ogólne, takie jak Instrukcje wycofane i Nie zatrzymane cykle, zdarzenia buforu procesora CPU, zdarzenia rozgałęzienia i zdarzenia pamięci podręcznej L2. Liczniki zdarzeń dostępnej platformy są określane przez producenta procesora.

  Kategorie zdarzeń mogą być współużytkowane między licznikami przenośnymi i platformowymi. Na przykład następujące kategorie danych są często wspólne dla obu typów:

- Zdarzenia pamięci.

- Wydarzenia frontowe.

- Zdarzenia oddziału.

  Dane licznika wydajności można zbierać na dwa sposoby w profilu:

- Zbieraj dane z jednego lub więcej liczników podczas profilowania według instrumentacji.

- Określ zdarzenie licznika jako interwał próbkowania podczas profilowania przez próbkowanie. Aby uzyskać więcej informacji, zobacz [Jak: Wybieranie zdarzeń próbkowania](../profiling/how-to-choose-sampling-events.md).

## <a name="to-collect-cpu-performance-counter-data-when-you-profile-by-instrumentation"></a>Aby zbierać dane licznika wydajności procesora podczas profilowania według oprzyrządowania

1. Na stronach **właściwości**sesji wydajności kliknij pozycję **Liczniki procesora CPU.**

2. Zaznacz pole wyboru **Zbieranie liczników procesora** CPU.

3. Rozwiń **Dostępne liczniki wydajności** drzewa, aż znajdziesz przykładowe zdarzenia, które chcesz zebrać.

4. Dla każdego zdarzenia, które chcesz zebrać, wybierz zdarzenie, a następnie kliknij strzałkę w prawo, aby dodać zdarzenie do listy **Wybrane liczniki.**

    > [!NOTE]
    > **Dostępne liczniki wydajności** są włączone tylko wtedy, gdy zaznaczysz pole wyboru **Zbieraj liczniki procesora CPU.**

## <a name="see-also"></a>Zobacz też

[Konfigurowanie sesji](../profiling/configuring-performance-sessions.md)
wydajności[Właściwości](../profiling/performance-session-properties.md)
sesji[procesora CPU i windows liczniki](../profiling/cpu-and-windows-counters.md)
[Jak: Wybierz zdarzenia próbkowania](../profiling/how-to-choose-sampling-events.md)
