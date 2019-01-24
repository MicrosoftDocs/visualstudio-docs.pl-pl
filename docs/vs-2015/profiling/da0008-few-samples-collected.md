---
title: 'DA0008: Zebrano kilka próbek | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54800408"
---
# <a name="da0008-few-samples-collected"></a>DA0008: Kilka zebranych próbek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rule Id|DA0008|  
| Kategoria | Profilowanie użycia narzędzia |  
| Metoda profilowania | Próbkowanie |  
| Komunikat | Zebrano tylko kilka przykładów. Należy wziąć pod uwagę dłużej przebiegu lub zwiększenie częstotliwości próbkowania dla uzyskania bardziej znaczących wyników. |  
| Typ reguły | Informacji |  
  
## <a name="cause"></a>Przyczyna  
 Kilka przykładów zostały zebrane podczas uruchomienia profilowania.  
  
## <a name="rule-description"></a>Opis reguły  
 Gdy używana jest metoda pobierania próbek, należy zbierać są statystycznie istotne liczba próbek, aby upewnić się, że dane reprezentują program rzeczywiste zachowanie. Aby zminimalizować błędy pobierania próbek, należy spróbować zbieranie co najmniej 1000 próbek zachowanie wykonania instrukcji programu. Jeśli nie zbieraj, wystarczająco dużo próbki, można możesz błąd podczas analizowania danych profilowania.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Należy wziąć pod uwagę profilowania już wykonywania aplikacji lub za pomocą próbkowania szybciej uzyskać wyniki są statystycznie istotne. Aby dowiedzieć się, jak zmienić częstotliwość próbkowania w środowisku IDE programu Visual Studio, zobacz [jak: Wybieranie zdarzeń próbkowania](../profiling/how-to-choose-sampling-events.md). Aby uzyskać więcej informacji o tym, jak zmienić częstotliwość próbkowania, korzystając z wiersza polecenia Profiling Tools, zobacz [czasomierza](../profiling/timer.md) w [VSPerfCmd](../profiling/vsperfcmd.md) odwołania.
