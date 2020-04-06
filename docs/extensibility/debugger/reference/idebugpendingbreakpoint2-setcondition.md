---
title: IDebugPendingBreakpoint2::SetCondition | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugPendingBreakpoint2::SetCondition method
ms.assetid: 0534224f-654f-4862-bc4d-a9a81a5f8899
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4683d944f2489b8b21ff545c86e3d867283d644a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725724"
---
# <a name="idebugpendingbreakpoint2setcondition"></a>IDebugPendingBreakpoint2::SetCondition
Ustawia lub zmienia warunek skojarzony z oczekującym punktem przerwania.

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
[w] Struktura [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) określająca warunek do skonfigurowania.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Każdy warunek, który był wcześniej skojarzony z oczekującym punktem przerwania zostanie utracony. Wszystkie punkty przerwania powiązane z tego oczekującego punktu przerwania `bpCondition` są wywoływane, aby ustawić ich warunek na wartość określoną w parametrze.

## <a name="see-also"></a>Zobacz też
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
