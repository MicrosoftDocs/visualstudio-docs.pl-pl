---
title: IDebugExpressionEvaluationKomunikowanieEvent2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 35e57e361b59e76e187617b5e528b219e8e47897
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729562"
---
# <a name="idebugexpressionevaluationcompleteevent2"></a>IDebugExpressionEvaluationCompleteEvent2
Ten interfejs jest wysyłany przez aparat debugowania (DE) do menedżera debugowania sesji (SDM) po zakończeniu oceny wyrażenia asynchronicznej.

## <a name="syntax"></a>Składnia

```
IDebugExpressionEvaluationCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE implementuje ten interfejs do raportu ukończenia oceny wyrażenia rozpoczęte przez wywołanie [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany na tym samym obiekcie co ten interfejs. Moduł SDM używa [QueryInterface,](/cpp/atl/queryinterface) aby uzyskać dostęp do `IDebugEvent2` interfejsu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 DE tworzy i wysyła ten obiekt zdarzenia do raportu zakończenia oceny wyrażenia. Zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) która jest dostarczana przez SDM, gdy jest dołączony do programu jest debugowany.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugExpressionEvaluationCompleteEvent2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|Pobiera oryginalne wyrażenie.|
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|Pobiera wynik oceny wyrażenia.|

## <a name="remarks"></a>Uwagi
 DE musi wysłać to zdarzenie, czy ocena zakończyła się pomyślnie, czy nie.

 Jeśli ocena nie powiodła `DEBUG_PROPINFO_VALUE` `DEBUG_PROPINFO_ATTRIB` się, i flagi nie zostaną ustawione w [strukturze DEBUG_PROPERTY_INFO,](../../../extensibility/debugger/reference/debug-property-info.md) który jest zwracany przez [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) [(IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) obiekt jest tworzony przez DE i zwracany w `IDebugExpressionEvaluationCompleteEvent2` przypadku, jeśli ocena nie powiodła się).

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
