---
title: 'DA0011: Kosztowna funkcja CompareTo | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83708fa0e58381f50d1637e5f03255fc12376a7a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942441"
---
# <a name="da0011-expensive-compareto"></a>DA0011: Kosztowna funkcja CompareTo

|||  
|-|-|  
|Identyfikator reguły|DA0011|  
|Kategoria|Sposób użycia programu .NET framework|  
|Metod profilowania|Próbkowania<br /><br /> Pamięć .NET|  
|Komunikat|Funkcje CompareTo powinny być tanie i nie przydzielić wszystkie pamięci. Mniejsza złożoność funkcji CompareTo, jeśli jest to możliwe.|  
|Typ reguły|Ostrzeżenie|  

## <a name="cause"></a>Przyczyna  
 CompareTo — metoda tego typu jest kosztowne lub przydziela pamięć.  

## <a name="rule-description"></a>Opis reguły  
 Metody CompareTo powinny być skuteczne i nie należy przydzielić pamięci.  

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Zmniejsz złożoność CompareTo — metoda.