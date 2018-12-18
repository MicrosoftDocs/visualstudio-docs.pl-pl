---
title: Perftip | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be41b40dc4f20a0f983da1bf9e70c92ea4c2095f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51803100"
---
# <a name="perftips"></a>Perftip
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debuger programu Visual Studio *Perftip* i zintegrowane z debugerem **narzędzia diagnostyczne** ułatwiają monitorowanie i analizowanie wydajności aplikacji podczas debugowania.  
  
 Mimo że narzędzia diagnostyczne zintegrowane z debugerem to doskonały sposób stać się znane problemy z wydajnością podczas opracowywania, debuger może mieć znaczący wpływ na wydajność aplikacji. Aby zbierać dokładniejsze dane dotyczące wydajności, należy rozważyć użycie narzędzia diagnostyczne Visual Studio, działających poza debugerem zbyt jako dodatkową część swoje badania wydajności. Zobacz [uruchamianie narzędzi profilowania bez debugowania](http://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01).  
  
## <a name="perftips"></a>Perftip  
 Gdy debuger zatrzymuje wykonywanie w punkcie przerwania lub operacji przechodzenia krok po kroku, czas, jaki upłynął od przerwania i poprzedniego punktu przerwania pojawia się jako wskazówkę w oknie edytora. Aby uzyskać więcej informacji, zobacz [Perftip: informacje dotyczące wydajności w skrócie podczas debugowania za pomocą programu Visual Studio](http://blogs.msdn.com/b/visualstudioalm/archive/2014/08/18/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio.aspx).  
  
 ![PerfTip](../profiling/media/dbgdiag-perf-perftip.png "DBGDIAG_PERF_PerfTip")  
  
## <a name="diagnostics-tools-window"></a>Okno narzędzia diagnostyczne  
 Punkty przerwania i skojarzone chronometrażu danych o chronometrażu są rejestrowane w oknie narzędzia diagnostyczne  
  
 Poniższa ilustracja przedstawia okno narzędzia diagnostyczne w Visual Studio 2015 Update 1:  
  
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



