---
title: IDebugExpression2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 694db3cc5292f11f1718a51e31deec4a8e456b54
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325977"
---
# <a name="idebugexpression2"></a>IDebugExpression2
Ten interfejs reprezentuje gotową przeanalizowany wyrażenia wiązania i oceny.

## <a name="syntax"></a>Składnia

```
IDebugExpression2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs reprezentujący wyrażenie przeanalizowany, gotowy do obliczenia.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) zwraca ten interfejs. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) zwraca [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfejsu. Te interfejsy są dostępne tylko wtedy, gdy debugowanego została wstrzymana, a ramka stosu jest dostępna.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugExpression2`.

|Metoda|Opis|
|------------|-----------------|
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Oblicza wyrażenie asynchronicznie.|
|[Abort](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Kończy się obliczenia wyrażenia asynchroniczne.|
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Oblicza wyrażenie synchronicznie.|

## <a name="remarks"></a>Uwagi
 Gdy program został zatrzymany, Menedżer debugowania sesji (SDM) uzyskuje dostęp do ramki stosu z DE wywołaniem [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Następnie wywołuje SDM [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) można pobrać [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfejsu. Następuje po wywołaniu [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) utworzyć `IDebugExpression2` interfejs, który reprezentuje przeanalizowany gotowy do obliczenia wyrażenia.

 Wywołuje SDM, albo [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) lub [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) faktycznie obliczenia wyrażenia i zwraca wartości.

 W implementacji `IDebugExpressionContext2::ParseText`, DE korzysta z modelu COM `CoCreateInstance` funkcję, aby utworzyć wystąpienie ewaluatora wyrażeń i Uzyskaj [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) interfejsu (Zobacz przykład w `IDebugExpressionEvaluator` interfejsu). Następnie wywołuje DE [przeanalizować](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) uzyskać [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) interfejsu. Ten interfejs jest używany w implementacji `IDebugExpression2::EvaluateSync` i `IDebugExpression2::EvaluateAsync` przeprowadzenie oceny.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)