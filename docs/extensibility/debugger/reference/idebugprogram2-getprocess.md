---
title: IDebugProgram2::GetProcess | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aca1842e92e7e1c164a6468e6c1e94a352ef67c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722781"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Pobierz proces, w który działa ten program.

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
[na zewnątrz] Zwraca interfejs [IDebugProcess2,](../../../extensibility/debugger/reference/idebugprocess2.md) który reprezentuje proces.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Chyba że aparat debugowania (DE) implementuje interfejs [IDebugEngineLaunch2,](../../../extensibility/debugger/reference/idebugenginelaunch2.md) implementacja `E_NOTIMPL` DE tej metody zawsze powinna zostać zwracana, ponieważ DE nie może określić, który proces jest uruchomiony w i dlatego nie może spełnić implementacji tej metody.

 Implementacja `IDebugEngineLaunch2` interfejsu oznacza, że DE musi wiedzieć, jak utworzyć proces; w związku z tym de implementacji interfejsu [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) jest w stanie wiedzieć, w jakim procesie jest uruchomiony w.

## <a name="see-also"></a>Zobacz też
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
