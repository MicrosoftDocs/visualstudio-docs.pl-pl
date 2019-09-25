---
title: 'CA1823: Unikaj nieużywanych pól prywatnych'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f0aa23ff93e193ee06509c1cb635404ec827793
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233360"
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823: Unikaj nieużywanych pól prywatnych

|||
|-|-|
|TypeName|AvoidUnusedPrivateFields|
|CheckId|CA1823|
|Kategoria|Microsoft.Performance|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Ta reguła jest raportowana, gdy istnieje pole prywatne w kodzie, ale nie jest ono używane przez żadną ścieżkę kodu.

## <a name="rule-description"></a>Opis reguły
Zostały wykryte pola prywatne, które w zestawie nie są widoczne jako dostępne.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Usuń pole lub Dodaj kod, który go używa.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Można bezpiecznie pominąć ostrzeżenie z tej reguły.

## <a name="related-rules"></a>Powiązane reguły
[CA1812: Unikaj klas wewnętrznych bez wystąpień](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801: Przejrzyj nieużywane parametry](../code-quality/ca1801-review-unused-parameters.md)

[CA1804: Usuń nieużywane elementy lokalne](../code-quality/ca1804-remove-unused-locals.md)

[CA1811: Unikaj niewywołanego kodu prywatnego](../code-quality/ca1811-avoid-uncalled-private-code.md)