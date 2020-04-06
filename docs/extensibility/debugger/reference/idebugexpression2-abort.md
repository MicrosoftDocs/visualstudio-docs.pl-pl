---
title: IDebugExpression2::Przerwanie | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5de2e34a8ae1e038c2109627099dacc5bd03a1ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729770"
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
Ta metoda anuluje ocenę wyrażenia asynchronicznego, jak rozpoczęto wywołanie [metody EvaluateAsync.](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)

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
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Gdy ocena wyrażenia asynchronicznej zostanie anulowana, nie wysyłaj zdarzenia [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) do wywołania zwrotnego zdarzenia [przekazanego](../../../extensibility/debugger/reference/idebugprogram2-attach.md) do metody Dołączanie lub [Dołączanie.](../../../extensibility/debugger/reference/idebugengine2-attach.md)

## <a name="see-also"></a>Zobacz też
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
