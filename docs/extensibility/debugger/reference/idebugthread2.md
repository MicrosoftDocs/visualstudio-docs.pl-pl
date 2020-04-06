---
title: IDebugThread2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2
helpviewer_keywords:
- IDebugThread2 interface
ms.assetid: 221b4b1b-4a26-466e-bc29-5eff800fab13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1965ff1b4cfa89e4584c194942dec7ae486473ff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718591"
---
# <a name="idebugthread2"></a>IDebugThread2
Ten interfejs reprezentuje wątek uruchomiony w programie.

## <a name="syntax"></a>Składnia

```
IDebugThread2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania wątku wykonania w jednym programie.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołanie [GetThread,](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md) aby uzyskać ten interfejs reprezentujący aktualnie aktywny wątek.

 Ten interfejs jest również używany do tworzenia żądania punktu przerwania (patrz [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)).

 Ten interfejs jest również zwracany podczas rozpoznawania wiązanego lub błędu punktu przerwania (patrz [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) i [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)).

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugThread2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)|Pobiera listę ramek stosu dla tego wątku.|
|[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)|Pobiera nazwę wątku.|
|[SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)|Ustawia nazwę wątku.|
|[GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)|Pobiera program, w którym jest uruchomiony wątek.|
|[CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)|Określa, czy następną instrukcję można ustawić na danej ramki stosu i kontekstu kodu.|
|[SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)|Ustawia następną instrukcję do danej ramki stosu i kontekstu kodu.|
|[GetThreadId](../../../extensibility/debugger/reference/idebugthread2-getthreadid.md)|Pobiera identyfikator wątku systemowego.|
|[Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)|Zawiesza wątek.|
|[Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)|Wznawia wątek.|
|[GetThreadProperties](../../../extensibility/debugger/reference/idebugthread2-getthreadproperties.md)|Pobiera właściwości, które opisują wątek.|
|[GetLogicalThread](../../../extensibility/debugger/reference/idebugthread2-getlogicalthread.md)|Pobiera wątku logicznego skojarzonego z tym wątku fizycznego.|

## <a name="remarks"></a>Uwagi
 Ponieważ pojedynczy wątek fizyczny można uruchomić `IDebugThread2` w wielu programach, więcej niż jeden z więcej niż jednego programu może reprezentować ten sam wątek fizyczny.

 W przypadku wystąpienia punktu przerwania lub wyjątku zdarzenie jest wysyłane przez [wywołanie zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md). Jednym z argumentów tej `IDebugThread2` metody jest interfejs reprezentujący bieżący wątek. [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) służy do uzyskania interfejsu [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) dla bieżącej ramki stosu.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [Wydarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
