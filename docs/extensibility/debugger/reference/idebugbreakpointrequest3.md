---
title: IDebugBreakpointRequest3 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26a5a69094c320ed105137de24b809d3163bdba9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54955183"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Ten interfejs reprezentuje informacje niezbędne do tworzenia i powiązać dowolnego typu punktu przerwania. To rozszerzenie [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugBreakpointRequest3 : IDebugBreakpointRequest2  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Menedżer debugowania sesji (SDM) zwykle implementuje ten interfejs.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Aparat debugowania (DE) uzyskuje dostęp do tego interfejsu, wywołując [QueryInterface](/cpp/atl/queryinterface) interfejsu IDebugBreakpointRequest2 odebrane w wywołaniu [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 Oprócz metod odziedziczone [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md), `IDebugBreakpointRequest3` interfejsu udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Pobiera informacje o żądaniu punktu przerwania, opisujący tego żądania punktu przerwania.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest używany do dostarczania informacji dodatkowych DE za pośrednictwem [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) struktury. Te dodatkowe informacje zawiera identyfikator dostawcy DE (w postaci identyfikatora GUID), nazwę punktu śledzenia i nazwa ograniczenia punktu przerwania.  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)