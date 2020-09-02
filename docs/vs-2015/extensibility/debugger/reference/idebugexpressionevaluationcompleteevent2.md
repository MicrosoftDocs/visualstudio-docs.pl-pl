---
title: IDebugExpressionEvaluationCompleteEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7692a06004a1f9d31a31f91c081c6168d89a8dc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65694390"
---
# <a name="idebugexpressionevaluationcompleteevent2"></a>IDebugExpressionEvaluationCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs jest wysyłany przez aparat debugowania (DE) do Menedżera debugowania sesji (SDM), gdy Obliczanie wyrażenia asynchronicznego zostało zakończone.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugExpressionEvaluationCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Element DE implementuje ten interfejs, aby zgłosić ukończenie obliczania wyrażenia uruchomionego przez wywołanie do [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany w tym samym obiekcie co ten interfejs. Model SDM używa [metody QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) do uzyskiwania dostępu do `IDebugEvent2` interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Element DE tworzy i wysyła ten obiekt Event, aby zgłosić zakończenie obliczania wyrażenia. Zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , która jest dostarczana przez model SDM, gdy jest dołączona do debugowanego programu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 W poniższej tabeli przedstawiono metody `IDebugExpressionEvaluationCompleteEvent2` .  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|Pobiera oryginalne wyrażenie.|  
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|Pobiera wynik oceny wyrażenia.|  
  
## <a name="remarks"></a>Uwagi  
 DE musi wysłać to zdarzenie, niezależnie od tego, czy Ocena zakończyła się powodzeniem, czy nie.  
  
 Jeśli Ocena zakończyła się niepowodzeniem `DEBUG_PROPINFO_VALUE` , `DEBUG_PROPINFO_ATTRIB` flagi i nie zostaną ustawione w strukturze [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) , która jest zwracana przez [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (obiekt [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) jest tworzony przez de i zwraca w `IDebugExpressionEvaluationCompleteEvent2` zdarzeniu, jeśli szacowanie nie powiodło się).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
