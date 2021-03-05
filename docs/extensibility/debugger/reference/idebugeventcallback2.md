---
description: Ten interfejs jest używany przez aparat debugowania (DE) do wysyłania zdarzeń debugowania do Menedżera debugowania sesji (SDM).
title: IDebugEventCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cb33bcbdff14b0f95aab5d8f300473c13d4c342f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152913"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Ten interfejs jest używany przez aparat debugowania (DE) do wysyłania zdarzeń debugowania do Menedżera debugowania sesji (SDM).

## <a name="syntax"></a>Składnia

```
IDebugEventCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] implementuje ten interfejs, aby odbierać zdarzenia z aparatu debugowania.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Aparat debugowania zazwyczaj otrzymuje ten interfejs, gdy wywołania SDM [dołączają](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [dołączają](../../../extensibility/debugger/reference/idebugengine2-attach.md)lub [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Aparat debugowania wysyła zdarzenia do modelu SDM przez wywołanie [zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugEventCallback2` .

|Metoda|Opis|
|------------|-----------------|
|[Zdarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Wysyła powiadomienie o zdarzeniach debugowania do modelu SDM.|

## <a name="remarks"></a>Uwagi
 Mimo że [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) i [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) określają, że przyjmują `IDebugEventCallback2` interfejs, nie jest to przypadek, a wskaźnik interfejsu zawsze będzie wartością null. Zamiast tego aparat debugowania musi używać `IDebugEventCallback2` interfejsu otrzymanego w wywołaniu metody [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)lub [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

 Jeśli pakiet implementuje [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) w kodzie zarządzanym, stanowczo zaleca się <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> wywoływanie różnych interfejsów, które są przesyłane do [zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Dołącz](../../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md)
