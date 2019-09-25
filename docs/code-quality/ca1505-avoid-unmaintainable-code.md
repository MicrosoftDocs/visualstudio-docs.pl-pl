---
title: 'CA1505: Unikaj kodu trudnego w utrzymaniu'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3ba027ef2e663870d0af50bc6d2154133f7980c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234540"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: Unikaj kodu trudnego w utrzymaniu

|||
|-|-|
|TypeName|AvoidUnmantainableCode|
|CheckId|CA1505|
|Kategoria|Microsoft. łatwość obsługi|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Typ lub metoda ma niską wartość indeksu konserwacji.

## <a name="rule-description"></a>Opis reguły

Indeks utrzymania jest obliczany przy użyciu następujących metryk: wierszy kodu, woluminu programowego i złożoności cyklomatyczna. Wolumin programu to miara trudności w zrozumieniu typu lub metody, która jest oparta na liczbie operatorów i operandów w kodzie. Złożoność cyklomatyczna jest miarą złożoności strukturalnej typu lub metody. Możesz dowiedzieć się więcej o metrykach kodu w zakresie [złożoności miar i utrzymania kodu zarządzanego](../code-quality/code-metrics-values.md).

Niski indeks utrzymania wskazuje, że typ lub metoda prawdopodobnie trudno jest zachować i będzie to dobry kandydat do przeprojektowania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby rozwiązać ten problem, Zaprojektuj typ lub metodę, a następnie spróbuj podzielić go na mniejsze i bardziej ukierunkowane typy lub metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Możesz pominąć to ostrzeżenie, gdy typ lub metoda nie mogą być podzielona lub jest uznawany za utrzymaną mimo jej dużego rozmiaru.

## <a name="see-also"></a>Zobacz także

- [Ostrzeżenia dotyczące utrzymania](../code-quality/maintainability-warnings.md)
- [Mierzenie złożoności i łatwość utrzymania kodu zarządzanego](../code-quality/code-metrics-values.md)