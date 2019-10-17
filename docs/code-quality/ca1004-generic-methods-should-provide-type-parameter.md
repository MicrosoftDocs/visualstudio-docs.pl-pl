---
title: 'CA1004: Generyczne metody powinny dostarczyć parametry typu'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1004
- GenericMethodsShouldProvideTypeParameter
helpviewer_keywords:
- GenericMethodsShouldProvideTypeParameter
- CA1004
ms.assetid: 38755f6a-fb45-4bf2-932e-0354ad826499
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 86dab876992227107beaa843412809a609ff1e4d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72446908"
---
# <a name="ca1004-generic-methods-should-provide-type-parameter"></a>CA1004: Generyczne metody powinny dostarczyć parametry typu

|||
|-|-|
|TypeName|GenericMethodsShouldProvideTypeParameter|
|CheckId|CA1004|
|Kategoria|Microsoft. Design|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Sygnatura parametru widocznej na zewnątrz metody generycznej nie zawiera typów, które odpowiadają wszystkim parametrom typu metody.

## <a name="rule-description"></a>Opis reguły
Wnioskowanie to ustalenie argumentu typu metody ogólnej przez typ argumentu przekazanego do metody, zamiast użycia jawnej specyfikacji argumentu typu. Aby włączyć wnioskowanie, podpis parametru metody ogólnej musi zawierać parametr, który jest tego samego typu co parametr typu dla metody. W tym przypadku argument typu nie musi zostać określony. Jeśli używasz wnioskowania dla wszystkich parametrów typu, składnia wywołania metod ogólnych i nieogólnych jest taka sama. Upraszcza to użyteczność metod ogólnych.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Zmień projekt tak, aby podpis parametru zawiera ten sam typ dla każdego parametru typu metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły. Dostarczanie typów ogólnych w składni, która jest łatwa do zrozumienia i użycia, skraca czas wymagany do uczenia i zwiększania szybkości wdrażania nowych bibliotek.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje składnię do wywoływania dwóch metod ogólnych. Argument typu dla `InferredTypeArgument` jest wywnioskowany, a argument typu dla `NotInferredTypeArgument` musi być jawnie określony.

[!code-vb[FxCop.Design.Inference#1](../code-quality/codesnippet/VisualBasic/ca1004-generic-methods-should-provide-type-parameter_1.vb)]
[!code-csharp[FxCop.Design.Inference#1](../code-quality/codesnippet/CSharp/ca1004-generic-methods-should-provide-type-parameter_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
[CA1005: Unikaj nadużywania parametrów w typach ogólnych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010: Kolekcje powinny implementować interfejs ogólny](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: Nie deklaruj składowych statycznych w typach ogólnych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002: Nie ujawniaj list ogólnych](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1006: Nie zagnieżdżaj typów ogólnych w sygnaturach składowych](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1003: Użyj wystąpień ogólnej procedury obsługi zdarzeń](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007: Używaj typów ogólnych wszędzie tam, gdzie jest to odpowiednie](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Zobacz także
[Typy ogólne](/dotnet/csharp/programming-guide/generics/index)
