---
title: 'DA0008: kilka próbek zebranych | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DATooFewSamples
- vs.performance.8
- vs.performance.DA0008
- vs.performance.rules.DA0008
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 15f8eeb370a3f1e61981e0e936704d33f6b44bbd
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779444"
---
# <a name="da0008-few-samples-collected"></a>DA0008: Kilka zebranych przykładów

|||
|-|-|
|Identyfikator zasady|DA0008|
|Kategoria|Użycie narzędzia profilowania|
|Metoda profilowania|Sond|
|Komunikat|Zebrano tylko kilka przykładów. Należy rozważyć dłuższy przebieg lub szybszy współczynnik próbkowania, aby uzyskać bardziej znaczące wyniki.|
|Typ reguły|Informacje programu|

## <a name="cause"></a>Przyczyna
 Tylko kilka przykładów zostało zebranych w przebiegu profilowania.

## <a name="rule-description"></a>Opis reguły
 Gdy używana jest metoda próbkowania, należy zebrać statystycznie znaczącą liczbę próbek, aby upewnić się, że dane reprezentują rzeczywiste zachowanie programu. Aby zminimalizować błędy próbkowania, należy spróbować zebrać co najmniej 1000 próbek zachowań wykonywania instrukcji programu. Jeśli nie zbierasz wystarczającej ilości próbek, podczas analizowania danych profilowania możesz być w stanie wystąpić.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Należy rozważyć profilowanie dłuższego uruchomienia aplikacji lub użycie szybszej szybkości próbkowania w celu uzyskania statystycznie znaczących wyników. Aby uzyskać informacje o sposobie zmiany częstotliwości próbkowania w środowisku IDE programu Visual Studio, zobacz [How to: Choose Events próbking](../profiling/how-to-choose-sampling-events.md). Aby uzyskać więcej informacji o sposobie zmiany częstotliwości próbkowania podczas korzystania z wiersza polecenia narzędzia profilowania, zobacz [Timer](../profiling/timer.md) w [VSPerfCmd](../profiling/vsperfcmd.md) Reference.
