---
title: IDebugPortEx2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bed6cd047af4ba57a1880d87e30a990dcf83efac
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340434"
---
# <a name="idebugportex2"></a>IDebugPortEx2
Ten interfejs umożliwia sesji debugowanie kontrolki manager (SDM), programów i procesów uruchomionych na porcie.

## <a name="syntax"></a>Składnia

```
IDebugPortEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Dostawcy niestandardowego portu implementuje ten interfejs dla tego samego obiektu, który implementuje [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md).

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Wywołania SDM [QueryInterface](/cpp/atl/queryinterface) na `IDebugPort2` interfejsu w celu uzyskania tego interfejsu.

## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności
 W poniższej tabeli przedstawiono metody `IDebugPortEx2`.

|Metoda|Opis|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Uruchamia plik wykonywalny.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Wznawia wykonanie procesu.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Określa, czy Proces może zostać zakończone.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Kończy proces.|
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Pobiera identyfikator procesu samego portu.|
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Pobiera program skojarzony z węzłem programu.|

## <a name="remarks"></a>Uwagi
 Ten interfejs jest zwykle prywatnych między SDM i dostawcy numery portów.

 Jeśli to konieczne, aparat debugowania (DE) można wyszukać ten interfejs [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interfejsu przekazany do [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) i użyj [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) do uruchomienia programu. To nie to wymagane, jednak i DE można zrobić, niezależnie od rodzaju należy ją wykonać, aby uruchomić program żądania.

## <a name="requirements"></a>Wymagania
 Nagłówek: portpriv.h

 Przestrzeń nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz także
- [Interfejsy podstawowe](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)