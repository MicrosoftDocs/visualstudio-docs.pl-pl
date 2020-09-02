---
title: 'DA0008: kilka próbek zebranych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DATooFewSamples
- vs.performance.8
- vs.performance.DA0008
- vs.performance.rules.DA0008
ms.assetid: 8a5b78aa-7b3d-476c-a47d-abfaff3fae7c
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 03fd9b6fd794320faf76119616900b79d5bf4333
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187858"
---
# <a name="da0008-few-samples-collected"></a>DA0008: Zebrano kilka próbek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identyfikator reguły | DA0008 |  
| Kategoria | Użycie narzędzia profilowania |  
| Metoda profilowania | Próbkowanie |  
| Komunikat | Zebrano tylko kilka przykładów. Aby uzyskać bardziej znaczące wyniki, należy wziąć pod uwagę dłuższy przebieg lub szybszy współczynnik próbkowania. |  
| Typ reguły | Informacje |  
  
## <a name="cause"></a>Przyczyna  
 Tylko kilka przykładów zostało zebranych w przebiegu profilowania.  
  
## <a name="rule-description"></a>Opis reguły  
 Gdy używana jest metoda próbkowania, należy zebrać statystycznie znaczącą liczbę próbek, aby upewnić się, że dane reprezentują rzeczywiste zachowanie programu. Aby zminimalizować błędy próbkowania, należy spróbować zebrać co najmniej 1000 próbek zachowań wykonywania instrukcji programu. Jeśli nie zbierasz wystarczającej ilości próbek, podczas analizowania danych profilowania możesz być w stanie wystąpić.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Należy rozważyć profilowanie dłuższego uruchomienia aplikacji lub użycie szybszej szybkości próbkowania w celu uzyskania statystycznie znaczących wyników. Aby uzyskać informacje o sposobie zmiany częstotliwości próbkowania w środowisku IDE programu Visual Studio, zobacz [How to: Choose Events próbking](../profiling/how-to-choose-sampling-events.md). Aby uzyskać więcej informacji o sposobie zmiany częstotliwości próbkowania podczas korzystania z wiersza polecenia narzędzia profilowania, zobacz [Timer](../profiling/timer.md) w [VSPerfCmd](../profiling/vsperfcmd.md) Reference.
