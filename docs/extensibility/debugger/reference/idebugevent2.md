---
title: IDebugEvent2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ca850f06fa2c17bb6f7c6ccb0756ad2498c67b9d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53870167"
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
 Nagłówek: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Zdarzenia](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)