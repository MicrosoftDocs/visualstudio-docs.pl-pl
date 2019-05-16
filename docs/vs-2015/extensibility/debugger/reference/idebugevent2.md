---
title: IDebugEvent2 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f663be5910b342a6adba5da0b84d7e0d80cacc10
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695415"
---
# <a name="idebugevent2"></a>IDebugEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs jest używany do komunikowania się krytyczne informacje debugowania, takie jak zatrzymywanie w punkcie przerwania i niekrytyczne informacje, takie jak komunikat debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) i portu niestandardowego dostawcy implementować ten interfejs dla tego samego obiektu, jak wszystkie inne interfejsy zdarzeń.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Przy użyciu interfejsu argumentu identyfikator (IID) do [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) lub [zdarzeń](../../../extensibility/debugger/reference/idebugportevents2-event.md), Menedżer debugowania sesji (SDM) wywołuje [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) na `IDebugEvent2` interfejs do uzyskiwania Interfejs odpowiedniego zdarzenia.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Zdarzenia](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
