---
title: 'CA1005: Unikaj nadmiernego użycia parametrów w typach ogólnych'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
helpviewer_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34f9b8a79e38bdb9b6b097588697e2cd6c3545f7
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236592"
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005: Unikaj nadmiernego użycia parametrów w typach ogólnych

|||
|-|-|
|TypeName|AvoidExcessiveParametersOnGenericTypes|
|CheckId|CA1005|
|Kategoria|Microsoft.Design|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Widoczny na zewnątrz typ ogólny ma więcej niż dwa parametry typu.

## <a name="rule-description"></a>Opis reguły
Im więcej parametrów typu zawiera typ ogólny, tym trudniej poznać i zapamiętać, co reprezentuje każdy z nich. Jest to zazwyczaj oczywiste z jednym parametrem typu, jak `List<T>`w, i w niektórych przypadkach z dwoma parametrami typu, `Dictionary<TKey, TValue>`jak w. Jeśli istnieje więcej niż dwa parametry typu, trudności są zbyt duże dla większości użytkowników (na `TooManyTypeParameters<T, K, V>` przykład w C# lub `TooManyTypeParameters(Of T, K, V)` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Zmień projekt tak, aby używał nie więcej niż dwóch parametrów typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżenia z tej reguły, chyba że projekt absolutnie wymaga więcej niż dwóch parametrów typu. Dostarczanie typów ogólnych w składni, która jest łatwa do zrozumienia i użycia, skraca czas wymagany do uczenia i zwiększania szybkości wdrażania nowych bibliotek.

## <a name="related-rules"></a>Powiązane reguły
[CA1010: Kolekcje powinny implementować interfejs ogólny](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: Nie deklaruj statycznych składowych na typach ogólnych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002: Nie ujawniaj list ogólnych](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1006: Nie zagnieżdżaj typów ogólnych w sygnaturach składowych](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004: Metody ogólne powinny podawać parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Użyj ogólnych wystąpień programu obsługi zdarzeń](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007 Używaj typów ogólnych, tam gdzie to konieczne](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Zobacz także
[Typy ogólne](/dotnet/csharp/programming-guide/generics/index)