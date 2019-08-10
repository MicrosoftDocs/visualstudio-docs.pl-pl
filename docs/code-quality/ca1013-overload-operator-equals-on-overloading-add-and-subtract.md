---
title: 'CA1013: Przeciążaj operator równości w przypadku przeciążania operatorów dodawania i odejmowania'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
helpviewer_keywords:
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8c82e7303ea4016974be04c3d8745cb2011017f0
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923159"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: Przeciążaj operator równości w przypadku przeciążania operatorów dodawania i odejmowania

|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Typ publiczny lub chroniony implementuje operatory dodawania lub odejmowania bez implementowania operatora porównania.

## <a name="rule-description"></a>Opis reguły
Gdy wystąpienia typu można łączyć za pomocą operacji, takich jak dodawanie i odejmowanie, należy prawie zawsze definiować równość `true` dla wszystkich dwóch wystąpień, które mają te same wartości elementów.

Nie można użyć domyślnego operatora równości w przeciążonej implementacji operatora równości. Wykonanie tej operacji spowoduje przepełnienie stosu. Aby zaimplementować operator równości, użyj metody Object. Equals w implementacji. Zobacz Poniższy przykład.

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, należy zaimplementować operator równości, tak aby był matematycznie spójny z operatorami dodawania i odejmowania.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Jeśli domyślna implementacja operatora równości zapewnia poprawne zachowanie dla tego typu, można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="example"></a>Przykład
W poniższym przykładzie zdefiniowano typ (`BadAddableType`), który narusza tę regułę. Ten typ powinien implementować operator równości, aby wszystkie dwa wystąpienia, które mają te same wartości pól `true` , były sprawdzane pod kątem równości. Typ `GoodAddableType` pokazuje poprawioną implementację. Należy zauważyć, że ten typ powoduje także implementację operatora nierówności <xref:System.Object.Equals%2A> i zastąpień w celu spełnienia innych reguł. Zaimplementowana <xref:System.Object.GetHashCode%2A>zostanie również kompletna implementacja.

[!code-csharp[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]

## <a name="example"></a>Przykład
Poniższy przykład sprawdza, czy są używane wystąpienia typów, które wcześniej zostały zdefiniowane w tym temacie, aby zilustrować domyślne i prawidłowe zachowanie operatora równości.

[!code-csharp[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]

Ten przykład generuje następujące wyniki:

```txt
Bad type:  {2,2} {2,2} are equal? No
Good type: {3,3} {3,3} are equal? Yes
Good type: {3,3} {3,3} are == ?   Yes
Bad type:  {2,2} {9,9} are equal? No
Good type: {3,3} {9,9} are == ?   No
```

## <a name="see-also"></a>Zobacz także

- [Operatory równości](/dotnet/standard/design-guidelines/equality-operators)