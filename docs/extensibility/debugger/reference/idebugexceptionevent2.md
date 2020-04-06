---
title: IDebugExceptionEvent2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2
helpviewer_keywords:
- IDebugExceptionEvent2 interface
ms.assetid: 53d32e59-a84b-4710-833e-c5ab08100516
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbd53d56b21886e972b33c219367edd603cbf0d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729780"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
Aparat debugowania (DE) wysyła ten interfejs do menedżera debugowania sesji (SDM), gdy wyjątek jest zgłaszany w programie aktualnie wykonywanym.

## <a name="syntax"></a>Składnia

```
IDebugExceptionEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE implementuje ten interfejs, aby zgłosić, że wystąpił wyjątek w programie debugowanym. Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany na tym samym obiekcie co ten interfejs. Moduł SDM używa [QueryInterface,](/cpp/atl/queryinterface) aby uzyskać dostęp do `IDebugEvent2` interfejsu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 DE tworzy i wysyła ten obiekt zdarzenia do raportu wyjątek. Zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) która jest dostarczana przez SDM, gdy jest dołączona do programu jest debugowana.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugExceptionEvent2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Pobiera szczegółowe informacje o wyjątku, który został zwolniony to zdarzenie.|
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Pobiera opis czytelny dla człowieka dla wyjątku, który został zgłoszony to zdarzenie.|
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Określa, czy aparat debugowania (DE) obsługuje opcję przekazywania tego wyjątku do programu debugowanego po wznowieniu wykonywania.|
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Określa, czy wyjątek powinien być przekazywany do programu debugowanego po wznowieniu wykonywania lub jeśli wyjątek powinien zostać odrzucony.|

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Uwagi
 Przed wysłaniem zdarzenia DE sprawdza, czy to zdarzenie wyjątku został wyznaczony pierwszej lub drugiej szansy wyjątek przez poprzednie wywołanie [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md). Jeśli został wyznaczony jako wyjątek pierwszej szansy, `IDebugExceptionEvent2` zdarzenie jest wysyłane do SDM. Jeśli nie, DE daje aplikacji szansę obsługi wyjątku. Jeśli nie podano obsługi wyjątków i jeśli wyjątek został wyznaczony jako `IDebugExceptionEvent2` wyjątek drugiej szansy, zdarzenie jest wysyłane do SDM. W przeciwnym razie DE wznawia wykonywanie programu, a system operacyjny lub środowisko wykonawcze obsługuje wyjątek.

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
