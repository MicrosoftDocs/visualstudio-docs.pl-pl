---
description: Ta metoda anuluje obliczanie wyrażeń asynchronicznych jako rozpoczęte przez wywołanie metody EvaluateAsync).
title: 'IDebugExpression2:: Abort | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d6c355d2c4ee3cf63551f54b050b0ea42f4fdddc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092452"
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
Ta metoda anuluje obliczanie wyrażeń asynchronicznych jako rozpoczęte przez wywołanie metody [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) .

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
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Gdy szacowanie wyrażeń asynchronicznych zostało anulowane, nie wysyłaj zdarzenia [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) do wywołania zwrotnego zdarzenia przekazywanego do metody [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) lub [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .

## <a name="see-also"></a>Zobacz też
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
