---
description: Delegat reprezentujący kod do wykonania w obiekcie System.Threading.Tasks.Task.
title: m_action pola | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- m_action field, Task class [.NET Framework debug engines]
ms.assetid: 201838c2-260d-4071-b6c3-f526874e19c9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 838494eb612ffaa18931e42227619b22bc297b4f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901477"
---
# <a name="m_action-field"></a>m_action pola
Delegat reprezentujący kod do wykonania w <xref:System.Threading.Tasks.Task> obiekcie .

 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

 Ponieważ nie można uzyskać dostępu do tego wewnętrznego członka z .NET Framework, w języku CIL (Common Intermediate Language) znajduje się następująca składnia.

## <a name="syntax"></a>Składnia

```csharp
.field assembly object m_action
```

## <a name="remarks"></a>Uwagi
 Jest to `action` parametr w <xref:System.Threading.Tasks.Task.%23ctor%2A> konstruktorze.

## <a name="see-also"></a>Zobacz też
- [Task, klasa](../../extensibility/debugger/task-class-internal-members.md)
