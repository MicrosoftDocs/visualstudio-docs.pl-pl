---
description: Obiekt reprezentujący dane, które będą używane przez tę akcję.
title: m_stateObject pole | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 92fdad68506c62440c7f3e130caee49b4fe780da
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158764"
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
