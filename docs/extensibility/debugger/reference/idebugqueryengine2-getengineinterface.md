---
title: IDebugQueryEngine2::GetEngineInterface | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2::GetEngineInterface
helpviewer_keywords:
- IDebugQueryEngine2::GetEngineInterface
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 82f3214783a35e668bf3164c8659f60f863e9a43
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720665"
---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
Pobiera niestandardowy aparat debugowania (DE) interfejs.

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
[na zewnątrz] Zwraca `IUnknown` obiekt reprezentuje aparat debugowania (DE) i który może być wyszukiwany dla innego prawidłowego interfejsu skojarzonego z DE (na przykład [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) lub [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)).

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Wynikowy interfejs powinien być używany z ostrożnością, ponieważ wywołanie za pośrednictwem interfejsów pobranych z tej metody omija przetwarzanie menedżera debugowania sesji i może spowodować, że moduł SDM stanie się złym stanem lub generuje błędy podczas debugowania.

## <a name="see-also"></a>Zobacz też
- [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
