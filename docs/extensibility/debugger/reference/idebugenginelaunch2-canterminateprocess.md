---
description: Określa, czy proces może być zakończony.
title: 'IDebugEngineLaunch2:: CanTerminateProcess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
helpviewer_keywords:
- IDebugEngineLaunch2::CanTerminateProcess
ms.assetid: 7973454d-c957-4123-a0ee-80ebcdbbd2d1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 20df2c6d44e9bb0afd6610d6ded01ed637035b4b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077450"
---
# <a name="idebugenginelaunch2canterminateprocess"></a>IDebugEngineLaunch2::CanTerminateProcess
Określa, czy proces może być zakończony.

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
podczas Obiekt [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , który reprezentuje proces, który ma zostać zakończony.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu. Zwraca `S_FALSE` czy aparat nie może zakończyć procesu, na przykład z powodu odmowy dostępu.

## <a name="remarks"></a>Uwagi
 Jeśli ta metoda zwraca `S_OK` , Metoda [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md) może być wywoływana w celu rzeczywistego zakończenia procesu.

## <a name="see-also"></a>Zobacz też
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)
