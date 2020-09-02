---
title: 'IDebugPortEvents2:: Event | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 28738b94ecc711833a4e16204b20f64d88687fe5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188554"
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta metoda wysyła zdarzenia, które oznaczają tworzenie i niszczenie procesów i programów na porcie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Event(  
   IDebugCoreServer2* pServer,  
   IDebugPort2*       pPort,  
   IDebugProcess2*    pProcess,  
   IDebugProgram2*    pProgram,  
   IDebugEvent2*      pEvent,  
   REFIID             riidEvent  
);  
```  
  
```csharp  
int Event(  
   IDebugCoreServer2 pServer,   
   IDebugPort2       pPort,   
   IDebugProcess2    pProcess,   
   IDebugProgram2    pProgram,   
   IDebugEvent2      pEvent,   
   ref Guid          riidEvent  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pMachine`  
 podczas Obiekt [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) , który reprezentuje serwer debugowania (istnieje jeden dla każdego wystąpienia [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ), w którym wystąpiło zdarzenie.  
  
 `pPort`  
 podczas Obiekt [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) , który reprezentuje port, w którym wystąpiło zdarzenie.  
  
 `pProcess`  
 podczas Obiekt [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , który reprezentuje proces, w którym wystąpiło zdarzenie.  
  
 `pProgram`  
 podczas Obiekt [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , który reprezentuje program, w którym wystąpiło zdarzenie.  
  
 `pEvent`  
 podczas Obiekt [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) , który identyfikuje zdarzenie. Możliwe są następujące zdarzenia:  
  
- [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)  
  
- [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)  
  
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)  
  
  `riidEvent`  
  podczas Identyfikator GUID zdarzenia. Ponieważ zdarzenie jest rzutowane do [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) przed wywołaniem tej metody, ten identyfikator ułatwia ustalenie, które zdarzenie jest wysyłane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
