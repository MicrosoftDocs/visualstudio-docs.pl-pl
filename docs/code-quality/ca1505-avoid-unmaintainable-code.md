---
title: 'CA1505: Unikaj kodu trudnego w utrzymaniu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 085f3b5ad38e846880d39e813550301a81066745
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54957185"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: Unikaj kodu trudnego w utrzymaniu

|||
|-|-|
|TypeName|AvoidUnmantainableCode|
|CheckId|CA1505|
|Kategoria|Microsoft.Maintainability|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ lub metoda ma niską wartość indeksu konserwacji.

## <a name="rule-description"></a>Opis reguły
 Indeks łatwości utrzymania jest obliczana przy użyciu następujących metryk: wiersze kodu, program woluminu i złożoność cykliczną. Program wolumin jest miarą trudności wiedzę na temat typu lub metody, która opiera się na liczbie operatorów i argumentów operacji w kodzie. Złożoność Cyklomatyczna jest miarą strukturalnych złożoność tego typu lub metody. Dowiedz się więcej na temat metryk kodu [mierzenie złożoności i łatwości konserwacji zarządzanego kodu](../code-quality/code-metrics-values.md).

 Niski indeks konserwacji wskazuje, że typ lub metoda są prawdopodobnie trudne do utrzymania i jest dobrym kandydatem do przeprojektowania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać problem to naruszenie, zmodyfikowanie typu lub metody i spróbuj podzielić ją na mniejsze i bardziej ukierunkowaną typów ani metod.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Wyklucz to ostrzeżenie, gdy typ lub metoda jest nadal uważana za łatwego w utrzymaniu, niezależnie od jego duży rozmiar lub typie lub metodzie nie można podzielić.

## <a name="see-also"></a>Zobacz także

- [Ostrzeżenia dotyczące konserwacji](../code-quality/maintainability-warnings.md)
- [Mierzenie złożoności i poziomu łatwości konserwacji kodu zarządzanego](../code-quality/code-metrics-values.md)