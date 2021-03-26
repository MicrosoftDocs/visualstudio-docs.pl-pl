---
description: Ten interfejs reprezentuje proces uruchomiony na porcie.
title: IDebugProcess2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0d56687cb3559b5807b488fa44dfdfc4048e4c58
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081610"
---
# <a name="idebugprocess2"></a>IDebugProcess2
Ten interfejs reprezentuje proces uruchomiony na porcie. Jeśli port jest portem lokalnym, `IDebugProcess2` zazwyczaj reprezentuje proces fizyczny na komputerze lokalnym.

## <a name="syntax"></a>Składnia

```
IDebugProcess2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez niestandardowego dostawcę portu do zarządzania programami jako grupą. Ten interfejs musi być zaimplementowany przez dostawcę portu.

 Aparat debugowania implementuje także ten interfejs, jeśli obsługuje uruchamianie programu za pomocą [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest wywoływany głównie przez Menedżera debugowania sesji (SDM) w celu współdziałania z grupą programów identyfikowanych w tym procesie.

 Wywołaj metodę [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) lub [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) , aby uzyskać ten interfejs. Ten interfejs jest również zwracany przez wywołanie `IDebugEngineLaunch2::LaunchSuspended` .

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugProcess2` .

|Metoda|Opis|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Pobiera opis procesu.|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Wylicza programy, które są zawarte w tym procesie.|
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Pobiera tytuł, przyjazną nazwę lub nazwę pliku procesu.|
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Pobiera wystąpienie serwera maszynowego, na którym działa ten proces.|
|[Zakończ](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Kończy proces.|
|[Dołącz](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Dołącza do procesu.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Określa, czy model SDM może odłączać proces.|
|[Odłącz](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Odłącza debuger od procesu.|
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Pobiera identyfikator procesu systemowego.|
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Pobiera unikatowy identyfikator globalny dla tego procesu.|
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> PRZESTARZAŁE|Pobiera nazwę sesji, która debuguje proces.<br /><br /> Przestarzałe. ZAWSZE powinna być zwracana `E_NOTIMPL` .]|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Wylicza wątki uruchomione w procesie.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Żąda zatrzymania następnego programu z uruchomionym kodem w tym procesie.|
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Pobiera port, na którym działa ten proces.|

## <a name="remarks"></a>Uwagi
 `IDebugProcess2`Zawiera co najmniej jeden interfejs [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) .

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)
- [Dalej](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)
- [Zdarzenie](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [Zdarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
