---
title: DA0011-drogie CompareTo | Microsoft Docs
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e3b21745454a74d0251dad547ab45e845190f06d
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85328180"
---
# <a name="da0011-expensive-compareto"></a>DA0011: Kosztowna funkcja CompareTo

|||
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
