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
ms.openlocfilehash: 296eb6407e3ce63b0eb28ff86c215c12ec724ce9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545317"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Testuj obecność pustych ciągów przy użyciu długości ciągu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Kategoria|Microsoft. Performance|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Ciąg jest porównywany z ciągiem pustym przy użyciu <xref:System.Object.Equals%2A?displayProperty=fullName> .

## <a name="rule-description"></a>Opis reguły
 Porównywanie ciągów przy użyciu <xref:System.String.Length%2A?displayProperty=fullName> właściwości lub <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> metody jest znacznie szybsze niż użycie <xref:System.Object.Equals%2A> . Jest to spowodowane wykonywaniem <xref:System.Object.Equals%2A> znacznie większej liczby instrukcji MSIL niż albo <xref:System.String.IsNullOrEmpty%2A> Liczba instrukcji wykonanych w celu pobrania <xref:System.String.Length%2A> wartości właściwości i porównania jej z zerem.

 Należy pamiętać, że <xref:System.Object.Equals%2A> i <xref:System.String.Length%2A> = = 0 zachowywać się inaczej w przypadku ciągów o wartości null. Jeśli spróbujesz pobrać wartość <xref:System.String.Length%2A> właściwości dla ciągu o wartości null, środowisko uruchomieniowe języka wspólnego wygeneruje <xref:System.NullReferenceException?displayProperty=fullName> . Jeśli wykonujesz porównanie między ciągiem o wartości null i pustym ciągiem, środowisko uruchomieniowe języka wspólnego nie zgłasza wyjątku; Porównanie zwraca wartość `false` . Testowanie dla wartości null nie ma znacząco wpływu na względną wydajność tych dwóch metod. W przypadku określania wartości docelowej [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] Użyj <xref:System.String.IsNullOrEmpty%2A> metody. W przeciwnym razie użyj <xref:System.String.Length%2A> porównania = = wszędzie tam, gdzie to możliwe.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zmień porównanie tak, aby korzystało z <xref:System.String.Length%2A> właściwości i testu dla ciągu o wartości null. W przypadku określania wartości docelowej [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] Użyj <xref:System.String.IsNullOrEmpty%2A> metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli wydajność nie jest problemem, bezpieczniej jest pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje różne techniki, które są używane do wyszukania pustego ciągu.

 [!code-csharp[FxCop.Performance.StringTest#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.StringTest/cs/FxCop.Performance.StringTest.cs#1)]
