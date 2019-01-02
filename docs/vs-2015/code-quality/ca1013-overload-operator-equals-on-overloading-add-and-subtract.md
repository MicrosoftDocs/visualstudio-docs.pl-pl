---
title: 'CA1013: Dokonaj przeciążenia operatora równości przy przeciążaniu operatorów dodawania i odejmowania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9958a853c6b463283d9e917256613ce7b58b6f95
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53948923"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: Dokonaj przeciążenia operatora równości przy przeciążaniu operatorów dodawania i odejmowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony implementuje operatory dodawania lub odejmowania bez implementowania operatora porównania.

## <a name="rule-description"></a>Opis reguły
 W przypadku wystąpień typu mogą być połączone za pomocą operacji, takich jak dodawanie i odejmowanie, prawie zawsze należy zdefiniować równości, aby zwrócić `true` dla dwóch wystąpień, które mają takie same wartości składowych.

 Nie można używać operatora równości Domyślna implementacja Przeciążony operator równości. Ten sposób spowoduje przepełnienie stosu. Aby zaimplementować operator równości, użyj metody metody Object.Equals w danej implementacji. Zobacz poniższy przykład.

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
 Aby naprawić naruszenie tej zasady, implementuje operator równości, aby były ze sobą matematycznie zgodne z operatorów dodawania i odejmowania.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, gdy domyślna implementacja operatora równości udostępnia poprawne zachowanie dla typu.

## <a name="example"></a>Przykład
 W poniższym przykładzie zdefiniowano typ (`BadAddableType`) który narusza tę regułę. Ten typ należy zaimplementować operator równości, który ma być sprawia, że dwa wystąpienia, mających takie same wartości pola, testowanie `true` pod kątem równości. Typ `GoodAddableType` przedstawia implementację poprawiony. Zwróć uwagę, że ten typ także implementuje operator nierówności i zastępuje <xref:System.Object.Equals%2A> spełniać inne zasady. Pełne wdrożenie będzie także implementować <xref:System.Object.GetHashCode%2A>.

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AddAndSubtract/cs/FxCop.Design.AddAndSubtract.cs#1)]

## <a name="example"></a>Przykład
 Poniższy przykład sprawdza pod kątem równości, za pomocą wystąpień typów, które zostały wcześniej zdefiniowane w tym temacie, aby zilustrować domyślne i poprawnego zachowania dla operatora równości.

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestAddAndSubtract/cs/FxCop.Design.TestAddAndSubtract.cs#1)]

 Ten przykład generuje następujące dane wyjściowe.

 **Zły typ: {2,2} {2,2} są takie same? Nie**
**dobre typu: {3,3} {3,3} są takie same? Tak**
**dobre typu: {3,3} {3,3} są ==?   Tak**
**zły typ: {2,2} {9,9} są takie same? Nie**
**dobre typu: {3,3} {9,9} są ==?   Brak**
## <a name="see-also"></a>Zobacz też
 [Operatory równości](http://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
