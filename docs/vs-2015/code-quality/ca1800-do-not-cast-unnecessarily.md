---
title: 'CA1800: nie należy rzutować niepotrzebnie | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 466309cef8905faa9b659e2d3652975d815767fb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663102"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: Nie przeprowadzaj niepotrzebnych operacji rzutowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Kategoria|Microsoft. Performance|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Metoda wykonuje duplikaty rzutowania dla jednego z jego argumentów lub zmiennych lokalnych. Aby przeprowadzić pełną analizę według tej reguły, testowany zestaw musi być skompilowany przy użyciu informacji debugowania, a wymagany plik bazy danych programu (. pdb) musi być dostępny.

## <a name="rule-description"></a>Opis reguły
 Zduplikowane rzutowania zmniejszają wydajność, zwłaszcza gdy rzutowania są wykonywane w niedużej iteracji. W przypadku jawnych zduplikowanych operacji rzutowania Zapisz wynik rzutowania w zmiennej lokalnej i Użyj zmiennej lokalnej zamiast zduplikowanych operacji rzutowania.

 Jeśli operator C# `is` jest używany do sprawdzania, czy rzutowanie zostanie wykonane pomyślnie przed rzeczywistym rzutem, rozważ przetestowanie wyniku dla operatora `as`. Zapewnia to te same funkcje bez niejawnej operacji rzutowania wykonywanej przez operator `is`.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, zmodyfikuj implementację metody w celu zminimalizowania liczby operacji rzutowania.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Istnieje możliwość bezpiecznego pomijania ostrzeżenia z tej reguły lub w celu zignorowania jej w całości, jeśli wydajność nie jest istotna.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia metodę, która narusza regułę przy użyciu operatora C# `is`. Druga metoda spełnia regułę przez zamianę operatora `is` na test względem wyniku dla operatora `as`, który zmniejsza liczbę operacji rzutowania na iterację z dwóch do jednego.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCastsAsIs/cs/FxCop.Performance.UnnecessaryCastsAsIs.cs#1)]

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia metodę `start_Click`, która ma wiele duplikatów jawnych, co narusza regułę i metodę `reset_Click`, która spełnia reguły przez przechowywanie rzutowania w zmiennej lokalnej.

 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/cs/FxCop.Performance.UnnecessaryCasts.cs#1)]
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/vb/FxCop.Performance.UnnecessaryCasts.vb#1)]

## <a name="see-also"></a>Zobacz też
 [zgodnie z oczekiwaniami](https://msdn.microsoft.com/library/a9be126b-cbf4-4990-a70d-d0e1983cad0e) [](https://msdn.microsoft.com/library/bc62316a-d41f-4f90-8300-c6f4f0556e43)
