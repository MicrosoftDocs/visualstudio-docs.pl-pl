---
description: Ten interfejs jest wysyłany przez aparat debugowania (DE) do Menedżera debugowania sesji (SDM), gdy Obliczanie wyrażenia asynchronicznego zostało zakończone.
title: IDebugExpressionEvaluationCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b30b61c0b7a9a9f3e06465a6b194c882213afb34
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105092205"
---
# <a name="idebugexpressionevaluationcompleteevent2"></a>IDebugExpressionEvaluationCompleteEvent2
Ten interfejs jest wysyłany przez aparat debugowania (DE) do Menedżera debugowania sesji (SDM), gdy Obliczanie wyrażenia asynchronicznego zostało zakończone.

## <a name="syntax"></a>Składnia

```
IDebugExpressionEvaluationCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Element DE implementuje ten interfejs, aby zgłosić ukończenie obliczania wyrażenia uruchomionego przez wywołanie do [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany w tym samym obiekcie co ten interfejs. Model SDM używa [metody QueryInterface](/cpp/atl/queryinterface) do uzyskiwania dostępu do `IDebugEvent2` interfejsu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Element DE tworzy i wysyła ten obiekt Event, aby zgłosić zakończenie obliczania wyrażenia. Zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , która jest dostarczana przez model SDM, gdy jest dołączona do debugowanego programu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugExpressionEvaluationCompleteEvent2` .

|Metoda|Opis|
|------------|-----------------|
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|Pobiera oryginalne wyrażenie.|
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|Pobiera wynik oceny wyrażenia.|

## <a name="remarks"></a>Uwagi
 DE musi wysłać to zdarzenie, niezależnie od tego, czy Ocena zakończyła się powodzeniem, czy nie.

 Jeśli Ocena zakończyła się niepowodzeniem `DEBUG_PROPINFO_VALUE` , `DEBUG_PROPINFO_ATTRIB` flagi i nie zostaną ustawione w strukturze [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) , która jest zwracana przez [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (obiekt [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) jest tworzony przez de i zwraca w `IDebugExpressionEvaluationCompleteEvent2` zdarzeniu, jeśli szacowanie nie powiodło się).

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
