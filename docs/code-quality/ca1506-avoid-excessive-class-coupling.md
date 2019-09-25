---
title: 'CA1506: Unikaj nadmiernego sprzężenia klas'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1721fd52c00c5b312c88f19d48b668b12d28f050
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234495"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: Unikaj nadmiernego sprzężenia klas

|||
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|Kategoria|Microsoft. łatwość obsługi|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna

Typ lub metoda jest sprzężona z wieloma innymi typami.

## <a name="rule-description"></a>Opis reguły

Ta reguła mierzy sprzęgnięcie klasy przez liczenie unikatowych odwołań typów, które zawiera typ lub metoda.

Typy i metody o wysokim stopniu sprzęgania klas mogą być trudne do utrzymania. Dobrym sposobem jest posiadanie typów i metod, które wykazują niskie sprzężenie i wysoką spójność.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby rozwiązać ten problem, spróbuj ponownie zaprojektować typ lub metodę w celu zmniejszenia liczby typów, do których jest sprzężona.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Wyklucz to ostrzeżenie, gdy typ lub metoda jest uznawana za łatwość utrzymania pomimo dużej liczby zależności od innych typów.

## <a name="see-also"></a>Zobacz także

- [Ostrzeżenia dotyczące konserwacji](../code-quality/maintainability-warnings.md)
- [Mierzenie złożoności i poziomu łatwości konserwacji kodu zarządzanego](../code-quality/code-metrics-values.md)