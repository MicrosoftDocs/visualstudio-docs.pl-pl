---
title: Metoda GetTaskSchedulersForDebugger | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- GetTaskSchedulersForDebugger method, TaskScheduler class [.NET Framework debug engines]
ms.assetid: 58aa236a-5ab8-4695-b303-89dffdbcd946
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c8d038c8c67731fe1bff9ec705b5ddf416807a57
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353718"
---
# <a name="gettaskschedulersfordebugger-method"></a>GetTaskSchedulersForDebugger, metoda
Pobiera tablicę wszystkich <xref:System.Threading.Tasks.TaskScheduler> obiektów, które są aktualnie aktywne.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

 Ponieważ nie można uzyskać dostępu do tego elementu wewnętrznego z programu .NET Framework, następującej składni znajduje się w typowych Intermediate Language (CIL).

## <a name="syntax"></a>Składnia

```csharp
.method assembly hidebysig static class System.Threading.Tasks.TaskScheduler[] GetTaskSchedulersForDebugger() cil managed
```

## <a name="return-value"></a>Wartość zwracana
 Tablica wszystkich <xref:System.Threading.Tasks.TaskScheduler> obiekty, które są aktualnie aktywne, w tym <xref:System.AppDomain>.

## <a name="remarks"></a>Uwagi
 Ta metoda nie jest bezpieczny dla wątków i nie należy jej używać równocześnie z innymi wystąpieniami <xref:System.Threading.Tasks.TaskScheduler>. Tę metodę można wywołać z debugera, tylko wtedy, gdy jest debugera wstrzymał inne wątki.

## <a name="see-also"></a>Zobacz także
- [TaskScheduler, klasa](../../extensibility/debugger/taskscheduler-class-internal-members.md)