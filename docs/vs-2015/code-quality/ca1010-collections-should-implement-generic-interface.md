---
title: 'CA1010: Kolekcje powinny implementować interfejs ogólny | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 930e80530b10449c0a2e0d740d97e20f4b0cc5b5
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704274"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: Kolekcje powinny implementować interfejs ogólny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ widoczny na zewnątrz implementuje <xref:System.Collections.IEnumerable?displayProperty=fullName> interfejsu, ale nie implementuje <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> interfejsu i zawierający obiekty docelowe zestawu [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]. Ta zasada powoduje ignorowanie typy, które implementują <xref:System.Collections.IDictionary?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły
 Aby poszerzyć użyteczność kolekcji, zaimplementuj jeden z interfejsów kolekcji generycznej. Następnie Kolekcja może być używana, aby wypełnić typy generyczne kolekcji, takie jak następujące:

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>

- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>

- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zaimplementować jedną z następujących interfejsów kolekcji generycznej:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>

- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>

- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Bezpiecznie Pomijaj ostrzeżeń dla tej reguły; Kolekcja będzie jednak bardziej ograniczone użycie.

## <a name="example-violation"></a>Przykład naruszenia

### <a name="description"></a>Opis
 W poniższym przykładzie pokazano klasę (typ odwołania), która pochodzi z inną niż ogólna `CollectionBase` klasy, która narusza tę regułę.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericViolation/cs/FxCop.Design.CollectionsGenericViolation.cs#1)]

### <a name="comments"></a>Komentarze
 Aby naprawić naruszenie tej naruszenia, należy zaimplementować interfejsów ogólnych lub Zmień klasę bazową do typu, który już implementuje zarówno ogólnych i nieogólnych interfejsy, takie jak `Collection<T>` klasy.

## <a name="fix-by-base-class-change"></a>Rozwiązać przez zmianę w klasie bazowej

### <a name="description"></a>Opis
 Poniższy przykład naprawia naruszenia, zmieniając klasy bazowej kolekcji z inną niż ogólna `CollectionBase` klasy ogólnej `Collection<T>` (`Collection(Of T)` w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) klasy.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.CollectionsGenericBase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericBase/cs/FxCop.Design.CollectionsGenericBase.cs#1)]

### <a name="comments"></a>Komentarze
 Zmiana klasy bazowej klasy już wydana jest uznawane za istotną zmianę dla istniejących konsumentów.

## <a name="fix-by-interface-implementation"></a>Napraw, implementacja interfejsu

### <a name="description"></a>Opis
 Poniższy przykład naprawia naruszenia przez zaimplementowanie tych interfejsów ogólnych: `IEnumerable<T>`, `ICollection<T>`, i `IList<T>` (`IEnumerable(Of T)`, `ICollection(Of T)`, i `IList(Of T)` w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericInterface/cs/FxCop.Design.CollectionsGenericInterface.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1005: Unikaj nadużywania parametrów na typach generycznych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1000: Nie deklaruj składowych statycznych w typach ogólnych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Nie ujawniaj list ogólnych](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Nie zagnieżdżaj typów ogólnych w sygnaturach składowych](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Metody ogólne powinny podawać parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Użyj wystąpień obsługi zdarzeń generycznych](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Używaj typów ogólnych wszędzie, gdzie jest to odpowiednie](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Zobacz też
 [Typy ogólne](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
