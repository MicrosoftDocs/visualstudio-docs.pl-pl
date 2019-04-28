---
title: IDebugExpression2::Abort | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 490c131820cbe16b8e18be649ad5439c024ad3c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62874248"
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
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)