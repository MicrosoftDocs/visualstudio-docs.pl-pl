---
title: 'CA1035: Implementacje interfejsu ICollection mają silnie typizowane składowe'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d9e74daa464a55a543b5eb8c189c9ddf1295301
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236023"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: Implementacje interfejsu ICollection mają silnie typizowane składowe

|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|Kategoria|Microsoft.Design|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Typ publiczny lub chroniony implementuje <xref:System.Collections.ICollection?displayProperty=fullName> , ale nie zapewnia metody silnie wpisanej do. <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName> Silnie wpisana wersja <xref:System.Collections.ICollection.CopyTo%2A> musi akceptować dwa parametry i nie może <xref:System.Array?displayProperty=fullName> zawierać ani tablicy <xref:System.Object?displayProperty=fullName> jako pierwszego parametru.

## <a name="rule-description"></a>Opis reguły
Ta reguła wymaga <xref:System.Collections.ICollection> implementacji, aby zapewnić składowe silnie wpisane, tak aby użytkownicy nie musieli rzutować <xref:System.Object> argumentów na typ, gdy korzystają z funkcji dostarczonych przez interfejs. Ta reguła zakłada, że typ, który <xref:System.Collections.ICollection> implementuje, służy do zarządzania kolekcją wystąpień typu, który jest silniejszy niż. <xref:System.Object>

 <xref:System.Collections.ICollection><xref:System.Collections.IEnumerable?displayProperty=fullName> implementuje interfejs. Jeśli obiekty w kolekcji <xref:System.ValueType?displayProperty=fullName>są rozbudowane, musisz dostarczyć <xref:System.Collections.IEnumerable.GetEnumerator%2A> element członkowski o jednoznacznie określonym typie, aby uniknąć spadku wydajności powodowanego przez opakowanie. Nie jest to wymagane, gdy obiekty kolekcji są typu referencyjnego.

Aby zaimplementować silnie wpisaną wersję elementu członkowskiego interfejsu, należy zaimplementować elementy członkowskie interfejsu jawnie za pomocą nazw w formularzu `InterfaceName.InterfaceMemberName`, takich jak <xref:System.Collections.ICollection.CopyTo%2A>. Jawne elementy członkowskie interfejsu używają typów danych zadeklarowanych przez interfejs. Zaimplementuj silnie wpisane elementy członkowskie przy użyciu nazwy składowej interfejsu, <xref:System.Collections.ICollection.CopyTo%2A>takiej jak. Zadeklaruj elementy członkowskie z jednoznacznie określonymi typami jako publiczne i zadeklaruj parametry i zwróć wartości jako typ silny, który jest zarządzany przez kolekcję. Silne typy zastępują słabsze typy, takie jak <xref:System.Object> i <xref:System.Array> , które są zadeklarowane przez interfejs.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, zaimplementuj jawnie element członkowski interfejsu (Zadeklaruj go jako <xref:System.Collections.ICollection.CopyTo%2A>). Dodaj publiczną silnie wpisaną składową, `CopyTo`zadeklarowaną jako, i podejmij silnie wpisaną tablicę jako pierwszy parametr.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Pomiń ostrzeżenie z tej reguły w przypadku zaimplementowania nowej kolekcji opartej na obiektach, takiej jak drzewo binarne, gdzie typy, które poszerzają nową kolekcję, określają typ silny. Te typy powinny być zgodne z tą regułą i uwidaczniają silnie wpisaną składowe.

## <a name="example"></a>Przykład
Poniższy przykład ilustruje poprawny sposób implementacji <xref:System.Collections.ICollection>.

[!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
[CA1038 Moduły wyliczające powinny być silnie wpisane](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

[CA1039: Listy są silnie wpisane](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.Array?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>