---
title: IDebugPendingBreakpoint2::GetState | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2::GetState
helpviewer_keywords:
- GetState method
- IDebugPendingBreakpoint2::GetState method
ms.assetid: e88d543f-2e83-4ba7-86ca-f874e39955ff
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c630a22c0e5f5e16060b8399bc5ae2ae0ba62346
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006844"
---
# <a name="idebugpendingbreakpoint2getstate"></a>IDebugPendingBreakpoint2::GetState
Pobiera stan oczekujący punkt przerwania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetState(   
   PENDING_BP_STATE_INFO* pState  
);  
```  
  
```csharp  
int GetState(   
   PENDING_BP_STATE_INFO[] pState  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pState`  
 [out w] A [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) strukturę, która jest wypełniane opis oczekujących punktów przerwania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)