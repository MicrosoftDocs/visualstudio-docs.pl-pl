---
title: IDebugProgram2::GetProcess | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a443d7f17397526ae0f990627314d8feedad48d4
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212578"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Uzyskaj procesu, który tego programu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetProcess(
   IDebugProcess2** ppProcess
);
```

```csharp
int GetProcess(
   out IDebugProcess2 ppProcess
);
```

## <a name="parameters"></a>Parametry
`ppProcess`\
[out] Zwraca [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) interfejs, który reprezentuje proces.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 O ile nie implementuje aparat debugowania (DE) [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) interfejsu, DE implementacja tej metody zawsze powinna zwrócić `E_NOTIMPL` DE nie może ustalić, który proces jest uruchomiony w i dlatego nie może spełnia implementacja tej metody.

 Implementowanie `IDebugEngineLaunch2` interfejs oznacza, że Niemcy musi wiedzieć, jak można utworzyć procesu; w związku z tym, DE implementacji [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfejsu jest w stanie wiedzieć, jakie procesy jest uruchomiony w.

## <a name="see-also"></a>Zobacz także
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)