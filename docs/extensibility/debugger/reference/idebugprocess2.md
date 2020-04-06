---
title: IDebugProcess2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72659491ec6718397a4fbb494175eea0896c7f7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723800"
---
# <a name="idebugprocess2"></a>IDebugProcess2
Ten interfejs reprezentuje proces uruchomiony na porcie. Jeśli port jest portem `IDebugProcess2` lokalnym, zwykle reprezentuje proces fizyczny na komputerze lokalnym.

## <a name="syntax"></a>Składnia

```
IDebugProcess2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez niestandardowego dostawcę portu do zarządzania programami jako grupa. Ten interfejs musi być zaimplementowany przez dostawcę portu.

 Aparat debugowania implementuje również ten interfejs, jeśli obsługuje uruchamianie programu za pośrednictwem [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest wywoływany głównie przez menedżera debugowania sesji (SDM) w celu interakcji z grupą programów zidentyfikowanych w tym procesie.

 Wywołanie [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) lub [GetProcess,](../../../extensibility/debugger/reference/idebugport2-getprocess.md) aby uzyskać ten interfejs. Ten interfejs jest również `IDebugEngineLaunch2::LaunchSuspended`zwracany przez wywołanie .

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugProcess2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Pobiera opis procesu.|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Wylicza programy, które są zawarte w tym procesie.|
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Pobiera tytuł, przyjazną nazwę lub nazwę pliku procesu.|
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Pobiera wystąpienie serwera komputera, na który jest uruchomiony ten proces.|
|[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Kończy proces.|
|[Dołącz](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Dołącza się do procesu.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Określa, czy SDM może odłączyć proces.|
|[Odłącz](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Odłącza debugera od procesu.|
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Pobiera identyfikator procesu systemowego.|
|[GetProcessId (ida getprocessid)](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Pobiera globalnie unikatowy identyfikator dla tego procesu.|
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [PRZESTARZAŁE]|Pobiera nazwę sesji, która jest debugowanie procesu.<br /><br /> [PRZESTARZAŁE. ZAWSZE POWINIEN `E_NOTIMPL`ZWRACAĆ .]|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Wylicza wątki uruchomione w procesie.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Żąda, aby następny program z uruchomionym kodem w tym procesie został zatrzymany.|
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Pobiera port, na który jest uruchomiony ten proces.|

## <a name="remarks"></a>Uwagi
 Zawiera `IDebugProcess2` jeden lub więcej interfejsów [IDebugProgram2.](../../../extensibility/debugger/reference/idebugprogram2.md)

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProcess ( GetProcess )](../../../extensibility/debugger/reference/idebugport2-getprocess.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [GetProcess ( GetProcess )](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)
- [Dalej](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)
- [Wydarzenie](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [Wydarzenie](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
