---
title: GetScheduledTasksForDebugger Metoda | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738665"
---
# <a name="getscheduledtasksfordebugger-method"></a>GetScheduledTasksForDebugger, metoda
Pobiera tablicę wszystkich zaplanowanych zadań.

 **Obszar nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montaż:** mscorlib (w *mscorlib.dll*)

 Ponieważ nie można uzyskać dostępu do tego wewnętrznego elementu członkowskiego z programu .NET Framework, następująca składnia znajduje się we wspólnym języku pośrednim (CIL).

## <a name="syntax"></a>Składnia

```csharp
.method assembly hidebysig instance class System.Threading.Tasks.Task[] GetScheduledTasksForDebugger() cil managed
```

## <a name="return-value"></a>Wartość zwracana
 Tablica wszystkich zaplanowanych zadań. Każde zadanie jest wykonywane lub zakończyło wykonywanie.

## <a name="remarks"></a>Uwagi
 Ta metoda nie jest bezpieczna dla wątków i nie należy <xref:System.Threading.Tasks.TaskScheduler>jej używać jednocześnie z innymi wystąpieniami programu . Wywołanie tej metody z debugera tylko wtedy, gdy debuger zawiesił wszystkie inne wątki.

## <a name="see-also"></a>Zobacz też
- [Klasa TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)
