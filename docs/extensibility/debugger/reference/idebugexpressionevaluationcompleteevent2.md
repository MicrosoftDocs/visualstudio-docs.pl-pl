---
title: IDebugExpressionEvaluationCompleteEvent2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d56671d3e0edecde7d67937e07b70cab335efefe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53963408"
---
# <a name="idebugexpressionevaluationcompleteevent2"></a>IDebugExpressionEvaluationCompleteEvent2
Ten interfejs jest wysyłane przez aparat debugowania (DE) w celu Menedżer debugowania sesji (SDM), po zakończeniu oceny wyrażenia asynchroniczne.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugExpressionEvaluationCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 DE implementuje ten interfejs do zakończenia raportu oceny wyrażenia uruchomione przez wywołanie do [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu. Używa SDM [QueryInterface](/cpp/atl/queryinterface) dostęp do `IDebugEvent2` interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 DE tworzy i wysyła tego obiektu zdarzenia do raportowania zakończenia Obliczanie wyrażenia. Zdarzenia są wysyłane przy użyciu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkcji wywołania zwrotnego, która jest dostarczana przez SDM, gdy jest on dołączony do debugowanego programu.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugExpressionEvaluationCompleteEvent2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|Pobiera oryginalne wyrażenie.|  
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|Pobiera wynik obliczania wyrażenia.|  
  
## <a name="remarks"></a>Uwagi  
 DE musi wysłać to zdarzenie, czy ocena zakończyła się powodzeniem.  
  
 Jeśli ocena zakończyła się niepowodzeniem, `DEBUG_PROPINFO_VALUE` i `DEBUG_PROPINFO_ATTRIB` nie będzie można ustawić flagi [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) strukturę, która jest zwracana przez [getpropertyinfo —](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) ( [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiekt jest tworzony przez DE i zwracane w `IDebugExpressionEvaluationCompleteEvent2` zdarzeń, jeśli oceny nie powiodła się).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)