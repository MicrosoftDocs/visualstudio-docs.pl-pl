---
title: 'DA0501: Średnie wykorzystanie CPU przez proces poddawany profilowaniu. | Microsoft Docs'
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
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 076afd65d356f319357221c0d33489895311dcc3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759551"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: Średnie wykorzystanie CPU przez proces poddawany profilowaniu.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identyfikator reguły | DA501 |  
| Kategoria | Monitorowanie zasobów |  
| Metoda profilowania | Wszystkie |  
| Komunikat | Średnie użycie procesora CPU przez proces poddawany profilowaniu. |  
| Typ reguły | Informacji |  
  
 Podczas profilowania za pomocą próbkowania pamięci platformy .NET i metod rywalizacji zasobów musi zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  
  
## <a name="rule-description"></a>Opis reguły  
 Ten komunikat raporty procent czasu procesor był zajęty, wykonując instrukcje z aplikacji. Wystąpienia wartości zgłoszonej jest średnią we wszystkich interwałach pomiarowych, w których była aktywna PROFILOWANEGO procesu. Wartość może być większa niż 100% na maszynie z więcej niż jednego procesora.  
  
## <a name="how-to-use-rule-data"></a>Sposób użycia danych reguły  
 Aby porównać wydajność różnych wersji lub kompilacjach programu lub aby zrozumieć wydajność aplikacji w ramach scenariuszy testowania różnych, należy użyć wartości reguły.



