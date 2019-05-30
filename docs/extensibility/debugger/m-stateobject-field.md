---
title: Pole m_stateObject | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95947a1367ea1ddf4aa88689f731971d5c7d0a6c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330836"
---
# <a name="mstateobject-field"></a>m_stateObject field
Obiekt, który reprezentuje dane, które będzie używane przez akcję.

 **Namespace:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

 Ponieważ nie można uzyskać dostępu do tego elementu wewnętrznego z programu .NET Framework, następującej składni znajduje się w typowych Intermediate Language (CIL).

## <a name="syntax"></a>Składnia

```
.field assembly object m_stateObject
```

## <a name="remarks"></a>Uwagi
 Jest to `state` parametru w <xref:System.Threading.Tasks.Task.%23ctor%2A> konstruktora. Warto również pole zapasowe dla <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> właściwości.

## <a name="see-also"></a>Zobacz także
- [Task — klasa](../../extensibility/debugger/task-class-internal-members.md)