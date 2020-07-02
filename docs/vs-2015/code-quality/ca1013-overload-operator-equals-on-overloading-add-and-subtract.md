---
title: 'CA1013: Operator przeciążenia jest równy na przeciążeniu Dodaj i Odejmij | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
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
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2304b78073b806dfc4aec9686f061d946b379ded
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545421"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: Przeciążaj operator równości w przypadku przeciążania operatorów dodawania i odejmowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony implementuje operatory dodawania lub odejmowania bez implementowania operatora porównania.

## <a name="rule-description"></a>Opis reguły
 Gdy wystąpienia typu można łączyć za pomocą operacji, takich jak dodawanie i odejmowanie, należy prawie zawsze definiować równość `true` dla wszystkich dwóch wystąpień, które mają te same wartości elementów.

 Nie można użyć domyślnego operatora równości w przeciążonej implementacji operatora równości. Wykonanie tej operacji spowoduje przepełnienie stosu. Aby zaimplementować operator równości, użyj metody Object. Equals w implementacji. Zobacz poniższy przykład.

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
 W poniższym przykładzie zdefiniowano typ ( `BadAddableType` ), który narusza tę regułę. Ten typ powinien implementować operator równości, aby wszystkie dwa wystąpienia, które mają te same wartości pól, były sprawdzane pod `true` kątem równości. Typ `GoodAddableType` pokazuje poprawioną implementację. Należy zauważyć, że ten typ powoduje także implementację operatora nierówności i zastąpień <xref:System.Object.Equals%2A> w celu spełnienia innych reguł. Zaimplementowana zostanie również kompletna implementacja <xref:System.Object.GetHashCode%2A> .

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AddAndSubtract/cs/FxCop.Design.AddAndSubtract.cs#1)]

## <a name="example"></a>Przykład
 Poniższy przykład sprawdza, czy są używane wystąpienia typów, które wcześniej zostały zdefiniowane w tym temacie, aby zilustrować domyślne i prawidłowe zachowanie operatora równości.

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestAddAndSubtract/cs/FxCop.Design.TestAddAndSubtract.cs#1)]

 Ten przykład generuje następujące dane wyjściowe.

 **Zły typ: {2,2} {2,2} są równe? Brak** 
 **dobrego typu: {3,3} {3,3} są równe? Tak** 
 **dobry typ: {3,3} {3,3} czy = =?   Tak** 
 **zły typ: {2,2} {9,9} jest równe? Brak** 
 **dobrego typu: {3,3} {9,9} czy =?   Nie**
## <a name="see-also"></a>Zobacz też
 [Operatory równości](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
