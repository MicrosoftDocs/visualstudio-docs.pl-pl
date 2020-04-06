---
title: IDebugExpressionContext2 | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729639"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
Ten interfejs reprezentuje kontekst oceny wyrażenia

## <a name="syntax"></a>Składnia

```
IDebugExpressionContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania kontekstu, w którym wyrażenie może być oceniane.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) zwraca ten interfejs. Ten interfejs jest dostępny tylko wtedy, gdy program debugowany został wstrzymany i ramka stosu jest dostępna.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugExpressionContext2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|Pobiera nazwę kontekstu oceny.|
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Analizuje wyrażenie tekstowe do oceny.|

## <a name="remarks"></a>Uwagi
 Kontekst oceny można traktować jako zakres wykonywania oceny wyrażenia.

 Po zatrzymaniu programu menedżer debugowania sesji (SDM) uzyskuje ramkę stosu z DE z wywołaniem [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). SDM następnie wywołuje [GetExpressionContext,](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) aby uzyskać `IDebugExpressionContext2` interfejs. Po tym następuje [wywołanie ParseText,](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) aby utworzyć interfejs [IDebugExpression2,](../../../extensibility/debugger/reference/idebugexpression2.md) który reprezentuje analizowane wyrażenie gotowe do oceny.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
