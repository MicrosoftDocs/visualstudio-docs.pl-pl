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
ms.openlocfilehash: a0c832b7eb4a94506c5e15dfa5858bb9f6753912
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546266"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Poprawnie testuj nie-liczby (NaN)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Wyrażenie testuje wartość w odniesieniu do <xref:System.Single.NaN?displayProperty=fullName> lub <xref:System.Double.NaN?displayProperty=fullName> .

## <a name="rule-description"></a>Opis reguły
 <xref:System.Double.NaN?displayProperty=fullName>, która reprezentuje nie liczbę, wyniki w przypadku niezdefiniowania operacji arytmetycznej. Dowolne wyrażenie, które sprawdza równość między wartością i <xref:System.Double.NaN?displayProperty=fullName> zawsze zwraca `false` . Dowolne wyrażenie, które sprawdza nierówność między wartością i <xref:System.Double.NaN?displayProperty=fullName> zawsze zwraca wartość `true` .

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady i dokładnie określić, czy wartość reprezentuje <xref:System.Double.NaN?displayProperty=fullName> , użyj lub, <xref:System.Single.IsNaN%2A?displayProperty=fullName> <xref:System.Double.IsNaN%2A?displayProperty=fullName> Aby przetestować wartość.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono dwa wyrażenia, które niepoprawnie przetestuje wartość z <xref:System.Double.NaN?displayProperty=fullName> i wyrażenie, które prawidłowo używa <xref:System.Double.IsNaN%2A?displayProperty=fullName> do przetestowania wartości.

 [!code-csharp[FxCop.Usage.TestForNaN#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/cs/FxCop.Usage.TestForNaN.cs#1)]
 [!code-vb[FxCop.Usage.TestForNaN#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/vb/FxCop.Usage.TestForNaN.vb#1)]
