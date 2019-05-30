---
title: IDebugEvent2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f87184481c5d01e74d284b175078b67f6f2612d1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310599"
---
# <a name="idebugevent2"></a>IDebugEvent2
Ten interfejs jest używany do komunikowania się krytyczne informacje debugowania, takie jak zatrzymywanie w punkcie przerwania i niekrytyczne informacje, takie jak komunikat debugowania.

## <a name="syntax"></a>Składnia

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) i portu niestandardowego dostawcy implementować ten interfejs dla tego samego obiektu, jak wszystkie inne interfejsy zdarzeń.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Przy użyciu interfejsu argumentu identyfikator (IID) do [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) lub [zdarzeń](../../../extensibility/debugger/reference/idebugportevents2-event.md), Menedżer debugowania sesji (SDM) wywołuje [QueryInterface](/cpp/atl/queryinterface) na `IDebugEvent2` interfejs do uzyskiwania Interfejs odpowiedniego zdarzenia.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugEvent2`.

|Metoda|Opis|
|------------|-----------------|
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Pobiera atrybuty dla tego zdarzenia debugowania.|

## <a name="remarks"></a>Uwagi
 Interfejsy bardziej określonego zdarzenia, takie jak [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), pochodzi z interfejsu IDebugEvent2, ale zamiast tego są implementowane jako oddzielny interfejs na ten sam obiekt jako `IDebugEvent2`.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)