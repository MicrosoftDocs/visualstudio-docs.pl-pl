---
title: 'CA1038: moduły wyliczające powinny być silnie wpisane | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e660b1af58dca8d0d69ce2844076382c4a5a1f12
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548268"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: Moduły wyliczające powinny być silnie typizowane
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony implementuje <xref:System.Collections.IEnumerator?displayProperty=fullName> , ale nie zapewnia jednoznacznie wpisanej wersji <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> właściwości. Typy, które pochodzą z następujących typów, są wykluczone z tej reguły:

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Opis reguły
 Ta reguła wymaga, <xref:System.Collections.IEnumerator> Aby implementacje zapewniały również silnie wpisaną wersję <xref:System.Collections.IEnumerator.Current%2A> właściwości, dzięki czemu użytkownicy nie muszą rzutować wartości zwracanej na typ Strong, gdy korzystają z funkcjonalności dostarczonej przez interfejs. Ta reguła zakłada, że typ, który implementuje <xref:System.Collections.IEnumerator> zawiera kolekcję wystąpień typu, który jest silniejszy niż <xref:System.Object> .

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, zaimplementuj jawnie Właściwość interfejsu (Zadeklaruj ją jako `IEnumerator.Current` ). Dodaj publiczną silnie wpisaną wersję właściwości, zadeklarowaną jako `Current` i zwracającą silnie wpisaną obiekt.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń ostrzeżenie z tej reguły podczas implementowania modułu wyliczającego opartego na obiektach do użycia z kolekcją opartą na obiektach, taką jak drzewo binarne. Typy, które zwiększają nową kolekcję, definiują silnie jednoznacznie zdefiniowany moduł wyliczający i uwidaczniają właściwość o jednoznacznie określonym typie.

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje poprawny sposób implementacji typu silnie określonego <xref:System.Collections.IEnumerator> .

 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes/cs/FxCop.Design.IEnumeratorStrongTypes.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1035: Implementacje interfejsu ICollection mają silnie typizowane składowe](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1039: Listy są silnie typizowane](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.Collections.IEnumerator?displayProperty=fullName> <xref:System.Collections.CollectionBase?displayProperty=fullName>
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
