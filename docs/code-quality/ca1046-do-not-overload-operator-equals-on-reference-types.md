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
ms.openlocfilehash: 9f9304fcd86a9b36a729b1436fe16471b449ac0d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778726"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: Nie przeciążaj operatora równości w typach referencyjnych

|||
|-|-|
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|
|CheckId|CA1046|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Odwołanie do publicznego lub publiczny zagnieżdżony typ przeciążenia operatora równości.

## <a name="rule-description"></a>Opis reguły
 Dla typów odwołań domyślna implementacja operatora równości jest prawie zawsze poprawna. Domyślnie dwa odwołania są równe tylko wtedy, gdy wskazują ten sam obiekt.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Usuń implementacja operatora równości.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, gdy typ odwołania, który zachowuje się jak określonym wbudowanym typie wartości. Jeśli jest to istotne w celu dodawania lub odejmowania na wystąpienia typu, jest prawdopodobnie poprawna, implementuje operatora równości i pominąć naruszenia.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano domyślne zachowanie podczas porównywania dwóch odwołań.

 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]

## <a name="example"></a>Przykład

Następująca aplikacja porównuje niektórych odwołań.

[!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]

Ten przykład generuje następujące wyniki:

```txt
a = new (2,2) and b = new (2,2) are equal? No
c and a are equal? Yes
b and a are == ? No
c and a are == ? Yes
```

## <a name="related-rules"></a>Powiązane reguły

[CA1013: Dokonaj przeciążenia operatora równości przy przeciążaniu operatorów dodawania i odejmowania](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>Zobacz także

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Operatory równości](/dotnet/standard/design-guidelines/equality-operators)