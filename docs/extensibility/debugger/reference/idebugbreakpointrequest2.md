---
title: IDebugBreakpointRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 55e7c73b720e326b823c3038928d7141ea732155
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352920"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
Ten interfejs reprezentuje informacje niezbędne do tworzenia i powiązać dowolnego typu punktu przerwania.

## <a name="syntax"></a>Składnia

```
IDebugBreakpointRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Menedżer debugowania sesji (SDM) zwykle implementuje ten interfejs.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Aparat debugowania (DE) otrzyma ten interfejs, za pomocą wywołania [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) aby można było utworzyć oczekujący punkt przerwania. Wywołanie [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) można pobrać tego interfejsu z DE.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugBreakpointRequest2`.

|Metoda|Opis|
|------------|-----------------|
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Pobiera typ lokalizacji punktu przerwania tego żądania punktu przerwania.|
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Pobiera informacje o żądaniu punktu przerwania, opisujący tego żądania punktu przerwania.|

## <a name="remarks"></a>Uwagi
 Po program debugowany został załadowany, wywołanie [powiązać](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) wiąże oczekujący punkt przerwania do żądanej lokalizacji w programie.

## <a name="requirements"></a>Wymagania
 Header: msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)
- [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)