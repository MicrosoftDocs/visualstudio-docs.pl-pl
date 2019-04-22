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
ms.openlocfilehash: 740ef26af6f1f84d23ef27de5176df1b3de98b34
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59232499"
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

Można pominąć to ostrzeżenie, gdy typie lub metodzie nie można podzielić lub jest uznawany za łatwego w utrzymaniu niezależnie od jego duży rozmiar.

## <a name="see-also"></a>Zobacz także

- [Utrzymanie — ostrzeżenia](../code-quality/maintainability-warnings.md)
- [Mierzenie złożoności i łatwości konserwacji zarządzanego kodu](../code-quality/code-metrics-values.md)