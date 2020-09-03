---
title: 'IDebugQueryEngine2:: GetEngineInterface | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80720665"
---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
Pobiera niestandardowy interfejs aparatu debugowania.

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
określoną Zwraca `IUnknown` obiekt reprezentujący aparat debugowania (de), który może być badany innym prawidłowym interfejsem skojarzonym z de (na przykład [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) lub [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)).

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Interfejs wynikowy powinien być używany z zachowaniem, ponieważ wywoływanie przez interfejsy pobrane z tej metody powoduje obejście przetwarzania Menedżera debugowania sesji i może skutkować nieprawidłowym stanem modelu SDM lub wygenerowaniem błędów podczas debugowania.

## <a name="see-also"></a>Zobacz też
- [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
