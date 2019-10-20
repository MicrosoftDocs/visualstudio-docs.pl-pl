---
title: 'CA2230: Użyj parametrów dla argumentów zmiennych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a690544a7ed03094587a2aaf1c44b7ed68e8f2a9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662830"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: Użyj parametrów dla zmiennych argumentów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony zawiera metodę publiczną lub chronioną, która używa konwencji wywoływania `VarArgs`.

## <a name="rule-description"></a>Opis reguły
 Konwencja wywoływania `VarArgs` jest używana z niektórymi definicjami metod, które pobierają zmienną liczbę parametrów. Metoda korzystająca z konwencji wywoływania `VarArgs` Common Language Specification nie jest zgodna ze specyfikacją CLS i może nie być dostępna w różnych językach programowania.

 W C#programie konwencja wywoływania `VarArgs` jest używana, gdy lista parametrów metody zostanie zakończona słowem kluczowym `__arglist`. Visual Basic nie obsługuje konwencji wywoływania `VarArgs`, a Wizualizacja C++ pozwala jej używać tylko w niezarządzanym kodzie, który używa notacji wielokropka `...`.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły w programie C#, należy użyć słowa kluczowego [params](https://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012) zamiast `__arglist`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia dwie metody, jeden, który narusza regułę i jeden, który spełnia regułę.

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.Reflection.CallingConventions?displayProperty=fullName> [niezależność od języka i składniki niezależne od języka](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
