---
title: IDebugStepCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStepCompleteEvent2
helpviewer_keywords:
- IDebugStepCompleteEvent2 interface
ms.assetid: eba2b76e-f90d-486b-ae5c-c47f1b8ba2e5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 068f07fa9610ef3aea7e59002370cffb93264b6a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352027"
---
# <a name="idebugstepcompleteevent2"></a>IDebugStepCompleteEvent2
Ten interfejs jest wysyłane przez aparat debugowania (DE) w celu Menedżer debugowania sesji (SDM), po zakończeniu program debugowany, krok po kroku, Przekrocz nad lub poza wiersza kodu źródłowego lub instrukcji lub instrukcji krok.

## <a name="syntax"></a>Składnia

```
IDebugStepCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE implementuje ten interfejs do zgłaszania zakończenia operacji kroku. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu. Używa SDM [QueryInterface](/cpp/atl/queryinterface) dostęp do `IDebugEvent2` interfejsu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 DE tworzy i wysyła tego obiektu zdarzenia do zgłaszania zakończenia operacji kroku. Zdarzenia są wysyłane przy użyciu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkcji wywołania zwrotnego, która jest dostarczana przez SDM, gdy jest on dołączony do debugowanego programu.

## <a name="remarks"></a>Uwagi
 Po ukończeniu kroku debugowanego programu zostało wstrzymane raz, a IDE aktualizuje jego systemu windows.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)