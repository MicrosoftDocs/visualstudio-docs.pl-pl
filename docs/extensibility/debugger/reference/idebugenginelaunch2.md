---
title: IDebugEngineLaunch2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee77cbd680df2c851d53aac298605023227fa6f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730491"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
Używane przez aparat debugowania (DE) do uruchamiania i kończenia programów.

## <a name="syntax"></a>Składnia

```
IDebugEngineLaunch2 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez niestandardowe DE, jeśli ma specjalne wymagania dotyczące uruchamiania procesu, który nie może być obsługiwany całkowicie przez port niestandardowy. Zwykle jest to przypadek, gdy cześć jest częścią interpretera i debugowany proces jest skryptem: interpreter musi być uruchamiany jako pierwszy, a następnie skrypt zostaje załadowany i uruchomiony. Port może uruchomić interpreter, ale skrypt może wymagać specjalnej obsługi (który ma rolę DE). Ten interfejs jest implementowany tylko wtedy, gdy istnieją unikatowe wymagania dotyczące uruchamiania programu, którego nie może obsłużyć port niestandardowy.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest wywoływany przez Menedżera debugowania sesji (SDM), jeśli model SDM może uzyskać ten interfejs z interfejsu [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) (przy użyciu polecenia QueryInterface). Jeśli ten interfejs może zostać uzyskany, model SDM wie, że DE ma specjalne wymagania i wywołuje ten interfejs, aby uruchomić program zamiast uruchamiania go przez port.

## <a name="methods-in-vtable-order"></a>Metody w kolejności tablic wirtualnych
 W poniższej tabeli przedstawiono metody `IDebugEngineLaunch2` .

|Metoda|Opis|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Uruchamia proces za pomocą DE.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Wznawia wykonywanie procesu.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Określa, czy proces może być zakończony.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Kończy proces.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg. h

 Przestrzeń nazw: Microsoft. VisualStudio. Debugger. Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
