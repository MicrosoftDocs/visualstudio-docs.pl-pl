---
title: 'CA1006: Nie zagnieżdżaj typów ogólnych w sygnaturach składowych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotNestGenericTypesInMemberSignatures
- CA1006
helpviewer_keywords:
- CA1006
- DoNotNestGenericTypesInMemberSignatures
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 00992fc71f07d820620cecbe57eac4f3b3702701
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539649"
---
# <a name="ca1006-do-not-nest-generic-types-in-member-signatures"></a>CA1006: Nie zagnieżdżaj typów ogólnych w podpisach składowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DoNotNestGenericTypesInMemberSignatures|
|CheckId|CA1006|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Widoczny na zewnątrz element członkowski ma sygnaturę zawierającą argument typu zagnieżdżonego.

## <a name="rule-description"></a>Opis reguły
 Argument typu zagnieżdżonego jest argumentem typu, który jest również typem ogólnym. Aby wywołać element członkowski, którego podpis zawiera argument typu zagnieżdżonego, użytkownik musi zainicjować wystąpienie pierwszego typu ogólnego i przekazać go do konstruktora drugiego typu ogólnego. Wymagana procedura oraz składnia są złożone i należy ich unikać.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zmień projekt, aby usunąć argument typu zagnieżdżonego.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Dostarczanie typów ogólnych w składni, która jest łatwa do zrozumienia i użycia, skraca czas wymagany do uczenia i zwiększania szybkości wdrażania nowych bibliotek.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia metodę, która narusza regułę i składnię, która jest wymagana do wywołania metody naruszania.

 [!code-csharp[FxCop.Design.NestedGenerics#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedGenerics/cs/FxCop.Design.NestedGenerics.cs#1)]
 [!code-vb[FxCop.Design.NestedGenerics#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NestedGenerics/vb/FxCop.Design.NestedGenerics.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1005: Unikaj nadmiernego użycia parametrów w typach ogólnych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Kolekcje powinny implementować interfejs ogólny](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Nie deklaruj statycznych składowych na typach ogólnych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Nie uwidaczniaj list ogólnych](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1004: Metody ogólne powinny podawać parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Użyj ogólnych wystąpień procedury obsługi zdarzeń](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Używaj typów ogólnych tam, gdzie to odpowiednie](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Zobacz też
 [Typy ogólne](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
