---
title: 'IDebugProcess3:: Step | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5069a40f4e3ea4b1fba74c8133a18b46f2b3f2d2
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386228"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Powoduje, że proces przechodzi krok po kroku jedną instrukcję lub instrukcję.  
  
> [!NOTE]
> Ta metoda powinna być używana zamiast [kroku](../../../extensibility/debugger/reference/idebugprogram2-step.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Step(  
   IDebugThread2* pThread,  
   STEPKIND       sk,  
   STEPUNIT       step,  
);  
```  
  
```csharp  
int Step(  
   IDebugThread2 pThread,   
   enum_STEPKIND sk,   
   enum_STEPUNIT step  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pThread`  
 podczas Obiekt [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) reprezentujący poddany wątek.  
  
 `sk`  
 podczas Jedna z wartości [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) .  
  
 `step`  
 podczas Jedna z wartości [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) .  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 W przypadku każdej synchronizacji wątków lub komunikacji między wątkami inne wątki w procesie powinny być uruchamiane, gdy określony wątek działa.  
  
 **Ostrzeżenie** Nie wysyłaj zdarzenia zatrzymania ani bezpośredniego (synchronicznego) zdarzenia do [zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) podczas obsługi tego wywołania; w przeciwnym razie debuger może przestać odpowiadać.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)   
 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)   
 [Zdarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
