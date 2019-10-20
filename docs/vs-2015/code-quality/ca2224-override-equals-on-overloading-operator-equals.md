---
title: 'CA2224: Zastąp wartość Equals w przypadku przeciążania operatora Equals | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d35052bb2a1efb1a466ffc67c95c83e5b3a76533
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671875"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: Przesłoń metodę equals, przeciążając operator equals
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Typ publiczny implementuje operator równości, ale nie przesłania <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Opis reguły
 Operator równości jest przeznaczony do składniowo wygodny sposób uzyskiwania dostępu do funkcjonalności metody <xref:System.Object.Equals%2A>. W przypadku zaimplementowania operatora równości jego logika musi być taka sama jak wartość <xref:System.Object.Equals%2A>.

 C# Kompilator generuje ostrzeżenie, jeśli kod narusza tę regułę.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy usunąć implementację operatora równości lub przesłonić <xref:System.Object.Equals%2A> i mieć dwie metody zwracają te same wartości. Jeśli operator równości nie wprowadza niespójnych zachowań, można naprawić naruszenie, dostarczając implementację <xref:System.Object.Equals%2A>, która wywołuje metodę <xref:System.Object.Equals%2A> w klasie bazowej.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli operator równości zwraca tę samą wartość, co dziedziczona implementacja <xref:System.Object.Equals%2A>, bezpiecznie jest pomijać ostrzeżenie z tej reguły. Przykładowa sekcja zawiera typ, który może bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="examples-of-inconsistent-equality-definitions"></a>Przykłady niespójnych definicji równości

### <a name="description"></a>Opis
 W poniższym przykładzie przedstawiono typ z niespójnymi definicjami równości. `BadPoint` zmienia znaczenie, dostarczając niestandardową implementację operatora równości, ale nie przesłania <xref:System.Object.Equals%2A> tak, aby zachowywały się identycznie.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorEqualsRequiresEquals/cs/FxCop.Usage.OperatorEqualsRequiresEquals.cs#1)]

## <a name="example"></a>Przykład
 Poniższy kod testuje zachowanie `BadPoint`.

 [!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestOperatorEqualsRequiresEquals/cs/FxCop.Usage.TestOperatorEqualsRequiresEquals.cs#1)]

 Ten przykład generuje następujące dane wyjściowe.

 **a = ([0] 1, 1) i b = ([1] 2, 2) są równe? Nie** 
**a = = b? Nie** 
**a1 i a są równe? Tak** 
**a1 = = a? Tak** 
**b i bCopy są równe? Nie** 
**b = = bCopy? Tak**
## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który technicznie narusza tę regułę, ale nie działa w sposób niespójny.

 [!code-csharp[FxCop.Usage.ValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ValueTypeEquals/cs/FxCop.Usage.ValueTypeEquals.cs#1)]

## <a name="example"></a>Przykład
 Poniższy kod testuje zachowanie `GoodPoint`.

 [!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestValueTypeEquals/cs/FxCop.Usage.TestValueTypeEquals.cs#1)]

 Ten przykład generuje następujące dane wyjściowe.

 **a = (1, 1) i b = (2, 2) są równe? Nie** 
**a = = b? Nie** 
**a1 i a są równe? Tak** 
**a1 = = a? Tak** 
**b i bCopy są równe? Tak** 
**b = = bCopy? Tak**
## <a name="class-example"></a>Przykład klasy

### <a name="description"></a>Opis
 Poniższy przykład pokazuje klasę (typ referencyjny), która narusza tę regułę.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassViolation/cs/FxCop.Usage.OverrideEqualsClassViolation.cs#1)]

## <a name="example"></a>Przykład
 Poniższy przykład naprawia naruszenie, zastępując <xref:System.Object.Equals%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassFixed/cs/FxCop.Usage.OverrideEqualsClassFixed.cs#1)]

## <a name="structure-example"></a>Przykład struktury

### <a name="description"></a>Opis
 Poniższy przykład pokazuje strukturę (typ wartości), która narusza tę regułę.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructViolation/cs/FxCop.Usage.OverrideEqualsStructViolation.cs#1)]

## <a name="example"></a>Przykład
 Poniższy przykład naprawia naruszenie, zastępując <xref:System.ValueType.Equals%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructFixed/cs/FxCop.Usage.OverrideEqualsStructFixed.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1046: Nie przeciążaj operatora równości w typach referencyjnych](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Przeciążenia operatora mają nazwane alternatywy](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: Operatory powinny mieć symetryczne przeciążenia](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2218: Przesłoń metodę GetHashCode przy przesłanianiu metody Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
