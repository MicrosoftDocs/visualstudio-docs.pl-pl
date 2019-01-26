---
title: 'CA1900: Pola typu wartości powinny być przenośne'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 84861aa1d17f041061d1666d6f78c9d273b948b4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037775"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900: Pola typu wartości powinny być przenośne

|||
|-|-|
|TypeName|ValueTypeFieldsShouldBePortable|
|CheckId|CA1900|
|Kategoria|Microsoft.Portability|
|Zmiana kluczowa|Przerywanie — Jeśli pola są widoczne poza zestawem.<br /><br /> Bez podziału — Jeśli pole nie jest widoczna spoza zestawu.|

## <a name="cause"></a>Przyczyna
 Ta reguła sprawdza, czy struktury, które są zadeklarowane za pomocą jawnego układu, zostaną prawidłowo wyrównane podczas przekazywania do kodu niezarządzanego w 64-bitowych systemach operacyjnych. IA-64 nie zezwala na dostępów do niewyrównanych pamięci i proces ulegnie awarii, jeśli to naruszenie nie został rozwiązany.

## <a name="rule-description"></a>Opis reguły
 Struktury, które mają jawne układ, który zawiera niewyrównane pola powodują awarię na 64-bitowych systemach operacyjnych.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Wszystkie pola, które są mniejsze niż 8 bajtów musi mieć wartość przesunięcia, które są wielokrotnością ich rozmiar i pola, które są 8 bajtów lub więcej musi mieć przesunięcia, których to wielokrotność liczby 8. Innym rozwiązaniem jest użycie `LayoutKind.Sequential` zamiast `LayoutKind.Explicit`, jeśli jest to uzasadnione.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 To ostrzeżenie powinno być pomijane, tylko wtedy, gdy wystąpi błąd.