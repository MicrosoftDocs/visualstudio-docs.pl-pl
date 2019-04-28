---
title: Zestaw reguł globalizacji dla zarządzanego kodu
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 28199eb9fa09e2096939ffa8e678eb9812a61b1f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816403"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Zestaw reguł globalizacji dla zarządzanego kodu
Można użyć reguły globalizacji firmy Microsoft zestaw reguł, aby skoncentrować się na problemy, które mogą uniemożliwić dane w aplikacji pojawianiu się poprawnie w różnych językach, ustawień regionalnych i kultur. Należy uwzględnić tej reguły, jeśli aplikacja jest lokalizowana globalizowana, lub obie.

|Reguła|Opis|
|----------|-----------------|
|[CA1300](../code-quality/ca1300-specify-messageboxoptions.md)|Określ argument MessageBoxOptions|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Unikaj duplikowania akceleratorów|
|[CA1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Nie umieszczaj trwale w kodzie ciągów specyficznych dla ustawień regionalnych|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Nie przekazuj literałów jako zlokalizowanych parametrów|
|[CA1304](../code-quality/ca1304-specify-cultureinfo.md)|Określ argument CultureInfo|
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|Określ argument IFormatProvider|
|[CA1306](../code-quality/ca1306-set-locale-for-data-types.md)|Ustaw ustawienia regionalne dla typów danych|
|[CA1307](../code-quality/ca1307-specify-stringcomparison.md)|Określ argument StringComparison|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Normalizuj ciągi do postaci zapisanej wielkimi literami|
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Użyj porządkowego ustawienia właściwości StringComparison|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Określ kierowanie dla argumentów ciągu P/Invoke|