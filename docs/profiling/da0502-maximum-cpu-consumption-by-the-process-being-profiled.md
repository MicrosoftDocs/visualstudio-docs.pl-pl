---
title: 'DA0502: Maksymalne zużycie procesora przez profilowany proces | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0502
- vs.performance.DA0502
- vs.performance.502
ms.assetid: 1ee53df5-b0dc-4265-9d4f-527830d08725
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5c3cb5169d078ba1242bf898ba93e31a7a488bb8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779340"
---
# <a name="da0502-maximum-cpu-consumption-by-the-process-being-profiled"></a>DA0502: Maksymalne zużycie procesora przez profilowany proces

|||
|-|-|
|Identyfikator reguły|DA0502|
|Kategoria|Monitorowanie zasobów|
|Metoda profilowania|Wszystkie|
|Komunikat|Ta reguła służy wyłącznie do celów informacyjnych. Licznik Czasu\\procesora Process() % mierzy zużycie procesora w procesie profilowania. Zgłoszona wartość jest maksymalną obserwowaną we wszystkich odstępach czasu pomiaru.|
|Typ reguły|Informacyjne|

 Podczas profilowania przy użyciu próbkowania, .NET pamięci lub metody rywalizacji o zasoby, należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="rule-description"></a>Opis reguły
 Ten komunikat informuje o maksymalnym procentowym czasie, przez który procesor był zajęty wykonywaniem instrukcji z aplikacji. Zgłoszona wartość jest maksymalną wartością zgłoszoną dla wszystkich interwałów pomiaru, w których profilowany proces był aktywny. Wartość procentowa może być większa niż 100% na komputerze z więcej niż jednym procesorem.

## <a name="how-to-use-the-rule-data"></a>Jak korzystać z danych reguły
 Użyj wartości reguły, aby porównać wydajność różnych wersji lub kompilacji programu lub zrozumieć wydajność aplikacji w różnych scenariuszach profilowania.
