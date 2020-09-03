---
title: 'CA1035: implementacje ICollection mają jednoznacznie wpisane elementy członkowskie | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2e679fb3cc62ba80cfb7b56dfd7fa6590375565e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546617"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: Implementacje interfejsu ICollection mają silnie typizowane składowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony implementuje <xref:System.Collections.ICollection?displayProperty=fullName> , ale nie zapewnia metody silnie wpisanej do <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName> . Silnie wpisana wersja <xref:System.Collections.ICollection.CopyTo%2A> musi akceptować dwa parametry i nie może zawierać <xref:System.Array?displayProperty=fullName> ani tablicy <xref:System.Object?displayProperty=fullName> jako pierwszego parametru.

## <a name="rule-description"></a>Opis reguły
 Ta reguła wymaga <xref:System.Collections.ICollection> implementacji, aby zapewnić składowe silnie wpisane, tak aby użytkownicy nie musieli rzutować argumentów na <xref:System.Object> Typ, gdy korzystają z funkcji dostarczonych przez interfejs. Ta reguła zakłada, że typ, który implementuje, służy <xref:System.Collections.ICollection> do zarządzania kolekcją wystąpień typu, który jest silniejszy niż <xref:System.Object> .

 <xref:System.Collections.ICollection> implementuje <xref:System.Collections.IEnumerable?displayProperty=fullName> interfejs. Jeśli obiekty w kolekcji są rozbudowane <xref:System.ValueType?displayProperty=fullName> , musisz dostarczyć element członkowski o jednoznacznie określonym typie, <xref:System.Collections.IEnumerable.GetEnumerator%2A> Aby uniknąć spadku wydajności powodowanego przez opakowanie. Nie jest to wymagane, gdy obiekty kolekcji są typu referencyjnego.

 Aby zaimplementować silnie wpisaną wersję elementu członkowskiego interfejsu, należy zaimplementować elementy członkowskie interfejsu jawnie za pomocą nazw w formularzu `InterfaceName.InterfaceMemberName` , takich jak <xref:System.Collections.ICollection.CopyTo%2A> . Jawne elementy członkowskie interfejsu używają typów danych zadeklarowanych przez interfejs. Zaimplementuj silnie wpisane elementy członkowskie przy użyciu nazwy składowej interfejsu, takiej jak <xref:System.Collections.ICollection.CopyTo%2A> . Zadeklaruj elementy członkowskie z jednoznacznie określonymi typami jako publiczne i zadeklaruj parametry i zwróć wartości jako typ silny, który jest zarządzany przez kolekcję. Silne typy zastępują słabsze typy, takie jak <xref:System.Object> i <xref:System.Array> , które są zadeklarowane przez interfejs.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, zaimplementuj jawnie element członkowski interfejsu (Zadeklaruj go jako <xref:System.Collections.ICollection.CopyTo%2A> ). Dodaj publiczną silnie wpisaną składową, zadeklarowaną jako `CopyTo` , i podejmij silnie wpisaną tablicę jako pierwszy parametr.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń ostrzeżenie z tej reguły w przypadku zaimplementowania nowej kolekcji opartej na obiektach, takiej jak drzewo binarne, gdzie typy, które poszerzają nową kolekcję, określają typ silny. Te typy powinny być zgodne z tą regułą i uwidaczniają silnie wpisaną składowe.

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje poprawny sposób implementacji <xref:System.Collections.ICollection> .

 [!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ICollectionStrongTypes/cs/FxCop.Design.ICollectionStrongTypes.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1038: Moduły wyliczające powinny być silnie typizowane](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

 [CA1039: Listy są silnie typizowane](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>
