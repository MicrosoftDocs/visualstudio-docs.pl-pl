---
title: 'CA1004: Metody ogólne powinny podawać parametr typu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: cec1af3bfb528902631f0007bd19d2bb4dc8a7e7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54971900"
---
# <a name="ca1004-generic-methods-should-provide-type-parameter"></a>CA1004: Metody ogólne powinny podawać parametr typu

|||
|-|-|
|TypeName|GenericMethodsShouldProvideTypeParameter|
|CheckId|CA1004|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Podpis parametru metody ogólnej widocznego na zewnątrz zawiera typy, które odnoszą się do wszystkich parametrów typu metody.

## <a name="rule-description"></a>Opis reguły
 Wnioskowanie to ustalenie argumentu typu metody ogólnej przez typ argumentu przekazanego do metody, zamiast użycia jawnej specyfikacji argumentu typu. Aby włączyć wnioskowanie, podpis parametru metody ogólnej musi zawierać parametr, który jest tego samego typu co parametr typu dla metody. W tym przypadku argument typu nie musi zostać określony. Gdy używasz wnioskowania dla wszystkich parametrów typu składnia wywoływania metod rodzajowych i nierodzajowych wystąpienia jest identyczna. Upraszcza to użycie metod ogólnych.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zmienić projekt tak, aby podpis parametru zawiera ten sam typ, dla każdego typu parametru metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Typy ogólne w składni, który jest łatwy do zrozumienia i użycia, zapewniając skraca czas, jest wymagana, aby dowiedzieć się, która zwiększa szybkość przyjęcia nowe biblioteki.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje składnię wywołania dwóch metod ogólnych. Typ argumentu dla `InferredTypeArgument` jest wnioskowany i typ argumentu dla `NotInferredTypeArgument` muszą być jawnie określone.

 [!code-vb[FxCop.Design.Inference#1](../code-quality/codesnippet/VisualBasic/ca1004-generic-methods-should-provide-type-parameter_1.vb)]
 [!code-csharp[FxCop.Design.Inference#1](../code-quality/codesnippet/CSharp/ca1004-generic-methods-should-provide-type-parameter_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1005: Unikaj nadużywania parametrów na typach generycznych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Kolekcje powinny implementować interfejs ogólny](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Nie deklaruj składowych statycznych w typach ogólnych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Nie ujawniaj list ogólnych](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Nie zagnieżdżaj typów ogólnych w sygnaturach składowych](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1003: Użyj wystąpień obsługi zdarzeń generycznych](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Używaj typów ogólnych wszędzie, gdzie jest to odpowiednie](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Zobacz także
 [Typy ogólne](/dotnet/csharp/programming-guide/generics/index)