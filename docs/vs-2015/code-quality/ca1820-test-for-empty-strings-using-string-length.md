---
title: 'CA1820: przetestowanie pustych ciągów przy użyciu długości ciągu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6711dac907de2777cf892b20269fec7e99d3bd6f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657505"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Zbadaj pod kątem ciągów pustych przy użyciu długości ciągu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Kategoria|Microsoft. Performance|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Ciąg jest porównywany z pustym ciągiem przy użyciu <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły
 Porównywanie ciągów przy użyciu właściwości <xref:System.String.Length%2A?displayProperty=fullName> lub metody <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> jest znacznie szybsze niż używanie <xref:System.Object.Equals%2A>. Jest to spowodowane tym, że <xref:System.Object.Equals%2A> wykonuje znacznie więcej instrukcji MSIL niż <xref:System.String.IsNullOrEmpty%2A> lub liczba instrukcji wykonanych w celu pobrania wartości właściwości <xref:System.String.Length%2A> i porównania jej z zerem.

 Należy pamiętać, że <xref:System.Object.Equals%2A> i <xref:System.String.Length%2A> = = 0 zachowywać się inaczej w przypadku ciągów o wartości null. Jeśli spróbujesz uzyskać wartość właściwości <xref:System.String.Length%2A> w ciągu o wartości null, środowisko uruchomieniowe języka wspólnego zgłosi <xref:System.NullReferenceException?displayProperty=fullName>. Jeśli wykonujesz porównanie między ciągiem o wartości null i pustym ciągiem, środowisko uruchomieniowe języka wspólnego nie zgłasza wyjątku; Porównanie zwraca `false`. Testowanie dla wartości null nie ma znacząco wpływu na względną wydajność tych dwóch metod. W przypadku [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] określania wartości docelowej Użyj metody <xref:System.String.IsNullOrEmpty%2A>. W przeciwnym razie użyj porównania <xref:System.String.Length%2A> = = wszędzie tam, gdzie to możliwe.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zmień porównanie tak, aby używało właściwości <xref:System.String.Length%2A> i testu dla ciągu o wartości null. Jeśli [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] określania wartości docelowej, użyj metody <xref:System.String.IsNullOrEmpty%2A>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli wydajność nie jest problemem, bezpieczniej jest pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje różne techniki, które są używane do wyszukania pustego ciągu.

 [!code-csharp[FxCop.Performance.StringTest#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.StringTest/cs/FxCop.Performance.StringTest.cs#1)]
