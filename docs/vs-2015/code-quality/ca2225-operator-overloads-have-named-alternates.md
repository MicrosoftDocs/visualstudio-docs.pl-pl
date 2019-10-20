---
title: 'CA2225: przeciążenia operatorów mają nazwane alternatywy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 212abc1fa5e2debfaf7ca81d82c8d94e9ddb0879
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658876"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: Operator overloads ma nazwanych zastępców
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Wykryto przeciążony operator i nie znaleziono metody alternatywnej o oczekiwanej nazwie.

## <a name="rule-description"></a>Opis reguły
 Przeciążanie operatora umożliwia użycie symboli do reprezentowania obliczeń dla typu. Na przykład typ, który przeciąża symbol plus (+) dla dodania, zazwyczaj ma alternatywny element członkowski o nazwie "Add". Nazwany alternatywny element członkowski zapewnia dostęp do tych samych funkcji co operator i jest udostępniany deweloperom programu w językach, które nie obsługują przeciążonych operatorów.

 Ta reguła bada operatory wymienione w poniższej tabeli.

|C#|Visual Basic|C++|Nazwa alternatywna|
|---------|------------------|-----------|--------------------|
|+ (binarny)|+|+ (binarny)|Dodaj|
|+=|+=|+=|Dodaj|
|&|Lub|&|BitwiseAnd|
|&=|I =|&=|BitwiseAnd|
|&#124;|Lub|&#124;|Bitowy|
|&#124;=|Lub =|&#124;=|Bitowy|
|--|Brak|--|Dekrementacji|
|/|/|/|Mieszczon|
|/=|/=|/=|Mieszczon|
|==|=|==|Ubiegł|
|^|XOR|^|XOR|
|^=|XOR =|^=|XOR|
|>|>|>|Porównaniu|
|>=|>=|>=|Porównaniu|
|++|Brak|++|Pełny|
|<>|!=|Ubiegł|
|<<|<<|<<|LeftShift|
|<<=|<<=|<<=|LeftShift|
|<|<|<|Porównaniu|
|<=|<=|\<=|Porównaniu|
|&&|Brak|&&|LogicalAnd|
|&#124;&#124;|Brak|&#124;&#124;|Logiczny|
|!|Brak|!|LogicalNot|
|%|Mod|%|Mod lub reszta|
|%=|Brak|%=|Mod|
|* (binarny)|*|*|Mnożenia|
|*=|Brak|*=|Mnożenia|
|~|Niemożliwe|~|OnesComplement|
|>>|>>|>>|RightShift|
=|Brak|>>=|RightShift|
|-(binarny)|-(binarny)|-(binarny)|Odjęt|
|-=|Brak|-=|Odjęt|
|true|IsTrue|Brak|IsTrue (Właściwość)|
|-(jednoargumentowe)|Brak|-|Negate|
|+ (jednoargumentowy)|Brak|+|dłużon|
|false|IsFalse|False|IsTrue (Właściwość)|

 Nie można obciążyć elementu = = w wybranym języku.

 Reguła sprawdza także niejawne i jawne Operatory rzutowania w typie (`SomeType`) przez sprawdzanie metod o nazwie `ToSomeType` i `FromSomeType`.

 W C#przypadku, gdy operator binarny jest przeciążony, odpowiedni operator przypisania, jeśli istnieje, również jest niejawnie przeciążony.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zaimplementować alternatywną metodę dla operatora; Nadaj mu nazwę przy użyciu zalecanej nazwy alternatywnej.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżenia z tej reguły, jeśli implementujesz bibliotekę udostępnioną. Aplikacje mogą ignorować ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie zdefiniowano strukturę, która narusza tę regułę. Aby poprawić przykład, Dodaj publiczną metodę `Add(int x, int y)` do struktury.

 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorOverloadsHaveNamedAlternates/cs/FxCop.Usage.OperatorOverloadsHaveNamedAlternates.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1046: Nie przeciążaj operatora równości w typach referencyjnych](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2226: Operatory powinny mieć symetryczne przeciążenia](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Przesłaniaj metodę Equals w przypadku przeciążania operacji równości operatorów](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: Przesłoń metodę GetHashCode przy przesłanianiu metody Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
