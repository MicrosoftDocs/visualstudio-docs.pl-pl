---
title: DA0011-drogie CompareTo | Microsoft Docs
description: Metoda CompareTo typu jest kosztowna lub przydziela pamięć.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 91219bed2ca0e8b4bbc28825e1505b9d5f78bbc8
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466157"
---
# <a name="da0011-expensive-compareto"></a>DA0011: Kosztowna funkcja CompareTo

|Element|Wartość|
|-|-|
|Identyfikator reguły|DA0011|
|Kategoria|Użycie .NET Framework|
|Metody profilowania|Próbkowanie<br /><br /> Pamięć platformy .NET|
|Komunikat|Funkcje CompareTo powinny być tanie i nie mogą przydzielać żadnej pamięci. Zmniejsz złożoność funkcji CompareTo, jeśli jest to możliwe.|
|Typ reguły|Ostrzeżenie|

## <a name="cause"></a>Przyczyna
 Metoda CompareTo typu jest kosztowna lub przydziela pamięć.

## <a name="rule-description"></a>Opis reguły
 Metody CompareTo powinny być wydajne i nie powinny przydzielić pamięci.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Zmniejsz złożoność metody CompareTo.
