---
title: Zestaw reguł globalizacji dla kodu zarządzanego | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1630769b5150d9cef7b00e575ac9c555f5bc5be1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667602"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Zestaw reguł globalizacji dla zarządzanego kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można użyć zestawu reguł globalizacji firmy Microsoft, aby skoncentrować się na problemach, które mogą uniemożliwić poprawne wyświetlanie danych w aplikacji w różnych językach, ustawieniach regionalnych i kulturach. Ten zestaw reguł powinien być dołączany, jeśli aplikacja jest zlokalizowana, globalna lub obie.

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
