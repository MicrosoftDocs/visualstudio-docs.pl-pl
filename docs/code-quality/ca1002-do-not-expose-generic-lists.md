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
ms.openlocfilehash: 4e2f7bba8f86ed1a2877fd622c5fd93560a9c5fa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779824"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002: Nie uwidaczniaj list ogólnych

|||
|-|-|
|TypeName|DoNotExposeGenericLists|
|CheckId|CA1002|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ zawiera widoczne na zewnątrz elementu członkowskiego, który jest <xref:System.Collections.Generic.List%601?displayProperty=fullName> wpisz zwraca <xref:System.Collections.Generic.List%601?displayProperty=fullName> typu lub którego podpis zawiera <xref:System.Collections.Generic.List%601?displayProperty=fullName> parametru.

## <a name="rule-description"></a>Opis reguły
 <xref:System.Collections.Generic.List%601?displayProperty=fullName> jest kolekcją ogólną, zapewniające wydajność i nie o dziedziczeniu. <xref:System.Collections.Generic.List%601?displayProperty=fullName> nie zawiera wirtualnych elementów członkowskich, które ułatwiają zmiany zachowania odziedziczoną klasę. Następujące kolekcje ogólne są zaprojektowane do obsługi dziedziczenia i powinny zostać ujawnione zamiast <xref:System.Collections.Generic.List%601?displayProperty=fullName>.

- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zmienić <xref:System.Collections.Generic.List%601?displayProperty=fullName> typu do jednej z kolekcji ogólnych, które jest przeznaczone do obsługi dziedziczenia.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły, chyba, że zestaw, który generuje to ostrzeżenie jest nie należy traktować jako biblioteki do ponownego użycia. Na przykład będzie bezpiecznie pominąć to ostrzeżenie w aplikacji wydajność dostosowana gdzie uzyskane korzyści wydajności z użycia list ogólnych.

## <a name="related-rules"></a>Powiązane reguły
 [CA1005: Unikaj nadużywania parametrów na typach generycznych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Kolekcje powinny implementować interfejs ogólny](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Nie deklaruj składowych statycznych w typach ogólnych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1006: Nie zagnieżdżaj typów ogólnych w sygnaturach składowych](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Metody ogólne powinny podawać parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Użyj wystąpień obsługi zdarzeń generycznych](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Używaj typów ogólnych wszędzie, gdzie jest to odpowiednie](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Zobacz także
 [Typy ogólne](/dotnet/csharp/programming-guide/generics/index)