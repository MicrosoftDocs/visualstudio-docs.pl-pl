---
title: 'CA1019: Zdefiniuj metody dostępu dla argumentów atrybutów | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
helpviewer_keywords:
- CA1019
- DefineAccessorsForAttributeArguments
ms.assetid: 197f2378-3c43-427e-80de-9ec25006c05c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 81d61fca4728739cc6b548122781c67421a58270
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53859391"
---
# <a name="ca1019-define-accessors-for-attribute-arguments"></a>CA1019: Zdefiniuj metody dostępu dla argumentów atrybutu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

### <a name="description"></a>Opis
 Poniższy przykład przedstawia dwa atrybuty, które definiują obowiązkowy parametr (pozycyjny). Pierwszy implementacji atrybutu jest nieprawidłowo zdefiniowana. Drugi implementacja jest poprawna.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.AttributeAccessors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/cs/FxCop.Design.AttributeAccessors.cs#1)]
 [!code-vb[FxCop.Design.AttributeAccessors#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessors/vb/FxCop.Design.AttributeAccessors.vb#1)]

## <a name="positional-and-named-arguments"></a>Argumenty pozycyjne i nazwane

### <a name="description"></a>Opis
 Argumenty pozycyjne i nazwane należy wyczyścić klientom korzystającym z biblioteki, w której argumenty są obowiązkowe dla atrybutu i której argumenty są opcjonalne.

 Poniższy przykład pokazuje implementację atrybut, który ma argumentów nazwanych i pozycyjnych.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.AttributeAccessorsNamed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamed/cs/FxCop.Design.AttributeAccessorsNamed.cs#1)]

### <a name="comments"></a>Komentarze
 Poniższy przykład pokazuje, jak zastosować atrybut niestandardowy do dwie właściwości.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.AttributeAccessorsNamedApplied#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeAccessorsNamedApplied/cs/FxCop.Design.AttributeAccessorsNamedApplied.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1813: Unikaj niezapieczętowanych atrybutów](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Zobacz też
 [Atrybuty](http://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
