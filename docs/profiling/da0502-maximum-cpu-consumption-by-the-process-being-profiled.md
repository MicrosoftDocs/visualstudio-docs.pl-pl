---
title: 'DA0502: Maksymalne użycie Procesora przez profilowany proces | Dokumentacja firmy Microsoft'
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
ms.workload:
- multiple
ms.openlocfilehash: e7092e6424a5f00ed4461a91ed10bbf530597082
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56612260"
---
# <a name="da0502-maximum-cpu-consumption-by-the-process-being-profiled"></a>DA0502: Maksymalne użycie Procesora przez profilowany proces

|||
|-|-|
|Identyfikator reguły|DA0502|
|Kategoria|Monitorowanie zasobów|
|Metoda profilowania|Wszystkie|
|Komunikat|Ta reguła jest wyłącznie w celach informacyjnych. Funkcja Process() licznik\\% czasu procesora mierzy użycie Procesora przez profilowany proces. Zgłaszana wartość to maksimum zaobserwowane we wszystkich interwałach pomiarowych.|
|Typ reguły|Informacyjny|

 Podczas profilowania za pomocą próbkowania pamięci platformy .NET i metod rywalizacji zasobów musi zebrać co najmniej 10 próbek do wyzwolenia tej reguły.

## <a name="rule-description"></a>Opis reguły
 Ten komunikat zgłasza maksymalny procent czasu procesor był zajęty, wykonując instrukcje z aplikacji. Wystąpienia wartości zgłoszonej jest maksymalną wartość zgłaszaną wśród wszystkich interwałów pomiarowych, w których był aktywny proces poddawany profilowaniu. Wartość procentowa może być większa niż 100% na maszynie z więcej niż jednego procesora.

## <a name="how-to-use-the-rule-data"></a>Sposób użycia danych reguły
 Użyj wartości reguły, aby porównać wydajność różnych wersji lub kompilacjach programu lub aby zrozumieć wydajność aplikacji w różnych scenariuszach profilowania.