---
title: 'CA1502: Unikaj nadmiernej złożoności'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidExcessiveComplexity
- CA1502
helpviewer_keywords:
- CA1502
- AvoidExcessiveComplexity
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: aa10945e87022546240d05304f59478b33bb5596
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55916768"
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502: Unikaj nadmiernej złożoności

|||
|-|-|
|TypeName|AvoidExcessiveComplexity|
|CheckId|CA1502|
|Kategoria|Microsoft.Maintainability|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Metoda ma złożoność cyklomatyczną nadmierne.

## <a name="rule-description"></a>Opis reguły

*Złożoność Cyklomatyczna* mierzy liczbę liniowo niezależnych ścieżek za pośrednictwem metody, która jest określana przez liczbę i złożoność rozgałęzień warunkowych. Złożoność cyklomatyczna niski na ogół wskazuje metodę, która jest łatwy do zrozumienia, testowania i obsługi. Złożoność cyklomatyczna jest obliczana na podstawie grafu przepływu sterowania, metody i znajduje się w następujący sposób:

złożoność cyklomatyczna = liczba krawędzi — liczba węzłów + 1

gdy węzeł reprezentuje Rozgałęzienie logiki i krawędź reprezentuje linię między węzłami.

Reguły raporty naruszenie zasad, gdy złożoność cyklomatyczna jest więcej niż 25.

Dowiedz się więcej na temat metryk kodu [mierzenie złożoności i łatwości konserwacji zarządzanego kodu](../code-quality/code-metrics-values.md),

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, Refaktoryzuj metody do jego złożoność cykliczną.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli nie łatwo można zmniejszyć złożoność i metoda jest łatwy do zrozumienia, testowania i obsługi. W szczególności metoda, która zawiera dużą `switch` (`Select` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) instrukcja jest kandydatem do wykluczenia. Ryzyko destabilizing kod podstawowy zaległości w cyklu rozwoju lub wprowadzenia nieoczekiwanej zmianie w zachowania w czasie wykonywania w kodzie uprzednio wysłane może przeważyć zalety łatwości utrzymania refaktoryzacji kodu.

## <a name="how-cyclomatic-complexity-is-calculated"></a>Jak obliczana jest złożoność Cyklomatyczna

Złożoność cyklomatyczna jest obliczany przez dodanie 1 do następujących:

- Liczba gałęzi (takich jak `if`, `while`, i `do`)

- Liczba `case` instrukcje w `switch`

## <a name="example"></a>Przykład

Poniższe przykłady przedstawiają metody, które mają różnej złożoności cyklomatycznej.

**Złożoność Cyklomatyczna 1**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_1.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_1.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_1.cs)]

## <a name="example"></a>Przykład

**Złożoność Cyklomatyczna 2**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_2.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_2.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_2.cs)]

## <a name="example"></a>Przykład

**Złożoność Cyklomatyczna 3**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_3.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_3.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_3.cs)]

## <a name="example"></a>Przykład

**Złożoność Cyklomatyczna 8**

[!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_4.cpp)]
[!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_4.vb)]
[!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_4.cs)]

## <a name="related-rules"></a>Powiązane reguły

[CA1501: Unikaj nadmiernego dziedziczenia](../code-quality/ca1501-avoid-excessive-inheritance.md)

## <a name="see-also"></a>Zobacz także

- [Mierzenie złożoności i poziomu łatwości konserwacji kodu zarządzanego](../code-quality/code-metrics-values.md)