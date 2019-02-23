---
title: IDebugProcess2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6ef6df6419f43201555f1dcc275b44d2a0e9737
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685743"
---
# <a name="idebugprocess2"></a>IDebugProcess2
Ten interfejs reprezentuje proces uruchomiony na porcie. Jeśli port lokalny port, następnie `IDebugProcess2` zazwyczaj reprezentuje fizyczny proces na komputerze lokalnym.

## <a name="syntax"></a>Składnia

```
IDebugProcess2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez dostawcę numery portów do zarządzania programami jako grupa. Ten interfejs musi być implementowany przez dostawcy portu.

 Aparat debugowania także implementuje ten interfejs, gdy obsługuje uruchamianie programu przy użyciu [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest wywoływana przede wszystkim przez Menedżer debugowania sesji (SDM) w celu interakcji z grupy programów identyfikowane w ramach tego procesu.

 Wywołaj [getprocess —](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) lub [getprocess —](../../../extensibility/debugger/reference/idebugport2-getprocess.md) można pobrać tego interfejsu. Ten interfejs jest także zwracany przez wywołanie metody `IDebugEngineLaunch2::LaunchSuspended`.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugProcess2`.

|Metoda|Opis|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Pobiera opis procesu.|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Wylicza programy, które są zawarte w ramach tego procesu.|
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Pobiera tytuł, przyjazną nazwę lub nazwę procesu.|
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Pobiera wystąpienie serwera maszyny, na którym ten proces jest uruchomiony na.|
|[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Kończy proces.|
|[Attach](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Dołącza do procesu.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Określa, jeśli model SDM można odłączyć procesu.|
|[Detach](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Odłącza debuger z procesu.|
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Pobiera identyfikator procesu systemu.|
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Pobiera unikatowy identyfikator globalny dla tego procesu.|
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [PRZESTARZAŁE]|Pobiera nazwę sesji, która jest debugowanie procesu.<br /><br /> [PRZESTARZAŁE. NALEŻY ZAWSZE ZWRÓCENIA `E_NOTIMPL`.]|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Wylicza wątków, uruchomiony w procesie.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Żądania wysyłane przez następnego programu Uruchamianie kodu w tym zatrzymania procesu.|
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Pobiera portu, którego ten proces.|

## <a name="remarks"></a>Uwagi
 `IDebugProcess2` Zawiera jeden lub więcej [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfejsów.

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)
- [Next](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)