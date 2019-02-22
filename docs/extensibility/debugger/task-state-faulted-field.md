---
title: Pole TASK_STATE_FAULTED | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_FAULTED field, Task class [.NET Framework debug engines]
ms.assetid: ced826ae-09a9-4acf-af00-a2343d396bb8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b877d7370396db4653ff9af81a5654f2d357522
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56692726"
---
# <a name="taskstatefaulted-field"></a>Pole TASK_STATE_FAULTED
Zadanie zakończone z powodu nieobsługiwanego wyjątku.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

 Ponieważ nie można uzyskać dostępu do tego elementu wewnętrznego z programu .NET Framework, następującej składni znajduje się w typowych Intermediate Language (CIL).

## <a name="syntax"></a>Składnia

```csharp
.field static assembly literal int32 TASK_STATE_FAULTED = int32(0x00400000)
```

## <a name="remarks"></a>Uwagi
 Jeśli [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) pole zawiera wartość ta <xref:System.Threading.Tasks.Task.Status%2A> właściwość zwraca <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.

## <a name="see-also"></a>Zobacz także
- [Task — klasa](../../extensibility/debugger/task-class-internal-members.md)