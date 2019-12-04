---
title: 'DA0026: nadmierne przetwarzanie czasu procesora CPU w jądrze | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0026
- vs.performance.DA0026
- vs.performance.26
ms.assetid: 4cfc8a29-b29b-4a72-b386-03d8856fdf8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2c8b4cb63eb4647ddab4220ed6729894fe8a456f
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777492"
---
# <a name="da0026-excessive-kernel-cpu-time-processing"></a>DA0026: Nadmierne przetwarzanie czasu procesora CPU w trybie jądra

|||
|-|-|
|Identyfikator zasady|CZYNNOŚĆ|
|Kategoria|Użycie narzędzia profilowania|
|Metoda profilowania|Sond|
|Komunikat|Mierzona stosunkowo dużą ilość czasu procesora CPU w trybie jądra. Rozważ zbadanie źródła z włączonym próbką SysCall.|
|Typ reguły|Informacje programu|

 Podczas profilowania przy użyciu metod pobierania próbek, pamięci .NET lub rywalizacji o zasoby należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="cause"></a>Przyczyna
 Proporcjonalny czas procesora CPU wykonywany w trybie jądra przekroczył czas spędzony w trybie użytkownika. Rozważ ponowne utworzenie profilu i próbkowanie liczby wywołań systemowych (systemowe) w celu określenia przyczyny czasu wykonywania wysokiego trybu jądra.

## <a name="rule-description"></a>Opis reguły
 Stosunkowo długi czas, przez jaki aplikacja poświęcana na wykonywanie w trybie jądra może uzasadnić dalsze badanie. Aplikacja trybu użytkownika przechodzi do trybu jądra w celu wykonania operacji we/wy, oczekiwania na elementy pierwotne synchronizacji wątków lub procesów lub wywołania systemowe. Można zbadać rodzaje wywołań systemowych, które są używane przez aplikację i jakie funkcje są odpowiedzialne za nich przy wybraniu opcji zbierania przykładowych stosów wywołań na podstawie wywołań systemowych.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby zbadać rodzaje wywołań systemowych wykonywanych przez aplikację, należy ponownie uruchomić profil i wybrać opcję zbierania próbek w oparciu o wywołania systemowe. Aby uzyskać więcej informacji, zobacz [jak: wybrać zdarzenia próbkowania](../profiling/how-to-choose-sampling-events.md) , jeśli są uruchamiane narzędzia profilowania w środowisku IDE. Jeśli uruchamiasz narzędzia profilowania z wiersza polecenia, zobacz sekcję **Opcje interwału próbkowania** artykułu [VSPerfCmd](../profiling/vsperfcmd.md) w dokumentacji narzędzi wiersza polecenia narzędzia profilowania.
