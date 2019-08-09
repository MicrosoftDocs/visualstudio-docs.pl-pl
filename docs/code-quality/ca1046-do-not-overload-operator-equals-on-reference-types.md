---
title: 'CA1046: Nie przeciążaj operatora równości w typach referencyjnych'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d765bfda87fe184256304b86f145f4f02adb7db6
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922626"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: Nie przeciążaj operatora równości w typach referencyjnych

|||
|-|-|
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|
|CheckId|CA1046|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
Publiczny lub zagnieżdżony typ referencyjny jest przeciążać operator równości.

## <a name="rule-description"></a>Opis reguły
Dla typów odwołań domyślna implementacja operatora równości jest prawie zawsze poprawna. Domyślnie dwa odwołania są równe tylko wtedy, gdy wskazują ten sam obiekt.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Usuń implementację operatora równości.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Jeśli typ referencyjny zachowuje się jak typ wartości wbudowanej, bezpieczne jest Pomijanie ostrzeżenia z tej reguły. Jeśli ma to na celu dodanie lub odjęcie wystąpienia typu, prawdopodobnie jest on poprawny, aby zaimplementować operator równości i pominąć naruszenie.

## <a name="example"></a>Przykład
Poniższy przykład ilustruje zachowanie domyślne podczas porównywania dwóch odwołań.

[!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]

## <a name="example"></a>Przykład

Poniższa aplikacja porównuje niektóre odwołania.

[!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]

Ten przykład generuje następujące wyniki:

```txt
a = new (2,2) and b = new (2,2) are equal? No
c and a are equal? Yes
b and a are == ? No
c and a are == ? Yes
```

## <a name="related-rules"></a>Powiązane reguły

[CA1013: Operator przeciążenia jest równy na przeciążeniu Dodaj i Odejmij](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Operatory równości](/dotnet/standard/design-guidelines/equality-operators)