---
title: 'DA0501: Średnie wykorzystanie CPU przez proces poddawany profilowaniu. | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d9835ad1965d1fd9a31113117eeb07ed62fd8ec4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777466"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: Średnie zużycie procesora cpu przez proces profilowany.

|||
|-|-|
|Identyfikator reguły|Da501|
|Kategoria|Monitorowanie zasobów|
|Metoda profilowania|Wszystkie|
|Komunikat|Średnie użycie procesora przez profilowany proces|
|Typ reguły|Informacje|

 Podczas profilowania przy użyciu próbkowania, .NET pamięci lub metody rywalizacji o zasoby, należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="rule-description"></a>Opis reguły
 Ten komunikat informuje procent czasu, przez który procesor był zajęty wykonywaniem instrukcji z aplikacji. Zgłoszona wartość jest średnią we wszystkich interwałach pomiaru, w których profilowany proces był aktywny. Wartość wartości może być większa niż 100% na komputerze z więcej niż jednym procesorem.

## <a name="how-to-use-rule-data"></a>Jak korzystać z danych reguły
 Użyj wartości reguły, aby porównać wydajność różnych wersji lub kompilacji programu lub zrozumieć wydajność aplikacji w różnych scenariuszach testowych.
