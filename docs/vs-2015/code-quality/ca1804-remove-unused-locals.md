---
title: 'CA1804: Usuń nieużywane elementy lokalne | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4bd57d76acd0c46e39bb2c01449146715abc0666
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543887"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: Usuwaj nieużywane zmienne lokalne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|Kategoria|Microsoft. Performance|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Metoda deklaruje zmienną lokalną, ale nie używa zmiennej, z wyjątkiem ewentualnej odbiorcy instrukcji przypisania. Do analizy według tej reguły testowany zestaw musi być skompilowany przy użyciu informacji debugowania, a plik bazy danych programu (. pdb) musi być dostępny.

## <a name="rule-description"></a>Opis reguły
 Nieużywane zmienne lokalne i niepotrzebne przydziały zwiększają rozmiar zestawu i zmniejszają wydajność.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy usunąć lub użyć zmiennej lokalnej. Należy zauważyć, że kompilator języka C#, który jest dołączony do [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] usuwania nieużywanych zmiennych lokalnych, gdy `optimize` opcja jest włączona.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń ostrzeżenie z tej reguły, jeśli zmienna była emitowana przez kompilator. Można również bezpiecznie pominąć ostrzeżenie z tej reguły lub wyłączyć regułę, jeśli obsługa wydajności i kodu nie są zasadniczymi problemami.

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono kilka nieużywanych zmiennych lokalnych.

 [!code-csharp[FxCop.Performance.UnusedLocals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/cs/FxCop.Performance.UnusedLocals.cs#1)]
 [!code-vb[FxCop.Performance.UnusedLocals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnusedLocals/vb/FxCop.Performance.UnusedLocals.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1809: Unikaj zbyt wielu zmiennych lokalnych](../code-quality/ca1809-avoid-excessive-locals.md)

 [CA1811: Unikaj niewywołanego kodu prywatnego](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Unikaj klas wewnętrznych bez wystąpień](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Dokonaj przeglądu nieużywanych parametrów](../code-quality/ca1801-review-unused-parameters.md)
