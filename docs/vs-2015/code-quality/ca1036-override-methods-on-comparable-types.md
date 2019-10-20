---
title: 'CA1036: Zastąp metody na porównywalnych typach | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 779e6258f9c5be256a7973a5d917045507fc82e6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661830"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Przesłaniaj metody na typach porównywalnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony implementuje interfejs <xref:System.IComparable?displayProperty=fullName> i nie przesłania <xref:System.Object.Equals%2A?displayProperty=fullName> lub nie przeciąża operatora specyficznego dla języka pod kątem równości, nierówności, mniejszej niż lub większej niż. Zasada nie zgłasza naruszenia, jeśli typ dziedziczy tylko implementację interfejsu.

## <a name="rule-description"></a>Opis reguły
 Typy, które definiują niestandardowy porządek sortowania, implementują interfejs <xref:System.IComparable>. Metoda <xref:System.IComparable.CompareTo%2A> zwraca liczbę całkowitą, która wskazuje poprawną kolejność sortowania dla dwóch wystąpień tego typu. Ta zasada identyfikuje typy, które ustawiają kolejność sortowania; oznacza to, że zwykłe znaczenie, nierówność, mniejsze niż i większe niż nie ma zastosowania. Po wprowadzeniu implementacji <xref:System.IComparable>, należy również przesłonić <xref:System.Object.Equals%2A> tak, aby zwracały wartości spójne z <xref:System.IComparable.CompareTo%2A>. W przypadku zastąpienia <xref:System.Object.Equals%2A> i kodowania w języku, który obsługuje przeciążenia operatorów, należy również dostarczyć operatory spójne z <xref:System.Object.Equals%2A>.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Przesłoń <xref:System.Object.Equals%2A>. Jeśli język programowania obsługuje przeciążanie operatora, należy podać następujące operatory:

- op_Equality

- op_Inequality

- op_LessThan

- op_GreaterThan

  W C#programie tokeny używane do reprezentowania tych operatorów są następujące: = =,! =, \< i >.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można bezpiecznie pominąć ostrzeżenie z tej reguły, gdy naruszenie jest spowodowane przez brakujące operatory, a język programowania nie obsługuje przeciążania operatora, tak jak w przypadku Visual Basic .NET. Jest również bezpieczne, aby pominąć ostrzeżenie dla tej reguły, gdy zostanie ona wykorzystana przez operatory równości inne niż op_Equality, jeśli określisz, że implementacja operatorów nie ma sensu w kontekście aplikacji. Należy jednak zawsze przekraczać op_Equality i operator = =, jeśli przesłonisz obiekt. Equals.

## <a name="example"></a>Przykład
 Poniższy przykład zawiera typ, który poprawnie implementuje <xref:System.IComparable>. Komentarze do kodu identyfikują metody, które spełniają różne reguły, które są powiązane z <xref:System.Object.Equals%2A>m i <xref:System.IComparable> interfejsem.

 [!code-csharp[FxCop.Design.IComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IComparable/cs/FxCop.Design.IComparable.cs#1)]

## <a name="example"></a>Przykład
 Następująca aplikacja testuje zachowanie implementacji <xref:System.IComparable>, która została pokazana wcześniej.

 [!code-csharp[FxCop.Design.TestIComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestIComparable/cs/FxCop.Design.TestIComparable.cs#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.IComparable?displayProperty=fullName><xref:System.Object.Equals%2A?displayProperty=fullName>
 [Operatory równości](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
