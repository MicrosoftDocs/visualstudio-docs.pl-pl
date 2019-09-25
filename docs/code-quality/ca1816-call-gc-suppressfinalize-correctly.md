---
title: 'CA1816: Poprawnie wywołaj metodę GC.SuppressFinalize'
ms.date: 06/30/2018
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3fdd20df37586e50b5236872f1d84de48d08c87a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233531"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: Poprawnie wywołaj metodę GC.SuppressFinalize

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|Kategoria|Programu. Użycie|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Naruszenia tej reguły mogą być spowodowane przez:

- Metoda, która jest implementacją <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> i nie wywołuje. <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>

- Metoda, która nie jest implementacją <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> i wywołuje. <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>

- Metoda, która wywołuje <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> i przekazuje coś innego niż [this (C#)](/dotnet/csharp/language-reference/keywords/this) lub [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

## <a name="rule-description"></a>Opis reguły

<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> Metoda umożliwia użytkownikom zwalnianie zasobów w dowolnym momencie przed udostępnieniem obiektu do wyrzucania elementów bezużytecznych. <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> Jeśli metoda jest wywoływana, zwalnia zasoby obiektu. To sprawia, że finalizacja nie jest konieczna. <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>należy wywołać <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> , aby moduł zbierający elementy bezużyteczne nie wywoływał finalizatora obiektu.

Aby zapobiec, że typy pochodne z finalizatorami nie mają być <xref:System.IDisposable> ponownie wdrażane i wywoływane, niezapieczętowane typy bez finalizatorów powinny nadal być <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>wywoływane.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły:

- Jeśli metoda jest implementacją programu <xref:System.IDisposable.Dispose%2A>, Dodaj wywołanie do. <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>

- Jeśli metoda nie jest implementacją programu <xref:System.IDisposable.Dispose%2A>, należy usunąć <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> wywołanie lub przenieść <xref:System.IDisposable.Dispose%2A> je do implementacji typu.

- Zmień wszystkie wywołania na <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> , aby przekazać [(C#)](/dotnet/csharp/language-reference/keywords/this) lub do [mnie (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Pomiń tylko ostrzeżenie z tej reguły, jeśli zamierzasz celowo sterować <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> okresem istnienia innych obiektów w programie. Nie pomijaj ostrzeżenia z tej reguły, jeśli implementacja <xref:System.IDisposable.Dispose%2A> nie wywołuje. <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> W tej sytuacji niepowodzenie pomijania finalizowania oceny wydajności i nie zapewnia żadnych korzyści.

## <a name="example-that-violates-ca1816"></a>Przykład naruszający CA1816

Ten kod przedstawia metodę, która wywołuje <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>, ale nie przekazuje [tego (C#)](/dotnet/csharp/language-reference/keywords/this) ani [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me). W efekcie ten kod narusza reguły CA1816.

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]

## <a name="example-that-satisfies-ca1816"></a>Przykład, który spełnia wymagania CA1816

Ten przykład przedstawia metodę, która prawidłowo wywołuje <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> , przekazując [ten (C#)](/dotnet/csharp/language-reference/keywords/this) lub [Me (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass#me).

[!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_2.vb)]
[!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_2.cs)]

## <a name="related-rules"></a>Powiązane reguły

- [CA2215 Metody Dispose powinny wywoływać metodę Dispose klasy bazowej](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)
- [CA2216 Typy jednorazowe powinny deklarować finalizator](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>Zobacz także

- [Usuń wzorzec](/dotnet/standard/design-guidelines/dispose-pattern)