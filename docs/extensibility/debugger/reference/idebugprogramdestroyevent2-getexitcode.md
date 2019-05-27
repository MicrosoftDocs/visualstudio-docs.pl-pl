---
title: IDebugProgramDestroyEvent2::GetExitCode | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramDestroyEvent2::GetExitCode
helpviewer_keywords:
- IDebugProgramDestroyEvent2::GetExitCode
ms.assetid: 7f540cf6-e2d1-42b0-913e-a26d654b7659
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 627f8a4a21663521fe757026da9b3ac177151e0d
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212544"
---
# <a name="idebugprogramdestroyevent2getexitcode"></a>IDebugProgramDestroyEvent2::GetExitCode
Pobiera kod zakończenia programu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetExitCode( 
   DWORD* pdwExit
);
```

```csharp
int GetExitCode( 
   out uint pdwExit
);
```

## <a name="parameters"></a>Parametry
`pdwExit`\
[out] Zwraca kod zakończenia programu.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)