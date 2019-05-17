---
title: 'CA2213: Pola możliwe do likwidacji należy likwidować'
ms.date: 05/14/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b38157fcc23561b47a919151aa78a71f98b3909b
ms.sourcegitcommit: 283f2dbce044a18e9f6ac6398f6fc78e074ec1ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2019
ms.locfileid: "65805001"
---
# <a name="ca2213-disposable-fields-should-be-disposed"></a>CA2213: Pola możliwe do likwidacji należy likwidować

|||
|-|-|
|TypeName|DisposableFieldsShouldBeDisposed|
|CheckId|CA2213|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Typ, który implementuje <xref:System.IDisposable?displayProperty=fullName> deklaruje pola, które są typami, które implementują także <xref:System.IDisposable>. <xref:System.IDisposable.Dispose%2A> Metody pól nie jest wywoływany przez <xref:System.IDisposable.Dispose%2A> metody typu deklarującego.

## <a name="rule-description"></a>Opis reguły

Typ jest odpowiedzialny za usuwania wszystkich niezarządzanych zasobów. Reguła CA2213 sprawdza czy typu usuwalnego (czyli takiego, które implementuje <xref:System.IDisposable>) `T` deklaruje pole `F` oznacza to wystąpienie typu usuwalnego `FT`. Dla każdego pola `F` który został przypisany obiekt utworzony lokalnie w obrębie metody lub inicjatory typu zawierającego `T`, reguła próbuje zlokalizować wywołanie `FT.Dispose`. Reguła wyszukuje metody wywoływane przez `T.Dispose` i jeden poziom w dół (czyli metody wywoływane przez metody wywołane `T.Dispose`).

> [!NOTE]
> Inne niż [specjalne przypadki](#special-cases), reguła CA2213 generowane tylko dla pól, przypisane obiekt rozporządzalny lokalnie utworzonego w ramach inicjatory i metod typu zawierającego. Jeśli obiekt jest utworzony lub przypisane poza typu `T`, nie jest wyzwalana reguła. Zmniejsza to szumu w przypadkach, gdzie typ zawierający nie posiada odpowiedzialność usuwania obiektu.

### <a name="special-cases"></a>Specjalne przypadki

CA2213 reguły mogą również uruchamiane w przypadku pól z następujących typów nawet, jeśli obiekt, który ich nie jest tworzony lokalnie:

- <xref:System.IO.Stream?displayProperty=nameWithType>
- <xref:System.IO.TextReader?displayProperty=nameWithType>
- <xref:System.IO.TextWriter?displayProperty=nameWithType>
- <xref:System.Resources.IResourceReader?displayProperty=nameWithType>

Przekazywanie obiektu z jednego z następujących typów do konstruktora, a następnie przypisując go do pola wskazuje *dispose przenoszenie własności* do nowo skonstruowanego typu. Oznacza to, że nowo skonstruowany typ odpowiada teraz do usuwania obiektu. Jeśli obiekt nie jest usuwane, naruszenie CA2213 występuje.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy wywołać <xref:System.IDisposable.Dispose%2A> w polach, które są typami, które implementują <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Jest to bezpieczne Pomijaj ostrzeżeń dla tej reguły, jeśli:

- Flagą typu nie odpowiada dla przy zwalnianiu zasobów przechowywanych przez pole (oznacza to, że typ ma *dispose własność*)
- Wywołanie <xref:System.IDisposable.Dispose%2A> występuje dokładniejsze wywoływania niż sprawdzanie reguły

## <a name="example"></a>Przykład

Poniższy fragment kodu przedstawia typ `TypeA` implementującej <xref:System.IDisposable>.

[!code-csharp[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]

Poniższy fragment kodu przedstawia typ `TypeB` który narusza regułę CA2213 przez zadeklarowanie pola `aFieldOfADisposableType` jako możliwe do rozporządzania typ (`TypeA`) i nie wywołuje metody <xref:System.IDisposable.Dispose%2A> pola.

[!code-csharp[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.IDisposable?displayProperty=fullName>
- [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)