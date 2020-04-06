---
title: IDebugExpression2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2e23ad4f673e4e150ea677d993c5b36a4e386c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729689"
---
# <a name="idebugexpression2"></a>IDebugExpression2
Ten interfejs reprezentuje analizowane wyrażenie gotowe do powiązania i oceny.

## <a name="syntax"></a>Składnia

```
IDebugExpression2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania analizowane wyrażenie gotowe do oceny.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) zwraca ten interfejs. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) zwraca interfejs [IDebugExpressionContext2.](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) Te interfejsy są dostępne tylko wtedy, gdy program debugowany został wstrzymany i ramka stosu jest dostępna.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugExpression2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Ocenia to wyrażenie asynchronicznie.|
|[Przerwanie](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Kończy ocenę wyrażenia asynchronicznej.|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Ocenia to wyrażenie synchronicznie.|

## <a name="remarks"></a>Uwagi
 Po zatrzymaniu programu menedżer debugowania sesji (SDM) uzyskuje ramkę stosu z DE z wywołaniem [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Następnie SDM wywołuje [GetExpressionContext,](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) aby uzyskać interfejs [IDebugExpressionContext2.](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) Po tym następuje [wywołanie ParseText,](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) aby utworzyć `IDebugExpression2` interfejs, który reprezentuje analizowane wyrażenie gotowe do oceny.

 SDM wywołuje [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) faktycznie ocenić wyrażenie i produkcji wartości.

 W implementacji `IDebugExpressionContext2::ParseText`DE używa `CoCreateInstance` funkcji COM do tworzenia wystąpienia oceniającego wyrażenie i uzyskać interfejs [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) `IDebugExpressionEvaluator` (zobacz przykład w interfejsie). DE następnie wywołuje [Parse,](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) aby uzyskać interfejs [IDebugParsedExpression.](../../../extensibility/debugger/reference/idebugparsedexpression.md) Ten interfejs jest używany `IDebugExpression2::EvaluateSync` w `IDebugExpression2::EvaluateAsync` implementacji i do przeprowadzenia oceny.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)
