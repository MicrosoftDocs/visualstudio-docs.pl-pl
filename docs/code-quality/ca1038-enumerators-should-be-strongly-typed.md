---
title: 'CA1038: Moduły wyliczające powinny być silnie typizowane'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56c2281f76b9064427d1d651523b9cda441eb029
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236018"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: Moduły wyliczające powinny być silnie typizowane

|||
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|Kategoria|Microsoft.Design|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Typ publiczny lub chroniony implementuje <xref:System.Collections.IEnumerator?displayProperty=fullName> , <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> ale nie zapewnia jednoznacznie wpisanej wersji właściwości. Typy, które pochodzą z następujących typów, są wykluczone z tej reguły:

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Opis reguły
Ta reguła wymaga <xref:System.Collections.IEnumerator> , aby implementacje zapewniały również silnie wpisaną <xref:System.Collections.IEnumerator.Current%2A> wersję właściwości, dzięki czemu użytkownicy nie muszą rzutować wartości zwracanej na typ Strong, gdy korzystają z funkcjonalności dostarczonej przez interfejs. Ta reguła zakłada, że typ, który <xref:System.Collections.IEnumerator> implementuje zawiera kolekcję wystąpień typu, który jest silniejszy niż. <xref:System.Object>

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, zaimplementuj jawnie Właściwość interfejsu (Zadeklaruj ją jako `IEnumerator.Current`). Dodaj publiczną silnie wpisaną wersję właściwości, zadeklarowaną jako `Current`i zwracającą silnie wpisaną obiekt.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Pomiń ostrzeżenie z tej reguły podczas implementowania modułu wyliczającego opartego na obiektach do użycia z kolekcją opartą na obiektach, taką jak drzewo binarne. Typy, które zwiększają nową kolekcję, definiują silnie jednoznacznie zdefiniowany moduł wyliczający i uwidaczniają właściwość o jednoznacznie określonym typie.

## <a name="example"></a>Przykład
Poniższy przykład ilustruje poprawny sposób implementacji typu silnie określonego <xref:System.Collections.IEnumerator> .

[!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../code-quality/codesnippet/CSharp/ca1038-enumerators-should-be-strongly-typed_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
[CA1035: Implementacje ICollection mają jednoznacznie wpisane elementy członkowskie](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

[CA1039: Listy są silnie wpisane](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.IEnumerator?displayProperty=fullName>
- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.DictionaryBase?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>