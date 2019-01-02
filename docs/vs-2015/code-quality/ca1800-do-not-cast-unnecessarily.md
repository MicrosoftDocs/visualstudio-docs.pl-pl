---
title: 'CA1800: Nie Rzutuj niepotrzebnie | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 31e6d986a4c319e16592a95ef9e816d864ebb6f3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53887112"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: Nie Rzutuj niepotrzebnie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Metoda wykonuje zduplikowane rzutowania na jednym z jego argumentów ani zmiennych lokalnych. Zakończenie analizy przez tę regułę przetestowane zestawu muszą zostać skompilowane przy użyciu informacji o debugowaniu i plik bazy danych (PDB) programu skojarzone muszą być dostępne.

## <a name="rule-description"></a>Opis reguły
 Zduplikowane rzutowania zmniejszają wydajność, zwłaszcza gdy rzutowania są wykonywane w niedużej iteracji. W przypadku jawnego rzutowania zduplikowanych operacji przechować wynik rzutowania w zmiennej lokalnej, a następnie użyć zmiennej lokalnej zamiast operacji zduplikowane rzutowania.

 Jeśli C# `is` operator jest używany do sprawdzenia, czy rzutowanie zostanie wykonane pomyślnie, przed wykonaniem rzeczywiste rzutowania należy wziąć pod uwagę testowanie oddziaływania `as` operator zamiast tego. Dzięki temu te same funkcje bez operacji niejawne rzutowanie, która jest wykonywana przez `is` operatora.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zmodyfikować implementacji metody, aby zminimalizować liczbę operacji rzutowania.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne, ostrzeżenia od tej reguły lub całkowicie, ignorowanie reguły, jeśli wydajność nie ma znaczenia.

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano metodę, która narusza regułę przy użyciu języka C# `is` operatora. Druga metoda spełnia reguły, zastępując `is` operatora z testem względem wynik `as` operatora, co zmniejsza liczbę operacji rzutowania na iterację od dwóch do jednego.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCastsAsIs/cs/FxCop.Performance.UnnecessaryCastsAsIs.cs#1)]

## <a name="example"></a>Przykład
 W poniższym przykładzie pokazano metodę `start_Click`, ma wiele zduplikowanych ma jawnych rzutowań, który narusza regułę, a metoda `reset_Click`, spełniającego reguły, przechowując rzutowanie w zmiennej lokalnej.

 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/cs/FxCop.Performance.UnnecessaryCasts.cs#1)]
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/vb/FxCop.Performance.UnnecessaryCasts.vb#1)]

## <a name="see-also"></a>Zobacz też
 [jako](http://msdn.microsoft.com/library/a9be126b-cbf4-4990-a70d-d0e1983cad0e) [jest](http://msdn.microsoft.com/library/bc62316a-d41f-4f90-8300-c6f4f0556e43)
