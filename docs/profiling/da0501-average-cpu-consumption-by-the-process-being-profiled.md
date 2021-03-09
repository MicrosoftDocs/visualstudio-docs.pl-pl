---
title: DA0501 — średnie użycie procesora przez profilowany proces. | Microsoft Docs
description: Ten komunikat przedstawia wartość procentową czasu, przez który procesor był zajęty wykonywaniem instrukcji z aplikacji.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 242a3ff10042a53997b17f662af145440df2e95a
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2021
ms.locfileid: "102465832"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: średnie użycie procesora przez profilowany proces.

|Element|Wartość|
|-|-|
|Identyfikator reguły|DA501|
|Kategoria|Monitorowanie zasobów|
|Metoda profilowania|Wszystko|
|Komunikat|Średnie użycie procesora przez profilowany proces|
|Typ reguły|Informacje|

 Podczas profilowania przy użyciu metod pobierania próbek, pamięci .NET lub rywalizacji o zasoby należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="rule-description"></a>Opis reguły
 Ten komunikat przedstawia wartość procentową czasu, przez który procesor był zajęty wykonywaniem instrukcji z aplikacji. Raportowana wartość jest wartością średnią dla wszystkich interwałów pomiarowych, w przypadku których proces profilowany jest aktywny. Wartość może być większa niż 100% na komputerze z więcej niż jednym procesorem.

## <a name="how-to-use-rule-data"></a>Jak używać danych reguł
 Użyj wartości reguły, aby porównać wydajność różnych wersji lub kompilacji programu lub zrozumieć wydajność aplikacji w różnych scenariuszach testowych.
