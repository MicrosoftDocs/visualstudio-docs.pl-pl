---
title: DA0502 — maksymalne użycie procesora CPU przez profilowany proces | Microsoft Docs
description: Ten komunikat zgłasza maksymalny procent czasu, przez który procesor był zajęty wykonywaniem instrukcji z aplikacji.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0502
- vs.performance.DA0502
- vs.performance.502
ms.assetid: 1ee53df5-b0dc-4265-9d4f-527830d08725
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 45071fb94b00be721e8c76c69dc5135a59f3a9b1
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2021
ms.locfileid: "102465780"
---
# <a name="da0502-maximum-cpu-consumption-by-the-process-being-profiled"></a>DA0502: maksymalne użycie procesora CPU przez profilowany proces

|Element|Wartość|
|-|-|
|Identyfikator reguły|DA0502|
|Kategoria|Monitorowanie zasobów|
|Metoda profilowania|Wszystko|
|Komunikat|Ta reguła służy tylko do celów informacyjnych. \\Licznik czas procesora (%) mierzy użycie procesora przez proces profilowania. Raportowana wartość jest maksimum zaobserwowane we wszystkich interwałach pomiarowych.|
|Typ reguły|Informacyjne|

 Podczas profilowania przy użyciu metod pobierania próbek, pamięci .NET lub rywalizacji o zasoby należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="rule-description"></a>Opis reguły
 Ten komunikat zgłasza maksymalny procent czasu, przez który procesor był zajęty wykonywaniem instrukcji z aplikacji. Raportowana wartość jest wartością maksymalną raportowaną we wszystkich interwałach pomiarowych, w których proces profilowany był aktywny. Wartość procentowa może być większa niż 100% na komputerze z więcej niż jednym procesorem.

## <a name="how-to-use-the-rule-data"></a>Jak korzystać z danych reguły
 Wartość reguły służy do porównywania wydajności różnych wersji lub kompilacji programu lub do zrozumienia wydajności aplikacji w różnych scenariuszach profilowania.
