---
title: 'CA1043: Użyj argumentu całkowitego lub ciągu dla indeksatorów | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 03d21a824d2d3a9151dad139575f32e3417cbd39
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546838"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043: Używaj argumentów typu liczba całkowita lub ciąg dla indeksatorów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony zawiera indeksator publiczny lub chroniony, który używa typu indeksu innego niż <xref:System.Int32?displayProperty=fullName> , <xref:System.Int64?displayProperty=fullName> , <xref:System.Object?displayProperty=fullName> , lub <xref:System.String?displayProperty=fullName> .

## <a name="rule-description"></a>Opis reguły
 Indeksatory, czyli właściwości indeksowane, powinny używać typów całkowitych lub ciągów dla indeksu. Te typy są zwykle używane do indeksowania struktur danych i zwiększają użyteczność biblioteki. Użycie <xref:System.Object> typu powinno być ograniczone do tych przypadków, w których nie można określić określonego typu Integer lub String w czasie projektowania. Jeśli projekt wymaga innych typów indeksu, należy rozważyć, czy typ reprezentuje logiczny magazyn danych. Jeśli nie reprezentuje logicznego magazynu danych, należy użyć metody.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zmień indeks na typ Integer lub String lub użyj metody zamiast indeksatora.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń ostrzeżenie z tej reguły tylko po starannym uwzględnieniu potrzeby niestandardowego indeksatora.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano indeksator, który używa <xref:System.Int32> indeksu.

 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cpp/FxCop.Design.IntegralOrStringIndexers.cpp#1)]
 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cs/FxCop.Design.IntegralOrStringIndexers.cs#1)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/vb/FxCop.Design.IntegralOrStringIndexers.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1023: Indeksatory nie powinny być wielowymiarowe](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)

 [CA1024: Używaj właściwości, o ile to możliwe](../code-quality/ca1024-use-properties-where-appropriate.md)
