---
title: 'DA0010: Kosztowna funkcja GetHashCode | Dokumentacja firmy Microsoft'
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
- vs.performance.rules.DAExpensiveGetHashCode
- vs.performance.DA0010
- vs.performance.rules.DA0010
- vs.performance.10
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d27b696f38ddd90fc736204342051e4b5d87cd1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751448"
---
# <a name="da0010-expensive-gethashcode"></a>DA0010: Expensive GetHashCode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio 2017, zobacz [DA0010: kosztowna funkcja GetHashCode](https://docs.microsoft.com/visualstudio/profiling/da0010-expensive-gethashcode) w witrynie docs.microsoft.com.  

  

|||  
|-|-|  
|Identyfikator reguły|DA0010|  
|Kategoria|Sposób użycia programu .NET framework|  
|Metod profilowania|Próbkowania<br /><br /> Pamięć .NET|  
|Komunikat|Funkcje GetHashCode powinny być tanie i nie alokować wszystkie pamięci. Mniejsza złożoność funkcji wartości skrótu, jeśli jest to możliwe.|  
|Typ komunikatu|Ostrzeżenie|  
  
## <a name="cause"></a>Przyczyna  
 Wywołania metody GetHashCode tego typu są znaczna część danych profilowania, lub metoda przydziela pamięć.  
  
## <a name="rule-description"></a>Opis reguły  
 Wyznaczania wartości skrótu jest techniką, szybko lokalizowania określonego elementu w dużych kolekcji. Ponieważ tabele skrótów mogą być bardzo duże i musi obsługiwać bardzo intensywny dostępu, tabele zbędnych danych powinna być bardzo wydajne. Domniemanie to wymaganie jest, że metody GetHashCode w programie .NET Framework nie należy przydzielić pamięci. Przydzielanie pamięci zwiększa obciążenie moduł odśmiecania pamięci i udostępnia metody do potencjalnych opóźnienia, jeśli stają się niezbędne do uruchomienia wyrzucania elementów bezużytecznych w wyniku żądania alokacji.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Zmniejsz złożoność metody.

