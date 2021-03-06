---
description: Zadanie zostało ukończone pomyślnie.
title: TASK_STATE_RAN_TO_COMPLETION pole | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_RAN_TO_COMPLETION field, Task class [.NET Framework debug engines]
ms.assetid: 0f4830af-fe0c-4141-b768-817f4e426b8c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0f4963b257f5c53336660274da1a99736411c2e8
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223212"
---
# <a name="task_state_ran_to_completion-field"></a>Pole TASK_STATE_RAN_TO_COMPLETION
Zadanie zostało ukończone pomyślnie.

 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

 Ponieważ nie można uzyskać dostępu do tego wewnętrznego elementu członkowskiego z .NET Framework, następująca składnia jest dostępna w typowym języku pośrednim (CIL).

## <a name="syntax"></a>Składnia

```csharp
.field static assembly literal int32 TASK_STATE_RAN_TO_COMPLETION = int32(0x02000000)
```

## <a name="remarks"></a>Uwagi
 Jeśli pole [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) zawiera tę wartość, <xref:System.Threading.Tasks.Task.Status%2A> Właściwość zwraca <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>Zobacz też
- [Klasa zadania](../../extensibility/debugger/task-class-internal-members.md)
