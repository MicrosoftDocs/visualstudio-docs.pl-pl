---
title: 'CA1308: Normalizuj ciągi do postaci zapisanej wielkimi literami'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 06fe8d4fbd4def14bfb8a24f4f211a121c809930
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922237"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: Normalizuj ciągi do postaci zapisanej wielkimi literami

|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Kategoria|Microsoft. Globalizacja|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Operacja normalizuje ciąg do małych liter.

## <a name="rule-description"></a>Opis reguły
Ciągi powinny być znormalizowane do użycia wielkich liter. Niewielka grupa znaków, gdy są konwertowane na małe litery, nie może przekonywać rundy. Aby przeznaczyć na rundę, można przekonwertować znaki z jednego ustawienia regionalnego na inne ustawienia regionalne, które reprezentują dane znakowe w różny sposób, a następnie w celu dokładnego pobrania oryginalnych znaków z konwertowanych znaków.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Zmień operacje, które konwertują ciągi na małe litery, aby ciągi były konwertowane na wielkie litery. Na przykład zmień `String.ToLower(CultureInfo.InvariantCulture)` na `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Można bezpiecznie pominąć komunikat ostrzegawczy, gdy nie podejmowana jest decyzja o zabezpieczeniach na podstawie wyniku (na przykład gdy jest wyświetlany w interfejsie użytkownika).

## <a name="see-also"></a>Zobacz także
[Ostrzeżenia dotyczące globalizacji](../code-quality/globalization-warnings.md)