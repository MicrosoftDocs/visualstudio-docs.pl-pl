---
description: Zadanie jest uruchomione, ale nie zostało jeszcze ukończone.
title: TASK_STATE_EXECUTED pola | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TASK_STATE_EXECUTED field, Task class [.NET Framework debug engines]
ms.assetid: 75b8f9d0-b908-40d0-b109-70feaed2ab0c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ca0d2f578cc4e20b71e562d5b82245995bfd2969
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902855"
---
# <a name="task_state_executed-field"></a>TASK_STATE_EXECUTED pola
Zadanie jest uruchomione, ale nie zostało jeszcze ukończone.

 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w mscorlib.dll)

 Ponieważ nie można uzyskać dostępu do tego wewnętrznego członka z .NET Framework, w języku CIL (Common Intermediate Language) znajduje się następująca składnia.

## <a name="syntax"></a>Składnia

```csharp
.field static assembly literal int32 TASK_STATE_EXECUTED = int32(0x00020000)
```

## <a name="remarks"></a>Uwagi
 Jeśli pole [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) zawiera tę wartość, właściwość <xref:System.Threading.Tasks.Task.Status%2A> zwraca wartość <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>Zobacz też
- [Task, klasa](../../extensibility/debugger/task-class-internal-members.md)
