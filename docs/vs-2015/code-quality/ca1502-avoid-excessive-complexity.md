---
title: 'CA1502: Unikaj nadmiernej złożoności | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5da2e2bf26bb1894987caa8b748181d952bd7c18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547839"
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502: Unikaj nadmiernej złożoności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|AvoidExcessiveComplexity|
|CheckId|CA1502|
|Kategoria|Microsoft. łatwość obsługi|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Metoda ma nadmierną Złożoność cyklomatyczna.

## <a name="rule-description"></a>Opis reguły
 *Złożoność cyklomatyczna* mierzy liczbę liniowo niezależnych ścieżek za pomocą metody, która jest określana przez liczbę i złożoność gałęzi warunkowych. Niska Złożoność cyklomatyczna zazwyczaj wskazuje metodę, która jest łatwa do zrozumienia, testowania i konserwowania. Złożoność cyklomatyczna jest obliczana na podstawie grafu przepływu sterowania metody i jest podawana w następujący sposób:

 Złożoność cyklomatyczna = liczba krawędzi — liczba węzłów + 1

 gdzie węzeł reprezentuje punkt rozgałęzienia logiki, a krawędź reprezentuje linię między węzłami.

 Reguła zgłasza naruszenie, gdy Złożoność cyklomatyczna jest większa niż 25.

 Możesz dowiedzieć się więcej o metrykach kodu podczas [mierzenia złożoności i utrzymania kodu zarządzanego](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md),

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy rozwiązać metodę, aby zmniejszyć jej złożoność cyklomatyczna.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jeśli złożoność nie zostanie łatwo zredukowana, można bezpiecznie pominąć ostrzeżenie z tej reguły, a metoda jest łatwa do zrozumienia, testowania i konserwowania. W szczególności Metoda, która zawiera duże `switch` ( `Select` w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) instrukcji, jest kandydatem do wykluczenia. Ryzyko destabilizacji podstawy kodu w cyklu programowania lub wprowadzenie nieoczekiwanej zmiany zachowania w czasie wykonywania w wcześniej dostarczonym kodzie może wzważyć korzyści płynące z refaktoryzacji kodu.

## <a name="how-cyclomatic-complexity-is-calculated"></a>Jak jest obliczana Złożoność cyklomatyczna
 Złożoność cyklomatyczna jest obliczana przez dodanie 1 do następujących:

- Liczba gałęzi (takich jak `if` , `while` i `do` )

- Liczba `case` instrukcji w `switch`

  W poniższych przykładach przedstawiono metody, które mają różne złożone cyklomatyczna.

## <a name="example"></a>Przykład
 **Złożoność cyklomatyczna 1**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#1)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#1)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#1)]

## <a name="example"></a>Przykład
 **Złożoność cyklomatyczna 2**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#2)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#2)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#2)]

## <a name="example"></a>Przykład
 **Złożoność cyklomatyczna 3**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#3)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#3)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#3)]

## <a name="example"></a>Przykład
 **Złożoność cyklomatyczna 8**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#4)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#4)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#4)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1501: Unikaj nadmiernego dziedziczenia](../code-quality/ca1501-avoid-excessive-inheritance.md)

## <a name="see-also"></a>Zobacz też
 [Mierzenie złożoności i łatwości konserwacji zarządzanego kodu](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
