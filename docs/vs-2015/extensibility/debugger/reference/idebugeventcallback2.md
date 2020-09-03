---
title: IDebugEventCallback2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6114a31701e5abc4714f315b4e4f1ecf022c401c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163823"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs jest używany przez aparat debugowania (DE) do wysyłania zdarzeń debugowania do Menedżera debugowania sesji (SDM).  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] implementuje ten interfejs, aby odbierać zdarzenia z aparatu debugowania.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Aparat debugowania zazwyczaj otrzymuje ten interfejs, gdy wywołania SDM [dołączają](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [dołączają](../../../extensibility/debugger/reference/idebugengine2-attach.md)lub [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Aparat debugowania wysyła zdarzenia do modelu SDM przez wywołanie [zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych  
 W poniższej tabeli przedstawiono metody `IDebugEventCallback2` .  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Zdarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Wysyła powiadomienie o zdarzeniach debugowania do modelu SDM.|  
  
## <a name="remarks"></a>Uwagi  
 Mimo że [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) i [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) określają, że przyjmują `IDebugEventCallback2` interfejs, nie jest to przypadek, a wskaźnik interfejsu zawsze będzie wartością null. Zamiast tego aparat debugowania musi używać `IDebugEventCallback2` interfejsu otrzymanego w wywołaniu metody [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)lub [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Jeśli pakiet implementuje [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) w kodzie zarządzanym, stanowczo zaleca się <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> wywoływanie różnych interfejsów, które są przesyłane do [zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg. h  
  
 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Klej](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md)
