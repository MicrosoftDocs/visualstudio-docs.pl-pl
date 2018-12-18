---
title: IDebugEventCallback2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2c1e0f6425b6c466d54b6ed24bace0e406e7035d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792102"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ten interfejs jest używany przez aparat debugowania (DE), aby wysyłać zdarzenia debugowania Menedżer debugowania sesji (SDM).  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] implementuje ten interfejs, aby odbierać zdarzenia z aparatu debugowania.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Aparat debugowania zazwyczaj otrzymuje ten interfejs, gdy wywołuje SDM [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md), lub [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Aparat debugowania wysyła zdarzenia do SDM, wywołując [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugEventCallback2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Wysyła powiadomienie debugowania zdarzeń SDM.|  
  
## <a name="remarks"></a>Uwagi  
 Mimo że [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) i [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) Określ, czy przyjmują `IDebugEventCallback2` interfejsu, nie jest to i wskaźnik interfejsu będzie zawsze wartość null. Zamiast tego należy użyć aparatu debugowania `IDebugEventCallback2` interfejsu odebrane w wywołaniu [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md), lub [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Jeśli pakiet implementuje [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) w kodzie zarządzanym zdecydowanie zalecane jest, <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> wywołana na różnych interfejsów, które są przekazywane do [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Dołącz](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)

