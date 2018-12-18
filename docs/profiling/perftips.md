---
title: Perftip | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2933f29cb3668e12731e79151ba17480dda96ea5
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220558"
---
# <a name="perftips"></a>Perftip
Debuger programu Visual Studio *Perftip* i zintegrowane z debugerem **narzędzia diagnostyczne** ułatwiają monitorowanie i analizowanie wydajności aplikacji podczas debugowania.  
  
 Mimo że narzędzia diagnostyczne zintegrowane z debugerem to doskonały sposób stać się znane problemy z wydajnością podczas opracowywania, debuger może mieć znaczący wpływ na wydajność aplikacji. Aby zbierać dokładniejsze dane dotyczące wydajności, należy rozważyć użycie narzędzia diagnostyczne Visual Studio, działających poza debugerem zbyt jako dodatkową część swoje badania wydajności. Zobacz [uruchamianie narzędzi z lub bez debugera profilowania](../profiling/running-profiling-tools-with-or-without-the-debugger.md).  
  
## <a name="perftips"></a>Perftip  
 Gdy debuger zatrzymuje wykonywanie w punkcie przerwania lub operacji przechodzenia krok po kroku, czas, jaki upłynął od przerwania i poprzedniego punktu przerwania pojawia się jako wskazówkę w oknie edytora. Aby uzyskać więcej informacji, zobacz [Perftip: informacje dotyczące wydajności w skrócie podczas debugowania za pomocą programu Visual Studio](https://blogs.msdn.microsoft.com/devops/2014/08/18/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/).  
  
 ![PerfTip](../profiling/media/dbgdiag_perf_perftip.png "DBGDIAG_PERF_PerfTip")  
  
## <a name="diagnostics-tools-window"></a>Okno narzędzia diagnostyczne  
 Punkty przerwania i danych o chronometrażu skojarzone są rejestrowane w **narzędzia diagnostyczne** okna.  
  
 Pokazano grafiki **narzędzia diagnostyczne** okna w Visual Studio 2015 Update 1:  
  
 ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
-   **Zdarzenia przerwania** osi czasu Oznacz punkty przerwania, które zostały trafień w sesji debugowania. Kliknij zdarzenie, aby go zaznaczyć **debugera** listy szczegóły.  
  
-   **Wykorzystanie procesora CPU** wykres przedstawia zmiany w użyciu procesora CPU dla wszystkich rdzeni procesora w sesji debugowania.  
  
-   **Zdarzenia** listę **debugera** w okienku szczegółów obejmują elementy, dla każdego zdarzenia przerwania.  
  
-   **Czas trwania** kolumny zdarzeniu przerwania przedstawia czas, jaki upłynął od zdarzenia i poprzedniego punktu przerwania.  
  
## <a name="turn-perftips-on-or-off"></a>Włączanie funkcji PerfTips i wyłączanie  
 Aby włączyć lub wyłączyć Perftip:  
  
1.  Na **debugowania** menu, wybierz **opcje**.  
  
2.  Zaznacz lub wyczyść **Pokaż upłynęło PerfTip podczas debugowania**.  
  
## <a name="turn-the-diagnostic-tools-window-on-or-off"></a>Włącz okno narzędzia diagnostyczne lub wyłącz  
 Aby włączyć lub wyłączyć w oknie narzędzia diagnostyczne:  
  
1.  Na **debugowania** menu, wybierz **opcje**.  
  
2.  Zaznacz lub wyczyść **Włącz narzędzia diagnostyczne podczas debugowania**.

## <a name="see-also"></a>Zobacz także
 [Profilowanie w programie Visual Studio](../profiling/index.md)  
 [Pierwsze spojrzenie na narzędziach profilowania](../profiling/profiling-feature-tour.md)
