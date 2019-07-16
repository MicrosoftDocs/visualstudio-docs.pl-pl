---
title: 'DA0011: Kosztowna funkcja CompareTo | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 86d41a2717eb3ef7bd49f8d34b85198a55e5101c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68158647"
---
# <a name="da0011-expensive-compareto"></a>DA0011: Kosztowna funkcja CompareTo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [DA0011: Kosztowna funkcja CompareTo](https://docs.microsoft.com/visualstudio/profiling/da0011-expensive-compareto).  
  
|||  
|-|-|  
|Identyfikator reguły|DA0011|  
|Kategoria|Sposób użycia programu .NET framework|  
|Metod profilowania|Próbkowania<br /><br /> Pamięć .NET|  
|Message|Funkcje CompareTo powinny być tanie i nie przydzielić wszystkie pamięci. Mniejsza złożoność funkcji CompareTo, jeśli jest to możliwe.|  
|Typ reguły|Ostrzeżenie|  
  
## <a name="cause"></a>Przyczyna  
 CompareTo — metoda tego typu jest kosztowne lub przydziela pamięć.  
  
## <a name="rule-description"></a>Opis reguły  
 Metody CompareTo powinny być skuteczne i nie należy przydzielić pamięci.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Zmniejsz złożoność CompareTo — metoda.
