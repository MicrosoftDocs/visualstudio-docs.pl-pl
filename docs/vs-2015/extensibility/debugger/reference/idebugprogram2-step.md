---
title: 'IDebugProgram2:: Step | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dd9d314865eb2051b67d7c127a6c5cc2395b1863
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387229"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Wykonuje krok.  
  
> [!NOTE]
> Ta metoda jest przestarzała. Zamiast tego użyj metody [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```csharp  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pThread`  
 podczas Obiekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , który reprezentuje poddany wątek.  
  
 `sk`  
 podczas Wartość z wyliczenia [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) , która określa rodzaj kroku.  
  
 `step`  
 podczas Wartość z wyliczenia [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) , która określa jednostkę kroku (na przykład przez instrukcję lub instrukcję).  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 W przypadku gdy istnieje jakakolwiek synchronizacja wątków lub komunikacja między wątkami, inne wątki w programie powinny być uruchamiane, gdy określony wątek działa.  
  
> [!WARNING]
> Nie wysyłaj zdarzenia zatrzymania ani bezpośredniego (synchronicznego) zdarzenia do [zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) podczas obsługi tego wywołania; w przeciwnym razie debuger może przestać odpowiadać.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Zdarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
