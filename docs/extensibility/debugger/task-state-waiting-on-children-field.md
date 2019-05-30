---
title: Pole TASK_STATE_WAITING_ON_CHILDREN | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_WAITING_ON_CHILDREN field, Task class [.NET Framework debug engines]
ms.assetid: 6f26b098-84ad-4f6e-ba27-6136581ba630
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae7f7930161b07dc8aeb4f3ff8bfb506e9f6e737
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345391"
---
# <a name="taskstatewaitingonchildren-field"></a>Pole TASK_STATE_WAITING_ON_CHILDREN
Zadanie zostało zakończone, wykonywanie jej delegata i niejawnie Trwa oczekiwanie na ukończenie dołączonych zadań podrzędnych.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

 Ponieważ nie można uzyskać dostępu do tego elementu wewnętrznego z programu .NET Framework, następującej składni znajduje się w typowych Intermediate Language (CIL).

## <a name="syntax"></a>Składnia

```csharp
.field static assembly literal int32 TASK_STATE_WAITING_ON_CHILDREN = int32(0x01000000)
```

## <a name="remarks"></a>Uwagi
 Jeśli [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) pole zawiera wartość ta <xref:System.Threading.Tasks.Task.Status%2A> właściwość zwraca <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>.

## <a name="see-also"></a>Zobacz także
- [Task — klasa](../../extensibility/debugger/task-class-internal-members.md)