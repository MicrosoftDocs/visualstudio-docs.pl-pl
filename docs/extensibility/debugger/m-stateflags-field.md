---
title: m_stateFlags pole | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateFlags field, Task class [.NET Framework debug engines]
ms.assetid: 82b20efc-08f2-4cd2-91f6-4e01e3da906b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c6e49ad2965ef99d5ceaafc3cb5f4de3589321d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925238"
---
# <a name="m_stateflags-field"></a>pole m_stateFlags
Przechowuje informacje o bieżącym stanie <xref:System.Threading.Tasks.Task> obiektu.

 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

 Ponieważ nie można uzyskać dostępu do tego wewnętrznego elementu członkowskiego z .NET Framework, następująca składnia jest dostępna w typowym języku pośrednim (CIL).

## <a name="syntax"></a>Składnia

```csharp
.field assembly int32 modreq(System.Runtime.CompilerServices.IsVolatile) m_stateFlags
```

## <a name="remarks"></a>Uwagi
 Zazwyczaj używasz właściwości, <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=fullName> Aby uzyskać dostęp do tej wartości.

 Ten element członkowski może być dowolną kombinacją następujących wartości:

- [TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)

- [TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)

- [TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)

- [TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)

- [TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)

## <a name="see-also"></a>Zobacz też
- [Klasa zadania](../../extensibility/debugger/task-class-internal-members.md)
