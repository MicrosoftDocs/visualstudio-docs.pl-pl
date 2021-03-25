---
description: Obiekt reprezentujący dane, które będą używane przez tę akcję.
title: m_stateObject pole | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c2128073f47c76244a18e18005a431f9317686c3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054793"
---
# <a name="m_stateobject-field"></a>pole m_stateObject
Obiekt reprezentujący dane, które będą używane przez tę akcję.

 **Przestrzeń nazw:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Zestaw:** mscorlib (w *mscorlib.dll*)

 Ponieważ nie można uzyskać dostępu do tego wewnętrznego elementu członkowskiego z .NET Framework, następująca składnia jest dostępna w typowym języku pośrednim (CIL).

## <a name="syntax"></a>Składnia

```
.field assembly object m_stateObject
```

## <a name="remarks"></a>Uwagi
 Jest to `state` parametr w <xref:System.Threading.Tasks.Task.%23ctor%2A> konstruktorze. Jest to również pole zapasowe dla <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> właściwości.

## <a name="see-also"></a>Zobacz też
- [Klasa zadania](../../extensibility/debugger/task-class-internal-members.md)
