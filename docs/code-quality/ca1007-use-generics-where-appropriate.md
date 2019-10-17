---
title: 'CA1007: Używaj danych generycznych wszędzie, gdzie jest to odpowiednie'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d2c9416d1cdc655df110c7230b9f0e29290221a7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72441703"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007: Używaj danych generycznych wszędzie, gdzie jest to odpowiednie

|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|Kategoria|Microsoft. Design|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Metoda widoczna na zewnątrz zawiera parametr referencyjny typu <xref:System.Object?displayProperty=fullName> i zawierający elementy docelowe zestawu .NET Framework 2,0.

## <a name="rule-description"></a>Opis reguły
Parametr Reference jest parametrem modyfikowanym za pomocą słowa kluczowego `ref` (`ByRef` w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Typ argumentu, który jest dostarczony dla parametru reference musi dokładnie odpowiadać typowi parametru Reference. Aby użyć typu, który jest pochodną typu parametru odwołania, należy najpierw rzutować i przypisać do zmiennej typu parametru odwołania. Użycie metody generycznej pozwala na przekazywanie wszystkich typów, które podlegają ograniczeniom, do metody bez uprzedniego rzutowania typu na typ parametru odwołania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, należy określić metodę ogólna i zastąpić parametr <xref:System.Object> przy użyciu parametru typu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje procedurę wymiany ogólnego przeznaczenia, która jest zaimplementowana jako metody nierodzajowe i rodzajowe. Zwróć uwagę na to, jak efektywnie ciągi są zamieniane przy użyciu metody ogólnej w porównaniu do metody niegenerycznej.

[!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
[!code-csharp[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
[CA1005: Unikaj nadużywania parametrów w typach ogólnych](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010: Kolekcje powinny implementować interfejs ogólny](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: Nie deklaruj składowych statycznych w typach ogólnych](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002: Nie ujawniaj list ogólnych](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1006: Nie zagnieżdżaj typów ogólnych w sygnaturach składowych](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004: Metody ogólne powinny udostępniać parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Użyj wystąpień ogólnej procedury obsługi zdarzeń](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>Zobacz także
[Typy ogólne](/dotnet/csharp/programming-guide/generics/index)
