---
title: 'CA1010: Kolekcje powinny implementować interfejs generyczny | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
helpviewer_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 20238a844b45221207ca952d90d172ac720136ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655253"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: Kolekcje powinny implementować interfejs generyczny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Typ widoczny na zewnątrz implementuje interfejs <xref:System.Collections.IEnumerable?displayProperty=fullName>, ale nie implementuje interfejsu <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> i zawiera [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] elementów docelowych zestawu. Ta reguła ignoruje typy implementujące <xref:System.Collections.IDictionary?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły
 Aby poszerzyć użyteczność kolekcji, zaimplementuj jeden z interfejsów kolekcji generycznej. Następnie kolekcja może służyć do wypełniania typów ogólnych kolekcji, takich jak następujące:

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>

- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>

- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, zaimplementuj jeden z następujących ogólnych interfejsów kolekcji:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>

- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>

- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można bezpiecznie pominąć ostrzeżenie z tej reguły. jednak kolekcja będzie miała bardziej ograniczone użycie.

## <a name="example-violation"></a>Przykładowe naruszenie

### <a name="description"></a>Opis
 W poniższym przykładzie pokazano klasę (typ referencyjny), która pochodzi od nieogólnej klasy `CollectionBase`, która narusza tę regułę.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericViolation/cs/FxCop.Design.CollectionsGenericViolation.cs#1)]

### <a name="comments"></a>Komentarze
 Aby naprawić naruszenie tego naruszenia, należy zaimplementować interfejsy ogólne lub zmienić klasę bazową na typ, który implementuje zarówno interfejsy ogólne, jak i inne niż ogólne, takie jak Klasa `Collection<T>`.

## <a name="fix-by-base-class-change"></a>Napraw według zmiany klasy bazowej

### <a name="description"></a>Opis
 Poniższy przykład naprawia naruszenie, zmieniając klasę bazową kolekcji z klasy niegenerycznej `CollectionBase` na klasę generyczną `Collection<T>` (`Collection(Of T)` w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.CollectionsGenericBase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericBase/cs/FxCop.Design.CollectionsGenericBase.cs#1)]

### <a name="comments"></a>Komentarze
 Zmiana klasy bazowej już wydanej klasy jest traktowana jako istotna zmiana dla istniejących odbiorców.

## <a name="fix-by-interface-implementation"></a>Naprawa przez implementację interfejsu

### <a name="description"></a>Opis
 Poniższy przykład naprawia naruszenie, implementując te interfejsy ogólne: `IEnumerable<T>`, `ICollection<T>` i `IList<T>` (`IEnumerable(Of T)`, `ICollection(Of T)` i `IList(Of T)` w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericInterface/cs/FxCop.Design.CollectionsGenericInterface.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1005: Unikaj nadużywania parametrów w typach ogólnych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1000: Nie deklaruj składowych statycznych w typach ogólnych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Nie ujawniaj list ogólnych](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Nie zagnieżdżaj typów ogólnych w sygnaturach składowych](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Metody ogólne powinny udostępniać parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Użyj wystąpień ogólnej procedury obsługi zdarzeń](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Używaj typów ogólnych wszędzie tam, gdzie jest to odpowiednie](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Zobacz też
 [Typy ogólne](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
