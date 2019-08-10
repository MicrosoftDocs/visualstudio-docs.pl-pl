---
title: 'CA1002: Nie uwidaczniaj list ogólnych'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6e300edf07aa98facbe6059ba9574e238ec8f3e
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923254"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002: Nie uwidaczniaj list ogólnych

|||
|-|-|
|TypeName|DoNotExposeGenericLists|
|CheckId|CA1002|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
Typ zawiera widoczny na zewnątrz element członkowski, który jest <xref:System.Collections.Generic.List%601?displayProperty=fullName> typem, <xref:System.Collections.Generic.List%601?displayProperty=fullName> zwraca typ <xref:System.Collections.Generic.List%601?displayProperty=fullName> lub którego sygnatura zawiera parametr.

## <a name="rule-description"></a>Opis reguły
 <xref:System.Collections.Generic.List%601?displayProperty=fullName>jest kolekcją ogólną, która została zaprojektowana pod kątem wydajności i nie dziedziczenia. <xref:System.Collections.Generic.List%601?displayProperty=fullName>nie zawiera wirtualnych elementów członkowskich, które ułatwiają zmianę zachowania dziedziczonej klasy. Poniższe kolekcje ogólne są przeznaczone do dziedziczenia i powinny być udostępniane zamiast <xref:System.Collections.Generic.List%601?displayProperty=fullName>.

- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Zmień <xref:System.Collections.Generic.List%601?displayProperty=fullName> typ na jeden z kolekcji ogólnych przeznaczony do dziedziczenia.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżenia z tej reguły, chyba że zestaw, który podnosi to ostrzeżenie, nie powinien być biblioteką wielokrotnego użytku. Na przykład można bezpiecznie pominąć to ostrzeżenie w aplikacji dostrajania wydajności, w której uzyskano korzyść wydajności przy użyciu list ogólnych.

## <a name="related-rules"></a>Powiązane reguły
[CA1005: Unikaj nadmiernego użycia parametrów w typach ogólnych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010: Kolekcje powinny implementować interfejs ogólny](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: Nie deklaruj statycznych składowych na typach ogólnych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1006: Nie zagnieżdżaj typów ogólnych w sygnaturach składowych](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004: Metody ogólne powinny podawać parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Użyj ogólnych wystąpień programu obsługi zdarzeń](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007 Używaj typów ogólnych, tam gdzie to konieczne](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Zobacz także
[Typy ogólne](/dotnet/csharp/programming-guide/generics/index)