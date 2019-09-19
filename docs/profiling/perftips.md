---
title: Funkcja PerfTip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 93703bdd4bf2f0046176ceb1f6febd5564f61705
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128308"
---
# <a name="perftips"></a>Wskazówki dotyczące wydajności
Debuger programu Visual Studio *Funkcja PerfTip* i zintegrowany z debugerem **Narzędzia diagnostyczne** ułatwia monitorowanie i analizowanie wydajności aplikacji podczas debugowania.

 Chociaż narzędzia diagnostyczne zintegrowane z debugerem są doskonałym sposobem, aby poznać problemy z wydajnością podczas opracowywania, debuger może mieć znaczący wpływ na wydajność aplikacji. Aby zebrać dokładniejsze dane dotyczące wydajności, należy rozważyć użycie narzędzi diagnostycznych programu Visual Studio, które są uruchamiane poza debugerem, jako dodatkową częścią dochodzeń związanych z wydajnością. Zobacz [uruchamianie narzędzi z lub bez debugera profilowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="perftips"></a>Wskazówki dotyczące wydajności
 Gdy debuger przerywa wykonywanie w punkcie przerwania lub operacji krokowej, czas między przerwaniem a poprzednim punktem przerwania pojawia się jako Porada w oknie edytora. Aby uzyskać więcej informacji, [Zobacz funkcja PerfTip: Błyskawiczne informacje o wydajności podczas debugowania w programie Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/).

 ![PerfTip](../profiling/media/dbgdiag_perf_perftip.png "DBGDIAG_PERF_PerfTip")

## <a name="diagnostics-tools-window"></a>Okno narzędzi diagnostycznych
 Punkty przerwania i powiązane dane chronometrażu są rejestrowane w oknie **Narzędzia diagnostyczne** .

 Na poniższej ilustracji przedstawiono okno **Narzędzia diagnostyczne** w programie Visual Studio 2015 Update 1:

 ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")

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
- [Pierwsze spojrzenie na narzędziach profilowania](../profiling/profiling-feature-tour.md)
