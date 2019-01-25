---
title: 'CA1036: Przesłaniaj metody porównywalnych typów | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 127bb322a9dd5c841f71a5da49b0d9a6fceaf5e6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54779688"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Przesłaniaj metody porównywalnych typów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony implementuje <xref:System.IComparable?displayProperty=fullName> interfejsu i nie powoduje zastąpienia <xref:System.Object.Equals%2A?displayProperty=fullName> lub przeciążaj operator równości, nierówności, mniejsze lub większe niż specyficzny dla języka. Reguła nie raportuje naruszenie, jeśli typ dziedziczy implementacji interfejsu.

## <a name="rule-description"></a>Opis reguły
 Typy, które definiują niestandardowej kolejności sortowania implementować <xref:System.IComparable> interfejsu. <xref:System.IComparable.CompareTo%2A> Metoda zwraca wartość całkowitą, która wskazuje właściwy porządek sortowania dla dwóch wystąpień tego typu. Ta zasada Określa typy, które porządek sortowania; oznacza to, czy zwykłe znaczenia równości, nierówności, mniejsze niż i większa niż nie mają zastosowania. Gdy dostarczać implementację <xref:System.IComparable>, zazwyczaj należy także Przesłoń <xref:System.Object.Equals%2A> tak, aby zwraca wartości, które są zgodne z <xref:System.IComparable.CompareTo%2A>. Jeśli zastąpisz <xref:System.Object.Equals%2A> z kodowaniem są w języku, który obsługuje przeciążenia operatorów, należy również podać operatorów, które są zgodne z <xref:System.Object.Equals%2A>.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zastąpić <xref:System.Object.Equals%2A>. Jeśli język programowania obsługuje przeładowania operatora, należy podać następujące operatory:

- op_equality —

- op_inequality —

- op_LessThan

- op_greaterthan —

  W języku C# tokenów, które są używane do reprezentowania tych operatorów są następujące: ==,! =, \<, oraz >.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, gdy naruszenia przyczyną jest brak operatory języka programowania nie obsługuje przeładowania operatora, jak w przypadku języka Visual Basic .NET. Jest również bezpiecznie Pomijaj ostrzeżeń dla tej reguły, gdy generowane na operatory równości, inne niż op_equality — Jeśli stwierdzisz, że implementacja operatorów nie ma sensu w kontekście swojej aplikacji. Jednak należy zawsze za pośrednictwem op_equality — i == — operator w przypadku przesłania metody Object.Equals.

## <a name="example"></a>Przykład
 Poniższy przykład zawiera typ, który implementuje prawidłowo <xref:System.IComparable>. Komentarze w kodzie zidentyfikować metody, które spełniają różne reguły that are related to <xref:System.Object.Equals%2A> i <xref:System.IComparable> interfejsu.

 [!code-csharp[FxCop.Design.IComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IComparable/cs/FxCop.Design.IComparable.cs#1)]

## <a name="example"></a>Przykład
 Następująca aplikacja sprawdza zachowanie <xref:System.IComparable> implementacji, pokazaną wcześniej.

 [!code-csharp[FxCop.Design.TestIComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestIComparable/cs/FxCop.Design.TestIComparable.cs#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.IComparable?displayProperty=fullName><xref:System.Object.Equals%2A?displayProperty=fullName>
 [Operatory równości](http://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
