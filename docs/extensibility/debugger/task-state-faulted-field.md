---
description: Zadanie zostało ukończone z powodu nieobsługiwanego wyjątku.
title: TASK_STATE_FAULTED pola | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TASK_STATE_FAULTED field, Task class [.NET Framework debug engines]
ms.assetid: ced826ae-09a9-4acf-af00-a2343d396bb8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0a3e1bf4fe6a95bd55cf366d1f5b8f56d7ea9c05
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902842"
---
# <a name="task_state_faulted-field"></a>TASK_STATE_FAULTED pola
Zadanie zostało ukończone z powodu nieobsługiwanego wyjątku.

 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

 Ponieważ nie można uzyskać dostępu do tego wewnętrznego członka z .NET Framework, w języku CIL (Common Intermediate Language) znajduje się następująca składnia.

## <a name="syntax"></a>Składnia

```csharp
.field static assembly literal int32 TASK_STATE_FAULTED = int32(0x00400000)
```

## <a name="remarks"></a>Uwagi
 Jeśli pole [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) zawiera tę wartość, <xref:System.Threading.Tasks.Task.Status%2A> właściwość zwraca wartość <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName> .

## <a name="see-also"></a>Zobacz też
- [Task, klasa](../../extensibility/debugger/task-class-internal-members.md)
