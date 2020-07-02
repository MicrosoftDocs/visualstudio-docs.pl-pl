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
ms.openlocfilehash: 757d66ef719b3a1f39a9164dfd50ce1fcf8799db
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547800"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: Nie rzutuj niepotrzebnie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Kategoria|Microsoft. Performance|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Metoda wykonuje duplikaty rzutowania dla jednego z jego argumentów lub zmiennych lokalnych. Aby przeprowadzić pełną analizę według tej reguły, testowany zestaw musi być skompilowany przy użyciu informacji debugowania, a wymagany plik bazy danych programu (. pdb) musi być dostępny.

## <a name="rule-description"></a>Opis reguły
 Zduplikowane rzutowania zmniejszają wydajność, zwłaszcza gdy rzutowania są wykonywane w niedużej iteracji. W przypadku jawnych zduplikowanych operacji rzutowania Zapisz wynik rzutowania w zmiennej lokalnej i Użyj zmiennej lokalnej zamiast zduplikowanych operacji rzutowania.

 Jeśli operator języka C# `is` jest używany do sprawdzania, czy rzutowanie zakończy się powodzeniem przed wykonaniem rzeczywistego rzutowania, rozważ przetestowanie wyniku `as` operatora. Zapewnia to te same funkcje bez niejawnej operacji rzutowania wykonywanej przez `is` operatora.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, zmodyfikuj implementację metody w celu zminimalizowania liczby operacji rzutowania.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Istnieje możliwość bezpiecznego pomijania ostrzeżenia z tej reguły lub w celu zignorowania jej w całości, jeśli wydajność nie jest istotna.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia metodę, która narusza regułę przy użyciu operatora języka C# `is` . Druga metoda spełnia regułę przez zamianę `is` operatora z testem na wynik `as` operatora, co zmniejsza liczbę operacji rzutowania na iterację z dwóch do jednego.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCastsAsIs/cs/FxCop.Performance.UnnecessaryCastsAsIs.cs#1)]

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia metodę, `start_Click` , która ma wiele duplikatów jawnych, które naruszają regułę i metodę, `reset_Click` , która spełnia reguły przez przechowywanie rzutowania w zmiennej lokalnej.

 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/cs/FxCop.Performance.UnnecessaryCasts.cs#1)]
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/vb/FxCop.Performance.UnnecessaryCasts.vb#1)]

## <a name="see-also"></a>Zobacz też
 [zgodnie z oczekiwaniami](https://msdn.microsoft.com/library/a9be126b-cbf4-4990-a70d-d0e1983cad0e) [is](https://msdn.microsoft.com/library/bc62316a-d41f-4f90-8300-c6f4f0556e43)
