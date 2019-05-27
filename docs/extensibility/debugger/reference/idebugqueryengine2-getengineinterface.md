---
title: IDebugQueryEngine2::GetEngineInterface | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2::GetEngineInterface
helpviewer_keywords:
- IDebugQueryEngine2::GetEngineInterface
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fbb4f5018972777e51fbaad8d06f833309f6390f
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212923"
---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
Pobiera interfejs aparatu (DE) niestandardowe debugowania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetEngineInterface( 
   IUnknown** ppUnk
);
```

```csharp
int GetEngineInterface( 
   out object ppUnk
);
```

## <a name="parameters"></a>Parametry
`ppUnk`\
[out] Zwraca `IUnknown` obiekt reprezentuje aparat debugowania (DE) i może być odpytywany dla innych prawidłowe interfejsu skojarzonego z URZ (na przykład [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) lub [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)).

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wynikowy interfejsu powinny stosowana z rozwagą, ponieważ wywołanie za pośrednictwem interfejsów pobierane z tej metody zmierzone przetwarzania Menedżer debugowania sesji i może spowodować SDM, jakim jest w niepoprawnym stanie lub generowanie błędów podczas debugowania.

## <a name="see-also"></a>Zobacz także
- [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)