---
title: 'CA2216: Typy możliwe do likwidacji powinny deklarować finalizator'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisposableTypesShouldDeclareFinalizer
- CA2216
helpviewer_keywords:
- CA2216
- DisposableTypesShouldDeclareFinalizer
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e4baee9f532c0351feeced07ce9403245ccee14a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55927701"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216: Typy możliwe do likwidacji powinny deklarować finalizator

|||
|-|-|
|TypeName|DisposableTypesShouldDeclareFinalizer|
|CheckId|CA2216|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Typ, który implementuje <xref:System.IDisposable?displayProperty=fullName>i zawiera pola, które sugerują wykorzystanie zasobów niezarządzanych, nie implementuje finalizatora, zgodnie z opisem w <xref:System.Object.Finalize%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły

Naruszenie tej zasady jest zgłaszany, gdy możliwe do rozporządzania typ zawiera pola z następujących typów:

- <xref:System.IntPtr?displayProperty=fullName>

- <xref:System.UIntPtr?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy zaimplementować finalizator, który wywołuje swoje <xref:System.IDisposable.Dispose%2A> metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Bezpiecznie Pomijaj ostrzeżeń dla tej reguły, jeśli typ nie implementuje <xref:System.IDisposable> na potrzeby zwalniania niezarządzanych zasobów.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje typ, który narusza tę regułę.

[!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]

## <a name="related-rules"></a>Powiązane reguły

[CA2115: Wywołaj GC. KeepAlive podczas korzystania z zasobów natywnych](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

[CA1816: Wywołaj GC. SuppressFinalize poprawnie](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

[CA1049: Typy, które posiadają natywne zasoby powinny być usuwalne](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.IDisposable?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)