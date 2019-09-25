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
ms.openlocfilehash: c027bc4581919f814b4d93eacba77248349fdf8b
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231090"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: Przeciążenia operatorów mają nazwane elementy alternatywne

|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Kategoria|Microsoft.Usage|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Wykryto Przeciążenie operatora i nie znaleziono oczekiwanej nazwanej metody alternatywnej.

Domyślnie ta reguła sprawdza tylko typy widoczne na zewnątrz, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

Przeciążanie operatora umożliwia użycie symboli do reprezentowania obliczeń dla typu. Na przykład typ, który przeciąża symbol plus (+) dla dodania, zazwyczaj ma alternatywny element członkowski o nazwie "Add". Nazwany alternatywny element członkowski zapewnia dostęp do tych samych funkcji co operator i jest udostępniany deweloperom programu w językach, które nie obsługują przeciążonych operatorów.

Ta reguła bada operatory wymienione w poniższej tabeli.

|C#|Visual Basic|C++|Nazwa alternatywna|
|---------|------------------|-----------|--------------------|
|+ (binarny)|+|+ (binarny)|Dodaj|
|+=|+=|+=|Dodaj|
|&|Oraz|&|BitwiseAnd|
|&=|I =|&=|BitwiseAnd|
|&#124;|Lub|&#124;|Bitowy|
|&#124;=|Lub =|&#124;=|Bitowy|
|--|Brak|--|Dekrementacji|
|/|/|/|Mieszczon|
|/=|/=|/=|Mieszczon|
|==|=|==|Równa się|
|^|XOR|^|XOR|
|^=|XOR =|^=|XOR|
|>|>|>|{1&gt;Compare&lt;1}|
|>=|>=|>=|{1&gt;Compare&lt;1}|
|++|Brak|++|Pełny|
|<>|!=|Równa się|
|<<|<<|<<|LeftShift|
|<<=|<<=|<<=|LeftShift|
|<|<|<|{1&gt;Compare&lt;1}|
|<=|<=|\<=|{1&gt;Compare&lt;1}|
|&&|Brak|&&|LogicalAnd|
|&#124;&#124;|Brak|&#124;&#124;|LogicalOr|
|!|Brak|!|LogicalNot|
|%|Mod|%|Mod lub reszta|
|%=|Brak|%=|Mod|
|* (binarny)|*|*|Mnożenia|
|*=|Brak|*=|Mnożenia|
|~|nie|~|OnesComplement|
|>>|>>|>>|RightShift|
=|Brak|>>=|RightShift|
|-(binarny)|-(binarny)|-(binarny)|Odjęt|
|-=|Brak|-=|Odjęt|
|true|IsTrue|Brak|IsTrue (Właściwość)|
|-(jednoargumentowe)|Brak|-|Negate|
|+ (jednoargumentowy)|Brak|+|Dłużon|
|false|IsFalse|False|IsTrue (Właściwość)|

Nie można obciążyć elementu = = w wybranym języku.

Reguła sprawdza także niejawne i jawne Operatory rzutowania w typie`SomeType`() przez sprawdzenie metod o `ToSomeType` nazwie `FromSomeType`i.

W C#przypadku, gdy operator binarny jest przeciążony, odpowiedni operator przypisania, jeśli istnieje, również jest niejawnie przeciążony.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy zaimplementować alternatywną metodę dla operatora; Nadaj mu nazwę przy użyciu zalecanej nazwy alternatywnej.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżenia z tej reguły, jeśli implementujesz bibliotekę udostępnioną. Aplikacje mogą ignorować ostrzeżenie z tej reguły.

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca2225.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (użycie). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano strukturę, która narusza tę regułę. Aby poprawić ten przykład, Dodaj metodę publiczną `Add(int x, int y)` do struktury.

[!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]

## <a name="related-rules"></a>Powiązane reguły

- [CA1046: Nie przeciążać operatora równości w typach referencyjnych](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2226: Operatory powinny mieć symetryczne przeciążenia](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)
- [CA2224 Zastąp wartość Equals przy przeciążeniu operatora Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218 Zastąp GetHashCode przy zastępowaniu równości](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)
- [CA2231 Operator przeciążenia jest równy przy przesłanianiu wartości ValueType. Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)