---
title: 'CA2215: Metody Dispose powinny wywoływać metodę Dispose klasy bazowej'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2215
- DisposeMethodsShouldCallBaseClassDispose
- Dispose methods should call base class dispose
helpviewer_keywords:
- DisposeMethodsShouldCallBaseClassDispose
- CA2215
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 468b63ca554ea126bbd621a2502e54540e6ed068
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231278"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: Metody Dispose powinny wywoływać metodę Dispose klasy bazowej

|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Kategoria|Microsoft.Usage|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Typ, który implementuje <xref:System.IDisposable?displayProperty=fullName> dziedziczy z typu, który również implementuje <xref:System.IDisposable>. Metoda typu dziedziczenia nie <xref:System.IDisposable.Dispose%2A> wywołuje metody typu nadrzędnego. <xref:System.IDisposable.Dispose%2A>

## <a name="rule-description"></a>Opis reguły
Jeśli typ dziedziczy z typu jednorazowego, musi wywołać <xref:System.IDisposable.Dispose%2A> metodę typu podstawowego z poziomu własnej <xref:System.IDisposable.Dispose%2A> metody. Wywołanie metody Dispose typu podstawowego gwarantuje, że wszystkie zasoby utworzone przez typ podstawowy są wydane.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, wywołaj metodę `base`.<xref:System.IDisposable.Dispose%2A> <xref:System.IDisposable.Dispose%2A> w metodzie.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
W przypadku wywołania do `base`programu można bezpiecznie pominąć ostrzeżenie z tej reguły.<xref:System.IDisposable.Dispose%2A> występuje na bardziej szczegółowym poziomie wywoływania niż sprawdzanie reguł.

## <a name="example"></a>Przykład
Poniższy przykład przedstawia typ `TypeA` , który implementuje. <xref:System.IDisposable>

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]

## <a name="example"></a>Przykład
Poniższy przykład pokazuje typ `TypeB` , który dziedziczy po typie `TypeA` i prawidłowo wywołuje jego <xref:System.IDisposable.Dispose%2A> metodę.

[!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]

## <a name="see-also"></a>Zobacz także

- <xref:System.IDisposable?displayProperty=fullName>
- [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)