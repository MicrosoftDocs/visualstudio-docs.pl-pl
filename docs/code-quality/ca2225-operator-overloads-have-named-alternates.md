---
title: 'CA2225: Przeciążenia operatorów mają nazwane elementy alternatywne'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8a1c7015421b686d47bfea4c3341ec76748f8ad
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806618"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: Przeciążenia operatorów mają nazwane elementy alternatywne

|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Wykryto Przeciążony operator i nie można odnaleźć oczekiwanego alternatywną metodę o nazwie.

Domyślnie ta reguła przegląda tylko typy widoczne na zewnątrz, ale jest to [konfigurowalne](#configurability).

## <a name="rule-description"></a>Opis reguły

Przeciążanie operatora umożliwia korzystanie z symboli do reprezentowania obliczeń dla typu. Na przykład typ, który przeciążenia symbol znaku plus (+) do dodania zwykle mają alternatywny element członkowski o nazwie "Dodaj". Nazwany alternatywny element członkowski udostępnia taką samą funkcjonalność jak operator i jest dostarczany deweloperom programującym w językach, które nie obsługują przeciążonych operatorów.

Ta reguła sprawdza, czy operatory wymienione w poniższej tabeli.

|C#|Visual Basic|C++|Nazwa alternatywna|
|---------|------------------|-----------|--------------------|
|+ (binarnych)|+|+ (binarnych)|Dodaj|
|+=|+=|+=|Dodaj|
|&|Oraz|&|BitwiseAnd|
|&=|And=|&=|BitwiseAnd|
|&#124;|Lub|&#124;|BitwiseOr|
|&#124;=|Lub =|&#124;=|BitwiseOr|
|--|Brak|--|Dekrementacja|
|/|/|/|Dzielenie|
|/=|/=|/=|Dzielenie|
|==|=|==|Równa się|
|^|XOR|^|XOR|
|^=|Xor=|^=|XOR|
|>|>|>|{1&gt;Compare&lt;1}|
|>=|>=|>=|{1&gt;Compare&lt;1}|
|++|Brak|++|Inkrementacja|
|<>|!=|Równa się|
|<<|<<|<<|LeftShift|
|<<=|<<=|<<=|LeftShift|
|<|<|<|{1&gt;Compare&lt;1}|
|<=|<=|\<=|{1&gt;Compare&lt;1}|
|&&|Brak|&&|LogicalAnd|
|&#124;&#124;|Brak|&#124;&#124;|LogicalOr|
|!|Brak|!|LogicalNot|
|%|Mod|%|Mod lub pozostałej|
|%=|Brak|%=|Mod|
|* (binarnych)|*|*|Mnożenie|
|*=|Brak|*=|Mnożenie|
|~|nie|~|OnesComplement|
|>>|>>|>>|RightShift|
=|Brak|>>=|RightShift|
|-(binarnych)|-(binarnych)|-(binarnych)|Odejmowanie|
|-=|Brak|-=|Odejmowanie|
|true|IsTrue|Brak|IsTrue (właściwość)|
|-(jednoargumentowy)|Brak|-|Negate|
|+ (jednoargumentowy)|Brak|+|Plus|
|false|IsFalse|False|IsTrue (właściwość)|

N/d == nie mogą być przeciążone w wybranym języku.

Zasada sprawdza również operatory rzutowania jawne i niejawne w typie (`SomeType`) przez sprawdzenie, czy metody o nazwie `ToSomeType` i `FromSomeType`.

W języku C# gdy jest przeciążony operator binarny, odpowiedniego operatora przypisania, jest również niejawnie przeciążona.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy zaimplementować alternatywną metodę dla operatora; Nadaj mu przy użyciu zalecane alternatywne nazwy.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły, w przypadku wdrażania biblioteki udostępnionej. Aplikacje można zignorować ostrzeżenie od tej reguły.

## <a name="configurability"></a>Konfigurowalne

Po uruchomieniu tej reguły z [analizatory FxCop analizujące kod](install-fxcop-analyzers.md) (a nie przy użyciu statycznej analizy kodu) części, które można skonfigurować Twojej bazy kodu do uruchomienia tej reguły na, oparte na ich dostępność. Na przykład aby określić, że zasady powinny być uruchamiane wyłącznie w odniesieniu do powierzchni interfejsu API niepublicznych, Dodaj następujące pary klucz wartość w pliku .editorconfig w projekcie:

```
dotnet_code_quality.ca2225.api_surface = private, internal
```

Można skonfigurować tę opcję tylko reguły dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (użycie). Aby uzyskać więcej informacji, zobacz [analizatory FxCop analizujące kod z skonfigurować](configure-fxcop-analyzers.md).

## <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano strukturę, która narusza tę regułę. Aby rozwiązać problem w przykładzie, należy dodać publiczny `Add(int x, int y)` metody w strukturze.

[!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]

## <a name="related-rules"></a>Powiązane reguły

- [CA1046: Nie przeciążaj operatora równości w typach referencyjnych](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2226: Operatory powinny mieć symetryczne przeciążenia](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)
- [CA2224: Przesłoń metodę equals, przeciążając operator equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218: Przesłaniaj metodę GetHashCode w przesłaniania metody Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)
- [CA2231: Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)