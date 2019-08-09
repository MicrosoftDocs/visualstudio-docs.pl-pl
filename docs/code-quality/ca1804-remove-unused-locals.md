---
title: 'CA1804: Usuwaj nieużywane zmienne lokalne'
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bd3e9c56bb02995d9b99b57bb2799ab69b51a42d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921567"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: Usuwaj nieużywane zmienne lokalne

|||
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|Kategoria|Microsoft.Performance|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Metoda deklaruje zmienną lokalną, ale nie używa zmiennej, z wyjątkiem ewentualnej odbiorcy instrukcji przypisania. Do analizy według tej reguły testowany zestaw musi być skompilowany przy użyciu informacji debugowania, a plik bazy danych programu (. pdb) musi być dostępny.

## <a name="rule-description"></a>Opis reguły
Nieużywane zmienne lokalne i niepotrzebne przydziały zwiększają rozmiar zestawu i zmniejszają wydajność.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy usunąć lub użyć zmiennej lokalnej.

> [!NOTE]
> C# Kompilator usuwa nieużywane zmienne lokalne, `optimize` gdy opcja jest włączona.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Pomiń ostrzeżenie z tej reguły, jeśli zmienna była emitowana przez kompilator. Można również bezpiecznie pominąć ostrzeżenie z tej reguły lub wyłączyć regułę, jeśli obsługa wydajności i kodu nie są zasadniczymi problemami.

## <a name="example"></a>Przykład
W poniższym przykładzie przedstawiono kilka nieużywanych zmiennych lokalnych.

[!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
[!code-csharp[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
[CA1809: Unikaj nadmiernych ustawień lokalnych](../code-quality/ca1809-avoid-excessive-locals.md)

[CA1811: Unikaj niewywołanego kodu prywatnego](../code-quality/ca1811-avoid-uncalled-private-code.md)

[CA1812: Unikaj klas wewnętrznych bez wystąpień](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801: Przejrzyj nieużywane parametry](../code-quality/ca1801-review-unused-parameters.md)