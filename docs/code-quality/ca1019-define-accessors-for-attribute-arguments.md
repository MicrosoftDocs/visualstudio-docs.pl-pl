---
title: 'CA1019: Zdefiniuj metody dostępu dla argumentów atrybutu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e840ddacc327799d5f138c84476598b16c6e006a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53920660"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019: Zdefiniuj metody dostępu dla argumentów atrybutu

|||
|-|-|
|TypeName|DefineAccessorsForAttributeArguments|
|CheckId|CA1019|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 W jego konstruktorze atrybutu definiuje argumenty, które nie mają odpowiednich właściwości.

## <a name="rule-description"></a>Opis reguły
 Atrybuty mogą definiować obowiązkowe argumenty, które trzeba określić, aby móc zastosować atrybut do obiektu docelowego. Znane są również jako argumenty pozycyjne, ponieważ są one dostarczane do konstruktorów atrybutu jako parametry pozycyjne. Dla każdego obowiązkowego argumentu atrybut powinien również dostarczyć odpowiadającą właściwość tylko do odczytu, dzięki której można pobrać wartość argumentu w czasie wykonywania. Ta reguła sprawdza, czy dla każdego parametru konstruktora zdefiniowano odpowiadającą właściwość.

 Atrybuty mogą też definiować argumenty opcjonalne, które są znane również jako argumenty nazwane. Argumenty te są dostarczane do konstruktorów atrybutu poprzez nazwę i powinny mieć odpowiadającą właściwość umożliwiającą odczyt i zapis.

 Dla obowiązkowych i opcjonalnych argumentach, odpowiadające właściwości i parametry konstruktora należy korzystać z taką samą nazwę ale o innej wielkości liter. Właściwości użyj Pascal wielkość liter w wyrazie i wielkość liter w wyrazie pisane Użyj parametrów.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy dodać właściwość tylko do odczytu dla każdego parametru konstruktora, który nie ma żadnej.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomijaj ostrzeżeń dla tej reguły, jeśli nie chcesz, aby wartość obowiązkowego argumentu jako możliwe do pobierania.

## <a name="custom-attributes-example"></a>Przykład atrybutów niestandardowych

Poniższy przykład przedstawia dwa atrybuty, które definiują obowiązkowy parametr (pozycyjny). Pierwszy implementacji atrybutu jest nieprawidłowo zdefiniowana. Drugi implementacja jest poprawna.

[!code-csharp[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_1.cs)]
[!code-vb[FxCop.Design.AttributeAccessors#1](../code-quality/codesnippet/VisualBasic/ca1019-define-accessors-for-attribute-arguments_1.vb)]

## <a name="positional-and-named-arguments"></a>Argumenty pozycyjne i nazwane

Argumenty pozycyjne i nazwane ułatwiają Wyczyść, aby konsumenci biblioteki argumenty, które są wymagane dla atrybutu i której argumenty są opcjonalne.

Poniższy przykład pokazuje implementację atrybut, który zawiera argumenty pozycyjne i nazwane:

[!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_2.cs)]

Poniższy przykład pokazuje, jak zastosować atrybut niestandardowy do dwie właściwości:

[!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../code-quality/codesnippet/CSharp/ca1019-define-accessors-for-attribute-arguments_3.cs)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1813: Unikaj niezapieczętowanych atrybutów](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Zobacz także
 [Atrybuty](/dotnet/standard/design-guidelines/attributes)