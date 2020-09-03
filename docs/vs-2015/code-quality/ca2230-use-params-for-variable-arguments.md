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
ms.openlocfilehash: ce66e04272618b9df2ab1957af305bb9bf40ee9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540364"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: Użyj elementu params dla argumentów zmiennych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|UseParamsForVariableArguments|
|CheckId|CA2230|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ publiczny lub chroniony zawiera metodę publiczną lub chronioną, która używa `VarArgs` konwencji wywoływania.

## <a name="rule-description"></a>Opis reguły
 `VarArgs`Konwencja wywoływania jest używana z niektórymi definicjami metod, które pobierają zmienną liczbę parametrów. Metoda korzystająca z `VarArgs` konwencji wywoływania nie jest zgodna z Common Language Specification (CLS) i może nie być dostępna w różnych językach programowania.

 W języku C# `VarArgs` konwencja wywoływania jest używana, gdy lista parametrów metody zostanie zakończona `__arglist` słowem kluczowym. Visual Basic nie obsługuje `VarArgs` konwencji wywoływania, a Visual C++ zezwala na używanie jej tylko w niezarządzanym kodzie, który używa `...` notacji wielokropka.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły w języku C#, użyj słowa kluczowego [params](https://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012) zamiast `__arglist` .

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia dwie metody, jeden, który narusza regułę i jeden, który spełnia regułę.

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.Reflection.CallingConventions?displayProperty=fullName>[Niezależność od języka i składniki niezależne od języka](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
