---
title: IDebugPendingBreakpoint2::SetCondition | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugPendingBreakpoint2::SetCondition method
ms.assetid: 0534224f-654f-4862-bc4d-a9a81a5f8899
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1a71e22d118b64e15bb9da15b2f9152a90440f1a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347661"
---
# <a name="idebugpendingbreakpoint2setcondition"></a>IDebugPendingBreakpoint2::SetCondition
Ustawia lub zmienia warunek skojarzony z Oczekujący punkt przerwania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT SetCondition( 
   BP_CONDITION bpCondition
);
```

```csharp
int SetCondition( 
   BP_CONDITION bpCondition
);
```

## <a name="parameters"></a>Parametry
`bpCondition`\
[in] A [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) strukturę, która określa warunek, którego chcesz ustawić.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Dowolny warunek, który był wcześniej skojarzony z Oczekujący punkt przerwania zostaną utracone. Wszystkie punkty przerwania, powiązany z tym oczekujących punktów przerwania są wywoływane w celu ich warunek ustawiony na wartość określoną w `bpCondition` parametru.

## <a name="see-also"></a>Zobacz także
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)