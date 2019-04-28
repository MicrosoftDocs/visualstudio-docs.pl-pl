---
title: 'CA1010: Kolekcje powinny implementować interfejs ogólny'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
helpviewer_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c71912fdd70226e1b4be3c14be7c4e0bac26259d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779849"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: Kolekcje powinny implementować interfejs ogólny

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Typ implementuje <xref:System.Collections.IEnumerable?displayProperty=fullName> interfejsu, ale nie implementuje <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> interfejsu i zawierający .NET cele zestawu. Ta zasada powoduje ignorowanie typy, które implementują <xref:System.Collections.IDictionary?displayProperty=fullName>.

Domyślnie ta reguła przegląda tylko typy widoczne na zewnątrz, ale jest to [konfigurowalne](#configurability).

## <a name="rule-description"></a>Opis reguły

Aby poszerzyć użyteczność kolekcji, zaimplementuj jeden z interfejsów kolekcji generycznej. Następnie Kolekcja może być używana, aby wypełnić typy generyczne kolekcji, takie jak następujące:

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy zaimplementować jedną z następujących interfejsów kolekcji generycznej:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>
- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>
- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Bezpiecznie Pomijaj ostrzeżeń dla tej reguły; Jednak użycie kolekcji będą bardziej ograniczone.

## <a name="configurability"></a>Konfigurowalne

Po uruchomieniu tej reguły z [analizatory FxCop analizujące kod](install-fxcop-analyzers.md) (a nie przy użyciu statycznej analizy kodu) części, które można skonfigurować Twojej bazy kodu do uruchomienia tej reguły na, oparte na ich dostępność. Na przykład aby określić, że zasady powinny być uruchamiane wyłącznie w odniesieniu do powierzchni interfejsu API niepublicznych, Dodaj następujące pary klucz wartość w pliku .editorconfig w projekcie:

```
dotnet_code_quality.ca1010.api_surface = private, internal
```

Można skonfigurować tę opcję tylko reguły dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [analizatory FxCop analizujące kod z skonfigurować](configure-fxcop-analyzers.md).

## <a name="example-violation"></a>Przykład naruszenia

W poniższym przykładzie pokazano klasę (typ odwołania), która pochodzi z inną niż ogólna `CollectionBase` klasy, która narusza tę regułę.

[!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]

Aby naprawić naruszenie tej zasady, wykonaj jedną z następujących czynności:

- Implementowanie interfejsów ogólnych.
- Zmień klasę bazową do typu, który już implementuje zarówno ogólnych i nieogólnych interfejsy, takie jak `Collection<T>` klasy.

## <a name="fix-by-base-class-change"></a>Rozwiązać przez zmianę w klasie bazowej

Poniższy przykład naprawia naruszenia, zmieniając klasy bazowej kolekcji z inną niż ogólna `CollectionBase` klasy ogólnej `Collection<T>` (`Collection(Of T)` w języku Visual Basic) klasy.

[!code-csharp[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]

Zmiana klasy bazowej klasy już wydana jest uznawane za istotną zmianę dla istniejących konsumentów.

## <a name="fix-by-interface-implementation"></a>Napraw, implementacja interfejsu

Poniższy przykład naprawia naruszenia przez zaimplementowanie tych interfejsów ogólnych: `IEnumerable<T>`, `ICollection<T>`, i `IList<T>` (`IEnumerable(Of T)`, `ICollection(Of T)`, i `IList(Of T)` w języku Visual Basic).

[!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]

## <a name="related-rules"></a>Powiązane reguły

- [CA1005: Unikaj nadużywania parametrów na typach generycznych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1000: Nie deklaruj składowych statycznych w typach ogólnych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002: Nie ujawniaj list ogólnych](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006: Nie zagnieżdżaj typów ogólnych w sygnaturach składowych](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004: Metody ogólne powinny podawać parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1003: Użyj wystąpień obsługi zdarzeń generycznych](../code-quality/ca1003-use-generic-event-handler-instances.md)
- [CA1007: Używaj typów ogólnych wszędzie, gdzie jest to odpowiednie](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Zobacz także

- [Typy ogólne](/dotnet/csharp/programming-guide/generics/index)