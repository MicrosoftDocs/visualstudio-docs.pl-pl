---
title: TASK_STATE_EXECUTED Field | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_EXECUTED field, Task class [.NET Framework debug engines]
ms.assetid: 75b8f9d0-b908-40d0-b109-70feaed2ab0c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 290404da17b5e66ab447003db966cdb74a9087f0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348371"
---
# <a name="taskstateexecuted-field"></a>Pole TASK_STATE_EXECUTED
Zadanie jest uruchomiony, ale nie została jeszcze zakończona.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w mscorlib.dll)

 Ponieważ nie można uzyskać dostępu do tego elementu wewnętrznego z programu .NET Framework, następującej składni znajduje się w typowych Intermediate Language (CIL).

## <a name="syntax"></a>Składnia

```csharp
.field static assembly literal int32 TASK_STATE_EXECUTED = int32(0x00020000)
```

## <a name="remarks"></a>Uwagi
 Jeśli [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) pole zawiera wartość ta <xref:System.Threading.Tasks.Task.Status%2A> właściwość zwraca <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.

## <a name="see-also"></a>Zobacz także
- [Task — klasa](../../extensibility/debugger/task-class-internal-members.md)