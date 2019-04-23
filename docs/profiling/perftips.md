---
title: Perftip | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0713ae13038991ec65dcbebe350c9085f7d6a94a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60103423"
---
# <a name="perftips"></a>Perftip
Debuger programu Visual Studio *Perftip* i zintegrowane z debugerem **narzędzia diagnostyczne** ułatwiają monitorowanie i analizowanie wydajności aplikacji podczas debugowania.

 Mimo że narzędzia diagnostyczne zintegrowane z debugerem to doskonały sposób stać się znane problemy z wydajnością podczas opracowywania, debuger może mieć znaczący wpływ na wydajność aplikacji. Aby zbierać dokładniejsze dane dotyczące wydajności, należy rozważyć użycie narzędzia diagnostyczne Visual Studio, działających poza debugerem zbyt jako dodatkową część swoje badania wydajności. Zobacz [uruchamianie narzędzi z lub bez debugera profilowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="perftips"></a>Perftip
 Gdy debuger zatrzymuje wykonywanie w punkcie przerwania lub operacji przechodzenia krok po kroku, czas, jaki upłynął od przerwania i poprzedniego punktu przerwania pojawia się jako wskazówkę w oknie edytora. Aby uzyskać więcej informacji, zobacz [Perftip: Wydajność informacji o skrócie podczas debugowania przy użyciu programu Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/).

 ![PerfTip](../profiling/media/dbgdiag_perf_perftip.png "DBGDIAG_PERF_PerfTip")

## <a name="diagnostics-tools-window"></a>Okno narzędzia diagnostyczne
 Punkty przerwania i danych o chronometrażu skojarzone są rejestrowane w **narzędzia diagnostyczne** okna.

 Pokazano grafiki **narzędzia diagnostyczne** okna w Visual Studio 2015 Update 1:

 ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")

- **Zdarzenia przerwania** osi czasu Oznacz punkty przerwania, które zostały trafień w sesji debugowania. Kliknij zdarzenie, aby go zaznaczyć **debugera** listy szczegóły.

- **Wykorzystanie procesora CPU** wykres przedstawia zmiany w użyciu procesora CPU dla wszystkich rdzeni procesora w sesji debugowania.

- **Zdarzenia** listę **debugera** w okienku szczegółów obejmują elementy, dla każdego zdarzenia przerwania.

- **Czas trwania** kolumny zdarzeniu przerwania przedstawia czas, jaki upłynął od zdarzenia i poprzedniego punktu przerwania.

## <a name="turn-perftips-on-or-off"></a>Włączanie funkcji PerfTips i wyłączanie
 Aby włączyć lub wyłączyć Perftip:

1. Na **debugowania** menu, wybierz **opcje**.

2. Zaznacz lub wyczyść **Pokaż upłynęło PerfTip podczas debugowania**.

## <a name="turn-the-diagnostic-tools-window-on-or-off"></a>Włącz okno narzędzia diagnostyczne lub wyłącz
 Aby włączyć lub wyłączyć w oknie narzędzia diagnostyczne:

1. Na **debugowania** menu, wybierz **opcje**.

2. Zaznacz lub wyczyść **Włącz narzędzia diagnostyczne podczas debugowania**.

## <a name="see-also"></a>Zobacz także
- [Profilowanie w programie Visual Studio](../profiling/index.md)
- [Pierwsze spojrzenie na narzędziach profilowania](../profiling/profiling-feature-tour.md)
