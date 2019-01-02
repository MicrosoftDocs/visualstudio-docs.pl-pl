---
title: 'CA1816: Wywołaj GC. SuppressFinalize poprawnie'
ms.date: 06/30/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a3dcfdf8f094d50c5f462ae1a9d0ef4e85a0bb87
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53882289"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: Wywołaj GC. SuppressFinalize poprawnie

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Kategoria|Firmy Microsoft. Użycie|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Naruszenie tej zasady może być spowodowana przez:

- Metody, która jest implementacją <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> i nie wywołuje <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

- Metody, która nie jest implementacją <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> i wywołania <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

- Metoda, która wywołuje <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> i przekazuje na coś innego niż [tego (C#)](/dotnet/csharp/language-reference/keywords/this) lub [mi (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

## <a name="rule-description"></a>Opis reguły

<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> Metoda pozwala zwolnić zasoby w dowolnym momencie przed obiekt staje się dostępna dla wyrzucania elementów bezużytecznych. Jeśli <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> metoda jest wywoływana, zwalnia zasoby obiektu. To sprawia, że finalizacja niepotrzebne. <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> należy wywołać <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> więc moduł odśmiecania pamięci nie wywołać finalizatora obiektu.

Aby zapobiec konieczności ponownie przez typy pochodne z finalizatory <xref:System.IDisposable> i wywołać go, niezapieczętowane typy bez finalizatorów powinna nadal wywołać <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady:

- Jeśli metoda jest implementacją <xref:System.IDisposable.Dispose%2A>, dodaj wywołanie do <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>.

- Jeśli metoda nie jest implementacją <xref:System.IDisposable.Dispose%2A>, albo Usuń wywołanie funkcji <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> lub przenieść je na typ <xref:System.IDisposable.Dispose%2A> implementacji.

- Zmień wszystkie wywołania do <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> do przekazania [tego (C#)](/dotnet/csharp/language-reference/keywords/this) lub [mi (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Tylko Pomijaj ostrzeżeń dla tej reguły, jeśli używasz celowo <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> kontrolować okres istnienia innych obiektów. Nie pomijaj ostrzeżeń dla tej reguły, jeśli implementacja <xref:System.IDisposable.Dispose%2A> nie wywołuje <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>. W takiej sytuacji nie można wstrzymać finalizację obniża wydajność i oferuje nie korzyści.

## <a name="example-that-violates-ca1816"></a>Przykład, który narusza CA1816

Ten kod przedstawia metodę, która wywołuje <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>, ale nie zakończy się pomyślnie [tego (C#)](/dotnet/csharp/language-reference/keywords/this) lub [mi (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me). W wyniku tego kodu narusza regułę CA1816.

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]

## <a name="example-that-satisfies-ca1816"></a>Przykład, który spełnia CA1816

W tym przykładzie metodą oznacza poprawnie wywołania <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> , przekazując [tego (C#)](/dotnet/csharp/language-reference/keywords/this) lub [mi (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]

## <a name="related-rules"></a>Powiązane reguły

- [CA2215: Metody Dispose powinny wywoływać metodę dispose klasy bazowej](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)
- [CA2216: Typy możliwe do rozporządzania powinny deklarować finalizator](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Zobacz także

- [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)