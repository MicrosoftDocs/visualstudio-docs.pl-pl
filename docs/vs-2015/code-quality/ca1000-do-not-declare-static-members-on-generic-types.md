---
title: 'CA1000: Nie deklaruj składowych statycznych w typach ogólnych | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1000
- DoNotDeclareStaticMembersOnGenericTypes
helpviewer_keywords:
- DoNotDeclareStaticMembersOnGenericTypes
- CA1000
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 127a8cf5382e4822ae2a6b52e03b74682f53e2d8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54766888"
---
# <a name="ca1000-do-not-declare-static-members-on-generic-types"></a>CA1000: Nie deklaruj statycznych składowych na typach ogólnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|
|CheckId|CA1000|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Ogólny typ widoczny na zewnątrz zawiera `static` (`Shared` w języku Visual Basic) elementu członkowskiego.

## <a name="rule-description"></a>Opis reguły
 Gdy `static` nosi nazwę elementu członkowskiego typu ogólnego, argument typu musi być określona dla typu. Po wywołaniu wystąpienia ogólnego elementu członkowskiego, które nie obsługuje wnioskowania, dla elementu członkowskiego musi zostać określony argument typu. Składnia określająca argument typu w tych dwóch przypadkach są różne i łatwo o pomyłkę, jak pokazują następujące wywołania:

```vb
' Shared method in a generic type.
GenericType(Of Integer).SharedMethod()

' Generic instance method that does not support inference.
someObject.GenericMethod(Of Integer)()
```

```csharp
// Static method in a generic type.
GenericType<int>.StaticMethod();

// Generic instance method that does not support inference.
someObject.GenericMethod<int>();
```

 Ogólnie rzecz biorąc zarówno poprzednich deklaracjach należy unikać tak, aby argument typu nie ma należy określić, kiedy nosi nazwę elementu członkowskiego. Skutkuje to składnię do wywoływania elementów członkowskich w typach ogólnych, które nie różni się od składni dla innych typów ogólnych. Aby uzyskać więcej informacji, zobacz [CA1004: Metody ogólne powinny podawać parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Usuń statyczny element członkowski, lub zmień go do elementu członkowskiego wystąpienia.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Typy ogólne w składni, który jest łatwy do zrozumienia i użycia, zapewniając skraca czas, jest wymagana, aby dowiedzieć się, która zwiększa szybkość przyjęcia nowe biblioteki.

## <a name="related-rules"></a>Powiązane reguły
 [CA1005: Unikaj nadużywania parametrów na typach generycznych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Kolekcje powinny implementować interfejs ogólny](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1002: Nie ujawniaj list ogólnych](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Nie zagnieżdżaj typów ogólnych w sygnaturach składowych](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Metody ogólne powinny podawać parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Użyj wystąpień obsługi zdarzeń generycznych](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Używaj typów ogólnych wszędzie, gdzie jest to odpowiednie](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Zobacz też
 [Typy ogólne](http://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
