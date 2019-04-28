---
title: Pole m_action | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_action field, Task class [.NET Framework debug engines]
ms.assetid: 201838c2-260d-4071-b6c3-f526874e19c9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3911ad0eee59a8b6c34ecaef73df3b5d7eeff88
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925391"
---
# <a name="maction-field"></a>pole m_action
Delegat, który reprezentuje kod do wykonania w <xref:System.Threading.Tasks.Task> obiektu.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

 Ponieważ nie można uzyskać dostępu do tego elementu wewnętrznego z programu .NET Framework, następującej składni znajduje się w typowych Intermediate Language (CIL).

## <a name="syntax"></a>Składnia

```csharp
.field assembly object m_action
```

## <a name="remarks"></a>Uwagi
 Jest to `action` parametru w <xref:System.Threading.Tasks.Task.%23ctor%2A> konstruktora.

## <a name="see-also"></a>Zobacz także
- [Task — klasa](../../extensibility/debugger/task-class-internal-members.md)