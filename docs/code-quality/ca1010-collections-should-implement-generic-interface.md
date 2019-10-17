---
title: 'CA1010: Kolekcje powinny implementować interfejs generyczny'
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
ms.openlocfilehash: d3e50fb93e8cdfe6f65fe1b2de1da54b58a6a8c9
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449311"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: Kolekcje powinny implementować interfejs generyczny

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Kategoria|Microsoft. Design|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Typ implementuje interfejs <xref:System.Collections.IEnumerable?displayProperty=fullName>, ale nie implementuje interfejsu <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> i zawiera zestaw docelowy platformy .NET. Ta reguła ignoruje typy implementujące <xref:System.Collections.IDictionary?displayProperty=fullName>.

Domyślnie ta reguła sprawdza tylko typy widoczne na zewnątrz, ale [można to skonfigurować](#configurability).

## <a name="rule-description"></a>Opis reguły

Aby poszerzyć użyteczność kolekcji, zaimplementuj jeden z interfejsów kolekcji generycznej. Następnie kolekcja może służyć do wypełniania typów ogólnych kolekcji, takich jak następujące:

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, zaimplementuj jeden z następujących ogólnych interfejsów kolekcji:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>
- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>
- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Można bezpiecznie pominąć ostrzeżenie z tej reguły. Jednak użycie kolekcji będzie bardziej ograniczone.

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca1010.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).

## <a name="example-violation"></a>Przykładowe naruszenie

W poniższym przykładzie pokazano klasę (typ referencyjny), która pochodzi od nieogólnej klasy `CollectionBase`, która narusza tę regułę.

[!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]

Aby naprawić naruszenie tej reguły, wykonaj jedną z następujących czynności:

- Zaimplementuj interfejsy ogólne.
- Zmień klasę bazową na typ, który implementuje zarówno interfejsy ogólne, jak i inne niż ogólne, takie jak Klasa `Collection<T>`.

## <a name="fix-by-base-class-change"></a>Napraw według zmiany klasy bazowej

Poniższy przykład naprawia naruszenie, zmieniając klasę bazową kolekcji z klasy niegenerycznej `CollectionBase` do generycznej `Collection<T>` (`Collection(Of T)` w Visual Basic) klasy.

[!code-csharp[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]

Zmiana klasy bazowej już wydanej klasy jest traktowana jako istotna zmiana dla istniejących odbiorców.

## <a name="fix-by-interface-implementation"></a>Naprawa przez implementację interfejsu

Poniższy przykład naprawia naruszenie przez implementację tych interfejsów ogólnych: `IEnumerable<T>`, `ICollection<T>` i `IList<T>` (`IEnumerable(Of T)`, `ICollection(Of T)` i `IList(Of T)` w Visual Basic).

[!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]

## <a name="related-rules"></a>Powiązane reguły

- [CA1005: Unikaj nadużywania parametrów w typach ogólnych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1000: Nie deklaruj składowych statycznych w typach ogólnych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002: Nie ujawniaj list ogólnych](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006: Nie zagnieżdżaj typów ogólnych w sygnaturach składowych](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004: Metody ogólne powinny udostępniać parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1003: Użyj wystąpień ogólnej procedury obsługi zdarzeń](../code-quality/ca1003-use-generic-event-handler-instances.md)
- [CA1007: Używaj typów ogólnych wszędzie tam, gdzie jest to odpowiednie](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Zobacz także

- [Typy ogólne](/dotnet/csharp/programming-guide/generics/index)
