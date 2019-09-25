---
title: 'CA1820: Testuj obecność pustych ciągów przy użyciu długości ciągu'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b197cacc764f1f5472d3eb074ac89199db508408
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233429"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Testuj obecność pustych ciągów przy użyciu długości ciągu

|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Kategoria|Microsoft.Performance|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Ciąg jest porównywany z ciągiem pustym przy użyciu <xref:System.Object.Equals%2A?displayProperty=nameWithType>.

## <a name="rule-description"></a>Opis reguły

Porównywanie ciągów przy <xref:System.String.Length%2A?displayProperty=nameWithType> użyciu właściwości <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> lub metody jest szybsze niż używanie <xref:System.Object.Equals%2A>. Jest to spowodowane <xref:System.Object.Equals%2A> wykonywaniem znacznie większej liczby instrukcji MSIL <xref:System.String.IsNullOrEmpty%2A> niż albo liczba <xref:System.String.Length%2A> instrukcji wykonanych w celu pobrania wartości właściwości i porównania jej z zerem.

Dla ciągów o wartości <xref:System.Object.Equals%2A> null `<string>.Length == 0` i zachowywać się inaczej. Jeśli spróbujesz pobrać wartość <xref:System.String.Length%2A> właściwości dla ciągu o wartości null, środowisko uruchomieniowe języka wspólnego <xref:System.NullReferenceException?displayProperty=fullName>wygeneruje. Jeśli wykonujesz porównanie między ciągiem o wartości null i pustym ciągiem, środowisko uruchomieniowe języka wspólnego nie zgłasza wyjątku i zwraca wartość `false`. Testowanie dla wartości null nie ma znacząco wpływu na względną wydajność tych dwóch metod. W <xref:System.String.IsNullOrEmpty%2A> przypadku określania wartości docelowej .NET Framework 2,0 lub nowszej Użyj metody. W przeciwnym razie należy <xref:System.String.Length%2A> użyć porównania = = 0 wszędzie tam, gdzie jest to możliwe.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, Zmień porównanie, aby użyć <xref:System.String.IsNullOrEmpty%2A> metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli wydajność nie jest problemem, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje różne techniki, które są używane do wyszukania pustego ciągu.

[!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]