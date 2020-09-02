---
title: IDebugExpressionContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 344ae287b3784ceca87fbbab09ad2b2e0a304205
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729639"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
Ten interfejs reprezentuje kontekst oceny wyrażenia

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
