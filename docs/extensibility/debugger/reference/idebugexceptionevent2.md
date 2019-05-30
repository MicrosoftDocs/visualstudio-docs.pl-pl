---
title: IDebugExceptionEvent2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3fd2a449c71b69c654cd19846990f7b722f706de
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325994"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
Aparat debugowania (DE) wysyła ten interfejs do Menedżer debugowania sesji (SDM), gdy wyjątek jest generowany w programie obecnie wykonywane.

## <a name="syntax"></a>Składnia

```
IDebugExceptionEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE implementuje ten interfejs do raportu wystąpił wyjątek do debugowanego programu. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs musi zostać wdrożone na tym samym obiekcie danego interfejsu. Używa SDM [QueryInterface](/cpp/atl/queryinterface) dostęp do `IDebugEvent2` interfejsu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 DE tworzy i wysyła tego obiektu zdarzenia, aby zgłosić wyjątek. Zdarzenia są wysyłane przy użyciu [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) funkcji wywołania zwrotnego, która jest dostarczana przez SDM, gdy jest on dołączony do debugowanego programu.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugExceptionEvent2`.

|Metoda|Opis|
|------------|-----------------|
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Pobiera szczegółowe informacje o wyjątku, która wywołała zdarzenie.|
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Pobiera opis czytelny dla człowieka zgłoszony wyjątek, która wywołała zdarzenie.|
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Określa, czy aparat debugowania (DE) obsługuje możliwość przekazywania ten wyjątek do debugowanego po wznowieniu działania wykonywania.|
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Określa, czy wyjątek powinien zostać przekazany do aktualnie debugowanego po wznowieniu działania wykonywania, czy wyjątek powinien zostać odrzucony.|

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Uwagi
 Przed wysłaniem zdarzenia, DE sprawdza, jeśli to zdarzenie wyjątku wyznaczono wyjątek pierwszego rzędu lub szansy na sekundę przez poprzednie wywołanie [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md). Jeśli został wyznaczony jako wyjątku pierwszej szansy `IDebugExceptionEvent2` SDM jest wysyłane zdarzenie. W przeciwnym razie DE daje aplikacji możliwość obsługi wyjątku. Jeśli zostanie podana żadna procedura obsługi wyjątków, a wyjątek został wyznaczony jako wyjątek szansy na sekundę, `IDebugExceptionEvent2` SDM jest wysyłane zdarzenie. W przeciwnym razie DE wznawia działanie programu, a system operacyjny lub środowisko uruchomieniowe obsługuje wyjątek.

## <a name="see-also"></a>Zobacz także
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)