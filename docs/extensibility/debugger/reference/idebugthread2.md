---
description: Ten interfejs reprezentuje wątek uruchomiony w programie.
title: IDebugThread2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 24a9cef2e62dc2597871f270c9ee48ad58c0a0e1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086979"
---
# <a name="idebugthread2"></a>IDebugThread2
Ten interfejs reprezentuje wątek uruchomiony w programie.

## <a name="syntax"></a>Składnia

```
IDebugThread2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs, aby reprezentować wątek wykonywania w pojedynczym programie.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołaj metodę [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) , aby uzyskać ten interfejs reprezentujący aktualnie aktywny wątek.

 Ten interfejs jest również używany podczas tworzenia żądania punktu przerwania (zobacz [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)).

 Ten interfejs jest również zwracany podczas rozpoznawania powiązanego punktu przerwania lub błędu (zobacz [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) i [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)).

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugThread2` .

|Metoda|Opis|
|------------|-----------------|
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Pobiera listę ramek stosu dla tego wątku.|
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|Pobiera nazwę wątku.|
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|Ustawia nazwę wątku.|
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Pobiera program, w którym działa wątek.|
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Określa, czy Następna instrukcja może być ustawiona na daną ramkę stosu i kontekst kodu.|
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Ustawia następną instrukcję na daną ramkę stosu i kontekst kodu.|
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Pobiera identyfikator wątku systemowego.|
|[Wstrzymanie](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Wstrzymuje wątek.|
|[Wznawianie](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Wznawia wątek.|
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Pobiera właściwości opisujące wątek.|
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Pobiera wątek logiczny skojarzony z tym wątkiem fizycznym.|

## <a name="remarks"></a>Uwagi
 Ponieważ pojedynczy wątek fizyczny może działać w wielu programach, więcej niż jeden `IDebugThread2` z więcej niż jednego programu może reprezentować ten sam wątek fizyczny.

 Gdy wystąpi punkt przerwania lub wyjątek, zdarzenie jest wysyłane przez wywołanie [zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md). Jednym z argumentów tej metody jest `IDebugThread2` interfejs reprezentujący bieżący wątek. [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) jest używany do uzyskania interfejsu [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) dla bieżącej ramki stosu.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [Zdarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
