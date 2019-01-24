---
title: 'CA1038: Moduły wyliczające powinny być silnie typizowane | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: be143ecb57a952c45e518eef0d83d52274075614
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54754686"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: Moduły wyliczające powinny być silnie typizowane
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony implementuje <xref:System.Collections.IEnumerator?displayProperty=fullName> , ale nie udostępnia silnie typizowanej wersji <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> właściwości. Wyjątek od tej reguły są typy, które są uzyskiwane z następujących typów:

-   <xref:System.Collections.CollectionBase?displayProperty=fullName>

-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>

-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Opis reguły
 Ta reguła wymaga <xref:System.Collections.IEnumerator> implementacji w celu dostarczenia silnie typizowanej wersji <xref:System.Collections.IEnumerator.Current%2A> właściwość tak, aby użytkownicy nie musieli rzutować wartości zwróconej na typ silny, używając funkcje, które są dostarczane przez interfejs. Reguła ta zakłada, że typ, który zawiera <xref:System.Collections.IEnumerator> zawiera kolekcję wystąpień typów mocniejszych niż <xref:System.Object>.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, implementują właściwość interfejsu jawnego (Zadeklaruj go jako `IEnumerator.Current`). Dodaj publiczny silnie typizowanej wersji właściwości zadeklarowane jako `Current`, i zwraca obiekt silnie typizowanych.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomijaj ostrzeżeń dla tej reguły, podczas implementowania oparte na obiekt modułu wyliczającego do użytku z kolekcją obiektów, takich jak drzewa binarnego. Typy, które rozszerzają Nowa kolekcja będzie Definiowanie silnie typizowanej modułu wyliczającego i ujawniać silnie typizowane właściwości.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia właściwy sposób implementacji silnie typizowaną <xref:System.Collections.IEnumerator> typu.

 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes/cs/FxCop.Design.IEnumeratorStrongTypes.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1035: Implementacje interfejsu ICollection mają silnie typizowane składowe](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1039: Listy są silnie typizowane](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.Collections.IEnumerator?displayProperty=fullName><xref:System.Collections.CollectionBase?displayProperty=fullName>
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
