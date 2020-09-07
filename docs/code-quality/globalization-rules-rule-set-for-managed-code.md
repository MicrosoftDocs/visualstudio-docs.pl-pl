---
title: Zestaw reguł globalizacji dla zarządzanego kodu
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2af6126c751d03968dc7ecd87693e3546376c12a
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509864"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Zestaw reguł globalizacji dla zarządzanego kodu

Zestaw reguł globalizacji firmy Microsoft umożliwia skoncentrowanie się na problemach, które mogą uniemożliwić poprawne wyświetlanie danych w aplikacji w różnych językach, ustawieniach regionalnych i kulturach. Ten zestaw reguł powinien być dołączany, jeśli aplikacja jest zlokalizowana, globalna lub obie.

|Reguła|Opis|
|----------|-----------------|
|[CA1303](../code-quality/ca1303.md)|Nie przekazuj literałów jako zlokalizowanych parametrów|
|[CA1304](../code-quality/ca1304.md)|Określ argument CultureInfo|
|[CA1305](../code-quality/ca1305.md)|Określ argument IFormatProvider|
|[CA1307](../code-quality/ca1307.md)|Określ StringComparison dla jasności|
|[CA1308](../code-quality/ca1308.md)|Normalizuj ciągi do postaci zapisanej wielkimi literami|
|[CA1309](../code-quality/ca1309.md)|Użyj porządkowego ustawienia właściwości StringComparison|
|[CA1310](../code-quality/ca1310.md)|Określ StringComparison dla poprawności|
|[CA2101](../code-quality/ca2101.md)|Określ kierowanie dla argumentów ciągu P/Invoke|
