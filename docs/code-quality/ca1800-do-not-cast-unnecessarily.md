---
title: 'CA1800: Nie rzutuj niepotrzebnie'
ms.date: 10/26/2017
ms.topic: reference
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: a13aeeffbc77e4f40ff886c0d890f181697fcc11
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62797182"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: Nie rzutuj niepotrzebnie

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
Metoda wykonuje zduplikowane rzutowania na jednym z jego argumentów ani zmiennych lokalnych.

Zakończenie analizy przez tę regułę przetestowane zestawu muszą zostać skompilowane przy użyciu informacji o debugowaniu, a plik bazy danych (PDB) programu skojarzone muszą być dostępne.

## <a name="rule-description"></a>Opis reguły
Zduplikowane rzutowania zmniejszają wydajność, zwłaszcza gdy rzutowania są wykonywane w niedużej iteracji. W przypadku jawnego rzutowania zduplikowanych operacji przechować wynik rzutowania w zmiennej lokalnej, a następnie użyć zmiennej lokalnej zamiast operacji zduplikowane rzutowania.

Jeśli C# `is` operator jest używany do sprawdzenia, czy rzutowanie zostanie wykonane pomyślnie, przed wykonaniem rzeczywiste rzutowania należy wziąć pod uwagę testowanie oddziaływania `as` operator zamiast tego. Dzięki temu te same funkcje bez operacji niejawne rzutowanie, która jest wykonywana przez `is` operatora. W języku C# 7.0 i nowszych, należy użyć `is` operator [dopasowywania do wzorca](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) sprawdzenia konwersji typu, i rzutowane wyrażenia do zmiennej tego typu w jednym kroku.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zmodyfikować implementacji metody, aby zminimalizować liczbę operacji rzutowania.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne, ostrzeżenia od tej reguły lub całkowicie, ignorowanie reguły, jeśli wydajność nie ma znaczenia.

## <a name="examples"></a>Przykłady
 W poniższym przykładzie pokazano metodę, która narusza regułę przy użyciu języka C# `is` operatora. Druga metoda spełnia reguły, zastępując `is` operatora z testem względem wynik `as` operatora, co zmniejsza liczbę operacji rzutowania na iterację od dwóch do jednego. Trzecia metoda spełnia również reguły za pomocą `is` z [dopasowywania do wzorca](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) utworzyć zmienną żądanego typu, jeśli konwersja typu powiedzie się.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]

 W poniższym przykładzie pokazano metodę `start_Click`, ma wiele zduplikowanych ma jawnych rzutowań, który narusza regułę, a metoda `reset_Click`, spełniającego reguły, przechowując rzutowanie w zmiennej lokalnej.

 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]

## <a name="see-also"></a>Zobacz także

- [jako (odwołanie w C#)](/dotnet/csharp/language-reference/keywords/as)
- [jest (odwołanie w C#)](/dotnet/csharp/language-reference/keywords/is)