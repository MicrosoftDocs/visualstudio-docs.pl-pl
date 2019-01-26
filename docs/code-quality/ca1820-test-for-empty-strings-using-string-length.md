---
title: 'CA1820: Testuj obecność pustych ciągów przy użyciu długości ciągu'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: f3d1d68f3bfee2c0662deafc94c20f1bbf768636
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54956263"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Testuj obecność pustych ciągów przy użyciu długości ciągu

|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Ciąg jest porównywana do pustego ciągu za pomocą <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły
 Porównywanie ciągów za pomocą <xref:System.String.Length%2A?displayProperty=fullName> właściwości lub <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> metoda jest znacznie szybsze niż użycie <xref:System.Object.Equals%2A>. Jest to spowodowane <xref:System.Object.Equals%2A> wykonuje znacznie więcej instrukcji MSIL niż albo <xref:System.String.IsNullOrEmpty%2A> lub liczbę instrukcji wykonywane w celu pobrania <xref:System.String.Length%2A> właściwości wartość i porównać go na wartość zero.

 Należy pamiętać, że <xref:System.Object.Equals%2A> i <xref:System.String.Length%2A> == 0 zachowywać się inaczej dla ciągów o wartości null. Jeśli użytkownik próbuje pobrać wartość <xref:System.String.Length%2A> właściwości na pusty ciąg, środowisko uruchomieniowe języka wspólnego generuje <xref:System.NullReferenceException?displayProperty=fullName>. Jeśli wykonywane jest porównanie pusty ciąg pusty ciąg, środowisko uruchomieniowe języka wspólnego nie zgłasza wyjątku; Zwraca wynik porównania `false`. Testowanie pod kątem wartości null nie znacząco wpływa na względnej wydajności dwóm metodom. Podczas określania wartości [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], użyj <xref:System.String.IsNullOrEmpty%2A> metody. W przeciwnym razie użyj <xref:System.String.Length%2A> == porównania, jeśli to możliwe.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zmienić wartość porównania do użycia <xref:System.String.Length%2A> właściwość i testowanie pusty ciąg. Jeśli celem [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], użyj <xref:System.String.IsNullOrEmpty%2A> metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli wydajność nie ma problemu.

## <a name="example"></a>Przykład
 Poniższy przykład ilustruje różne techniki, które są używane do wyszukania pusty ciąg.

 [!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]