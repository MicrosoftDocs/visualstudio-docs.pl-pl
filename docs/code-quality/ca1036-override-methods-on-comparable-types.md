---
title: 'CA1036: Przesłaniaj metody porównywalnych typów'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 05f4bd750f1ec2ad4d336acb1a00b8848de389bf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825584"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Przesłaniaj metody porównywalnych typów

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony implementuje <xref:System.IComparable?displayProperty=fullName> interfejsu i nie powoduje zastąpienia <xref:System.Object.Equals%2A?displayProperty=fullName> lub przeciążaj operator charakterystyczny dla równości, nierówności, mniejsze-niż, mniejsze niż-niż. Reguła nie raportuje naruszenie, jeśli typ dziedziczy implementacji interfejsu.

## <a name="rule-description"></a>Opis reguły

Typy, które definiują niestandardowej kolejności sortowania implementować <xref:System.IComparable> interfejsu. <xref:System.IComparable.CompareTo%2A> Metoda zwraca wartość całkowitą, która wskazuje właściwy porządek sortowania dla dwóch wystąpień tego typu. Ta reguła umożliwia określenie typów, które porządek sortowania. Ustawienie kolejności sortowania oznacza, że zwykłe znaczenia równości, nierówności, mniej-niż i większa-niż nie mają zastosowania. Gdy dostarczać implementację <xref:System.IComparable>, zazwyczaj należy także Przesłoń <xref:System.Object.Equals%2A> tak, aby zwraca wartości, które są zgodne z <xref:System.IComparable.CompareTo%2A>. Jeśli zastąpisz <xref:System.Object.Equals%2A> z kodowaniem są w języku, który obsługuje przeciążenia operatorów, należy również podać operatorów, które są zgodne z <xref:System.Object.Equals%2A>.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy zastąpić <xref:System.Object.Equals%2A>. Jeśli język programowania obsługuje przeładowania operatora, należy podać następujące operatory:

- op_equality —

- op_inequality —

- op_LessThan

- op_greaterthan —

W języku C# tokenów, które są używane do reprezentowania tych operatorów są następujące:

```csharp
==
!=
<
>
```

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne ostrzeżenia reguły CA1036, gdy naruszenia przyczyną jest Brak operatorów i język programowania nie obsługuje przeładowania operatora, jak w przypadku za pomocą Visual Basic. Jest również bezpiecznie Pomijaj ostrzeżeń dla tej reguły, gdy generowane na operatory równości, inne niż op_equality — Jeśli stwierdzisz, że implementacja operatorów nie ma sensu w kontekście swojej aplikacji. Jednak należy zawsze za pośrednictwem op_equality — i == — operator w przypadku przesłania metody Object.Equals.

## <a name="example"></a>Przykład
 Poniższy przykład zawiera typ, który implementuje prawidłowo <xref:System.IComparable>. Komentarze w kodzie zidentyfikować metody, które spełniają różne reguły that are related to <xref:System.Object.Equals%2A> i <xref:System.IComparable> interfejsu.

 [!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]

## <a name="example"></a>Przykład
 Następująca aplikacja sprawdza zachowanie <xref:System.IComparable> implementacji, pokazaną wcześniej.

 [!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.IComparable?displayProperty=fullName>
- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Operatory równości](/dotnet/standard/design-guidelines/equality-operators)