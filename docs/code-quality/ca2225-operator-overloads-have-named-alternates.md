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
dev_langs:
- CSharp
ms.openlocfilehash: b4db3074d334fe32f95c4d1b8446921c4e4d47ba
ms.sourcegitcommit: 16175e0cea6af528e9ec76f0b94690faaf1bed30
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71481774"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: Przeciążenia operatorów mają nazwane elementy alternatywne

|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Category|Microsoft.Usage|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Wykryto Przeciążenie operatora i nie znaleziono oczekiwanej nazwanej metody alternatywnej.

Domyślnie ta reguła sprawdza tylko typy widoczne na zewnątrz, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

Przeciążanie operatora umożliwia użycie symboli do reprezentowania obliczeń dla typu. Na przykład typ, który przeciąża symbol Plus `+` dla dodania mógłby zwykle mieć alternatywny element członkowski o nazwie `Add`. Nazwany alternatywny element członkowski zapewnia dostęp do tych samych funkcji co operator. Jest ona dostarczana dla deweloperów, którzy programu w językach, którzy nie obsługują przeciążonych operatorów.

Ta reguła bada:

- Operatory niejawnych i jawnych rzutowania w typie przez sprawdzanie metod o nazwach `To<typename>` i `From<typename>`.

- Operatory wymienione w poniższej tabeli:

|C#|Visual Basic|C++|Nazwa metody alternatywnej|
|-|-|-|-|
|+ (binarny)|+|+ (binarny)|Add|
|+=|+=|+=|Add|
|&|Oraz|&|BitwiseAnd|
|&=|I =|&=|BitwiseAnd|
|&#124;|Lub|&#124;|Bitowy|
|&#124;=|Lub =|&#124;=|Bitowy|
|--|ND|--|Dekrementacji|
|/|/|/|Mieszczon|
|/=|/=|/=|Mieszczon|
|==|=|==|Równa się|
|^|XOR|^|XOR|
|^=|XOR =|^=|XOR|
|>|>|>|CompareTo lub Porównaj|
|>=|>=|>=|CompareTo lub Porównaj|
|++|ND|++|Pełny|
|!=|<>|!=|Równa się|
|<<|<<|<<|LeftShift|
|<<=|<<=|<<=|LeftShift|
|<|<|<|CompareTo lub Porównaj|
|<=|<=|\<=|CompareTo lub Porównaj|
|&&|ND|&&|LogicalAnd|
|&#124;&#124;|ND|&#124;&#124;|LogicalOr|
|!|ND|!|LogicalNot|
|%|Mod|%|Mod lub reszta|
|%=|ND|%=|Mod|
|* (binarny)|*|*|Mnożenia|
|*=|ND|*=|Mnożenia|
|~|nie|~|OnesComplement|
|>>|>>|>>|RightShift|
=|ND|>>=|RightShift|
|-(binarny)|-(binarny)|-(binarny)|Odjęt|
|-=|ND|-=|Odjęt|
|true|IsTrue|ND|IsTrue (Właściwość)|
|-(jednoargumentowe)|ND|-|Negate|
|+ (jednoargumentowy)|ND|+|Dłużon|
|false|IsFalse|False|IsTrue (Właściwość)|

\* N/A oznacza, że operator nie może być przeciążony w wybranym języku.

> [!NOTE]
> W C#przypadku, gdy operator binarny jest przeciążony, odpowiedni operator przypisania, jeśli istnieje, również jest niejawnie przeciążony.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy zaimplementować alternatywną metodę dla operatora. Nadaj mu nazwę przy użyciu zalecanej nazwy alternatywnej.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżenia z tej reguły, Jeśli wdrażasz bibliotekę udostępnioną. Aplikacje mogą ignorować ostrzeżenie z tej reguły.

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