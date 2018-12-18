---
title: 'DA0026: Nadmierne CPU jądra. czas przetwarzania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DA0026
- vs.performance.DA0026
- vs.performance.26
ms.assetid: 4cfc8a29-b29b-4a72-b386-03d8856fdf8a
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2dbf52ab216a2272cb3b6094126a34987588704
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749685"
---
# <a name="da0026-excessive-kernel-cpu-time-processing"></a>DA0026: Nadmierne przetwarzanie czasu procesora CPU w trybie jądra
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identyfikator reguły | TODO |  
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
 Aby zbadać rodzaje wywołań systemowych, wykonywanych przez aplikację, ponownie uruchom profil i wybierz opcję, aby zebrać przykładów, w oparciu o wywołania systemowe. Zobacz [porady: Wybieranie zdarzeń próbkowania](../profiling/how-to-choose-sampling-events.md) w przypadku korzystania z narzędzi profilowania w IDE, aby uzyskać więcej informacji. Jeśli używasz narzędzi profilowania z wiersza polecenia, zobacz **opcje interwału próbkowania** części [VSPerfCmd](../profiling/vsperfcmd.md) tematu w wierszu polecenia Profiling Tools odnoszą się narzędzia.



