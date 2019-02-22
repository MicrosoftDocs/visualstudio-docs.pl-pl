---
title: IDebugBreakpointRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a984634dbba0fc1d732fe98214a07d8d6c339d4
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698108"
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

## <a name="see-also"></a>Zobacz też
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)
- [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)