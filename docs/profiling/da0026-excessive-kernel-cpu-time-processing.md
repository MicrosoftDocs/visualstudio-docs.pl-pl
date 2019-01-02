---
title: 'DA0026: Przetwarzanie w czasie jądra nadmiernego użycia Procesora | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0026
- vs.performance.DA0026
- vs.performance.26
ms.assetid: 4cfc8a29-b29b-4a72-b386-03d8856fdf8a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 20abd86d12db44dac1a2b3a7772e90dee1b2721f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53855458"
---
# <a name="da0026-excessive-kernel-cpu-time-processing"></a>DA0026: Przetwarzanie w czasie jądra nadmiernego użycia Procesora

|||  
|-|-|  
|Identyfikator reguły|TODO|  
|Kategoria|Użycie narzędzia profilowania|  
|Metoda profilowania|Próbkowania|  
|Komunikat|Został zmierzony stosunkowo dużej ilości czasu Procesora w trybie jądra. Należy rozważyć zbadanie kodu źródłowego z włączonym próbkowaniem SysCall.|  
|Typ reguły|Informacje|  

 Podczas profilowania za pomocą próbkowania pamięci platformy .NET i metod rywalizacji zasobów musi zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  

## <a name="cause"></a>Przyczyna  
 Czas procesora CPU udział, który został wykonany w trybie jądra przekracza ilość czasu spędzonego w trybie użytkownika. Należy wziąć pod uwagę profilowanie ponownie i próbkowanie liczba wywołań systemowych (syscalls) w celu ustalenia przyczyny od czasu wykonania trybu jądra wysoka.  

## <a name="rule-description"></a>Opis reguły  
 Stosunkowo dużą część czas potrzebny aplikacji do wykonywania w trybie jądra mogą uzasadniać dalszego badania. Aplikacja w trybie użytkownika przechodzi do trybu jądra do wykonywania operacji We/Wy, poczekaj, aż wątek lub procesu synchronizacji w nim elementów podstawowych lub wykonać wywołania systemowe. Można zbadać rodzaje wywołań systemowych sprawia, że aplikacja, i funkcje, które odpowiadają po wybraniu opcji, aby zebrać stosy wywołań przykładowe opartym na wywołania systemowe.  

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby zbadać rodzaje wywołań systemowych, wykonywanych przez aplikację, ponownie uruchom profil i wybierz opcję, aby zebrać przykładów, w oparciu o wywołania systemowe. Zobacz [jak: Wybieranie zdarzeń próbkowania](../profiling/how-to-choose-sampling-events.md) w przypadku korzystania z narzędzi profilowania w IDE, aby uzyskać więcej informacji. Jeśli używasz narzędzi profilowania z wiersza polecenia, zobacz **przykładowe opcje interwału** części [VSPerfCmd](../profiling/vsperfcmd.md) artykułu w odwołaniu do narzędzia wiersza polecenia Profiling Tools.