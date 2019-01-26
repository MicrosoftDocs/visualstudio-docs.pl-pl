---
title: IDebugBreakpointResolution2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointResolution2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 451d5bce-b9c1-48ff-beaa-2b4c3e1ceea0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28a38631f9f1a18b5c104df60baa846ee49330d0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54931378"
---
# <a name="idebugbreakpointresolution2"></a>IDebugBreakpointResolution2
Ten interfejs reprezentuje informacje opisujące powiązany punkt przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugBreakpointResolution2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs jako część jego obsługę punktów przerwania. Ten interfejs zawiera opis powiązany punkt przerwania, który używa Menedżer debugowania sesji, gdy użytkownik przegląda właściwości punktu przerwania.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Wywołanie [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) zwraca ten interfejs.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugBreakpointResolution2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Pobiera typ punktu przerwania reprezentowany przez to rozwiązanie.|  
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Pobiera informacje o rozdzielczości punkt przerwania, opisujący tego punktu przerwania.|  
  
## <a name="requirements"></a>Wymagania  
 Header: msdbg.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)