---
title: IDebugProperty2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdd5b114e5b34b7c51b210f33d70d831f6188b06
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54921950"
---
# <a name="idebugproperty2"></a>IDebugProperty2
Ten interfejs reprezentuje właściwości ramki stosu, właściwości dokumentu programu lub niektóre inne właściwości. Właściwość jest zazwyczaj wynikiem oceny wyrażenia.  
  
> [!NOTE]
>  To wykorzystania "property" nie należy mylić z tej zmiennej składowej klasy, co oznacza, mimo że `IDebugProperty2` może reprezentować podmiot.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProperty2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 DE implementuje ten interfejs do reprezentowania określonego typu wartości. Na przykład wartość można wartość liczbową, w wyniku oceny wyrażenia kontekstu pamięci, służący do wyświetlania w pamięci lub Podaj listę rejestrów i ich wartości.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołaj [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) uzyskać ten interfejs, który reprezentuje wynik oceny. `IDebugExpression2::EvaluateAsync` zwraca ten interfejs, wysyłając [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) interfejs SDM, która z kolei wywołuje [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) można pobrać właściwości.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) zwraca ten interfejs umożliwia dokument skryptu skojarzone.  
  
 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) zwraca ten interfejs reprezentujący wartość zwracaną przez funkcję.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) zwraca reprezentują różne właściwości programu, np. nazwę lub w kontekście pamięci w tym interfejsie.  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) zwraca reprezentują różne właściwości ramki stosu, takie jak zmienne lokalne w tym interfejsie.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugProperty2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Wypełnia [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) strukturę, która opisuje właściwość, która.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Ustawia wartości właściwości z ciągu.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Ustawia wartość właściwości z wartości danego odwołania.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Wylicza element podrzędny elementu właściwości.|  
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Zwraca element nadrzędny właściwości.|  
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Zwraca właściwość, która opisuje właściwość najbardziej pochodnego właściwości.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Zwraca wartość bajty pamięci, wchodzących w skład wartości właściwości.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Zwraca kontekst pamięci dla wartości właściwości.|  
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Zwraca rozmiar w bajtach, wartość właściwości.|  
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Zwraca odwołanie do wartości tej właściwości.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Zwraca informacje rozszerzone właściwości.|  
  
## <a name="remarks"></a>Uwagi  
 Właściwość, reprezentowane przez `IDebugProperty2` interfejsu, można traktować jako wartość składającą się z nazwy, typu i adres. Bardziej ogólnie rzecz biorąc `IDebugProperty2` może reprezentować wszystkie elementy, które ma strukturę hierarchiczną, za pomocą elementów nadrzędnych i podrzędnych węzłów.  
  
 Właściwość jest zwykle przejściowe, trwających tylko tak długo, jak bieżącej ramki stosu, na przykład. Z drugiej strony, odwołanie, reprezentowane przez [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) interfejsu, jest dostępna tak długo, jak długo wartość pozostaje w pamięci.  
  
 Można użyć IDE `IDebugProperty2` interfejsu, aby umożliwić użytkownikom przeglądanie i modyfikowanie właściwości w czasie wykonywania.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)