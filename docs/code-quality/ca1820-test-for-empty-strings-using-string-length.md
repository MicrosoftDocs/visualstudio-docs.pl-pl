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
ms.openlocfilehash: ae65ad9c1ad740b3ea39dd97d7430804292df057
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796760"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Testuj obecność pustych ciągów przy użyciu długości ciągu

|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Ciąg jest porównywana do pustego ciągu za pomocą <xref:System.Object.Equals%2A?displayProperty=nameWithType>.

## <a name="rule-description"></a>Opis reguły

Porównywanie ciągów za pomocą <xref:System.String.Length%2A?displayProperty=nameWithType> właściwości lub <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> metoda jest szybsza niż przy użyciu <xref:System.Object.Equals%2A>. Jest to spowodowane <xref:System.Object.Equals%2A> wykonuje znacznie więcej instrukcji MSIL niż albo <xref:System.String.IsNullOrEmpty%2A> lub liczbę instrukcji wykonywane w celu pobrania <xref:System.String.Length%2A> właściwości wartość i porównać go na wartość zero.

Dla ciągów o wartości null <xref:System.Object.Equals%2A> i <xref:System.String.Length%2A> == 0 zachowywać się inaczej. Jeśli użytkownik próbuje pobrać wartość <xref:System.String.Length%2A> właściwości na pusty ciąg, środowisko uruchomieniowe języka wspólnego generuje <xref:System.NullReferenceException?displayProperty=fullName>. Jeśli wykonywane jest porównanie pusty ciąg pusty ciąg, środowisko uruchomieniowe języka wspólnego nie zgłasza wyjątku i zwraca `false`. Testowanie pod kątem wartości null nie znacząco wpływa na względnej wydajności dwóm metodom. Podczas określania wartości .NET Framework 2.0 lub nowszej, należy użyć <xref:System.String.IsNullOrEmpty%2A> metody. W przeciwnym razie użyj <xref:System.String.Length%2A> == 0 porównania, jeśli to możliwe.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy zmienić wartość porównania do użycia <xref:System.String.Length%2A> właściwość i testowanie pusty ciąg. Jeśli przeznaczony dla .NET Framework 2.0 lub nowszej, należy użyć <xref:System.String.IsNullOrEmpty%2A> metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli wydajność nie ma problemu.

## <a name="example"></a>Przykład

Poniższy przykład ilustruje różne techniki, które są używane do wyszukania pusty ciąg.

[!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]