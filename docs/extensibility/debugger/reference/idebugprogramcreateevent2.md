---
title: IDebugProgramCreateEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramCreateEvent2
helpviewer_keywords:
- IDebugProgramCreateEvent2 interface
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8081e05d18719af060ddf58045c06ec64036ae35
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331451"
---
# <a name="idebugprogramcreateevent2"></a>IDebugProgramCreateEvent2
Ten interfejs jest wysyłane przez aparat debugowania (DE) w celu Menedżer debugowania sesji (SDM), gdy program jest dołączony do.

## <a name="syntax"></a>Składnia

```
IDebugProgramCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE lub dostawcę, port niestandardowy implementuje raportu, czy program została utworzona, zwykle w czasie, który program jest dołączony do tego interfejsu. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu. Używa SDM `QueryInterface` metody w celu uzyskania dostępu do `IDebugEvent2` interfejsu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 DE lub dostawcę, port niestandardowy, tworzy i wysyła tego obiektu zdarzenia w celu tworzenia programu raportów. DE wysyła tego zdarzenia przy użyciu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkcji wywołania zwrotnego, która jest dostarczana przez SDM, gdy jest on dołączony do debugowanego programu. Dostawca numery portów wysyła tego zdarzenia przy użyciu [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) interfejsu.

## <a name="remarks"></a>Uwagi
 DE lub portu niestandardowego dostawcy publikuje nową [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) interfejsu, wywołując [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)