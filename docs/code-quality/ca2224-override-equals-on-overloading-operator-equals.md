---
title: 'CA2224: Przesłaniaj metodę equals w przypadku przeciążania operatora równości'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fa6bfa5b590d330d791eb8c735099e619ffaf3a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55922969"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: Przesłaniaj metodę equals w przypadku przeciążania operatora równości

|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Typ publiczny implementuje operator równości, ale nie przesłania <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły

Operator równości ma być syntaktycznie wygodny sposób uzyskać dostęp do funkcji <xref:System.Object.Equals%2A> metody. W przypadku zastosowania operatora równości swojej logiki musi być taka sama jak w przypadku <xref:System.Object.Equals%2A>.

Kompilator języka C# generuje ostrzeżenie, jeśli kod narusza tę regułę.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy albo usuń implementacja operatora równości lub zastąpić <xref:System.Object.Equals%2A> i mieć dwie metody zwracają takie same wartości. Operator równości nie wprowadza niespójne zachowanie, można naprawić naruszenia, zapewniając implementację <xref:System.Object.Equals%2A> wywołująca <xref:System.Object.Equals%2A> metody w klasie bazowej.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Bezpiecznie Pomijaj ostrzeżeń dla tej reguły, jeśli operatora równości zwraca taką samą wartość jak dziedziczona implementacja <xref:System.Object.Equals%2A>. W tym artykule przykładami typ, który można bezpiecznie Pomijaj ostrzeżeń dla tej reguły.

## <a name="examples-of-inconsistent-equality-definitions"></a>Przykłady definicje niespójne równości

Poniższy przykład pokazuje typ z definicjami niespójne równości. `BadPoint` zmienia znaczenie równości, zapewniając implementację niestandardową operatora równości, lecz nie przesłania <xref:System.Object.Equals%2A> tak, aby zachowuje się tak samo.

[!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]

Poniższy kod sprawdza zachowanie `BadPoint`.

[!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]

Ten przykład generuje następujące wyniki:

```txt
a =  ([0] 1,1) and b = ([1] 2,2) are equal? No
a == b ? No
a1 and a are equal? Yes
a1 == a ? Yes
b and bcopy are equal ? No
b == bcopy ? Yes
```

Poniższy przykład pokazuje typ, który z technicznego punktu widzenia narusza tę regułę, ale nie zachowywać się w sposób niezgodny.

[!code-csharp[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]

Poniższy kod sprawdza zachowanie `GoodPoint`.

[!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]

Ten przykład generuje następujące wyniki:

```txt
a =  (1,1) and b = (2,2) are equal? No
a == b ? No
a1 and a are equal? Yes
a1 == a ? Yes
b and bcopy are equal ? Yes
b == bcopy ? Yes
```

## <a name="class-example"></a>Przykład klasy

Poniższy przykład przedstawia klasę (typ odwołania), która narusza tę regułę.

[!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]

Poniższy przykład naprawia naruszenia przez zastąpienie <xref:System.Object.Equals%2A?displayProperty=fullName>.

[!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]

## <a name="structure-example"></a>Przykład struktury

Poniższy przykład pokazuje strukturę (typ wartości), która narusza tę regułę:

[!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]

Poniższy przykład naprawia naruszenia przez zastąpienie <xref:System.ValueType.Equals%2A?displayProperty=fullName>.

[!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]

## <a name="related-rules"></a>Powiązane reguły

[CA1046: Nie przeciążaj operatora równości w typach referencyjnych](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

[CA2225: Operator overloads ma nazwanych zastępców](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

[CA2226: Operatory powinny mieć symetryczne przeciążenia](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

[CA2218: Przesłaniaj metodę GetHashCode w przesłaniania metody Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

[CA2231: Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)