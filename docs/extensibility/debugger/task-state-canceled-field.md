---
title: pole TASK_STATE_CANCELED | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TASK_STATE_CANCELED field, Task class [.NET Framework debug engines]
ms.assetid: f4f5a96a-8230-493d-9696-8d2716bda261
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d59335a418febef45ebe35d4590c72b486921639
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712746"
---
# <a name="task_state_canceled-field"></a>Pole TASK_STATE_CANCELED
Zadanie zostało anulowane przed osiągnięciem stanu uruchomionego lub potwierdziło jego anulowanie i zostało ukończone bez wyjątku.

 **Obszar nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montaż:** mscorlib (w mscorlib.dll)

 Ponieważ nie można uzyskać dostępu do tego wewnętrznego elementu członkowskiego z programu .NET Framework, następująca składnia znajduje się we wspólnym języku pośrednim (CIL).

## <a name="syntax"></a>Składnia

```csharp
.field static assembly literal int32 TASK_STATE_CANCELED = int32(0x00800000)
```

## <a name="remarks"></a>Uwagi
 Jeśli pole [m_stateFlags](../../extensibility/debugger/m-stateflags-field.md) zawiera tę wartość, <xref:System.Threading.Tasks.Task.Status%2A> właściwość zwraca . <xref:System.Threading.Tasks.TaskStatus?displayProperty=fullName>

## <a name="see-also"></a>Zobacz też
- [Klasa zadań](../../extensibility/debugger/task-class-internal-members.md)
