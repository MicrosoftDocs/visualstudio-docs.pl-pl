---
title: 'CA2213: Pola możliwe do rozporządzania należy rozporządzać'
ms.date: 11/05/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- DisposableFieldsShouldBeDisposed
- CA2213
helpviewer_keywords:
- CA2213
- DisposableFieldsShouldBeDisposed
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: de8df7e124cd8dd8ba9764add4006f7244155de8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53882081"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Pola możliwe do rozporządzania należy rozporządzać

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Typ, który implementuje <xref:System.IDisposable?displayProperty=fullName> deklaruje pola, które są typami, które implementują także <xref:System.IDisposable>. <xref:System.IDisposable.Dispose%2A> Metody pól nie jest wywoływany przez <xref:System.IDisposable.Dispose%2A> metody typu deklarującego.

## <a name="rule-description"></a>Opis reguły

Typ jest odpowiedzialny za usuwania wszystkich niezarządzanych zasobów. Reguła CA2213 sprawdza czy typu usuwalnego (czyli takiego, które implementuje <xref:System.IDisposable>) `T` deklaruje pole `F` oznacza to wystąpienie typu usuwalnego `FT`. Dla każdego pola `F` który został przypisany obiekt utworzony lokalnie w obrębie metody lub inicjatory typu zawierającego `T`, reguła próbuje zlokalizować wywołanie `FT.Dispose`. Reguła wyszukuje metody wywoływane przez `T.Dispose` i jeden poziom w dół (czyli metody wywoływane przez metody wywołane `FT.Dispose`).

> [!NOTE]
> CA2213 reguła jest uruchamiana tylko dla pól, przypisane obiekt rozporządzalny lokalnie utworzonego w ramach inicjatory i metod typu zawierającego. Jeśli obiekt jest utworzony lub przypisane poza typu `T`, nie jest wyzwalana reguła. Zmniejsza to szumu w przypadkach, gdzie typ zawierający nie posiada odpowiedzialność usuwania obiektu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy wywołać <xref:System.IDisposable.Dispose%2A> w polach, które są typami, które implementują <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Bezpiecznie Pomijaj ostrzeżeń dla tej reguły, jeśli nie jesteś odpowiedzialny dla przy zwalnianiu zasobów przechowywanych przez pole lub wywołanie <xref:System.IDisposable.Dispose%2A> występuje dokładniejsze wywoływania niż sprawdzanie reguły.

## <a name="example"></a>Przykład

Poniższy fragment kodu przedstawia typ `TypeA` implementującej <xref:System.IDisposable>.

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

Poniższy fragment kodu przedstawia typ `TypeB` który narusza regułę CA2213 przez zadeklarowanie pola `aFieldOfADisposableType` jako możliwe do rozporządzania typ (`TypeA`) i nie wywołuje metody <xref:System.IDisposable.Dispose%2A> pola.

[!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.IDisposable?displayProperty=fullName>
- [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)