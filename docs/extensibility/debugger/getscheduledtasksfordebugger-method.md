---
title: GetScheduledTasksForDebugger — Metoda | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fca6c8e92cd0b4755bd79b8e142a7e1d283f868d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738665"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger, metoda
Pobiera tablicę wszystkich zaplanowanych zadań.

 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

 Ponieważ nie można uzyskać dostępu do tego wewnętrznego elementu członkowskiego z .NET Framework, następująca składnia jest dostępna w typowym języku pośrednim (CIL).

## <a name="syntax"></a>Składnia

```csharp
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed
```

## <a name="return-value"></a>Wartość zwracana
 Tablica wszystkich zaplanowanych zadań. Każde zadanie jest wykonywane lub zostało zakończone.

## <a name="remarks"></a>Uwagi
 Ta metoda nie jest bezpieczna wątkowo i nie należy jej używać jednocześnie z innymi wystąpieniami <xref:System.Threading.Tasks.TaskScheduler> . Wywołaj tę metodę z debugera tylko wtedy, gdy debuger zatrzymał wszystkie pozostałe wątki.

## <a name="see-also"></a>Zobacz też
- [Klasa TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)
