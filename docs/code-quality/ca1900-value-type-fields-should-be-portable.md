---
title: 'CA1900: Pola typu wartości powinny być przenośne'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4bef51c547d4a1614137e0691343bef635aed50d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233276"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: Pola typu wartości powinny być przenośne

|||
|-|-|
|TypeName|ValueTypeFieldsShouldBePortable|
|CheckId|CA1900|
|Kategoria|Microsoft. przenośność|
|Zmiana podziału|Przerywanie — Jeśli pole może być widoczne poza zestawem.<br /><br /> Bez przerywania — Jeśli pole nie jest widoczne poza zestawem.|

## <a name="cause"></a>Przyczyna
Ta reguła sprawdza, czy struktury zadeklarowane za pomocą jawnego układu są wyrównane prawidłowo, gdy są przekazywane do kodu niezarządzanego w 64-bitowych systemach operacyjnych. IA-64 nie zezwala na niewyrównany dostęp do pamięci, a proces zostanie rozwiązany, jeśli to naruszenie nie zostanie naprawione.

## <a name="rule-description"></a>Opis reguły
Struktury, które mają jawny układ, który zawiera niewyrównane pola, powodują awarie w 64-bitowych systemach operacyjnych.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Wszystkie pola, które są mniejsze niż 8 bajtów, muszą mieć przesunięcia, które są wielokrotnością rozmiaru, a pola, które mają 8 bajtów lub więcej, muszą mieć przesunięcia, które są wielokrotnością 8. Innym rozwiązaniem jest użycie `LayoutKind.Sequential` `LayoutKind.Explicit`zamiast, jeśli jest to uzasadnione.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
To ostrzeżenie powinno być pomijane tylko wtedy, gdy wystąpi błąd.