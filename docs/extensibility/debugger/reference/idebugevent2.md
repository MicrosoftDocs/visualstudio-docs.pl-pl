---
description: Ten interfejs jest używany do przekazywania zarówno krytycznych informacji debugowania, takich jak zatrzymywanie w punkcie przerwania, jak i informacje niekrytyczne, takie jak komunikat debugowania.
title: IDebugEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f5406c70703b594236dba47539e5cc76bbe67a73
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065765"
---
# <a name="idebugevent2"></a>IDebugEvent2
Ten interfejs jest używany do przekazywania zarówno krytycznych informacji debugowania, takich jak zatrzymywanie w punkcie przerwania, jak i informacje niekrytyczne, takie jak komunikat debugowania.

## <a name="syntax"></a>Składnia

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) i dostawca portu niestandardowego implementują ten interfejs na tym samym obiekcie co wszystkie inne interfejsy zdarzeń.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Przy użyciu argumentu identyfikatora interfejsu (IID) dla [zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) lub [zdarzenia](../../../extensibility/debugger/reference/idebugportevents2-event.md), Menedżer debugowania sesji (SDM) wywołuje polecenie [QueryInterface](/cpp/atl/queryinterface) w `IDebugEvent2` interfejsie, aby uzyskać odpowiedni interfejs zdarzenia.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugEvent2` .

|Metoda|Opis|
|------------|-----------------|
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Pobiera atrybuty dla tego zdarzenia debugowania.|

## <a name="remarks"></a>Uwagi
 Bardziej specyficzne interfejsy zdarzeń, takie jak [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), nie pochodzą z interfejsu IDebugEvent2, ale zamiast tego są implementowane jako osobny interfejs w tym samym obiekcie co `IDebugEvent2` .

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [Zdarzenie](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Zdarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
