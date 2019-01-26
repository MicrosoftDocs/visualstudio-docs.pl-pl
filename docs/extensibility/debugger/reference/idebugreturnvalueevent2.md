---
title: IDebugReturnValueEvent2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugReturnValueEvent2
helpviewer_keywords:
- IDebugReturnValueEvent2
ms.assetid: 2daded43-e427-4fbb-a19e-f3834e3723af
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ade206415b59f1de15427b929855f982bc5466d5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54947039"
---
# <a name="idebugreturnvalueevent2"></a>IDebugReturnValueEvent2
Ten interfejs jest wysyłane przez aparat debugowania (DE) do Menedżer debugowania sesji (SDM) po przejściu z lub funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugReturnValueEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 DE implementuje ten interfejs, aby zgłosić wartość zwrócona przez funkcję, która ma zmieniana poza lub za pośrednictwem. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu. Używa SDM [QueryInterface](/cpp/atl/queryinterface) dostęp do `IDebugEvent2` interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 DE tworzy i wysyła tego obiektu zdarzeń, aby zgłosić wartość zwracaną przez funkcję. Zdarzenia są wysyłane przy użyciu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkcji wywołania zwrotnego, która jest dostarczana przez SDM, gdy jest on dołączony do debugowanego programu.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugReturnValueEvent2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)|Pobiera wartość zwracana na przechodzenie krok po kroku z funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 Wartość zwrócona przez funkcję można uzyskać przez wywołanie metody [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md). Wartość zwracana jest wyświetlana w **Autos** okna.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)