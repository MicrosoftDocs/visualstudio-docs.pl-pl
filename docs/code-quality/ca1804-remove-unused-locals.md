---
title: 'CA1804: Usuń nieużywane zmienne lokalne'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 47578cc281334da7eeebeea6eaa5ef0c1c021c8f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53819864"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: Usuń nieużywane zmienne lokalne

|||
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Metoda deklaruje zmienną lokalną, ale nie używa prawdopodobnie zmiennej, z wyjątkiem jako adresata w instrukcji przypisania. Do analizy przez tę regułę przetestowane zestawu muszą zostać skompilowane przy użyciu informacji o debugowaniu i plik bazy danych (PDB) programu skojarzone muszą być dostępne.

## <a name="rule-description"></a>Opis reguły
 Nieużywane zmienne lokalne i niepotrzebne przydziały zwiększają rozmiar zestawu i zmniejszają wydajność.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, usuń lub użyć zmiennej lokalnej. Należy pamiętać, że kompilator języka C#, dołączone [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] Usuwa nieużywane zmienne lokalne podczas `optimize` opcja jest włączona.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomijaj ostrzeżeń dla tej reguły, jeśli zmienna kompilatora emitowane. Bezpieczne jest również Pomijaj ostrzeżeń dla tej reguły lub wyłączyć regułę, jeśli wydajność i konserwacja kodu nie są podstawowe kwestie.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje nieużywane zmienne lokalne.

 [!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
 [!code-csharp[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1809: Unikaj zbyt wielu zmiennych lokalnych](../code-quality/ca1809-avoid-excessive-locals.md)

 [CA1811: Unikaj niewywołanego kodu prywatnego](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Unikaj klas wewnętrznych bez wystąpień](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Przejrzyj nieużywane parametry](../code-quality/ca1801-review-unused-parameters.md)