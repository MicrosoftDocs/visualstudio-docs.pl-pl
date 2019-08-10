---
title: 'CA2218: Przesłaniaj metodę GetHashCode w razie przesłaniania metody Equals'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2218
- OverrideGetHashCodeOnOverridingEquals
helpviewer_keywords:
- OverrideGetHashCodeOnOverridingEquals
- CA2218
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5dbd8580f5aaeb88c08d35b50258510cb1a85ba2
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920287"
---
# <a name="ca2218-override-gethashcode-on-overriding-equals"></a>CA2218: Przesłaniaj metodę GetHashCode w razie przesłaniania metody Equals

|||
|-|-|
|TypeName|OverrideGetHashCodeOnOverridingEquals|
|CheckId|CA2218|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
Typ publiczny przesłania <xref:System.Object.Equals%2A?displayProperty=fullName> , ale nie przesłania <xref:System.Object.GetHashCode%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły
 <xref:System.Object.GetHashCode%2A>Zwraca wartość opartą na bieżącym wystąpieniu, która jest odpowiednia dla algorytmów wyznaczania wartości skrótu i struktur danych, takich jak tabela skrótów. Dwa obiekty, które są tego samego typu i są równe, muszą zwracać ten sam kod skrótu, aby upewnić się, że wystąpienia następujących typów działają poprawnie:

- <xref:System.Collections.Hashtable?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>

- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName>

- <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>

- <xref:System.Collections.Specialized.HybridDictionary?displayProperty=fullName>

- <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>

- <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>

- Typy, które implementują<xref:System.Collections.Generic.IEqualityComparer%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, należy wprowadzić implementację programu <xref:System.Object.GetHashCode%2A>. Dla pary obiektów tego samego typu, należy się upewnić, że implementacja zwraca tę samą wartość, jeśli implementacja <xref:System.Object.Equals%2A> zwraca `true` dla pary.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="class-example"></a>Przykład klasy

### <a name="description"></a>Opis
Poniższy przykład pokazuje klasę (typ referencyjny), która narusza tę regułę.

### <a name="code"></a>Kod
[!code-csharp[FxCop.Usage.GetHashCodeErrorClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_1.cs)]

### <a name="comments"></a>Komentarze
Poniższy przykład naprawia naruszenie przez zastąpienie <xref:System.Object.GetHashCode>.

### <a name="code"></a>Kod
[!code-csharp[FxCop.Usage.GetHashCodeFixedClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_2.cs)]

## <a name="structure-example"></a>Przykład struktury

### <a name="description"></a>Opis
Poniższy przykład pokazuje strukturę (typ wartości), która narusza tę regułę.

### <a name="code"></a>Kod
[!code-csharp[FxCop.Usage.GetHashCodeErrorStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_3.cs)]

### <a name="comments"></a>Komentarze
Poniższy przykład naprawia naruszenie przez zastąpienie <xref:System.Object.GetHashCode>.

### <a name="code"></a>Kod
[!code-csharp[FxCop.Usage.GetHashCodeFixedStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_4.cs)]

## <a name="related-rules"></a>Powiązane reguły
[CA1046: Nie przeciążać operatora równości w typach referencyjnych](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

[CA2225: Przeciążenia operatorów mają nazwane alternatywy](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

[CA2226: Operatory powinny mieć symetryczne przeciążenia](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

[CA2224 Zastąp wartość Equals przy przeciążeniu operatora Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

[CA2231 Operator przeciążenia jest równy przy przesłanianiu wartości ValueType. Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- <xref:System.Object.GetHashCode%2A?displayProperty=fullName>
- <xref:System.Collections.Hashtable?displayProperty=fullName>
- [Operatory równości](/dotnet/standard/design-guidelines/equality-operators)