---
title: 'CA1043: Użyj argumentu integral lub string dla indeksatorów'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ae1d75341a857d380f78a2b8c0532fcdad1f5e1b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53987601"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043: Użyj argumentu integral lub string dla indeksatorów

|||
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony zawiera publiczny lub chroniony indeksatora, który używa innego niż typ indeksu <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName>, lub <xref:System.String?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły
 Indeksatory, oznacza to, że właściwości indeksowanych powinny używać typu integer lub string dla indeksu. Te typy są zwykle używane do indeksowania struktur danych i zwiększyć użyteczność biblioteki. Korzystanie z <xref:System.Object> typu powinny być ograniczone do tych przypadków, w którym określonego typu integer lub string nie można określić w czasie projektowania. Jeśli projekt wymaga innych typów dla indeksu, ponowne rozpatrzenie czy typ reprezentuje magazyn danych logicznych. Jeśli nie stanowi w magazynie danych logicznych, należy użyć metody.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Zmień indeks typu integer lub string, lub użyć metody zamiast indeksatora.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomijaj ostrzeżeń dla tej reguły tylko po dokładnego rozważenia potrzebę niestandardowe indeksatora.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano działanie indeksatora, który używa <xref:System.Int32> indeksu.

 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CSharp/ca1043-use-integral-or-string-argument-for-indexers_1.cs)]
 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CPP/ca1043-use-integral-or-string-argument-for-indexers_1.cpp)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/VisualBasic/ca1043-use-integral-or-string-argument-for-indexers_1.vb)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1023: Indeksatory nie powinny być wielowymiarowe](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)

 [CA1024: Korzystanie z właściwości, gdzie jest to odpowiednie](../code-quality/ca1024-use-properties-where-appropriate.md)