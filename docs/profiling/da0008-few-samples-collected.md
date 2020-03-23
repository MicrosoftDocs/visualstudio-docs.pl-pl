---
title: 'DA0008: Kilka pobranych próbek | Dokumenty firmy Microsoft'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779444"
---
# <a name="da0008-few-samples-collected"></a>DA0008: Kilka zebranych przykładów

|||
|-|-|
|Identyfikator reguły|DA0008|
|Kategoria|Użycie narzędzi profilowania|
|Metoda profilowania|Próbkowanie|
|Komunikat|Zebrano tylko kilka próbek. Należy wziąć pod uwagę dłuższą lub szybszą częstotliwość próbkowania dla bardziej znaczących wyników.|
|Typ reguły|Informacje|

## <a name="cause"></a>Przyczyna
 W przebiegu profilowania zebrano zaledwie kilka próbek.

## <a name="rule-description"></a>Opis reguły
 Gdy używana jest metoda próbkowania, należy zebrać statystycznie istotną liczbę próbek, aby upewnić się, że dane reprezentują rzeczywiste zachowanie programu. Aby zminimalizować błędy próbkowania, należy spróbować zebrać co najmniej 1000 próbek zachowania wykonywania instrukcji programu. Jeśli nie zbierzesz wystarczającej liczby próbek, możesz zostać wprowadzony w błąd podczas analizowania danych profilowania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Rozważ profilowanie dłuższego przebiegu aplikacji lub przy użyciu szybszej częstotliwości próbkowania w celu uzyskania statystycznie istotnych wyników. Aby uzyskać informacje dotyczące zmieniania częstotliwości próbkowania w programie Visual Studio IDE, zobacz [Jak: Wybieranie zdarzeń próbkowania.](../profiling/how-to-choose-sampling-events.md) Aby uzyskać więcej informacji na temat sposobu zmiany częstotliwości próbkowania podczas korzystania z wiersza polecenia Narzędzia profilowania, zobacz [Czasomierz](../profiling/timer.md) w odwołaniu [VSPerfCmd.](../profiling/vsperfcmd.md)
