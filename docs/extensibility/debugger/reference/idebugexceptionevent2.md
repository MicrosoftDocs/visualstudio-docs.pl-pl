---
title: IDebugExceptionEvent2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80729780"
---
# <a name="idebugexceptionevent2"></a>IDebugExceptionEvent2
Aparat debugowania (DE) wysyła ten interfejs do Menedżera debugowania sesji (SDM), gdy zostanie zgłoszony wyjątek w aktualnie wykonywanym programie.

## <a name="syntax"></a>Składnia

```
IDebugExceptionEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 DE implementuje ten interfejs, aby zgłosić, że wystąpił wyjątek w debugowanym programie. Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musi być zaimplementowany w tym samym obiekcie co ten interfejs. Model SDM używa [metody QueryInterface](/cpp/atl/queryinterface) do uzyskiwania dostępu do `IDebugEvent2` interfejsu.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Element DE tworzy i wysyła ten obiekt Event, aby zgłosić wyjątek. Zdarzenie jest wysyłane przy użyciu funkcji wywołania zwrotnego [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , która jest dostarczana przez model SDM, gdy jest dołączona do debugowanego programu.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugExceptionEvent2` .

|Metoda|Opis|
|------------|-----------------|
|[GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)|Pobiera szczegółowe informacje o wyjątku, który uruchomił to zdarzenie.|
|[GetExceptionDescription](../../../extensibility/debugger/reference/idebugexceptionevent2-getexceptiondescription.md)|Pobiera czytelny dla człowieka opis dla zgłoszonego wyjątku, który uruchomił to zdarzenie.|
|[CanPassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md)|Określa, czy aparat debugowania (DE) obsługuje opcję przekazywania tego wyjątku do debugowanego programu podczas wznawiania wykonywania.|
|[PassToDebuggee](../../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md)|Określa, czy wyjątek powinien być przekazywać do debugowanego programu po wznowieniu wykonywania lub czy wyjątek powinien zostać odrzucony.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Uwagi
 Przed wysłaniem zdarzenia, firma DE sprawdza, czy to zdarzenie wyjątku wyznaczył wyjątek pierwszej lub drugiej szansy przez poprzednie wywołanie metody [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md). Jeśli został wystawiony jako wyjątek pierwszej szansy, `IDebugExceptionEvent2` zdarzenie jest wysyłane do modelu SDM. W przeciwnym razie, DE nadaje aplikacji szansę obsłużyć wyjątek. Jeśli nie podano procedury obsługi wyjątków i jeśli wyjątek został wystawiony jako wyjątek drugiej szansy, `IDebugExceptionEvent2` zdarzenie jest wysyłane do modelu SDM. W przeciwnym razie dewznawia wykonywanie programu, a system operacyjny lub środowisko uruchomieniowe obsługuje wyjątek.

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
