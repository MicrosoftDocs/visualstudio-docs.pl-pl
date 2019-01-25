---
title: 'DA0026: Przetwarzanie w czasie jądra nadmiernego użycia Procesora | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0026
- vs.performance.DA0026
- vs.performance.26
ms.assetid: 4cfc8a29-b29b-4a72-b386-03d8856fdf8a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fef0a3c42be1057bd1217ec676ae43b220d80345
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54768974"
---
# <a name="da0026-excessive-kernel-cpu-time-processing"></a>DA0026: Przetwarzanie w czasie jądra nadmiernego użycia Procesora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rule Id|TODO|  
| Kategoria | Profilowanie użycia narzędzia |  
| Metoda profilowania | Próbkowanie |  
| Komunikat | Został zmierzony stosunkowo dużej ilości czasu Procesora w trybie jądra. Należy rozważyć zbadanie kodu źródłowego z włączonym próbkowaniem SysCall. |  
| Typ reguły | Informacji |  
  
 Podczas profilowania za pomocą próbkowania pamięci platformy .NET i metod rywalizacji zasobów musi zebrać co najmniej 10 próbek do wyzwolenia tej reguły.  
  
## <a name="cause"></a>Przyczyna  
 Czas procesora CPU udział, który został wykonany w trybie jądra przekracza ilość czasu spędzonego w trybie użytkownika. Należy wziąć pod uwagę profilowanie ponownie i próbkowanie liczba wywołań systemowych (syscalls) w celu ustalenia przyczyny od czasu wykonania trybu jądra wysoka.  
  
## <a name="rule-description"></a>Opis reguły  
 Stosunkowo dużą część czas potrzebny aplikacji do wykonywania w trybie jądra mogą uzasadniać dalszego badania. Aplikacja w trybie użytkownika przechodzi do trybu jądra do wykonywania operacji We/Wy, poczekaj, aż wątek lub procesu synchronizacji w nim elementów podstawowych lub wykonać wywołania systemowe. Można zbadać rodzaje wywołań systemowych sprawia, że aplikacja, i funkcje, które odpowiadają po wybraniu opcji, aby zebrać stosy wywołań przykładowe opartym na wywołania systemowe.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby zbadać rodzaje wywołań systemowych, wykonywanych przez aplikację, ponownie uruchom profil i wybierz opcję, aby zebrać przykładów, w oparciu o wywołania systemowe. Zobacz [jak: Wybieranie zdarzeń próbkowania](../profiling/how-to-choose-sampling-events.md) w przypadku korzystania z narzędzi profilowania w IDE, aby uzyskać więcej informacji. Jeśli używasz narzędzi profilowania z wiersza polecenia, zobacz **opcje interwału próbkowania** części [VSPerfCmd](../profiling/vsperfcmd.md) tematu w wierszu polecenia Profiling Tools odnoszą się narzędzia.
