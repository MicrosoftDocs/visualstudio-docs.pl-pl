---
title: 'DA0006: Przesłoń metody Equals() dla typów wartości | Dokumentacja firmy Microsoft'
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
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a60bc533ccc826b09e288e7d8ca934702f0443e5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768308"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006: Przesłoń metodę equals typami wartości
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identyfikator reguły | DA0006 |  
| Kategoria |. NET Framework użycia |  
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



