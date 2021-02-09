---
title: Zbieranie danych licznika procesora CPU | Microsoft Docs
description: Dowiedz się, jak używać liczników zdarzeń procesora (sprzętu) do zbierania danych wydajności związanych z konkretnym sprzętem. W tym artykule wymieniono różne typy zdarzeń.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.cpucounters
helpviewer_keywords:
- profiling tools, using portable CPU counters
- performance tools, portable CPU counters
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0a085f732263e0d2eb3d7e1f211c54fac46fbc6e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876904"
---
# <a name="how-to-collect-cpu-counter-data"></a>Instrukcje: zbieranie danych licznika procesora CPU

Licznik zdarzeń procesora CPU służy do zbierania danych wydajności związanych z sprzętem. W tym artykule pokazano, jak zbierać dane licznika zdarzeń przy użyciu metody profilowania Instrumentacji.

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

## <a name="to-collect-cpu-performance-counter-data-when-you-profile-by-instrumentation"></a>Zbieranie danych licznika wydajności procesora CPU podczas profilowania przez instrumentację

1. Na **stronie właściwości** sesji wydajności kliknij pozycję **liczniki procesora.**

2. Zaznacz pole wyboru **Zbieraj liczniki procesora CPU** .

3. Rozwiń drzewo **dostępne liczniki wydajności** , aż znajdziesz Przykładowe zdarzenia, które chcesz zebrać.

4. Dla każdego zdarzenia, które chcesz zebrać, wybierz zdarzenie, a następnie kliknij strzałkę w prawo, aby dodać zdarzenie do listy **wybrane liczniki** .

    > [!NOTE]
    > **Dostępne liczniki wydajności** są włączone tylko po zaznaczeniu pola wyboru **Zbieraj liczniki procesora CPU** .

## <a name="see-also"></a>Zobacz też

[Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md) 
 [Właściwości](../profiling/performance-session-properties.md) 
 sesji wydajności Liczniki procesora i [systemu Windows](../profiling/cpu-and-windows-counters.md) 
 [Instrukcje: Wybieranie zdarzeń próbkowania](../profiling/how-to-choose-sampling-events.md)
