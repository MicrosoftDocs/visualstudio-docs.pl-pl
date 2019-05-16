---
title: 'CA2230: Użyj parametrów dla argumentów zmiennych | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8b833f520c574c32f90ff1ec5e20a9671184b78a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685102"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: Użyj elementu params dla argumentów zmiennych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 Aby naprawić naruszenie tej zasady w języku C#, należy użyć [params](https://msdn.microsoft.com/library/1690815e-b52b-4967-8380-5780aff08012) słowa kluczowego zamiast `__arglist`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 Poniższy kod przedstawia dwie metody, taki, który narusza regułę i taki, który spełnia reguły.

 [!code-csharp[FxCop.Usage.UseParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.UseParams/cs/FxCop.Usage.UseParams.cs#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.Reflection.CallingConventions?displayProperty=fullName> [Niezależność od języka i składniki niezależne od języka](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
