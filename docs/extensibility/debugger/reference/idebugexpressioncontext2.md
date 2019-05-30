---
title: IDebugExpressionContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3ad9c3d6bb1b0a5baccbcf5bf47eb02a8bb5efa5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325852"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
Ten interfejs reprezentuje kontekstu oceny wyrażenia

## <a name="syntax"></a>Składnia

```
IDebugExpressionContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania kontekst, w którym można obliczyć wyrażenia.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) zwraca tego interfejsu. Ten interfejs jest dostępny tylko wtedy, gdy debugowanego została wstrzymana, a ramka stosu jest dostępna.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugExpressionContext2`.

|Metoda|Opis|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|Pobiera nazwę kontekst oceny.|
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Analizuje oparte na tekście wyrażenie do oceny.|

## <a name="remarks"></a>Uwagi
 Kontekst oceny można traktować jako zakres do wykonywania oceny wyrażenia.

 Gdy program został zatrzymany, Menedżer debugowania sesji (SDM) uzyskuje dostęp do ramki stosu z DE wywołaniem [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Następnie wywołuje SDM [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) można pobrać `IDebugExpressionContext2` interfejsu. Następuje po wywołaniu [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) utworzyć [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) interfejs, który reprezentuje przeanalizowany gotowy do obliczenia wyrażenia.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)