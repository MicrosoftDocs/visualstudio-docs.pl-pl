---
title: 'DA0026: Nadmierne przetwarzanie procesora jądra | Dokumenty firmy Microsoft'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777492"
---
# <a name="da0026-excessive-kernel-cpu-time-processing"></a>DA0026: Nadmierne przetwarzanie czasu procesora CPU w trybie jądra

|||
|-|-|
|Identyfikator reguły|Todo|
|Kategoria|Użycie narzędzi profilowania|
|Metoda profilowania|Próbkowanie|
|Komunikat|Mierzono stosunkowo wysoką ilość czasu procesora w trybie jądra. Należy rozważyć zbadanie źródła z włączonym próbkowaniem SysCall.|
|Typ reguły|Informacje|

 Podczas profilowania przy użyciu próbkowania, .NET pamięci lub metody rywalizacji o zasoby, należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="cause"></a>Przyczyna
 Proporcja czasu procesora procesora, który został wykonany w trybie jądra, przekroczyła czas spędzony w trybie użytkownika. Należy rozważyć profilowanie ponownie i próbkowanie liczby wywołań systemowych (syscalls), aby określić przyczynę czasu wykonywania trybu wysokiego jądra.

## <a name="rule-description"></a>Opis reguły
 Stosunkowo wysoki odsetek czasu, który aplikacja spędziła w wykonaniu w trybie jądra, może wymagać dalszego zbadania. Aplikacja w trybie użytkownika przechodzi do trybu jądra, aby wykonywać operacje we/wy, czekać na pierwotne dane pierwotne synchronizacji wątku lub procesu lub wykonywać wywołania systemowe. Można zbadać rodzaje wywołań systemowych sprawia, że aplikacja i które funkcje, które są odpowiedzialne za nich po wybraniu opcji, aby zebrać przykładowe stosy wywołań na podstawie wywołań systemowych.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby zbadać rodzaje wywołań systemowych, które sprawia, że aplikacja, uruchom profil ponownie i wybierz opcję, aby zebrać próbki na podstawie wywołań systemowych. Zobacz [Jak: Wybierz zdarzenia próbkowania,](../profiling/how-to-choose-sampling-events.md) jeśli są uruchomione narzędzia profilowania wewnątrz IDE, aby uzyskać więcej informacji. Jeśli narzędzia profilowania są uruchomione z wiersza polecenia, zobacz **sekcję Opcje interwału przykładowego** artykułu [VSPerfCmd](../profiling/vsperfcmd.md) w narzędziach wiersza polecenia Narzędzia profilowania.
