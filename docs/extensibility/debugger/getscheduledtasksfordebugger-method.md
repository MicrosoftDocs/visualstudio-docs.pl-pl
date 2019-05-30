---
title: Metoda GetScheduledTasksForDebugger | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49a63462eece9bef09579c7284f72790a3914bc2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353732"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger, metoda
Pobiera tablicę wszystkich zaplanowanych zadań.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

 Ponieważ nie można uzyskać dostępu do tego elementu wewnętrznego z programu .NET Framework, następującej składni znajduje się w typowych Intermediate Language (CIL).

## <a name="syntax"></a>Składnia

```csharp
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed
```

## <a name="return-value"></a>Wartość zwracana
 Tablica wszystkich zaplanowanych zadań. Każde zadanie podrzędne jest wykonywanie lub zakończenia.

## <a name="remarks"></a>Uwagi
 Ta metoda nie jest bezpieczny dla wątków i nie należy jej używać równocześnie z innymi wystąpieniami <xref:System.Threading.Tasks.TaskScheduler>. Tę metodę można wywołać z debugera, tylko wtedy, gdy jest debugera wstrzymał inne wątki.

## <a name="see-also"></a>Zobacz także
- [TaskScheduler, klasa](../../extensibility/debugger/taskscheduler-class-internal-members.md)