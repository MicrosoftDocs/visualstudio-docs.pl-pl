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
ms.openlocfilehash: 2dc43e92b92b6f963900057a76dfe88e38a3638f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545226"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: Przeciążenia operatorów mają nazwane elementy alternatywne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
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
|&|oraz|&|BitwiseAnd|
|&=|I =|&=|BitwiseAnd|
|&#124;|Lub|&#124;|Bitowy|
|&#124;=|Lub =|&#124;=|Bitowy|
|--|Nie dotyczy|--|Dekrementacji|
|/|/|/|Dzielenie|
|/=|/=|/=|Dzielenie|
|==|=|==|Równa się|
|^|Xor|^|Xor|
|^=|XOR =|^=|Xor|
|>|>|>|Porównaj|
|>=|>=|>=|Porównaj|
|++|Nie dotyczy|++|Przyrost|
|<>|!=|Równa się|
|<<|<<|<<|LeftShift|
|<<=|<<=|<<=|LeftShift|
|<|<|<|Porównaj|
|<=|<=|\<=|Porównaj|
|&&|Nie dotyczy|&&|LogicalAnd|
|&#124;&#124;|Nie dotyczy|&#124;&#124;|Logiczny|
|!|Nie dotyczy|!|LogicalNot|
|%|Mod|%|Mod lub reszta|
|%=|Nie dotyczy|%=|Mod|
|* (binarny)|*|*|Mnożenie|
|*=|Nie dotyczy|*=|Mnożenie|
|~|Not|~|OnesComplement|
|>>|>>|>>|RightShift|
=|Nie dotyczy|>>=|RightShift|
|-(binarny)|-(binarny)|-(binarny)|Odejmowanie|
|-=|Nie dotyczy|-=|Odejmowanie|
|true|IsTrue|Nie dotyczy|IsTrue (Właściwość)|
|-(jednoargumentowe)|Nie dotyczy|-|Negate|
|+ (jednoargumentowy)|Nie dotyczy|+|Znak plus|
|fałsz|IsFalse|Fałsz|IsTrue (Właściwość)|

 Nie można obciążyć elementu = = w wybranym języku.

 Reguła sprawdza także niejawne i jawne Operatory rzutowania w typie ( `SomeType` ) przez sprawdzenie metod o nazwie `ToSomeType` i `FromSomeType` .

 W języku C#, gdy operator binarny jest przeciążony, odpowiedni operator przypisania, jeśli istnieje, jest również niejawnie przeciążony.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zaimplementować alternatywną metodę dla operatora; Nadaj mu nazwę przy użyciu zalecanej nazwy alternatywnej.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżenia z tej reguły, jeśli implementujesz bibliotekę udostępnioną. Aplikacje mogą ignorować ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie zdefiniowano strukturę, która narusza tę regułę. Aby poprawić ten przykład, Dodaj metodę publiczną `Add(int x, int y)` do struktury.

 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorOverloadsHaveNamedAlternates/cs/FxCop.Usage.OperatorOverloadsHaveNamedAlternates.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1046: Nie przeciążaj operatora równości w typach referencyjnych](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2226: Operatory powinny mieć symetryczne przeciążenia](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Przesłaniaj metodę equals w przypadku przeciążania operatora równości](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: Przesłaniaj metodę GetHashCode w razie przesłaniania metody Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
