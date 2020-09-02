---
title: Usługi debugera zaczynają za mało pamięci | Microsoft Docs
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
ms.openlocfilehash: 12215f9c740e68c4f2749a51b06c09a1385dae1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72737842"
---
# <a name="debugger-services-running-out-of-memory"></a>Za mało pamięci w usługach debugera
Usługa debugowania przekroczyła ilość pamięci i spowodowała przerwanie sesji debugowania.

## <a name="to-investigate-this-error-on-windows"></a>Aby zbadać ten błąd w systemie Windows
- Możesz sprawdzić wykres pamięci procesu w oknie **Narzędzia diagnostyczne** , aby sprawdzić, czy w aplikacji docelowej występuje ogromny wzrost ilości pamięci. W takim przypadku należy użyć narzędzia **użycie pamięci** do zdiagnozowania, jaki jest podstawowy problem, zobacz [Analizowanie użycia pamięci](../profiling/memory-usage.md).

- Jeśli aplikacja docelowa nie zużywa dużej ilości pamięci, użyj okna **Menedżera zadań** , aby sprawdzić użycie pamięci przez program Visual Studio (devenv.exe), proces roboczy (msvsmon.exe) lub VS Code (vsdbg.exe/vsdbg-ui.exe), aby określić, czy jest to problem z debugerem. Jeśli jest devenv.exe, należy rozważyć zmniejszenie liczby uruchomionych rozszerzeń programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Wpis w blogu: analizowanie procesora i pamięci podczas debugowania](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)
- [Informacje o zarządzaniu pamięcią](/windows/win32/memory/about-memory-management)
