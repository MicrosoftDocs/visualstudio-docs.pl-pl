---
title: 'DA0502: Maksymalne użycie procesora CPU przez proces poddawany profilowaniu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DA0502
- vs.performance.DA0502
- vs.performance.502
ms.assetid: 1ee53df5-b0dc-4265-9d4f-527830d08725
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd2665e9b8055812678fc1a17c0b9df0f0405e42
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51731252"
---
# <a name="da0502-maximum-cpu-consumption-by-the-process-being-profiled"></a>DA0502: Maksymalne wykorzystanie CPU przez proces poddawany profilowaniu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identyfikator reguły | DA0502 |  
| Kategoria | Monitorowanie zasobów |  
| Metoda profilowania | Wszystkie |  
| Komunikat | Ta reguła jest wyłącznie w celach informacyjnych. Funkcja Process() licznik\\% czasu procesora mierzy użycie Procesora przez profilowany proces. Zgłaszana wartość to maksimum zaobserwowane we wszystkich interwałach pomiarowych. |  
| Typ reguły | Informacyjny |  
  
 Podczas profilowania za pomocą próbkowania pamięci platformy .NET i metod rywalizacji zasobów musi zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  
  
## <a name="rule-description"></a>Opis reguły  
 Ten komunikat zgłasza maksymalny procent czasu procesor był zajęty, wykonując instrukcje z aplikacji. Wystąpienia wartości zgłoszonej jest maksymalną wartość zgłaszaną wśród wszystkich interwałów pomiarowych, w których był aktywny proces poddawany profilowaniu. Wartość procentowa może być większa niż 100% na maszynie z więcej niż jednego procesora.  
  
## <a name="how-to-use-the-rule-data"></a>Sposób użycia danych reguły  
 Użyj wartości reguły, aby porównać wydajność różnych wersji lub kompilacjach programu lub aby zrozumieć wydajność aplikacji w różnych scenariuszach profilowania.



