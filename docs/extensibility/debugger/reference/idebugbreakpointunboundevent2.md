---
title: IDebugBreakpointUnboundEvent2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointUnboundEvent2
helpviewer_keywords:
- IDebugBreakpointUnboundEvent2
ms.assetid: 6b1e1863-0c64-4d85-8ab9-aface522fdea
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14a16080424ae19e909751a797a49192a22e645d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54947871"
---
# <a name="idebugbreakpointunboundevent2"></a>IDebugBreakpointUnboundEvent2
Ten interfejs informuje Menedżer debugowania sesji (SDM), czy powiązany punkt przerwania został niezwiązanej z załadowanych programu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugBreakpointUnboundEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs jako część jego obsługę punktów przerwania. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu (SDM używa [QueryInterface](/cpp/atl/queryinterface) dostęp do `IDebugEvent2` interfejsu).  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 DE tworzy i wysyła tego obiektu zdarzenia, gdy powiązany punkt przerwania został niepowiązanej. Zdarzenia są wysyłane przy użyciu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkcji wywołania zwrotnego dostarczonych przez model SDM, gdy jest on dołączony do debugowanego programu.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugBreakpointUnboundEvent2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)|Pobiera punkt przerwania, które stały się niepowiązanych.|  
|[GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)|Pobiera powodów, dla którego punkt przerwania został niepowiązanej.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy zwalnia aparat debugowania, biblioteki DLL lub klasy, wszystkie punkty przerwania, które były powiązane z kodu w module musi być niezwiązanej z debugowanego programu. `IDebugBreakpointUnboundEvent2` Jest wysyłana dla każdego niepowiązanych punktu przerwania.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)