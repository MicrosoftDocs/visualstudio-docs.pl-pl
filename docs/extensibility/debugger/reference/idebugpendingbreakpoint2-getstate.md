---
title: IDebugPendingBreakpoint2::GetState | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::GetState
helpviewer_keywords:
- GetState method
- IDebugPendingBreakpoint2::GetState method
ms.assetid: e88d543f-2e83-4ba7-86ca-f874e39955ff
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 84ee5c48a74fa9ed707cc55be3cbc1ab49940552
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347779"
---
# <a name="idebugpendingbreakpoint2getstate"></a>IDebugPendingBreakpoint2::GetState
Pobiera stan oczekujący punkt przerwania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetState( 
   PENDING_BP_STATE_INFO* pState
);
```

```csharp
int GetState( 
   PENDING_BP_STATE_INFO[] pState
);
```

## <a name="parameters"></a>Parametry
`pState`\
[out w] A [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) strukturę, która jest wypełniane opis oczekujących punktów przerwania.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)