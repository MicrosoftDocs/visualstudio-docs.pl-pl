---
title: Metoda GetScheduledTasksForDebugger | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetScheduledTasksForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 7c9b4cde-6e4a-4cef-929f-7d02b1da5762
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b68f8f238c180d4152d99b42f8ac075ef6dd3e7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54990631"
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
 [TaskScheduler, klasa](../../extensibility/debugger/taskscheduler-class-internal-members.md)