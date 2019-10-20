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
ms.openlocfilehash: c3a08f4987fe57a94aaee8f3df6129782fd6448c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661763"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: Wyliczenia powinny być silnie typizowane
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony implementuje <xref:System.Collections.IEnumerator?displayProperty=fullName> ale nie udostępnia jednoznacznie wpisanej wersji właściwości <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName>. Typy, które pochodzą z następujących typów, są wykluczone z tej reguły:

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Opis reguły
 Ta reguła wymaga, aby implementacje <xref:System.Collections.IEnumerator> również zapewniały silnie wpisaną wersję właściwości <xref:System.Collections.IEnumerator.Current%2A>, dzięki czemu użytkownicy nie muszą rzutować wartości zwracanej na typ Strong, gdy używają funkcji dostarczonej przez interfejs. Ta reguła zakłada, że typ, który implementuje <xref:System.Collections.IEnumerator> zawiera kolekcję wystąpień typu, który jest silniejszy niż <xref:System.Object>.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, zaimplementuj jawnie Właściwość interfejsu (Zadeklaruj ją jako `IEnumerator.Current`). Dodaj publiczną silnie wpisaną wersję właściwości, zadeklarowaną jako `Current` i zwracają obiekt silnie określonego typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń ostrzeżenie z tej reguły podczas implementowania modułu wyliczającego opartego na obiektach do użycia z kolekcją opartą na obiektach, taką jak drzewo binarne. Typy, które zwiększają nową kolekcję, definiują silnie jednoznacznie zdefiniowany moduł wyliczający i uwidaczniają właściwość o jednoznacznie określonym typie.

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje poprawny sposób implementacji typu <xref:System.Collections.IEnumerator> o jednoznacznie określonym typie.

 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes/cs/FxCop.Design.IEnumeratorStrongTypes.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1035: Implementacje interfejsu ICollection mają silnie typizowane składowe](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1039: Listy są silnie typizowane](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Zobacz też
 <xref:System.Collections.IEnumerator?displayProperty=fullName><xref:System.Collections.CollectionBase?displayProperty=fullName>
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
