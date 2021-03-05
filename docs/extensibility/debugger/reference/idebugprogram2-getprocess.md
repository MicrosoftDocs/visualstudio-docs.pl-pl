---
description: Pobierz proces, w którym działa ten program.
title: 'IDebugProgram2:: GetProcess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 233bd9bbb41f64b375e899dba9c0be9a9fba3d97
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102168992"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Pobierz proces, w którym działa ten program.

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
określoną Zwraca interfejs [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , który reprezentuje proces.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Jeśli aparat debugowania (DE) nie implementuje interfejsu [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) , implementacja tej metody powinna zawsze zostać zwrócona, `E_NOTIMPL` ponieważ element de nie może ustalić, który proces jest uruchomiony w i dlatego nie może spełnić implementacji tej metody.

 Implementacja `IDebugEngineLaunch2` interfejsu oznacza, że de musi wiedzieć, jak utworzyć proces; w związku z tym, implementacja interfejsu [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) jest w stanie wiedzieć, który proces działa.

## <a name="see-also"></a>Zobacz też
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
