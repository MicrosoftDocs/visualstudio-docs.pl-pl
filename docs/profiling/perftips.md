---
title: Funkcja PerfTip | Microsoft Docs
ms.date: 9/11/2020
ms.topic: how-to
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f260307b677046be54e6d80b0d8fe122b13292e4
ms.sourcegitcommit: 14637be49401f56341c93043eab560a4ff6b57f6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075473"
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

![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools — Update1")

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

## <a name="see-also"></a>Zobacz także

- [Profilowanie w programie Visual Studio](../profiling/index.yml)
- [Pierwsze spojrzenie na narzędzia profilowania](../profiling/profiling-feature-tour.md)
