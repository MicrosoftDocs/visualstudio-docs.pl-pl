---
title: 'DA0501: Średnie użycie Procesora przez profilowany proces. | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 35ed8409ef59c002903dc26631d0af70e030c070
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53928201"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: Średnie użycie Procesora przez profilowany proces.

|||  
|-|-|  
|Identyfikator reguły|DA501|  
|Kategoria|Monitorowanie zasobów|  
|Metoda profilowania|Wszystkie|  
|Komunikat|Średnie użycie Procesora przez profilowany proces.|  
|Typ reguły|Informacje|  

 Podczas profilowania za pomocą próbkowania pamięci platformy .NET i metod rywalizacji zasobów musi zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  

## <a name="rule-description"></a>Opis reguły  
 Ten komunikat raporty procent czasu procesor był zajęty, wykonując instrukcje z aplikacji. Wystąpienia wartości zgłoszonej jest średnią we wszystkich interwałach pomiarowych, w których była aktywna PROFILOWANEGO procesu. Wartość może być większa niż 100% na maszynie z więcej niż jednego procesora.  

## <a name="how-to-use-rule-data"></a>Sposób użycia danych reguły  
 Aby porównać wydajność różnych wersji lub kompilacjach programu lub aby zrozumieć wydajność aplikacji w ramach scenariuszy testowania różnych, należy użyć wartości reguły.