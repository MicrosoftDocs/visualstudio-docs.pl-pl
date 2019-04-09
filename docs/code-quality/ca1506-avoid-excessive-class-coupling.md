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
ms.openlocfilehash: b655609548d3de293abe2adc0ec3fb5c6fcf297b
ms.sourcegitcommit: 36f5ffd6ae3215fe31837f4366158bf0d871f7a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59232486"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: Unikaj nadmiernego sprzężenia klas

|||
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|Kategoria|Microsoft.Maintainability|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Typ lub metoda jest sprzężona z wielu innych typów.

## <a name="rule-description"></a>Opis reguły

Ta reguła mierzy sprzęgnięcie klasy przez liczenie unikatowych odwołań typów, które zawiera typ lub metoda.

Typy i metody, które mają wysokim stopniu sprzężenia klas mogą być trudne w utrzymaniu. Jest dobrą praktyką, typów i metod, które wykazują sprzężenia i wysoka spójność.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby rozwiązać problem to naruszenie, spróbuj zmienić układ typu lub metody w celu zmniejszenia liczby typów, do których jest sprzężona.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Wyklucz to ostrzeżenie, gdy typ lub metoda jest uznawany za łatwego w utrzymaniu pomimo dużej liczby zależności od innych typów.

## <a name="see-also"></a>Zobacz także

- [Utrzymanie — Ostrzeżenia](../code-quality/maintainability-warnings.md)
- [Mierzenie złożoności i łatwości konserwacji zarządzanego kodu](../code-quality/code-metrics-values.md)