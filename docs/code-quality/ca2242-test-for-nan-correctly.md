---
title: 'CA2242: Poprawnie testuj nie-liczby (NaN)'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8912cb6eeec8009364936a42d572f4f3d83fae5e
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919919"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Poprawnie testuj nie-liczby (NaN)

|||
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
Wyrażenie testuje wartość w odniesieniu <xref:System.Single.NaN?displayProperty=fullName> do lub. <xref:System.Double.NaN?displayProperty=fullName>

## <a name="rule-description"></a>Opis reguły
 <xref:System.Double.NaN?displayProperty=fullName>, która reprezentuje nie liczbę, wyniki w przypadku niezdefiniowania operacji arytmetycznej. Dowolne wyrażenie, które sprawdza równość między wartością i <xref:System.Double.NaN?displayProperty=fullName> zawsze zwraca `false`. Dowolne wyrażenie, które sprawdza nierówność między wartością i <xref:System.Double.NaN?displayProperty=fullName> zawsze zwraca `true`wartość.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady i dokładnie określić, czy wartość reprezentuje <xref:System.Double.NaN?displayProperty=fullName>, użyj <xref:System.Single.IsNaN%2A?displayProperty=fullName> lub <xref:System.Double.IsNaN%2A?displayProperty=fullName> , aby przetestować wartość.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
W poniższym przykładzie przedstawiono dwa wyrażenia, które niepoprawnie przetestuje <xref:System.Double.NaN?displayProperty=fullName> wartość z i wyrażenie, które <xref:System.Double.IsNaN%2A?displayProperty=fullName> prawidłowo używa do przetestowania wartości.

[!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
[!code-csharp[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]