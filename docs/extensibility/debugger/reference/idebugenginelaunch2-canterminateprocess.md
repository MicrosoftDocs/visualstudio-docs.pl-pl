---
title: IDebugEngineLaunch2::CanTerminateProcess | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
helpviewer_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
ms.assetid: 7973454d-c957-4123-a0ee-80ebcdbbd2d1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f2e1d3ada2e5bf5f906d7c458a47e32f7e59c3c5
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212590"
---
# <a name="idebugenginelaunch2canterminateprocess"></a>IDebugEngineLaunch2::CanTerminateProcess
Określa, proces może zostać zakończone.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CanTerminateProcess ( 
   IDebugProcess2* pProcess
);
```

```csharp
int CanTerminateProcess ( 
   IDebugProcess2 pProcess
);
```

## <a name="parameters"></a>Parametry
`pProcess`\
[in] [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) obiekt, który reprezentuje proces, który ma zostać zakończony.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Zwraca `S_FALSE` Jeśli silnik nie można przerwać proces, na przykład, ponieważ nastąpiła odmowa dostępu.

## <a name="remarks"></a>Uwagi
 Jeśli ta metoda zwraca `S_OK`, następnie go [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md) można wywołać metody faktycznie zakończenia procesu.

## <a name="see-also"></a>Zobacz także
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)