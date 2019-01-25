---
title: 'CA1035: Implementacje interfejsu ICollection mają silnie typizowane składowe | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6eda1bc311c39d0ec1da9667ac078c22183e2bd0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54754705"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: Implementacje interfejsu ICollection mają silnie typizowane składowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

 [!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ICollectionStrongTypes/cs/FxCop.Design.ICollectionStrongTypes.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1038: Moduły wyliczające powinny być silnie typizowane](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

 [CA1039: Listy są silnie typizowane](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.Array?displayProperty=fullName><xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>
