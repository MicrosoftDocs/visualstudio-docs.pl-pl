---
title: 'CA1023: Indeksatory nie powinny być wielowymiarowe'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 08a45219eb2fceeaa9c58a140990ea577c941ff7
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923037"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023: Indeksatory nie powinny być wielowymiarowe

|||
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
Typ publiczny lub chroniony zawiera indeksator publiczny lub chroniony, który używa więcej niż jednego indeksu.

## <a name="rule-description"></a>Opis reguły
Indeksatory, czyli właściwości indeksowane, powinny używać jednego indeksu. Indeksatory wielowymiarowe mogą znacząco zmniejszyć użyteczność biblioteki. Jeśli projekt wymaga wielu indeksów, należy rozważyć, czy typ reprezentuje logiczny magazyn danych. Jeśli nie, użyj metody.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Zmień projekt tak, aby korzystał z Lone Integer lub indeksu ciągów, lub użyj metody zamiast indeksatora.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Pomiń ostrzeżenie z tej reguły tylko po starannym uwzględnieniu potrzeby niestandardowego indeksatora.

## <a name="example"></a>Przykład
Poniższy przykład przedstawia typ, `DayOfWeek03`, z wielowymiarowym indeksatorem, który narusza regułę. Indeksator może być traktowany jako typ konwersji, dlatego jest bardziej odpowiednio narażony jako metoda. Typ jest przeprojektowany w `RedesignedDayOfWeek03` celu spełnienia reguły.

[!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
[!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
[!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
[CA1043: Użyj argumentu całkowitego lub ciągu dla indeksatorów](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

[CA1024: Użyj właściwości, jeśli to konieczne](../code-quality/ca1024-use-properties-where-appropriate.md)