---
title: IDebugPropertyDestroyEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyDestroyEvent2
helpviewer_keywords:
- IDebugPropertyDestroyEvent2 interface
ms.assetid: 301b7a75-ecfa-46f1-9131-66cf3e4be147
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c2ab0bd3a0a4afcabb5ea04a6bea6ba20ff5c70
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56706174"
---
# <a name="idebugpropertydestroyevent2"></a>IDebugPropertyDestroyEvent2
Ten interfejs jest wysyłane przez aparat debugowania (DE) do Menedżer debugowania sesji (SDM) ma zostać zniszczone właściwość, która jest skojarzona z określonym dokumentem.

## <a name="syntax"></a>Składnia

```
IDebugPropertyDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE implementuje ten interfejs do zgłaszania właściwość została zniszczona. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu. Używa SDM [QueryInterface](/cpp/atl/queryinterface) dostęp do `IDebugEvent2` interfejsu. Ten interfejs jest implementowany, jeśli DE została wcześniej utworzona właściwość skojarzony ze skryptem; niszczenie właściwość usuwa skryptów skojarzonych z poziomu środowiska IDE.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 DE tworzy i wysyła tego obiektu zdarzenia do raportu, którego właściwość została zniszczona. Zdarzenia są wysyłane przy użyciu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkcji wywołania zwrotnego, która jest dostarczana przez SDM, gdy jest on dołączony do debugowanego programu.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugPropertyDestroyEvent2`.

|Metoda|Opis|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertydestroyevent2-getdebugproperty.md)|Pobiera właściwości, które mają zostać zniszczone.|

## <a name="remarks"></a>Uwagi
 Zobacz uwagi, na [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) Aby uzyskać szczegółowe informacje o tym, dlaczego korzysta z tych zdarzeń.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)