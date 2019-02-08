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
ms.openlocfilehash: 4e8d8b5b522f805bd7e8826cea5ced394c50064f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55919095"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: Normalizuj ciągi do postaci zapisanej wielkimi literami

|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Kategoria|Microsoft.Globalization|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Operacja normalizuje ciąg na małe litery.

## <a name="rule-description"></a>Opis reguły
 Ciągi powinny być znormalizowane do użycia wielkich liter. Niewielkiej liczby znaków, gdy są konwertowane na małe litery, nie mogą wykonywać rund. Można wykonywać rund, sposób konwertowania znaków z ustawień regionalnych co do innej wersji regionalnej, który reprezentuje dane znakowe inaczej, a następnie do dokładnie pobierać oryginalne znaki z przekonwertowanego znaków.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Zmień operacje, które konwersji ciągów znaków na małe litery, tak aby ciągi są konwertowane na wielkie litery w zamian. Na przykład zmienić `String.ToLower(CultureInfo.InvariantCulture)` do `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest to bezpieczne Pomiń komunikat ostrzegawczy, gdy nie wykonujesz decyzja dotycząca zabezpieczeń na podstawie wyniku (na przykład w przypadku wyświetlania go w interfejsie użytkownika).

## <a name="see-also"></a>Zobacz także
 [Ostrzeżenia dotyczące globalizacji](../code-quality/globalization-warnings.md)