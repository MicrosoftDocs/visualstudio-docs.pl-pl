---
title: Debuger usługi brakować pamięci | Dokumentacja firmy Microsoft
ms.date: 07/10/2019
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.debug_no_memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger
author: isadorasophia
ms.author: isgarcia
manager: caslan
ms.workload:
- multiple
ms.openlocfilehash: 05664ffd056f69215e6fb00d6d49a59382a3692f
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2019
ms.locfileid: "67861172"
---
# <a name="debugger-services-running-out-of-memory"></a>Debuger usług uruchomionych za mało pamięci
Debugowanie usług zabrakło pamięci i spowodował zakończenie sesji debugowania.

## <a name="to-investigate-this-error-on-windows"></a>Aby zbadać wystąpienie tego błędu dla Windows
- Możesz ewidencjonować wykres pamięci procesu **narzędzia diagnostyczne** oknie, aby zobaczyć, jeśli aplikacja docelowa występuje ogromnego wzrostu w pamięci. Jeśli tak, użyj **użycie pamięci** narzędzie, aby zdiagnozować, co to jest problem, zobacz [Analizowanie użycia pamięci](../profiling/memory-usage.md).

- Jeśli aplikacja docelowa nie wydaje się zużywałoby dużej ilości pamięci, należy użyć **Menedżera zadań** oknie, aby sprawdzić limit użycia pamięci programu Visual Studio (devenv.exe), proces roboczy (msvsmon.exe) lub programu VS Code (vsdbg.exe/vsdbg-ui.exe) do Ustal, czy problem debugera. Uruchamianie za mało pamięci procesu devenv.exe należy rozważyć zmniejszenie liczby rozszerzeń programu Visual Studio uruchomiony.

## <a name="see-also"></a>Zobacz też
- [Wpis w blogu: Analizowanie użycia Procesora i pamięci podczas debugowania](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [Zarządzanie pamięcią-informacje](/windows/win32/memory/about-memory-management)
