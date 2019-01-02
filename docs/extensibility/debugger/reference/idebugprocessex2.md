---
title: IDebugProcessEx2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e331702c98656fd0bee31c1b6e1a130fe2c30f77
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53962837"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Ten interfejs umożliwia sesji debugowania manager (SDM) powiadamiać procesu, który jest dołączenie do lub odłączenie od procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Dostawcy niestandardowego portu implementuje ten interfejs na ten sam obiekt jako [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) interfejs w celu:  
  
- Obsługa śledzenia sesji podłączony do procesu  
  
- Obsługa automatyczne dołączanie w wielu aparatów debugowania  
  
  Dostawca numery portów mogą implementować ten interfejs, jeśli go wybierze.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
  
-   Wywołania SDM [QueryInterface](/cpp/atl/queryinterface) na `IDebugProcess2` interfejsu w celu uzyskania tego interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugProcessEx2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informuje proces, że sesja jest teraz debugowanie procesu.|  
|[Detach](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informuje proces, czy sesja jest już debugowanie procesu.|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Dodaje węzły programu, aby uzyskać listę aparaty debugowania.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest prywatny między SDM i procesu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Portpriv.h  
  
 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)