---
title: IDebugBreakpointRequest3 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 505b0c0b05fa0f14578d770abec6c43ed6b80b01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734829"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Ten interfejs reprezentuje informacje niezbędne do tworzenia i wiązania dowolnego typu punktu przerwania. Jest to rozszerzenie [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).

## <a name="syntax"></a>Składnia

```
IDebugBreakpointRequest3 : IDebugBreakpointRequest2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Menedżer debugowania sesji (SDM) zazwyczaj implementuje ten interfejs.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Aparat debugowania (DE) uzyskuje dostęp do tego interfejsu, wywołując [QueryInterface](/cpp/atl/queryinterface) na interfejsie IDebugBreakpointRequest2 odebranym w wywołaniu [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 Oprócz metod dziedziczonych z [IDebugBreakpointRequest2,](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) `IDebugBreakpointRequest3` interfejs udostępnia następującą metodę.

|Metoda|Opis|
|------------|-----------------|
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Pobiera informacje o żądaniu punktu przerwania, który opisuje to żądanie punktu przerwania.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest używany do dostarczania dodatkowych informacji do DE za pośrednictwem [struktury BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md) Te dodatkowe informacje obejmują identyfikator dostawcy DE (w postaci identyfikatora GUID), nazwę punktu śledzenia i nazwę ograniczenia punktu przerwania.

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
