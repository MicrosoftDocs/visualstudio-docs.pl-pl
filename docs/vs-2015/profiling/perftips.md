---
title: Funkcja PerfTip | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa56b6731e359db486a111194a710069d41a2f1b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295868"
---
# <a name="perftips"></a>Wskazówki dotyczące wydajności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debuger programu Visual Studio *Funkcja PerfTip* i zintegrowany z debugerem **Narzędzia diagnostyczne** ułatwia monitorowanie i analizowanie wydajności aplikacji podczas debugowania.  
  
 Chociaż narzędzia diagnostyczne zintegrowane z debugerem są doskonałym sposobem, aby poznać problemy z wydajnością podczas opracowywania, debuger może mieć znaczący wpływ na wydajność aplikacji. Aby zebrać dokładniejsze dane dotyczące wydajności, należy rozważyć użycie narzędzi diagnostycznych programu Visual Studio, które są uruchamiane poza debugerem, jako dodatkową częścią dochodzeń związanych z wydajnością. Zobacz [Uruchamianie narzędzi profilowania bez debugowania](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01).  
  
## <a name="perftips"></a>Wskazówki dotyczące wydajności  
 Gdy debuger przerywa wykonywanie w punkcie przerwania lub operacji krokowej, czas między przerwaniem a poprzednim punktem przerwania pojawia się jako Porada w oknie edytora. Aby uzyskać więcej informacji, zobacz [Funkcja PerfTip: informacje o wydajności w skrócie, podczas debugowania w programie Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/).  
  
 ![Element PerfTip dla](../profiling/media/dbgdiag-perf-perftip.png "DBGDIAG_PERF_PerfTip")  
  
## <a name="diagnostics-tools-window"></a>Okno narzędzi diagnostycznych  
 Punkty przerwania i powiązane dane chronometrażu danych chronometrażu są rejestrowane w oknie narzędzia diagnostyczne  
  
 Na poniższej ilustracji przedstawiono okno narzędzia diagnostyczne w programie Visual Studio 2015 Update 1:  
  
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
