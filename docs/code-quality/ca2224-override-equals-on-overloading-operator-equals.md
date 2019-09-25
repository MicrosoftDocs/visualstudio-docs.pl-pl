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
ms.openlocfilehash: 72bcf01b9c0613bb390ac9adbbba2fb176db13bd
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231218"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: Przesłaniaj metodę equals w przypadku przeciążania operatora równości

|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Kategoria|Microsoft.Usage|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Typ publiczny implementuje operator równości, ale nie przesłania <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły

Operator równości jest przeznaczony do składniowo wygodny sposób uzyskiwania dostępu do funkcji <xref:System.Object.Equals%2A> metody. W przypadku zaimplementowania operatora równości jego logika musi być taka sama jak <xref:System.Object.Equals%2A>w.

C# Kompilator generuje ostrzeżenie, jeśli kod narusza tę regułę.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy usunąć implementację operatora równości lub przesłonić <xref:System.Object.Equals%2A> i mieć dwie metody zwracają te same wartości. Jeśli operator równości nie wprowadza niespójnych zachowań, można naprawić naruszenie, dostarczając implementację <xref:System.Object.Equals%2A> <xref:System.Object.Equals%2A> metody w klasie bazowej.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli operator równości zwraca tę samą wartość, co dziedziczona implementacja <xref:System.Object.Equals%2A>, można bezpiecznie pominąć ostrzeżenie z tej reguły. Przykłady w tym artykule obejmują typ, który może bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="examples-of-inconsistent-equality-definitions"></a>Przykłady niespójnych definicji równości

W poniższym przykładzie przedstawiono typ z niespójnymi definicjami równości. `BadPoint`zmienia znaczenie, dostarczając niestandardową implementację operatora równości, ale nie przesłania <xref:System.Object.Equals%2A> się tak, że zachowuje się identycznie.

[!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]

Poniższy kod testuje zachowanie `BadPoint`.

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

Poniższy przykład pokazuje typ, który technicznie narusza tę regułę, ale nie działa w sposób niespójny.

[!code-csharp[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]

Poniższy kod testuje zachowanie `GoodPoint`.

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

Poniższy przykład pokazuje klasę (typ referencyjny), która narusza tę regułę.

[!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]

Poniższy przykład naprawia naruszenie przez zastąpienie <xref:System.Object.Equals%2A?displayProperty=fullName>.

[!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]

## <a name="structure-example"></a>Przykład struktury

Poniższy przykład pokazuje strukturę (typ wartości), która narusza tę regułę:

[!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]

Poniższy przykład naprawia naruszenie przez zastąpienie <xref:System.ValueType.Equals%2A?displayProperty=fullName>.

[!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]

## <a name="related-rules"></a>Powiązane reguły

[CA1046: Nie przeciążać operatora równości w typach referencyjnych](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

[CA2225: Przeciążenia operatorów mają nazwane alternatywy](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

[CA2226: Operatory powinny mieć symetryczne przeciążenia](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

[CA2218 Zastąp GetHashCode przy zastępowaniu równości](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

[CA2231 Operator przeciążenia jest równy przy przesłanianiu wartości ValueType. Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)