---
title: IDebugExpression2::Abort | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 668b4fe87bb0c37796d63cb313c15d146c70a58e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910597"
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
Ta metoda anuluje Obliczanie wyrażenia asynchroniczne jako uruchomione przez wywołanie do [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Abort(  
   void  
);  
```  
  
```csharp  
int Abort();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Po anulowaniu Obliczanie wyrażenia asynchroniczne niewysłane [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) zdarzenia w celu wywołania zwrotnego zdarzenia przekazane do [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) lub [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)