---
title: IDebugEngineLaunch2::ResumeProcess | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::ResumeProcess
helpviewer_keywords:
- IDebugEngineLaunch2::ResumeProcess
ms.assetid: 61ccc14e-75c6-44e7-aae4-57a9aac52089
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9dc3d0b59c507743d78fd6954b8c98342fb4a0b
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212465"
---
# <a name="idebugenginelaunch2resumeprocess"></a>IDebugEngineLaunch2::ResumeProcess
Wznawia wykonanie procesu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT ResumeProcess ( 
   IDebugProcess2* pProcess
);
```

```csharp
int ResumeProcess ( 
   IDebugProcess2 pProcess
);
```

## <a name="parameters"></a>Parametry
`pProcess`\
[in] [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) obiekt, który reprezentuje proces wznowione.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest wywoływana po procesie została uruchomiona przy użyciu wywołania do [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) metody.

## <a name="see-also"></a>Zobacz także
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)