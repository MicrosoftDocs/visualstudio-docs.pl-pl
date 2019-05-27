---
title: IDebugExpressionEvaluationCompleteEvent2::GetExpression | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetExpression
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetExpression
ms.assetid: faf6b2dd-2afd-4852-b21c-7e8d3130e141
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bdab9bc2f3d7a9d408e43d06996262bb5bc1a3f5
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66201021"
---
# <a name="idebugexpressionevaluationcompleteevent2getexpression"></a>IDebugExpressionEvaluationCompleteEvent2::GetExpression
Pobiera oryginalne wyrażenie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetExpression( 
   IDebugExpression2** ppExpr
);
```

```csharp
int GetExpression( 
   out IDebugExpression2 ppExpr
);
```

## <a name="parameters"></a>Parametry
`ppExpr`\
[out] Zwraca [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) obiekt, który reprezentuje wyrażenie, które zostanie przeanalizowany.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda zwraca obiekt, który został utworzony w wywołaniu [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) metody.

## <a name="see-also"></a>Zobacz także
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)