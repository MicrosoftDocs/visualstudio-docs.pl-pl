---
description: Zadanie zakończyło wykonywanie delegata i nieoczekiwanie oczekuje na ukończenie dołączonych zadań podrzędnych.
title: TASK_STATE_WAITING_ON_CHILDREN pole | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_WAITING_ON_CHILDREN field, Task class [.NET Framework debug engines]
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1533ef28b32450d9b039c27e49ba655dddfd6ebe
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223210"
---
# <a name="task_state_waiting_on_children-field"></a>Pole TASK_STATE_WAITING_ON_CHILDREN
Zadanie zakończyło wykonywanie delegata i nieoczekiwanie oczekuje na ukończenie dołączonych zadań podrzędnych.

 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

 Ponieważ nie można uzyskać dostępu do tego wewnętrznego elementu członkowskiego z .NET Framework, następująca składnia jest dostępna w typowym języku pośrednim (CIL).

## <a name="syntax"></a>Składnia

```csharp
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)
```

## <a name="remarks"></a>Uwagi
 Jeśli pole [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) zawiera tę wartość, <xref:System.Threading.Tasks.Task.Status%2A> Właściwość zwraca <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>Zobacz też
- [Klasa zadania](../../extensibility/debugger/task-class-internal-members.md)
