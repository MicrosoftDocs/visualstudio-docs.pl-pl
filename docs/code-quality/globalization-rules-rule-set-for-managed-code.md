---
title: Zestaw reguł globalizacji dla zarządzanego kodu
ms.date: 11/04/2016
description: Zapoznaj się z regułami globalizacji ustawionymi w programie Visual Studio, które koncentrują się na problemach związanych z językami, lokalnymi i kulturami. Zobacz opisy reguł.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0bf96c8e4140e5b491624d6750b498a26726761c
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348882"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Zestaw reguł globalizacji dla zarządzanego kodu

Zestaw reguł globalizacji firmy Microsoft umożliwia skoncentrowanie się na problemach, które mogą uniemożliwić poprawne wyświetlanie danych w aplikacji w różnych językach, ustawieniach regionalnych i kulturach. Ten zestaw reguł powinien być dołączany, jeśli aplikacja jest zlokalizowana, globalna lub obie.

|Reguła|Opis|
|----------|-----------------|
|[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303)|Nie przekazuj literałów jako zlokalizowanych parametrów|
|[CA1304](/dotnet/fundamentals/code-analysis/quality-rules/ca1304)|Określ argument CultureInfo|
|[CA1305](/dotnet/fundamentals/code-analysis/quality-rules/ca1305)|Określ argument IFormatProvider|
|[CA1307](/dotnet/fundamentals/code-analysis/quality-rules/ca1307)|Określ StringComparison dla jasności|
|[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308)|Normalizuj ciągi do postaci zapisanej wielkimi literami|
|[CA1309](/dotnet/fundamentals/code-analysis/quality-rules/ca1309)|Użyj porządkowego ustawienia właściwości StringComparison|
|[CA1310](/dotnet/fundamentals/code-analysis/quality-rules/ca1310)|Określ StringComparison dla poprawności|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|Określ kierowanie dla argumentów ciągu P/Invoke|
