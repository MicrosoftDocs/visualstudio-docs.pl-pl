---
title: 'DA0006: Przesłoń metodę Equals() dla typów wartości | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2229edad7ff338251fea23740343e23f87aa2792
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158678"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006: Przesłoń metodę Equals() dla typów wartości
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identyfikator reguły | DA0006 |  
|Category|.NET Framework Usage|  
| Metody Profiiling | Próbkowanie |  
| Komunikat | Przesłoń metodę Equals i operator równości dla typów wartości. |  
| Typ Messge | Ostrzeżenie |  
  
## <a name="cause"></a>Przyczyna  
 Wywołania do metody Equals i operatory równości typu publicznego wartości są znaczna część danych profilowania. Rozważ zaimplementowanie bardziej efektywną metodę.  
  
## <a name="rule-description"></a>Opis reguły  
 Dla typów wartości dziedziczona implementacja operatora Equas wykorzystuje <xref:System.Reflection> biblioteki i porównuje zawartość wszystkich pól w typie. Odbicie jest obliczeniowo kosztowne, a porównanie równości każdego pola może być niepotrzebne. Jeśli oczekujesz, że użytkownicy będą porównywać lub sortować wystąpienia lub używać ich jako tabel haszowanych, typ wartości powinien implementować Equals. Jeśli język programowania obsługuje przeładowania operatora, należy również podać implementacja Operatory równości i nierówności.  
  
 Aby uzyskać więcej informacji na temat Przesłoń metodę Equals i operatory porównania, zobacz [wytyczne dotyczące implementowania Equals i Operator równości (==)](http://go.microsoft.com/fwlink/?LinkId=177818).  
  
## <a name="how-to-investigate-a-warning"></a>Jak badać ostrzeżenie  
 Na przykład implementacji Equals i operatory porównania, zobacz reguł analizy kodu [CA1815: Przesłoń metodę equals i operator równości dla typów wartości](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)
