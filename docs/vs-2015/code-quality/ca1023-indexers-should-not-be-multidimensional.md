---
title: 'CA1023: indeksatory nie powinny być wielowymiarowe | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 30eee67d54e4fc3c73b265240fff82b0729e1cfc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546655"
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023: Indeksatory nie powinny być wielowymiarowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|Kategoria|Microsoft. Design|
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
 Poniższy przykład przedstawia typ, `DayOfWeek03` , z wielowymiarowym indeksatorem, który narusza regułę. Indeksator może być traktowany jako typ konwersji, dlatego jest bardziej odpowiednio narażony jako metoda. Typ jest przeprojektowany w `RedesignedDayOfWeek03` celu spełnienia reguły.

 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cpp/FxCop.Design.OneDimensionForIndexer.cpp#1)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/cs/FxCop.Design.OneDimensionForIndexer.cs#1)]
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.OneDimensionForIndexer/vb/FxCop.Design.OneDimensionForIndexer.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1043: Używaj argumentów typu liczba całkowita lub ciąg dla indeksatorów](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA1024: Używaj właściwości, o ile to możliwe](../code-quality/ca1024-use-properties-where-appropriate.md)
