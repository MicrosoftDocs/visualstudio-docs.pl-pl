---
title: Pole m_action | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_action field, Task class [.NET Framework debug engines]
ms.assetid: 201838c2-260d-4071-b6c3-f526874e19c9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d33d356f606dc2622647de53b50f5c677b3c14eb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330980"
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