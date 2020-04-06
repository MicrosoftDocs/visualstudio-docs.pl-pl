---
title: IDebugEngineLaunch2 | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730491"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
Używany przez aparat debugowania (DE) do uruchamiania i kończonego programów.

## <a name="syntax"></a>Składnia

```
IDebugEngineLaunch2 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji
 Ten interfejs jest implementowany przez niestandardowe DE, jeśli ma specjalne wymagania dotyczące uruchamiania procesu, który nie może być obsługiwany całkowicie przez port niestandardowy. Zazwyczaj jest to przypadek, gdy DE jest częścią interpretera i proces debugowany jest skrypt: interpreter musi zostać uruchomiony najpierw, a następnie skrypt jest ładowany i uruchamiany. Port może uruchomić interpreter, ale skrypt może wymagać specjalnej obsługi (czyli tam, gdzie de ma rolę). Ten interfejs jest implementowany tylko wtedy, gdy istnieją unikatowe wymagania dotyczące uruchamiania programu, który nie może obsłużyć portu niestandardowego.

## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania
 Ten interfejs jest wywoływany przez menedżera debugowania sesji (SDM), jeśli SDM może uzyskać ten interfejs z interfejsu [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) (przy użyciu QueryInterface). Jeśli ten interfejs można uzyskać, SDM wie, że DE ma specjalne wymagania i wywołuje ten interfejs, aby uruchomić program zamiast portu uruchomić go.

## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable
 W poniższej tabeli `IDebugEngineLaunch2`przedstawiono metody .

|Metoda|Opis|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Uruchamia proces za pomocą DE.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Wznawia wykonywanie procesu.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Określa, czy proces można zakończyć.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Kończy proces.|

## <a name="requirements"></a>Wymagania
 Nagłówek: Msdbg.h

 Obszar nazw: Microsoft.VisualStudio.Debugger.Interop

 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Zobacz też
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
