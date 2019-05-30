---
title: IDebugThreadDestroyEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThreadDestroyEvent2
helpviewer_keywords:
- IDebugThreadDestroyEvent2
ms.assetid: fca3f603-9432-457b-9ddd-8b0ec17da046
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b7d0d2990c5286a277164d58e74ec2d96fa176e7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319998"
---
# <a name="idebugthreaddestroyevent2"></a>IDebugThreadDestroyEvent2
Ten interfejs jest wysyłane przez aparat debugowania (DE) w celu Menedżer debugowania sesji (SDM), po uruchomieniu wątku do zakończenia.

## <a name="syntax"></a>Składnia

```
IDebugThreadDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE implementuje ten interfejs do raportu, który wątek została zakończona. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu. Używa SDM [QueryInterface](/cpp/atl/queryinterface) dostęp do `IDebugEvent2` interfejsu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 DE tworzy i wysyła tego obiektu zdarzenia do raportu, który wątek została zakończona. Zdarzenia są wysyłane przy użyciu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkcji wywołania zwrotnego, która jest dostarczana przez SDM, gdy jest on dołączony do debugowanego programu.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugThreadDestroyEvent2`.

|Metoda|Opis|
|------------|-----------------|
|[GetExitCode](../../../extensibility/debugger/reference/idebugthreaddestroyevent2-getexitcode.md)|Pobiera kod wyjścia wątku.|

## <a name="remarks"></a>Uwagi
 Program Visual Studio używa tego zdarzenia do zaktualizowania **wątków** okna.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)