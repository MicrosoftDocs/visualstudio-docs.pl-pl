---
title: 'CA1036: Przesłaniaj metody porównywalnych typów'
ms.date: 03/11/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12b00c202373310b04021a46e74af2af7e10d535
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778999"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Przesłaniaj metody porównywalnych typów

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Typ implementuje <xref:System.IComparable?displayProperty=fullName> interfejsu i nie powoduje zastąpienia <xref:System.Object.Equals%2A?displayProperty=fullName> lub przeciążaj operator charakterystyczny dla równości, nierówności, mniejsze-niż, mniejsze niż-niż. Reguła nie raportuje naruszenie, jeśli typ dziedziczy implementacji interfejsu.

Domyślnie ta reguła przegląda tylko typy publiczne i chronione, ale jest to [konfigurowalne](#configurability).

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

Jest bezpieczne ostrzeżenia reguły CA1036, gdy naruszenia przyczyną jest Brak operatorów i język programowania nie obsługuje przeładowania operatora, jak w przypadku za pomocą Visual Basic. Jeśli okaże się, że implementacja operatorów nie ma sensu w kontekście swojej aplikacji, jest również bezpiecznie Pomijaj ostrzeżeń dla tej reguły, gdy zostanie wyzwolony go na operatory porównania niż op_equality —. Jednak zawsze powinien przesłonić op_equality — i == — operator w razie przesłonięcia <xref:System.Object.Equals%2A?displayProperty=nameWithType>.

## <a name="configurability"></a>Konfigurowalne

Po uruchomieniu tej reguły z [analizatory FxCop analizujące kod](install-fxcop-analyzers.md) (a nie przy użyciu statycznej analizy kodu) części, które można skonfigurować Twojej bazy kodu do uruchomienia tej reguły na, oparte na ich dostępność. Na przykład aby określić, że zasady powinny być uruchamiane wyłącznie w odniesieniu do powierzchni interfejsu API niepublicznych, Dodaj następujące pary klucz wartość w pliku .editorconfig w projekcie:

```
dotnet_code_quality.ca1036.api_surface = private, internal
```

Można skonfigurować tę opcję tylko reguły dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [analizatory FxCop analizujące kod z skonfigurować](configure-fxcop-analyzers.md).

## <a name="examples"></a>Przykłady

Poniższy kod zawiera typ, który implementuje prawidłowo <xref:System.IComparable>. Komentarze w kodzie zidentyfikować metody, które spełniają różne reguły that are related to <xref:System.Object.Equals%2A> i <xref:System.IComparable> interfejsu.

[!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]

Poniższy kod aplikacji sprawdza zachowanie <xref:System.IComparable> implementacji, pokazaną wcześniej.

[!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.IComparable?displayProperty=fullName>
- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Operatory równości](/dotnet/standard/design-guidelines/equality-operators)