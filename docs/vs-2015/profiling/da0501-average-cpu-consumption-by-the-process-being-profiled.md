---
title: 'DA0501: Średnie użycie Procesora przez profilowany proces. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1462ac73e599b870f015a02998c069f7613be0ae
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54771957"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: Średnie użycie Procesora przez profilowany proces.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rule Id|DA501|  
|Category|Resource Monitoring|  
| Metoda profilowania | Wszystkie |  
| Komunikat | Średnie użycie procesora CPU przez proces poddawany profilowaniu. |  
| Typ reguły | Informacji |  
  
 Podczas profilowania za pomocą próbkowania pamięci platformy .NET i metod rywalizacji zasobów musi zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  
  
## <a name="rule-description"></a>Opis reguły  
 Ten komunikat raporty procent czasu procesor był zajęty, wykonując instrukcje z aplikacji. Wystąpienia wartości zgłoszonej jest średnią we wszystkich interwałach pomiarowych, w których była aktywna PROFILOWANEGO procesu. Wartość może być większa niż 100% na maszynie z więcej niż jednego procesora.  
  
## <a name="how-to-use-rule-data"></a>Sposób użycia danych reguły  
 Aby porównać wydajność różnych wersji lub kompilacjach programu lub aby zrozumieć wydajność aplikacji w ramach scenariuszy testowania różnych, należy użyć wartości reguły.
