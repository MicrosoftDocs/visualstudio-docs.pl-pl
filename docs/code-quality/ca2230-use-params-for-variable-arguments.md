---
title: 'CA2230: Użyj elementu params dla argumentów zmiennych'
ms.date: 11/04/2016
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
ms.openlocfilehash: 505aa8cdc1371a3bc288772d77b49eb7a50e9830
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920145"
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
Konwencja `VarArgs` wywoływania jest używana z niektórymi definicjami metod, które pobierają zmienną liczbę parametrów. Metoda korzystająca `VarArgs` z konwencji wywoływania nie jest zgodna z Common Language Specification (CLS) i może nie być dostępna w różnych językach programowania.

W C#programie Konwencja `VarArgs` wywoływania jest używana, gdy `__arglist` lista parametrów metody zostanie zakończona słowem kluczowym. Visual Basic nie obsługuje `VarArgs` konwencji wywoływania, a Wizualizacja C++ pozwala jej używać tylko w niezarządzanym kodzie, który używa `...` notacji z elipsą.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły w programie C#, należy użyć `__arglist`słowa kluczowego [params](/dotnet/csharp/language-reference/keywords/params) zamiast.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
Poniższy przykład przedstawia dwie metody, jeden, który narusza regułę i jeden, który spełnia regułę.

[!code-csharp[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection.CallingConventions?displayProperty=fullName>
- [Niezależność od języka i składniki niezależne od języka](/dotnet/standard/language-independence-and-language-independent-components)