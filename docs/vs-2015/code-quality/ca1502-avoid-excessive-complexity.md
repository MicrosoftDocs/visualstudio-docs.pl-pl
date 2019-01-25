---
title: 'CA1502: Unikaj nadmiernej złożoności | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveComplexity
- CA1502
helpviewer_keywords:
- CA1502
- AvoidExcessiveComplexity
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e1885a07f4c9edbbdea9be4f0e74aaf8e4d3a6f9
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834564"
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502: Unikaj nadmiernej złożoności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidExcessiveComplexity|
|CheckId|CA1502|
|Kategoria|Microsoft.Maintainability|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Metoda ma złożoność cyklomatyczną nadmierne.

## <a name="rule-description"></a>Opis reguły
 *Złożoność Cyklomatyczna* mierzy liczbę liniowo niezależnych ścieżek za pośrednictwem metody, która jest określana przez liczbę i złożoność rozgałęzień warunkowych. Złożoność cyklomatyczna niski na ogół wskazuje metodę, która jest łatwy do zrozumienia, testowania i obsługi. Złożoność cyklomatyczna jest obliczana na podstawie grafu przepływu sterowania, metody i znajduje się w następujący sposób:

 złożoność cyklomatyczna = liczba krawędzi — liczba węzłów + 1

 gdy węzeł reprezentuje Rozgałęzienie logiki i krawędź reprezentuje linię między węzłami.

 Reguły raporty naruszenie zasad, gdy złożoność cyklomatyczna jest więcej niż 25.

 Dowiedz się więcej na temat metryk kodu [mierzenie złożoności i łatwości konserwacji zarządzanego kodu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md),

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Refaktoryzuj metody do jego złożoność cykliczną.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły, jeśli nie łatwo można zmniejszyć złożoność i metoda jest łatwy do zrozumienia, testowania i obsługi. W szczególności metoda, która zawiera dużą `switch` (`Select` w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) instrukcja jest kandydatem do wykluczenia. Ryzyko destabilizing kod podstawowy zaległości w cyklu rozwoju lub wprowadzenia nieoczekiwanej zmianie w zachowania w czasie wykonywania w kodzie uprzednio wysłane może przeważyć zalety łatwości utrzymania refaktoryzacji kodu.

## <a name="how-cyclomatic-complexity-is-calculated"></a>Jak obliczana jest złożoność Cyklomatyczna
 Złożoność cyklomatyczna jest obliczany przez dodanie 1 do następujących:

- Liczba gałęzi (takich jak `if`, `while`, i `do`)

- Liczba `case` instrukcje w `switch`

  Poniższe przykłady przedstawiają metody, które mają różnej złożoności cyklomatycznej.

## <a name="example"></a>Przykład
 **Złożoność Cyklomatyczna 1**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#1)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#1)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#1)]

## <a name="example"></a>Przykład
 **Złożoność Cyklomatyczna 2**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#2)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#2)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#2)]

## <a name="example"></a>Przykład
 **Złożoność Cyklomatyczna 3**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#3)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#3)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#3)]

## <a name="example"></a>Przykład
 **Złożoność Cyklomatyczna 8**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#4)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#4)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#4)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1501: Unikaj nadmiernego dziedziczenia](../code-quality/ca1501-avoid-excessive-inheritance.md)

## <a name="see-also"></a>Zobacz też
 [Mierzenie złożoności i poziomu łatwości konserwacji kodu zarządzanego](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
