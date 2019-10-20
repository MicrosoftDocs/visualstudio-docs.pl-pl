---
title: 'CA1046: nie przeciążać operatora równości w typach referencyjnych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 519faf2d49cb74d60d342d6bcf449f211076b0b4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661087"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: Nie przeciążaj operatora equals w typach referencyjnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|
|CheckId|CA1046|
|Kategoria|Microsoft. Design|
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

 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefTypesNoEqualityOp/cs/FxCop.Design.RefTypesNoEqualityOp.cs#1)]

## <a name="example"></a>Przykład
 Poniższa aplikacja porównuje niektóre odwołania.

 [!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefTypesNoEqualityOp/cs/FxCop.Design.TestRefTypesNoEqualityOp.cs#1)]

 Ten przykład generuje następujące dane wyjściowe.

 **a = New (2, 2) i b = New (2, 2) są równe? Nie** 
**c i a są równe? Tak** 
**b i a są = =? Nie** 
**c i a są = =? Tak**
## <a name="related-rules"></a>Powiązane reguły
 [CA1013: Dokonaj przeciążenia operatora równości przy przeciążaniu operatorów dodawania i odejmowania](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>Zobacz też
 [Operatory równości](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a) <xref:System.Object.Equals%2A?displayProperty=fullName>
