---
title: IDebugThread2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9dcb50f732d4c7aae94cf32036cd17340d636dd9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62868362"
---
# <a name="idebugthread2"></a>IDebugThread2
Ten interfejs reprezentuje wątku działającego w programie.

## <a name="syntax"></a>Składnia

```
IDebugThread2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania wątkiem wykonywania w jednym programie.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj [getthread —](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) uzyskać ten interfejs reprezentujący obecnie aktywnym wątkiem.

 Ten interfejs jest również używany podczas tworzenia żądania punktu przerwania (zobacz [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)).

 Ten interfejs jest także zwracany podczas rozpoznawania granicę lub błąd punktu przerwania (zobacz [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) i [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)).

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugThread2`.

|Metoda|Opis|
|------------|-----------------|
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Pobiera listę ramek stosu dla tego wątku.|
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|Pobiera nazwę wątku.|
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|Określa nazwę wątku.|
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Pobiera program, w którym jest uruchomiony wątek.|
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Określa, czy można ustawić następnej instrukcji w kontekst stosu danej ramki i kod.|
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Ustawia następną instrukcję do kontekstu stosu danej ramki i kod.|
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Pobiera identyfikator wątku systemu.|
|[Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Wstrzymuje działanie wątku.|
|[Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Wznawia działanie wątku.|
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Pobiera właściwości, które opisują wątku.|
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Pobiera logiczne wątek skojarzony z tym wątku fizycznym.|

## <a name="remarks"></a>Uwagi
 Ponieważ pojedynczego wątku fizycznym można uruchomić w wielu programach więcej niż jeden port `IDebugThread2` z więcej niż jeden program może reprezentować tego samego wątku fizycznym.

 Gdy punkt przerwania lub wyjątku, zdarzenia są wysyłane przez wywołanie metody [zdarzeń](../../../extensibility/debugger/reference/idebugeventcallback2-event.md). Jeden z argumentów do tej metody jest `IDebugThread2` interfejs reprezentujący bieżącego wątku. [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) służy do uzyskiwania [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) interfejs dla bieżącej ramki stosu.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)