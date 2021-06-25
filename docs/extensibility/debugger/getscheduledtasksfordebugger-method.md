---
description: Pobiera tablicę wszystkich zaplanowanych zadań.
title: GetScheduledTasksForDebugger, metoda | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 51da481edb636450770d0cff569b9ef411e17cf6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900957"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger, metoda
Pobiera tablicę wszystkich zaplanowanych zadań.

 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

 Ponieważ nie można uzyskać dostępu do tego wewnętrznego członka z .NET Framework, w języku CIL (Common Intermediate Language) znajduje się następująca składnia.

## <a name="syntax"></a>Składnia

```csharp
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed
```

## <a name="return-value"></a>Wartość zwracana
 Tablica wszystkich zaplanowanych zadań. Każde zadanie jest wykonywane lub zostało zakończone.

## <a name="remarks"></a>Uwagi
 Ta metoda nie jest bezpieczna wątkowo i nie należy jej używać jednocześnie z innymi wystąpieniami klasy <xref:System.Threading.Tasks.TaskScheduler> . Wywołaj tę metodę z debugera tylko wtedy, gdy debuger zawiesił wszystkie inne wątki.

## <a name="see-also"></a>Zobacz też
- [TaskScheduler, klasa](../../extensibility/debugger/taskscheduler-class-internal-members.md)
