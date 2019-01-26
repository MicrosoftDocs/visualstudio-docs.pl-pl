---
title: 'CA1035: Implementacje interfejsu ICollection mają silnie typizowane składowe'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 35fa1bb45013b885bfdabb014980f97fe670d697
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54921989"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: Implementacje interfejsu ICollection mają silnie typizowane składowe

|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony implementuje <xref:System.Collections.ICollection?displayProperty=fullName> , ale nie udostępnia silnie typizowane metody <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>. Silnie typizowaną wersję <xref:System.Collections.ICollection.CopyTo%2A> przyjmują dwa parametry i nie może mieć <xref:System.Array?displayProperty=fullName> lub tablicę <xref:System.Object?displayProperty=fullName> jako pierwszy parametr.

## <a name="rule-description"></a>Opis reguły
 Ta reguła wymaga <xref:System.Collections.ICollection> implementacji w celu dostarczenia silnie typizowane składowe, dzięki czemu użytkownicy nie musieli rzutować argumentów na <xref:System.Object> wpisz podczas korzystania z funkcji dostępnych przez interfejs. Reguła ta zakłada, że typ, który zawiera <xref:System.Collections.ICollection> robi tak, aby zarządzać kolekcją wystąpień typów mocniejszych niż <xref:System.Object>.

 <xref:System.Collections.ICollection> implementuje <xref:System.Collections.IEnumerable?displayProperty=fullName> interfejsu. Jeśli obiekty z kolekcji rozszerzony <xref:System.ValueType?displayProperty=fullName>, należy podać element silnie typizowaną dla <xref:System.Collections.IEnumerable.GetEnumerator%2A> w celu uniknięcia spadek wydajności, który jest spowodowany przez pakowanie. Nie jest to wymagane w przypadku obiektów kolekcji typu odwołania.

 Aby zaimplementować silnie typizowaną wersję składowej interfejsu, należy zaimplementować składowych interfejsu jawnie przy użyciu nazw w formie `InterfaceName.InterfaceMemberName`, takich jak <xref:System.Collections.ICollection.CopyTo%2A>. Elementy członkowskie interfejsu jawnego używania typów danych, które są zadeklarowane przez interfejs. Implementowanie silnie typizowanych elementów członkowskich przy użyciu nazwy elementu członkowskiego interfejsu, takiego jak <xref:System.Collections.ICollection.CopyTo%2A>. Zadeklaruj silnie typizowanych elementów członkowskich jako publiczne i można deklarować parametrów i zwracają wartości na typ silny, który jest zarządzany przez kolekcję. Silne typy Zastąp słabszych typów, takich jak <xref:System.Object> i <xref:System.Array> , są zadeklarowane przez interfejs.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, implementować składowej interfejsu jawnego (Zadeklaruj go jako <xref:System.Collections.ICollection.CopyTo%2A>). Dodaj członka publicznego silnie typizowaną, zadeklarowany jako `CopyTo`, potem z łatwością podjąć silnie typizowaną tablicę jako pierwszy parametr.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomijaj ostrzeżeń dla tej reguły, w przypadku implementowania nowej kolekcji opartej na obiektach takich jak drzewo binarne, gdzie typy rozszerzające możliwości Nowa kolekcja określić silnego typu. Te typy powinny są zgodne z tą regułą i udostępnić silnie typizowanych elementów członkowskich.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano poprawny sposób implementacji <xref:System.Collections.ICollection>.

 [!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1038: Moduły wyliczające powinny być silnie typizowane](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

 [CA1039: Listy są silnie typizowane](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.Array?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>