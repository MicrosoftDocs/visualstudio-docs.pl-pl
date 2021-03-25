---
description: Interfejs IDebugBreakpointRequest3 reprezentuje informacje niezbędne do utworzenia i powiązania dowolnego typu punktu przerwania.
title: IDebugBreakpointRequest3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6803b62975822f1b5219caa43844c8983303a998
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054416"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Ten interfejs reprezentuje informacje niezbędne do utworzenia i powiązania dowolnego typu punktu przerwania. Jest to rozszerzenie [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).

## <a name="syntax"></a>Składnia

```
IDebugBreakpointRequest3 : IDebugBreakpointRequest2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Menedżer debugowania sesji (SDM) zazwyczaj implementuje ten interfejs.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Aparat debugowania (DE) uzyskuje dostęp do tego interfejsu przez wywołanie [polecenia QueryInterface](/cpp/atl/queryinterface) w interfejsie IDebugBreakpointRequest2 odebranym w wywołaniu [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 Oprócz metod dziedziczonych z [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md), `IDebugBreakpointRequest3` interfejs uwidacznia następującą metodę.

|Metoda|Opis|
|------------|-----------------|
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Pobiera informacje o żądaniu punktu przerwania, które opisują to żądanie punktu przerwania.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest używany do udostępniania dodatkowych informacji w ramach struktury [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) . Te dodatkowe informacje obejmują identyfikator dostawcy (w postaci identyfikatora GUID), nazwę punkt śledzenia i nazwę ograniczenia punktu przerwania.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
