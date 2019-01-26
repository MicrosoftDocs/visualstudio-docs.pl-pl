---
title: 'CA2230: Użyj elementu params dla argumentów zmiennych'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: db6c66e65ed89e53d0cbbed671004c88bdbaed95
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54982978"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: Użyj elementu params dla argumentów zmiennych

|||
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony zawiera metodę publiczną lub chronioną, która używa `VarArgs` konwencji wywoływania.

## <a name="rule-description"></a>Opis reguły
 `VarArgs` Konwencja wywołania jest używana z niektórych definicji metod, które przyjmują zmienną liczbę parametrów. Za pomocą metody `VarArgs` konwencji wywoływania nie jest Common Language Specification (CLS) zgodne i nie mogą być niedostępne w językach programowania.

 W języku C# `VarArgs` konwencja wywołania jest używany po liście parametrów metody kończy się `__arglist` — słowo kluczowe. Język Visual Basic nie obsługuje `VarArgs` wywoływania Konwencji i Visual C++ umożliwia jego użycia tylko w kod niezarządzany, który używa elipsy `...` notacji.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady w języku C#, należy użyć [params](/dotnet/csharp/language-reference/keywords/params) słowa kluczowego zamiast `__arglist`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy kod przedstawia dwie metody, taki, który narusza regułę i taki, który spełnia reguły.

 [!code-csharp[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection.CallingConventions?displayProperty=fullName>
- [Niezależność od języka i składniki niezależne od języka](/dotnet/standard/language-independence-and-language-independent-components)