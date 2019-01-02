---
title: IDebugEventCallback2::Event | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEventCallback2::Event
helpviewer_keywords:
- IDebugEventCallback2::Event
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ca9ac17147604dda52e7446d6a97c90dad155ca6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53892692"
---
# <a name="idebugeventcallback2event"></a>IDebugEventCallback2::Event
Wysyła powiadomienia o zdarzeniach debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Event(   
   IDebugEngine2*  pEngine,  
   IDebugProcess2* pProcess,  
   IDebugProgram2* pProgram,  
   IDebugThread2*  pThread,  
   IDebugEvent2*   pEvent,  
   REFIID          riidEvent,  
   DWORD           dwAttrib  
);  
```  
  
```csharp  
int Event(   
   IDebugEngine2  pEngine,  
   IDebugProcess2 pProcess,  
   IDebugProgram2 pProgram,  
   IDebugThread2  pThread,  
   IDebugEvent2   pEvent,  
   ref Guid       riidEvent,  
   uint           dwAttrib  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pEngine`  
 [in] [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) obiekt, który reprezentuje aparat debugowania (DE), która wysyła tego zdarzenia. DE jest wymagany do wypełnienia tego parametru.  
  
 `pProcess`  
 [in] [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) obiekt, który reprezentuje proces, w której występuje zdarzenie. Ten parametr jest wypełniane przez Menedżer debugowania sesji (SDM). DE zawsze przekazuje wartość null dla tego parametru.  
  
 `pProgram`  
 [in] [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) obiekt, który reprezentuje program, w którym to zdarzenie występuje. W przypadku większości zdarzeń ten parametr nie jest wartością null.  
  
 `pThread`  
 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt, który reprezentuje wątek, w którym to zdarzenie występuje. Dla zdarzeniami zatrzymującymi, ten parametr nie może być wartością null jako ramka stosu jest uzyskiwana z tego parametru.  
  
 `pEvent`  
 [in] [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) obiekt, który reprezentuje zdarzenie debugowania.  
  
 `riidEvent`  
 [in] Identyfikator GUID, który identyfikuje interfejs zdarzenia, które można uzyskać z `pEvent` parametru.  
  
 `dwAttrib`  
 [in] Kombinacja flag z [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) wyliczenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Po wywołaniu tej metody `dwAttrib` parametru musi być zgodna wartość zwracana z [GetAttributes —](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) przekazanego do metody, nazywane obiektu zdarzenia `pEvent` parametru.  
  
 Wszystkie zdarzenia debugowania są ogłaszane asynchronicznie, niezależnie od tego, czy samego zdarzenia jest asynchroniczne, czy nie. Gdy DE wywołuje tę metodę, zwracana wartość nie wskazuje, czy zdarzenie zostało przetworzone, tylko, czy odebrano zdarzenie. W rzeczywistości w większości przypadków zdarzenie nie zostało przetworzone po powrocie z tej metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)