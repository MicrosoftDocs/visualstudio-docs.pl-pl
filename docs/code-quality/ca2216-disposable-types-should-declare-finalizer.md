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
ms.openlocfilehash: 1616e889b3892aa656692a3e5b0895d4b131b7f1
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231254"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216: Typy możliwe do likwidacji powinny deklarować finalizator

|||
|-|-|
|TypeName|DisposableTypesShouldDeclareFinalizer|
|CheckId|CA2216|
|Kategoria|Microsoft.Usage|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Typ, który implementuje <xref:System.IDisposable?displayProperty=fullName>i ma pola, które sugerują użycie niezarządzanych zasobów, nie implementuje finalizatora, zgodnie z opisem przez <xref:System.Object.Finalize%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły

Zgłoszono naruszenie tej reguły, jeśli typ jednorazowy zawiera pola następujących typów:

- <xref:System.IntPtr?displayProperty=fullName>

- <xref:System.UIntPtr?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, zaimplementuj finalizator, który wywoła <xref:System.IDisposable.Dispose%2A> metodę.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jeśli typ nie zostanie zaimplementowany <xref:System.IDisposable> na potrzeby zwalniania niezarządzanych zasobów, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje typ, który narusza tę regułę.

[!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]

## <a name="related-rules"></a>Powiązane reguły

[CA2115: Wywołaj metodę GC. Utrzymywanie aktywności w przypadku korzystania z zasobów natywnych](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

[CA1816: Wywołaj metodę GC. SuppressFinalize prawidłowo](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

[CA1049: Typy, które są właścicielami zasobów natywnych, powinny być jednorazowe](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.IDisposable?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)