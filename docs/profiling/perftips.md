---
title: Funkcja PerfTip | Microsoft Docs
description: Dowiedz się, jak używać debugera programu Visual Studio funkcja PerfTip i zintegrowanych narzędzia diagnostyczne do monitorowania i analizowania wydajności aplikacji podczas debugowania.
ms.date: 9/11/2020
ms.topic: how-to
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 73d6558264bb51f011d8f04b5a3096e95702c49b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892349"
---
# <a name="perftips"></a>Wskazówki dotyczące wydajności

Debuger programu Visual Studio *Funkcja PerfTip* i zintegrowany z debugerem **Narzędzia diagnostyczne** ułatwia monitorowanie i analizowanie wydajności aplikacji podczas debugowania.

Chociaż narzędzia diagnostyczne zintegrowane z debugerem są doskonałym sposobem, aby poznać problemy z wydajnością podczas opracowywania, debuger może mieć znaczący wpływ na wydajność aplikacji. Aby zebrać dokładniejsze dane dotyczące wydajności, należy rozważyć użycie narzędzi w profilerze wydajności jako dodatkowej części dochodzeń dotyczących wydajności. Zobacz [Uruchamianie narzędzi profilowania z debugerem lub bez niego](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="perftips"></a>Wskazówki dotyczące wydajności

Gdy debuger przerywa wykonywanie w punkcie przerwania lub operacji krokowej, czas między przerwaniem a poprzednim punktem przerwania pojawia się jako Porada w oknie edytora. Aby uzyskać więcej informacji, zobacz [Funkcja PerfTip: informacje o wydajności w skrócie, podczas debugowania w programie Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/).

![Element PerfTip dla](../profiling/media/dbgdiag_perf_perftip.png "DBGDIAG_PERF_PerfTip")

## <a name="diagnostics-tools-window"></a>Okno narzędzi diagnostycznych

Punkty przerwania i powiązane dane chronometrażu są rejestrowane w oknie **Narzędzia diagnostyczne** .

Na poniższej ilustracji przedstawiono okno **Narzędzia diagnostyczne** .

![Zrzut ekranu okna narzędzia diagnostyczne w debugerze programu Visual Studio, pokazujący oś czasu i wykresy zdarzeń dla pamięci i użycia procesora CPU.](../profiling/media/diagnostictools-update1.png)

- Oś czasu dla **zdarzeń przerwania** oznacza punkty przerwania, które zostały trafione w sesji debugowania. Kliknij zdarzenie, aby wybrać je na liście szczegóły **debugera** .

- Wykres **użycia procesora CPU** przedstawia zmianę użycia procesora CPU we wszystkich rdzeniach procesora w sesji debugowania.

- Lista **zdarzeń** w okienku szczegółów **debugera** zawiera elementy dla każdego zdarzenia przerwania.

- Kolumna **Duration** zdarzenia Break Wyświetla czas, który upłynął między zdarzeniem a poprzednim punktem przerwania.

## <a name="turn-perftips-on-or-off"></a>Włącz lub Wyłącz funkcja PerfTip

Aby włączyć lub wyłączyć funkcja PerfTip:

1. W menu **debugowanie** wybierz **Opcje**.

2. Zaznacz lub wyczyść **Widok element PerfTip dla, który upłynął podczas debugowania**.

## <a name="turn-the-diagnostic-tools-window-on-or-off"></a>Włącz lub Wyłącz okno narzędzia diagnostyczne

Aby włączyć lub wyłączyć okno narzędzia diagnostyczne:

1. W menu **debugowanie** wybierz **Opcje**.

2. Zaznacz lub wyczyść **opcję Włącz narzędzia diagnostyczne podczas debugowania**.

## <a name="see-also"></a>Zobacz też

- [Profilowanie w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
