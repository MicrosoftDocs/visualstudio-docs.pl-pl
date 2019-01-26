---
title: IDebugExpression2::EvaluateAsync | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd01cb13b302269a3a6d91fda14713d8a1412a45
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070758"
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
Ta metoda oblicza wyrażenie asynchronicznie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EvaluateAsync (   
   EVALFLAGS             dwFlags,  
   IDebugEventCallback2* pExprCallback  
);  
```  
  
```csharp  
int EvaluateAsync(  
   enum_EVALFLAGS       dwFlags,   
   IDebugEventCallback2 pExprCallback  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFlags`  
 [in] Kombinacja flag z [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) wyliczenie, które sterują Obliczanie wyrażenia.  
  
 `pExprCallback`  
 [in] Ten parametr jest zawsze wartość null.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Kod typowy błąd to:  
  
|Błąd|Opis|  
|-----------|-----------------|  
|E_EVALUATE_BUSY_WITH_EVALUATION|Inne wyrażenie jest aktualnie szacowana, a jednoczesne wyrażenia nie jest obsługiwana.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda powinna zwracać natychmiast, po rozpoczęciu Obliczanie wyrażenia. Gdy pomyślnie jest obliczane wyrażenie, [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) muszą być wysyłane do [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) zdarzeń wywołania zwrotnego, ponieważ dostarczane za pośrednictwem [dołączania ](../../../extensibility/debugger/reference/idebugprogram2-attach.md) lub [dołączyć](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zaimplementować tę metodę dla prostego `CExpression` obiekt, który implementuje [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) interfejsu.  
  
```cpp  
HRESULT CExpression::EvaluateAsync(EVALFLAGS dwFlags,  
                                   IDebugEventCallback2* pExprCallback)  
{  
    // Set the aborted state to FALSE  
    // in case the user tries to redo the evaluation after aborting.  
    m_bAborted = FALSE;  
    // Post the WM_EVAL_EXPR message in the message queue of the current thread.  
    // This starts the expression evaluation on a background thread.  
    PostThreadMessage(GetCurrentThreadId(), WM_EVAL_EXPR, 0, (LPARAM) this);  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)