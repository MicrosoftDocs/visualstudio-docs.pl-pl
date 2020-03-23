---
title: 'DA0011: Drogie CompareTo | Dokumenty firmy Microsoft'
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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d0eb4566fd4c8a513b1492cecffc16cb94a1fd83
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779431"
---
# <a name="da0011-expensive-compareto"></a>DA0011: Expensive CompareTo

|||
|-|-|
|Identyfikator reguły|DA0011|
|Kategoria|Użycie programu .NET Framework|
|Metody profilowania|Próbkowanie<br /><br /> Pamięć .NET|
|Komunikat|CompareTo funkcje powinny być tanie i nie przydzielić żadnej pamięci. Zmniejsz złożoność funkcji CompareTo, jeśli to możliwe.|
|Typ reguły|Ostrzeżenie|

## <a name="cause"></a>Przyczyna
 Metoda CompareTo typu jest kosztowna lub przydziela pamięć.

## <a name="rule-description"></a>Opis reguły
 CompareTo metody powinny być wydajne i nie należy przydzielać pamięci.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Zmniejsz złożoność CompareTo metody.
