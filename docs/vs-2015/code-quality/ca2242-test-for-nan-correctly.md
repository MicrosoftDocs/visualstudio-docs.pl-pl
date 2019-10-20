---
title: 'CA2242: pomyślnie przeprowadzono test dla elementu NaN | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8433ac081a45e3dbab80ffcd6f96e6d1db914337
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672011"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Testuj poprawnie pod kątem NaN
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Wyrażenie testuje wartość w odniesieniu do <xref:System.Single.NaN?displayProperty=fullName> lub <xref:System.Double.NaN?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły
 <xref:System.Double.NaN?displayProperty=fullName>, który reprezentuje nie liczbę, wyniki, gdy operacja arytmetyczna jest niezdefiniowana. Dowolne wyrażenie, które sprawdza równość między wartością a <xref:System.Double.NaN?displayProperty=fullName> zawsze zwraca `false`. Dowolne wyrażenie, które sprawdza nierówność między wartością i <xref:System.Double.NaN?displayProperty=fullName> zawsze zwraca `true`.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady i dokładnie określić, czy wartość reprezentuje <xref:System.Double.NaN?displayProperty=fullName>, użyj <xref:System.Single.IsNaN%2A?displayProperty=fullName> lub <xref:System.Double.IsNaN%2A?displayProperty=fullName> do przetestowania wartości.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono dwa wyrażenia, które niepoprawnie przetestują wartość względem <xref:System.Double.NaN?displayProperty=fullName> i wyrażenie, które prawidłowo używa <xref:System.Double.IsNaN%2A?displayProperty=fullName> do przetestowania wartości.

 [!code-csharp[FxCop.Usage.TestForNaN#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/cs/FxCop.Usage.TestForNaN.cs#1)]
 [!code-vb[FxCop.Usage.TestForNaN#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/vb/FxCop.Usage.TestForNaN.vb#1)]
