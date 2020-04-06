---
title: IDebugEventCallback2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a74825a955afdde03e63673c4b1b6afda5904953
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729886"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Ten interfejs jest używany przez aparat debugowania (DE) do wysyłania zdarzeń debugowania do menedżera debugowania sesji (SDM).

## <a name="syntax"></a>Składnia

```
IDebugEventCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]implementuje ten interfejs do odbierania zdarzeń z aparatu debugowania.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Aparat debugowania zazwyczaj odbiera ten interfejs, gdy SDM wywołuje [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)lub [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Aparat debugowania wysyła zdarzenia do SDM, wywołując [Zdarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugEventCallback2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[Wydarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Wysyła powiadomienie o zdarzeniach debugowania do SDM.|

## <a name="remarks"></a>Uwagi
 Chociaż [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) i [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) określają, że przyjmują `IDebugEventCallback2` interfejs, nie jest to przypadek, a wskaźnik interfejsu zawsze będzie wartością null. Zamiast tego aparat debugowania `IDebugEventCallback2` musi używać interfejsu odebranego w wywołaniu [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)lub [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

 Jeśli pakiet implementuje [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) w kodzie zarządzanym, zdecydowanie zaleca się, aby <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> wywołać na różnych interfejsach, które są przekazywane do [zdarzenia](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="requirements"></a>Wymagania
 Nagłówek: msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Dołącz](../../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [Dołącz](../../../extensibility/debugger/reference/idebugengine2-attach.md)
