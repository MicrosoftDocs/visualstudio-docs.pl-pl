---
title: IDebugExpressionContext2 | Microsoft Docs
description: Ten interfejs reprezentuje kontekst oceny wyrażenia
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6d8745207f1ab075aedd43815e7a97a4f0721bb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092296"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
Ten interfejs reprezentuje kontekst oceny wyrażenia.

## <a name="syntax"></a>Składnia

```
IDebugExpressionContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs, aby reprezentować kontekst, w którym można obliczyć wyrażenie.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) zwraca ten interfejs. Ten interfejs jest dostępny tylko wtedy, gdy debugowany program został wstrzymany i jest dostępna Ramka stosu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugExpressionContext2` .

|Metoda|Opis|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|Pobiera nazwę kontekstu oceny.|
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Analizuje wyrażenie tekstowe na potrzeby oceny.|

## <a name="remarks"></a>Uwagi
 Kontekst oceny można traktować jako zakres do wykonywania obliczeń wyrażeń.

 Gdy program został zatrzymany, Menedżer debugowania sesji (SDM) uzyskuje ramkę stosu od DE z wywołaniem do [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Model SDM następnie wywołuje [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) , aby uzyskać `IDebugExpressionContext2` interfejs. Następuje wywołanie [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) w celu utworzenia interfejsu [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) , który reprezentuje wyrażenie analizowane gotowe do oceny.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
