---
title: 'CA2215: Metody Dispose powinny wywoływać metodę dispose klasy bazowej'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8531bfd8407415aa1868fb5e1f633be442ce9bc7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53844226"
---
# <a name="ca2215-dispose-methods-should-call-base-class-dispose"></a>CA2215: Metody Dispose powinny wywoływać metodę dispose klasy bazowej

|||
|-|-|
|TypeName|DisposeMethodsShouldCallBaseClassDispose|
|CheckId|CA2215|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ, który implementuje <xref:System.IDisposable?displayProperty=fullName> dziedziczy z typu, który także implementuje <xref:System.IDisposable>. <xref:System.IDisposable.Dispose%2A> Metoda dziedziczącej typu nie mogą wywoływać <xref:System.IDisposable.Dispose%2A> metodę typu nadrzędnego.

## <a name="rule-description"></a>Opis reguły
 Jeśli typ dziedziczy z typu usuwalnego, musi on wywołać <xref:System.IDisposable.Dispose%2A> metody typu podstawowego z w obrębie własnej <xref:System.IDisposable.Dispose%2A> metody. Wywołanie metody typu podstawowego usuwania gwarantuje, czy wszystkie zasoby utworzone przez typ bazowy są wydawane.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy wywołać `base`.<xref:System.IDisposable.Dispose%2A> w swojej <xref:System.IDisposable.Dispose%2A> metody.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest to bezpieczne pominąć ostrzeżenie od tej reguły, jeśli wywołanie `base`.<xref:System.IDisposable.Dispose%2A> występuje, dokładniejsze wywoływania niż sprawdzanie reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano typu `TypeA` implementującej <xref:System.IDisposable>.

 [!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano typu `TypeB` który dziedziczy z typu `TypeA` i prawidłowo wywołuje jego <xref:System.IDisposable.Dispose%2A> metody.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]

## <a name="see-also"></a>Zobacz także

- <xref:System.IDisposable?displayProperty=fullName>
- [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)